
(DAW) Despliegue de Aplicaciones Web (2º DAW). UD06. Verificación y Validación

¡Bienvenidos a este nuevo vídeo de clase! 🎙️ Soy el profesor José Luis González y hoy vamos a hacer algo diferente. En lugar de una clase de código pura, en este vídeo nos enfocaremos en la calidad y el despliegue de aplicaciones web, centrándonos en el "Final Boss" de la unidad: Servicios de Red, Infraestructura y Orquestación.

Si quieres entender cómo encajan todas las piezas (desde dejar de usar IPs volátiles hasta orquestar un entorno completo donde la infraestructura se valida a sí misma), este vídeo es tu guía definitiva para dominar esta parte de la Unidad 06.

En este vídeo de clase analizamos:

DNS con BIND9: Por qué en entornos profesionales la volatilidad de las IPs es un problema y cómo el DNS nos permite crear mapas de red estables mediante registros A, CNAME y PTR.

Laboratorio de Redes: Cómo levantar un servidor DNS real utilizando Docker y cómo validar nuestra configuración con herramientas de diagnóstico como dig, nslookup y host.

Servicios de Directorio (LDAP): El papel de OpenLDAP en la gestión de identidades. Entenderemos el DIT (Directory Information Tree) y por qué es superior a una tabla SQL para la autenticación centralizada.

Orquestación con Docker Compose: Cómo diseñar redes aisladas y personalizadas (IPAM) para que nuestros servicios web, bases de datos y servidores de identidad convivan de forma segura.

El Escenario Integral: Análisis de una arquitectura completa que incluye Frontend, Backend, PostgreSQL, LDAP y DNS funcionando en armonía.

Validación Automática del Despliegue: La implementación de un servicio 'tester' con Playwright dentro de nuestro flujo de orquestación, garantizando que el sistema solo se considera "desplegado" si supera todas las pruebas de salud.

Este vídeo es ideal para visualizarlo mientras configuras tus archivos de orquestación, vas en el transporte público o simplemente quieres dar el paso definitivo de desarrollador a experto en despliegue e infraestructura.

Recursos y Enlaces del Vídeo 
🔗 Manual Completo de la Unidad 06 (GitHub): 
https://github.com/joseluisgs/DespliegueAplicacionesWeb-06-2025-2026

Si quieres convertirte en un experto, ya sabes: like y ¡suscríbete para seguir codificando un montón! ¡Nos vemos en el próximo deploy!