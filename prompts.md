Unidad 06, centrándose exclusivamente en Servicios de Red, Infraestructura y Orquestación.

IMPORTANTE - Presentación y Cierre:

El vídeo debe comenzar exactamente con: "¡Bienvenidos a este nuevo vídeo de clase! Soy el profesor José Luis González y hoy vamos a hacer algo diferente. En lugar de una clase de código pura, en este vídeo nos enfocaremos en la calidad y el despliegue de aplicaciones web, centrándonos en el 'Final Boss' de la unidad: los Servicios de Red, la Infraestructura y la Orquestación."

El vídeo debe terminar exactamente con: "Si quieres convertirte en un experto, ya sabes: like y ¡suscríbete para seguir codificando un montón! ¡Nos vemos en el próximo deploy!"

Directrices de Contenido (Basado específicamente en el documento 06-Servicios-Red-Infraestructura.md):

DNS con BIND9: Explicad por qué en despliegues profesionales no usamos IPs fijas debido a su volatilidad. Analizad la jerarquía DNS y los tipos de registros esenciales (A, CNAME, PTR, MX).

Laboratorio BIND9: Comentad cómo levantar un servidor DNS real en Docker y cómo realizar validaciones profesionales usando herramientas como dig, nslookup y host.

Servicios de Directorio (LDAP): Debatid por qué usamos LDAP para la identidad y no una simple tabla SQL. Explicad conceptos clave como el DIT (Directory Information Tree), los RDN y los Attributes.

Orquestación con Docker Compose: Analizad el diseño de redes aisladas. Explicad el uso de subredes personalizadas (IPAM) para garantizar que servicios críticos como el DNS tengan IPs predecibles dentro de la red interna de Docker.

El Escenario Integral: Describid la arquitectura completa: un Frontend en React, un Backend en Java/C#, una base de datos PostgreSQL, un servidor OpenLDAP y un DNS BIND9, todos conviviendo en armonía.

Validación Automática del Despliegue: Explicad la genialidad de incluir un servicio 'tester' (Playwright) dentro del docker-compose.yml que solo se ejecuta cuando el backend está 'healthy', certificando que toda la infraestructura funciona antes de dar el despliegue por bueno.

Tono y Estilo:

Tono de Masterclass técnica dinámica, simulando que estáis dibujando diagramas de red y configurando ficheros YAML mientras habláis.

Usad terminología técnica precisa: IP volatility, reverse lookup, DIT, entry, orchestration, healthcheck.

Recalcad que este es el enfoque de José Luis González para que los alumnos entiendan que un desarrollador de DAW también debe dominar la infraestructura donde vive su código."

---