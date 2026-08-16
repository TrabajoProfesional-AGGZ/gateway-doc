---
layout: default
title: Inicio
nav_order: 1
description: "Documentacion del API Gateway de SocioUnido"
---

# Gateway

Gateway unificado para el enrutamiento y agregación de los microservicios de "SocioUnido".

## Utilidad y funcionalidad

El gateway está diseñado para manejar las siguientes responsabilidades clave:

* **Punto único de entrada (Single Entry Point):** Centraliza todas las peticiones de las aplicaciones cliente (web y móvil) y las enruta dinámicamente hacia los microservicios correspondientes (Auth, Club, Pagos, Accesos, Analíticas).
* **Seguridad y control de tráfico:** Actúa como la primera barrera de defensa de la infraestructura, gestionando políticas de CORS, rate limiting (limitación de peticiones) y validación de tokens antes de que el tráfico golpee los servicios internos.
* **Agregación y optimización (Backend for Frontend):** Permite componer múltiples respuestas de distintos microservicios en una sola respuesta unificada hacia el cliente, reduciendo la latencia y el número de llamadas de red.

## ¿Qué vas a encontrar en esta página?

A continuación, se detalla toda la información técnica, arquitectónica y organizativa sobre esta implementación en particular:

* 🔀 **[Enrutamiento y políticas](enrutamiento.html):** Detalle de cómo KrakenD mapea las peticiones externas hacia los microservicios internos y las políticas de seguridad aplicadas.
* 🛠️ **[Justificación tecnológica](justificacion.html):** El porqué de los lenguajes y frameworks elegidos, nuestro pipeline de CI/CD, la estrategia de testing y validación.
* 🏗️ **[Arquitectura y diagramas](diagramas.html):** Representación visual de la arquitectura del gateway utilizando los modelos C3/C4.
* 📊 **[Métricas de la implementación](metricas.html):** Estadísticas del desarrollo, cantidad de commits, Pull Requests y distribución del trabajo en el equipo.
