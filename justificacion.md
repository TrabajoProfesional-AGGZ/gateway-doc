---
layout: default
title: Justificación tecnológica
nav_order: 3
---

# 🛠️ Justificación tecnológica

En esta sección documentamos las decisiones técnicas tomadas para la construcción del gateway, asegurando que cada herramienta elegida aporte valor real al desarrollo y mantenimiento del producto.

## Lenguajes y frameworks

Para este componente crítico, la selección tecnológica priorizó el rendimiento extremo, la concurrencia y la facilidad de configuración:

* **KrakenD (API Gateway):** Elegimos KrakenD por ser un gateway *stateless* (sin estado) de altísimo rendimiento. Al ser puramente declarativo y manejarse mediante archivos de configuración (usando plantillas `.tmpl` para modularizar por dominios como `pagos`, `auth`, `club`, etc.), nos permite escalar linealmente sin cuellos de botella en bases de datos.
* **Go (Underlying):** Al estar KrakenD construido en Go, heredamos sus capacidades de concurrencia masiva, permitiendo que el gateway maneje miles de peticiones por segundo con un consumo de recursos mínimo.
* **Docker y Docker Compose:** La contenerización es indispensable en nuestra arquitectura. Nos permite empaquetar la configuración consolidada de KrakenD y garantizar la paridad exacta entre entornos (desarrollo, *staging* y producción).

## Integración y despliegue continuo (CI/CD)

La implementación de pipelines de CI/CD es fundamental en el gateway para garantizar entregas ágiles y seguras. Nos permite automatizar la validación de la sintaxis de las plantillas y el despliegue a los distintos entornos, reduciendo el error humano y acelerando el *time-to-market*.

## Pruebas y validación de configuración

Para asegurar la robustez y estabilidad de las reglas de enrutamiento, mantenemos un estándar estricto de calidad:

* Se realizan pruebas de integración para verificar que la inyección de variables y la compilación de los archivos `.tmpl` (partials) resulten en una configuración JSON válida para el motor.
* Las configuraciones son validadas automáticamente en cada Pull Request mediante nuestro pipeline (GitHub Actions) antes de cualquier fusión a la rama principal.

## Documentación integral

Utilizamos **JustTheDocs** para mantener esta documentación viva, versionada junto con el código y fácilmente accesible para cualquier miembro del equipo. Esto centraliza el conocimiento y reduce los cuellos de botella en la comunicación.
