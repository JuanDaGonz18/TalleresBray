# Parte 2 – Análisis de la Arquitectura de Infraestructura

## 1. Descripción de la arquitectura

El sistema presentado sigue una arquitectura por capas diseñada para soportar una plataforma de rastreo y gestión de rutas en tiempo real.

La primera capa es la **Client Layer**, donde los usuarios interactúan con el sistema a través de una **aplicación móvil** y una **plataforma web administrativa**. Estas interfaces permiten consultar rutas, realizar seguimiento de entregas y gestionar información operativa.

Las solicitudes generadas por los clientes pasan a la **Edge / Access Layer**, donde se encuentra un **Load Balancer** que distribuye el tráfico entrante entre los servicios disponibles. Posteriormente las peticiones son enviadas a un **API Gateway en la nube**, el cual centraliza el acceso a los microservicios del sistema y maneja autenticación, control de tráfico y direccionamiento de solicitudes.

En la **Application Layer** el sistema se ejecuta mediante contenedores Docker que contienen distintos microservicios. Entre ellos se encuentran:

- **Route Engine**: encargado de calcular rutas y optimizar recorridos.
- **Tracking Service**: encargado de procesar y actualizar la ubicación de los vehículos en tiempo real.

Estos servicios están diseñados para escalar horizontalmente, lo que permite agregar más contenedores cuando aumenta la carga del sistema.

La siguiente capa es la **Data Layer**, donde se encuentra la base de datos principal alojada en un servidor regional. Esta base de datos mantiene la información operativa del sistema y cuenta con un mecanismo de **replicación hacia una base de datos de lectura (Read Replica)** para mejorar el rendimiento de consultas.

Finalmente, el sistema se integra con **External Services**, como un servicio de notificaciones que permite enviar mensajes por SMS, correo electrónico o notificaciones push a los usuarios.

Además, se incluye un sistema de **Monitoring & Alerts** utilizando herramientas como **Prometheus y Grafana**, que permiten supervisar el rendimiento del sistema y generar alertas cuando se detectan fallas o comportamientos anómalos.

---

# 2. Identificación de posibles cuellos de botella

Un **cuello de botella** es el componente que limita el rendimiento total del sistema, ya que su capacidad de procesamiento es menor que la del resto de componentes.

En el diagrama se pueden identificar tres posibles cuellos de botella.

---

## 2.1 Base de datos primaria

El primer cuello de botella potencial se encuentra en la **Primary Database**.

El sistema de rastreo genera una gran cantidad de consultas en tiempo real provenientes del servicio de tracking y del motor de rutas. Si todas estas solicitudes se concentran en la base de datos principal, esta puede saturarse rápidamente.

Esto es especialmente crítico durante:

- picos de tráfico
- consultas simultáneas de ubicación
- cargas estacionales del sistema

Aunque existe una réplica de lectura, muchas operaciones siguen dependiendo de la base de datos principal para escritura, lo que puede generar un punto único de congestión.

---

## 2.2 API Gateway

Otro posible cuello de botella es el **API Gateway**, ya que todo el tráfico del sistema pasa por este componente.

Si el volumen de solicitudes aumenta significativamente, el gateway puede experimentar:

- latencia
- saturación de conexiones
- limitaciones en el manejo de requests concurrentes

Esto afectaría directamente el acceso a todos los microservicios del sistema.

---

## 2.3 Servicio de Tracking en tiempo real

El **Tracking Service** también representa un componente crítico, ya que debe procesar constantemente actualizaciones de ubicación provenientes de múltiples dispositivos.

Este servicio puede recibir:

- miles de actualizaciones por minuto
- consultas de usuarios
- procesamiento de eventos de localización

Si el sistema no escala correctamente este microservicio, podría convertirse en un punto de saturación que ralentice la actualización de datos en el sistema.

---

# 3. Propuestas de mejora en la arquitectura

Para mejorar la resiliencia y escalabilidad del sistema se pueden implementar varias mejoras.

---

## 3.1 Implementar caching

Se puede agregar una capa de **cache (Redis o Memcached)** entre los servicios de aplicación y la base de datos.

Esto permitiría:

- reducir consultas repetitivas
- disminuir la carga sobre la base de datos
- mejorar la latencia del sistema

Especialmente para consultas frecuentes como:

- estado de rutas
- última ubicación conocida
- información de vehículos.

---

## 3.2 Escalamiento automático de microservicios

El sistema podría implementar **auto-scaling en contenedores**, permitiendo crear nuevas instancias de los servicios cuando la carga aumenta.

Esto ayudaría principalmente a:

- **Route Engine**
- **Tracking Service**

De esta forma el sistema puede manejar picos de tráfico sin degradar el rendimiento.

---

## 3.3 Separación de base de datos para lectura y escritura

Se recomienda implementar una arquitectura **Read/Write Split**, donde:

- la base principal maneje **escrituras**
- las réplicas manejen **consultas**

Esto reduce significativamente la carga sobre el servidor principal y mejora la escalabilidad del sistema.

---

## 3.4 Uso de colas de mensajería

Para desacoplar los servicios y manejar grandes volúmenes de eventos de tracking se podría integrar un sistema de mensajería como:

- Kafka
- RabbitMQ

Esto permitiría procesar actualizaciones de ubicación de forma **asíncrona** y evitar saturar los servicios principales.

---

# 4. Conclusión

La arquitectura propuesta presenta una estructura moderna basada en microservicios y contenedores, lo que permite escalabilidad y modularidad. Sin embargo, existen componentes críticos que pueden convertirse en cuellos de botella, especialmente la **base de datos principal**, el **API Gateway** y el **servicio de tracking en tiempo real**.

Implementando mecanismos como **caching, escalamiento automático, separación de bases de datos y sistemas de mensajería**, el sistema puede mejorar significativamente su capacidad de respuesta y resiliencia frente a altas cargas de trabajo.
