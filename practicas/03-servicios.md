# Práctica 03: Infraestructura de Servicios de Red (DNS, LDAP y Proxy)

## 🏢 Contexto: El ecosistema digital del IES Luis Vives

El IES Luis Vives quiere modernizar su infraestructura de red interna para los ciclos de informática. El objetivo es desplegar un sistema basado en **contenedores** que permita gestionar la navegación, el balanceo de carga y la autenticación centralizada de alumnos.

## 🎯 Objetivos de la práctica

1.  Configurar un servidor **DNS (BIND9)** para resolver nombres de dominio locales.
2.  Desplegar un directorio **LDAP (OpenLDAP)** para gestionar las identidades.
3.  Implementar un **Proxy Inverso (Nginx)** como puerta de entrada única.
4.  Configurar servidores backend con diferentes tecnologías (**Nginx** y **Apache**).
5.  Asegurar rutas específicas mediante **autenticación LDAP** a nivel de servidor web.

---

## 📐 Arquitectura del Sistema

Debes recrear el siguiente esquema de red en un único `docker-compose.yml`:

1.  **DNS (`ns1.iesluisvives.org`)**: El servidor que resolverá todas las peticiones.
2.  **Proxy Inverso (Nginx)**: Escucha en `iesluisvives.org`.
    *   Ruta `/daw` -> Redirige a un contenedor **Nginx** (Servidor DAW).
    *   Ruta `/dam` -> Redirige a un contenedor **Apache** (Servidor DAM).
3.  **Seguridad (LDAP)**:
    *   Ruta `/daw/calificaciones` -> Solo accesible si el usuario se autentica contra LDAP.
    *   Ruta `/dam/calificaciones` -> Solo accesible si el usuario se autentica contra LDAP.

---

## 📝 Tareas a realizar

### 1. Servidor DNS (BIND9)
Configura una zona para `iesluisvives.org`. El servidor debe resolver:
*   `iesluisvives.org` -> IP del Proxy.
*   `ldap.iesluisvives.org` -> IP del servidor LDAP.
*   `dns.iesluisvives.org` -> IP del propio servidor DNS.

### 2. Servidor de Directorio (OpenLDAP + phpLDAPadmin)
*   Crea una unidad organizativa `ou=users,dc=iesluisvives,dc=org`.
*   Crea un usuario de prueba: `alumno1` / `LuisVives123!`.
*   Usa `phpLDAPadmin` para verificar que los datos se han insertado correctamente.

### 3. Backend DAW (Nginx)
Un servidor Nginx simple que sirva un HTML básico diciendo "Bienvenido a DAW". Debe tener una carpeta interna `/calificaciones` con un archivo `index.html`.

### 4. Backend DAM (Apache)
Un servidor Apache que sirva un HTML básico diciendo "Bienvenido a DAM". Debe tener una carpeta interna `/calificaciones` con un archivo `index.html`.

### 5. Proxy Inverso y Auth LDAP
Esta es la parte crítica. Debes configurar el Nginx principal para:
1.  Hacer `proxy_pass` a los backends según la URL.
2.  Para las rutas `/calificaciones`, utilizar el módulo de autenticación LDAP (en Apache se hace con `mod_authnz_ldap` y en Nginx se puede gestionar desde el proxy o el backend).
    *   *Pista*: Para el backend de Apache, usa un archivo `.htaccess` o configuración de sitio para requerir el usuario de LDAP.

---

## 📦 Entregables

Debes entregar una carpeta con la siguiente estructura:

```text
📁 practica-03-servicios/
├── 📄 docker-compose.yml
├── 📁 dns/
│   ├── 📄 named.conf.local
│   └── 📄 db.iesluisvives.org
├── 📁 ldap/
│   └── 📄 users.ldif
├── 📁 nginx-proxy/
│   └── 📄 default.conf
├── 📁 backend-daw/
│   └── 📄 index.html
└── 📁 backend-dam/
    ├── 📄 index.html
    └── 📄 .htaccess (o config de Apache)
```

## 🧪 Verificación

Para dar por válida la práctica, el profesor ejecutará:
1.  `docker-compose up -d`
2.  Desde el navegador del host (configurando el DNS o usando `/etc/hosts`):
    *   Acceso a `http://iesluisvives.org/daw` -> OK.
    *   Acceso a `http://iesluisvives.org/dam` -> OK.
    *   Acceso a `http://iesluisvives.org/daw/calificaciones` -> **Debe saltar ventana de login**. Al introducir `alumno1`, debe dejar pasar.

---

## 🎯 Criterios de Evaluación (10 puntos)

*   **DNS (2p)**: Resolución correcta de todos los nombres.
*   **LDAP (2p)**: Estructura de usuarios correcta y persistente.
*   **Proxy Inverso (2p)**: Redirección correcta de `/daw` y `/dam`.
*   **Auth LDAP (3p)**: Bloqueo efectivo de las rutas de calificaciones y validación correcta contra el directorio.
*   **Limpieza y Docker (1p)**: Uso de redes personalizadas en Docker, volúmenes y código limpio.
