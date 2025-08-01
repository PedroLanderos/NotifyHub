# NotifyHub

**NotifyHub** es un microservicio de notificaciones desarrollado con **.NET 8**, que actualmente implementa el envío de notificaciones por **correo electrónico** a través de un sistema basado en **RabbitMQ**. Su arquitectura está diseñada para ser fácilmente extensible a otros canales de notificación (SMS, push, etc.).

Este servicio forma parte de una arquitectura de **microservicios distribuida**, consumiendo mensajes desde una cola y ejecutando la lógica correspondiente para enviar notificaciones.

---

## 🚀 Características

- Escucha eventos de notificación desde una cola RabbitMQ.
- Procesa y deserializa mensajes en formato JSON.
- Envía notificaciones por correo electrónico.
- Sistema extensible para múltiples tipos de notificación.
- Implementado como `BackgroundService` en .NET 8.
- Manejo de errores y reintentos mediante `BasicNack`.

---

## 🛠️ Tecnologías utilizadas

- [.NET 8 Worker Service](https://learn.microsoft.com/en-us/dotnet/core/extensions/workers)
- [RabbitMQ.Client](https://www.nuget.org/packages/RabbitMQ.Client)
- Microsoft.Extensions.Hosting / Configuration / Logging
- JSON serialization/deserialization (`System.Text.Json`)



