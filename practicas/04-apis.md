# Práctica 04: Automatización de Pruebas de API con Postman y Newman

## 🔗 Recursos de la API
*   **Base URL**: `https://jsonplaceholder.typicode.com`
*   **Endpoint Usuarios**: `https://jsonplaceholder.typicode.com/users`
*   **Endpoint Publicaciones**: `https://jsonplaceholder.typicode.com/posts`

## 📖 Contexto: Validación de Servicios Externos (CRUD Completo)

Como especialistas en Despliegue, debemos asegurar que las APIs que consumimos o desplegamos cumplen con el contrato técnico. En esta práctica validaremos el ciclo de vida completo de los recursos **Usuarios** y **Publicaciones** en **JSONPlaceholder**.

## 🎯 Objetivos de la práctica

1.  Implementar el flujo **CRUD completo** (Create, Read, Update, Patch, Delete).
2.  Validar la diferencia entre **PUT** (reemplazo total) y **PATCH** (modificación parcial).
3.  Gestionar la persistencia simulada mediante variables de entorno.
4.  Automatizar con **Newman** y **Docker** visualizando la salida por consola.

---

## 🛠️ Tareas a realizar

### 1. Estructura de la Colección
Crea una colección llamada `API-Expert-Validation` con la siguiente estructura de carpetas y peticiones:

#### Carpeta A: Gestión de Usuarios (`/users`)
*   **POST Create**: Crear un usuario. Guardar el `id` en la variable `user_id`.
*   **GET All**: Listar todos los usuarios. Validar que el array no esté vacío.
*   **GET by ID**: Obtener el usuario creado usando `{{user_id}}`.
*   **PUT Update**: Actualizar todos los campos del usuario `{{user_id}}`.
*   **PATCH Partial**: Actualizar solo el campo `phone` del usuario `{{user_id}}`.
*   **DELETE**: Eliminar el usuario `{{user_id}}`.

#### Carpeta B: Gestión de Publicaciones (`/posts`)
*   **POST Create**: Crear un post vinculado al `user_id`. Guardar el `id` en `post_id`.
*   **GET by ID**: Obtener el post `{{post_id}}`.
*   **PUT Update**: Cambiar el `title` y el `body` del post.
*   **DELETE**: Eliminar el post.

### 2. Validaciones Obligatorias (Scripts)
Cada petición debe incluir:
1.  **Código de Estado**: 200, 201 o 204 según corresponda.
2.  **Tiempo de respuesta**: Menor a 1000ms.
3.  **Integridad de Datos**: Validar que el ID devuelto coincide con el solicitado o que los campos actualizados tienen el valor correcto.

### 3. Automatización
Debes preparar un entorno Docker para ejecutar Newman de forma que la salida sea legible en la terminal del host.

---

## 📦 Entregables

```text
📁 practica-04-apis/
├── 📄 API-Expert-Validation.postman_collection.json
├── 📄 Remote.postman_environment.json
├── 📄 run-tests.sh (Script para lanzar Newman en Docker)
└── 📄 README.md (Instrucciones)
```

## 🎯 Criterios de Evaluación

*   **CRUD Completo (4p)**: Implementación de todos los verbos HTTP solicitados.
*   **Lógica de Variables (2p)**: Paso de IDs entre peticiones de forma automática.
*   **Scripts de Validación (2p)**: Pruebas robustas y aserciones de contenido.
*   **Salida Docker (2p)**: El script permite ver el reporte de Newman en la consola.