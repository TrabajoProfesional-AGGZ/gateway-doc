---
layout: default
title: Enrutamiento y políticas
nav_order: 2
---

# 🔀 Enrutamiento y políticas

A diferencia de los microservicios tradicionales que exponen un contrato interactivo (Swagger/OpenAPI), nuestro API Gateway está construido sobre **KrakenD**. Por lo tanto, los "endpoints" en esta capa son en realidad **reglas de enrutamiento** y composición de peticiones.

## Configuración por dominios (Partials)

Para mantener el gateway escalable, ordenado y facilitar el trabajo en equipo, la configuración no reside en un único archivo monolítico. Utilizamos el sistema de plantillas de KrakenD (`.tmpl`) para modularizar las rutas por dominio de negocio. 

Actualmente, el enrutamiento está dividido en los siguientes módulos:

* 🚪 **Accesos (`accesos.tmpl`):** Manejo de las reglas de ingreso físico o lógico, control de molinetes y validación de carnets.
* 📈 **Analíticas (`analiticas.tmpl`):** Conexión con los servicios de recolección de datos, métricas y el propio HealthChecker.
* 🤖 **Asistente virtual (`bot.tmpl`):** Puntos de entrada para la interacción con el motor de inteligencia artificial, el procesamiento de lenguaje natural (PLN) y la gestión de consultas automatizadas por parte de los usuarios.
* 🔐 **Autenticación (`auth.tmpl`):** Rutas destinadas a la gestión de identidad, login, registro y emisión/validación de tokens.
* ⚽ **Club (`club.tmpl`):** Enrutamiento para la gestión de socios, actividades y entidades principales de la institución.
* 💳 **Pagos (`pagos.tmpl`):** Puntos de entrada para el procesamiento de transacciones, cuotas y validación de pagos.

## Políticas aplicadas en las rutas

Al pasar por este Gateway, las peticiones externas son sometidas a las siguientes políticas estructurales antes de alcanzar los microservicios internos:

1. **Validación de token (JWT):** Las rutas protegidas verifican la firma y expiración del token del usuario directamente en el Gateway. Si el token es inválido, la petición se rechaza inmediatamente sin consumir recursos de los microservicios.
2. **CORS (Cross-Origin Resource Sharing):** Configuración centralizada para permitir el acceso seguro desde el Front-End web y la aplicación móvil de SocioUnido.
3. **Control de Timeouts:** Límites estrictos de tiempo de respuesta para evitar que un microservicio degradado o caído bloquee toda la plataforma web o sature la red.
4. **Endpoint Aggregation:** En rutas específicas, el Gateway se encarga de consultar a múltiples microservicios en paralelo y consolidar los datos en un único JSON de respuesta para el cliente, reduciendo la latencia y la carga de red.
