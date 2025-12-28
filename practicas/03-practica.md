# Práctica Integradora

- [Práctica Integradora](#práctica-integradora)
    - [Introducción al Proyecto Final](#introducción-al-proyecto-final)
  - [📋 ENUNCIADO DE LA PRÁCTICA](#-enunciado-de-la-práctica)
    - [Sistema de Gestión de Biblioteca Universitaria](#sistema-de-gestión-de-biblioteca-universitaria)
    - [🎯 Objetivos del Proyecto](#-objetivos-del-proyecto)
    - [📊 Modelo de Datos](#-modelo-de-datos)
      - [Entidades Principales](#entidades-principales)
      - [Relaciones](#relaciones)
    - [👥 Roles y Permisos](#-roles-y-permisos)
      - [Estructura LDAP Requerida](#estructura-ldap-requerida)
      - [Permisos por Rol](#permisos-por-rol)
    - [🔧 Requisitos Técnicos](#-requisitos-técnicos)
      - [Backend API REST](#backend-api-rest)
      - [Base de Datos](#base-de-datos)
      - [Frontend](#frontend)
      - [Infraestructura LDAP](#infraestructura-ldap)
      - [Infraestructura DNS](#infraestructura-dns)
    - [🧪 Requisitos de Testing](#-requisitos-de-testing)
      - [1. Tests Unitarios](#1-tests-unitarios)
      - [2. Tests de Integración (Testcontainers)](#2-tests-de-integración-testcontainers)
      - [3. Tests de API (Postman/Newman)](#3-tests-de-api-postmannewman)
      - [4. Tests E2E (Cypress)](#4-tests-e2e-cypress)
    - [📦 Docker Compose](#-docker-compose)
    - [📝 Entregables](#-entregables)
      - [1. Código Fuente](#1-código-fuente)
      - [2. Documentación](#2-documentación)
      - [3. Tests](#3-tests)
      - [4. Infraestructura](#4-infraestructura)
      - [5. Reportes](#5-reportes)
    - [🎯 Criterios de Evaluación](#-criterios-de-evaluación)
      - [Desglose de "Testing" (30%)](#desglose-de-testing-30)
    - [💡 Consejos y Recomendaciones](#-consejos-y-recomendaciones)
      - [Planificación](#planificación)
      - [Testing](#testing)
      - [Errores Comunes a Evitar](#errores-comunes-a-evitar)


### Introducción al Proyecto Final

Esta práctica integradora consolidará **todos los conocimientos** adquiridos en la unidad. Los alumnos desarrollarán un sistema completo de gestión con autenticación centralizada, implementando tests en todos los niveles y desplegándolo con Docker Compose. 

💡 **Nota del Profesor**:  Esta práctica simula un proyecto real de empresa.  No es un ejercicio trivial:  requiere planificación, investigación y resolución de problemas.  Trabajad de forma incremental, probando cada componente antes de integrarlo.  El objetivo es que experimentéis el ciclo completo de desarrollo → testing → despliegue. 

---

## 📋 ENUNCIADO DE LA PRÁCTICA

### Sistema de Gestión de Biblioteca Universitaria

**Contexto:**

La Universidad necesita modernizar su sistema de gestión de biblioteca.  El nuevo sistema debe permitir que estudiantes y profesores busquen libros, realicen reservas y gestionen préstamos.  El personal bibliotecario necesita funciones administrativas avanzadas.

La autenticación debe integrarse con el directorio LDAP existente de la universidad, que ya contiene todos los usuarios (estudiantes, profesores, personal administrativo).

---

### 🎯 Objetivos del Proyecto

Desarrollar e implementar un sistema completo que incluya:

1. **Backend API REST** (Java con Spring Boot **O** C# con ASP.NET Core)
2. **Base de datos relacional** (PostgreSQL)
3. **Autenticación LDAP** con gestión de roles
4. **Frontend web** (React, Vue, Angular o similar)
5. **Infraestructura de servicios** (DNS, LDAP)
6. **Suite completa de tests**: 
   - Tests unitarios (JUnit/NUnit)
   - Tests de integración (Testcontainers)
   - Tests de API (Postman/Newman)
   - Tests E2E (Cypress)
7. **Despliegue orquestado** con Docker Compose

---

### 📊 Modelo de Datos

#### Entidades Principales

**1. Book (Libro)**
```
- id: Long (PK)
- isbn: String (único, formato ISBN-13)
- title: String
- author: String
- publisher: String
- publicationYear: Integer
- category: String (Informática, Matemáticas, Física, Literatura, etc.)
- totalCopies: Integer
- availableCopies: Integer
- location: String (estantería/sección)
- description: Text
- coverImageUrl: String (opcional)
- createdAt: DateTime
- updatedAt: DateTime
```

**2. Loan (Préstamo)**
```
- id: Long (PK)
- bookId: Long (FK → Book)
- username: String (del usuario LDAP)
- loanDate: DateTime
- dueDate:  DateTime (15 días desde loanDate para estudiantes, 30 para profesores)
- returnDate: DateTime (nullable)
- status: Enum (ACTIVE, RETURNED, OVERDUE)
- renewalCount: Integer (máximo 2 renovaciones)
- notes: String (opcional)
```

**3. Reservation (Reserva)**
```
- id: Long (PK)
- bookId: Long (FK → Book)
- username: String
- reservationDate: DateTime
- expirationDate: DateTime (7 días desde reservationDate)
- status: Enum (PENDING, FULFILLED, CANCELLED, EXPIRED)
- notificationSent: Boolean
```

**4. Review (Reseña)**
```
- id: Long (PK)
- bookId: Long (FK → Book)
- username: String
- rating: Integer (1-5)
- comment: Text
- createdAt: DateTime
- helpful: Integer (contador de "útil")
```

#### Relaciones

- Un **Book** puede tener múltiples **Loans** (histórico)
- Un **Book** puede tener múltiples **Reservations**
- Un **Book** puede tener múltiples **Reviews**
- Un usuario (identificado por username de LDAP) puede tener múltiples préstamos y reservas

---

### 👥 Roles y Permisos

#### Estructura LDAP Requerida

```
dc=universidad,dc=local
│
├── ou=users
│   ├── ou=students (uid=estudiante1, uid=estudiante2, ...)
│   ├── ou=professors (uid=profesor1, uid=profesor2, ...)
│   └── ou=staff (uid=bibliotecario1, ...)
│
└── ou=groups
    ├── cn=students
    ├── cn=professors
    ├── cn=librarians
    └── cn=admins
```

#### Permisos por Rol

| Funcionalidad           | Student | Professor | Librarian | Admin |
| ----------------------- | ------- | --------- | --------- | ----- |
| Buscar libros           | ✅       | ✅         | ✅         | ✅     |
| Ver detalles de libro   | ✅       | ✅         | ✅         | ✅     |
| Reservar libro          | ✅       | ✅         | ❌         | ❌     |
| Ver mis préstamos       | ✅       | ✅         | ❌         | ❌     |
| Renovar préstamo        | ✅       | ✅         | ❌         | ❌     |
| Escribir reseña         | ✅       | ✅         | ❌         | ❌     |
| Realizar préstamo       | ❌       | ❌         | ✅         | ✅     |
| Devolver libro          | ❌       | ❌         | ✅         | ✅     |
| Gestionar libros (CRUD) | ❌       | ❌         | ✅         | ✅     |
| Ver todos los préstamos | ❌       | ❌         | ✅         | ✅     |
| Gestionar usuarios LDAP | ❌       | ❌         | ❌         | ✅     |
| Ver estadísticas        | ❌       | ❌         | ✅         | ✅     |

**Reglas de Negocio:**

- **Estudiantes**:  Máximo 3 préstamos simultáneos, 15 días de plazo
- **Profesores**:  Máximo 5 préstamos simultáneos, 30 días de plazo
- Un libro **no puede reservarse** si hay copias disponibles
- Las reservas **expiran** automáticamente después de 7 días
- Los préstamos pueden **renovarse máximo 2 veces** (si no hay reservas pendientes)
- Penalización:  Si un libro se devuelve con más de 7 días de retraso, el usuario no puede realizar préstamos durante 15 días

---

### 🔧 Requisitos Técnicos

#### Backend API REST

**Endpoints Mínimos Requeridos:**

**Autenticación:**
```
POST   /api/auth/login
POST   /api/auth/logout
GET    /api/auth/whoami
GET    /api/auth/validate
```

**Books:**
```
GET    /api/books                    # Listar con paginación y filtros
GET    /api/books/{id}               # Detalles de un libro
GET    /api/books/search? q={query}   # Búsqueda full-text
POST   /api/books                    # Crear libro (librarian+)
PUT    /api/books/{id}               # Actualizar libro (librarian+)
DELETE /api/books/{id}               # Eliminar libro (admin)
GET    /api/books/{id}/availability  # Disponibilidad en tiempo real
```

**Loans:**
```
GET    /api/loans                    # Mis préstamos (user) o todos (librarian+)
GET    /api/loans/{id}               # Detalle de préstamo
POST   /api/loans                    # Crear préstamo (librarian+)
PUT    /api/loans/{id}/return        # Devolver libro (librarian+)
PUT    /api/loans/{id}/renew         # Renovar préstamo (user)
GET    /api/loans/overdue            # Préstamos vencidos (librarian+)
```

**Reservations:**
```
GET    /api/reservations             # Mis reservas (user) o todas (librarian+)
POST   /api/reservations             # Crear reserva (user)
DELETE /api/reservations/{id}        # Cancelar reserva (user)
PUT    /api/reservations/{id}/fulfill # Cumplir reserva (librarian+)
```

**Reviews:**
```
GET    /api/books/{id}/reviews       # Reseñas de un libro
POST   /api/books/{id}/reviews       # Crear reseña (user)
PUT    /api/reviews/{id}             # Actualizar mi reseña
DELETE /api/reviews/{id}             # Eliminar mi reseña
POST   /api/reviews/{id}/helpful     # Marcar como útil
```

**Statistics (solo librarian+):**
```
GET    /api/statistics/dashboard     # Dashboard principal
GET    /api/statistics/popular-books # Libros más prestados
GET    /api/statistics/active-users  # Usuarios más activos
GET    /api/statistics/overdue-rate  # Tasa de retrasos
```

**Validaciones:**
- ISBN debe cumplir formato ISBN-13
- Las fechas no pueden ser en el pasado
- No se puede prestar un libro sin copias disponibles
- No se puede renovar un préstamo más de 2 veces
- No se puede eliminar un libro con préstamos activos

**Manejo de Errores:**
- Códigos HTTP apropiados (200, 201, 400, 401, 403, 404, 409, 500)
- Respuestas JSON consistentes con estructura: 
```json
{
  "timestamp": "2024-01-15T10:30:00Z",
  "status": 400,
  "error": "Bad Request",
  "message": "El ISBN proporcionado no es válido",
  "path": "/api/books"
}
```

---

#### Base de Datos

**Requisitos:**
- PostgreSQL 16
- Migraciones con Flyway (Java) o Entity Framework Migrations (. NET)
- Índices en campos de búsqueda frecuente (isbn, title, author, username)
- Constraints de integridad referencial
- Script de datos de prueba (`seed.sql`) con: 
  - Mínimo 50 libros de diferentes categorías
  - 10 préstamos activos
  - 5 reservas pendientes
  - 20 reseñas

---

#### Frontend

**Páginas Mínimas:**

1. **Login** (`/login`)
   - Formulario de autenticación LDAP
   - Mensajes de error claros
   - Redirección automática si ya está autenticado

2. **Catálogo** (`/catalog`)
   - Lista de libros con paginación
   - Filtros por categoría, autor, año
   - Búsqueda por título/ISBN
   - Indicador visual de disponibilidad
   - Botón de "Reservar" (solo si no hay copias)

3. **Detalle de Libro** (`/books/{id}`)
   - Información completa del libro
   - Disponibilidad en tiempo real
   - Reseñas de otros usuarios
   - Botón "Reservar" o "Préstamo disponible"
   - Formulario para escribir reseña (si está autenticado)

4. **Mis Préstamos** (`/my-loans`)
   - Lista de préstamos activos
   - Fecha de vencimiento destacada (rojo si vencido)
   - Botón "Renovar" (si es posible)
   - Historial de préstamos anteriores

5. **Mis Reservas** (`/my-reservations`)
   - Lista de reservas activas
   - Estado de cada reserva
   - Botón "Cancelar"

6. **Panel Bibliotecario** (`/librarian`) *(solo librarian+)*
   - Búsqueda de usuarios
   - Realizar préstamo (escanear ISBN + username)
   - Devolver libro
   - Gestión de libros (CRUD)
   - Ver préstamos vencidos

7. **Dashboard Estadísticas** (`/dashboard`) *(solo librarian+)*
   - Gráficos con datos relevantes
   - Top 10 libros más prestados
   - Usuarios con préstamos vencidos
   - Tasa de ocupación de la biblioteca

**Requisitos UX:**
- Diseño responsive (mobile-first)
- Feedback visual en todas las acciones (loading, success, error)
- Confirmación antes de acciones destructivas
- Indicadores de disponibilidad en tiempo real
- Navegación clara con breadcrumbs

---

#### Infraestructura LDAP

**Usuarios de Prueba Mínimos:**

- **Estudiantes**: mínimo 2 usuarios
  - `estudiante1` / `StudentPass123! `
  - `estudiante2` / `StudentPass123!`

- **Profesores**: mínimo 1 usuario
  - `profesor1` / `ProfessorPass123!`

- **Bibliotecarios**: mínimo 1 usuario
  - `bibliotecario1` / `LibrarianPass123!`

- **Administradores**: mínimo 1 usuario
  - `admin` / `AdminPass123!`

Cada usuario debe tener:
- Atributos: uid, cn, sn, givenName, mail, userPassword
- Pertenencia al grupo correspondiente (students, professors, librarians, admins)

---

#### Infraestructura DNS

**Configuración Mínima:**

```conf
; Zona:  universidad.local

ns1             IN      A       192.168.200.2   ; DNS Server
proxy           IN      A       192.168.200.10  ; Nginx
webapp          IN      A       192.168.200.20  ; Frontend
api             IN      A       192.168.200.30  ; Backend
db              IN      A       192.168.200.40  ; PostgreSQL
ldap            IN      A       192.168.200.50  ; OpenLDAP
ldapadmin       IN      A       192.168.200.51  ; phpLDAPadmin

; Aliases
www             IN      CNAME   proxy
frontend        IN      CNAME   webapp
backend         IN      CNAME   api
database        IN      CNAME   db
directory       IN      CNAME   ldap

; Servicios
_ldap._tcp      IN      SRV     0 5 389 ldap.universidad.local. 
```

---

### 🧪 Requisitos de Testing

#### 1. Tests Unitarios

**Cobertura Mínima:  80% de las líneas de código**

**Casos de Test Unitario Requeridos:**

- ✅ **LoanService**:
  - Crear préstamo con libro disponible
  - Rechazar préstamo sin copias disponibles
  - Rechazar si usuario excede límite de préstamos
  - Calcular fecha de vencimiento correcta según rol
  - Renovar préstamo válido
  - Rechazar renovación si excede máximo
  - Rechazar renovación si hay reservas pendientes
  - Devolver libro y actualizar disponibilidad
  - Calcular penalización por retraso

- ✅ **ReservationService**:
  - Crear reserva válida
  - Rechazar reserva si hay copias disponibles
  - Cancelar reserva
  - Expirar reservas automáticamente
  - Cumplir reserva (convertir en préstamo)

- ✅ **BookService**:
  - Crear libro con datos válidos
  - Validar formato ISBN-13
  - Actualizar libro
  - Rechazar eliminación si hay préstamos activos
  - Búsqueda por título/autor/ISBN
  - Calcular disponibilidad

- ✅ **ReviewService**:
  - Crear reseña válida
  - Validar rating (1-5)
  - Usuario solo puede reseñar libros que ha leído
  - Usuario puede editar/eliminar solo sus reseñas

**Mínimo total:  50 tests unitarios**

---

#### 2. Tests de Integración (Testcontainers)

**Requisitos:**
- PostgreSQL real en contenedor
- Tests de repositorio con JPA/EF Core
- Validación de constraints de BD
- Transacciones y rollback

**Casos de Test de Integración Requeridos:**

- ✅ Repositorios (cada entidad):
  - CRUD básico
  - Consultas personalizadas
  - Validación de constraints (unique, not null, FK)
  - Paginación y ordenamiento

- ✅ Servicios con BD real:
  - Transaccionalidad
  - Rollback en errores
  - Operaciones concurrentes

**Mínimo total: 20 tests de integración**

---

#### 3. Tests de API (Postman/Newman)

**Colección Postman Requerida:**

Mínimo **40 requests** organizados en carpetas:

- 📁 **Authentication** (4 requests)
  - Login válido/inválido
  - Whoami autenticado/no autenticado

- 📁 **Books** (10 requests)
  - Listar, buscar, crear, actualizar, eliminar
  - Casos de éxito y error
  - Validación de permisos

- 📁 **Loans** (10 requests)
  - Crear, devolver, renovar
  - Listar mis préstamos / todos los préstamos
  - Casos de validación

- 📁 **Reservations** (8 requests)
  - Crear, cancelar, cumplir
  - Validaciones de reglas de negocio

- 📁 **Reviews** (5 requests)
  - CRUD de reseñas
  - Marcar como útil

- 📁 **Statistics** (3 requests)
  - Dashboard, libros populares, tasa de retraso

**Cada request debe incluir:**
- Tests con `pm.test()`
- Validación de códigos de estado
- Validación de estructura de respuesta
- Variables de entorno para datos dinámicos

---

#### 4. Tests E2E (Cypress)

**Escenarios Cypress Requeridos (mínimo 5):**

1. ✅ **Flujo completo de estudiante**:
   - Login → Buscar libro → Reservar → Escribir reseña

2. ✅ **Flujo de bibliotecario**:
   - Login → Realizar préstamo → Devolver libro

3. ✅ **Renovación de préstamo**: 
   - Login como estudiante → Ver mis préstamos → Renovar

4. ✅ **Gestión de libros (CRUD)**:
   - Login como bibliotecario → Crear libro → Editar → (Intentar) Eliminar

5. ✅ **Dashboard de estadísticas**:
   - Login como admin → Ver dashboard → Verificar widgets de datos

**Requisitos técnicos:**
- Uso de `data-cy` attributes para selectores
- Comandos personalizados para login
- Aserciones robustas
- Manejo de estados asíncronos

---

### 📦 Docker Compose

**Requisitos:**

El sistema debe levantarse completamente con un único comando: 
```bash
docker-compose up -d
```

**Servicios requeridos:**
1. DNS (BIND9)
2. LDAP (OpenLDAP)
3. phpLDAPadmin
4. PostgreSQL
5. Backend API
6. Frontend
7. Nginx (reverse proxy)
8. Newman (profile:  testing)
9. Cypress (profile: testing)

**Red personalizada:**
- Subnet: 192.168.200.0/24
- IPs fijas para cada servicio
- DNS interno configurado

**Healthchecks:**
- Todos los servicios deben tener healthcheck
- Dependencias correctas con `depends_on` + `condition: service_healthy`

**Comandos de testing:**
```bash
# Tests de API
docker-compose --profile testing up newman

# Tests E2E
docker-compose --profile testing up cypress
```

---

### 📝 Entregables

#### 1. Código Fuente
- Repositorio Git (GitHub/GitLab) con estructura clara
- README. md con instrucciones de instalación y ejecución
- `.gitignore` apropiado
- Commits atómicos con mensajes descriptivos

#### 2. Documentación

**README.md principal** debe incluir:
- Descripción del proyecto
- Diagrama de arquitectura del sistema
- Tecnologías utilizadas y versiones
- Instrucciones de instalación
- Instrucciones de ejecución
- Usuarios de prueba y credenciales
- Capturas de pantalla de la aplicación funcionando

**TESTING.md** debe incluir:
- Estrategia de testing aplicada
- Cómo ejecutar cada tipo de test
- Interpretación de reportes
- Cobertura de código alcanzada

**API_DOCUMENTATION.md** (o Swagger/OpenAPI):
- Documentación de todos los endpoints
- Ejemplos de peticiones y respuestas
- Códigos de estado posibles

#### 3. Tests

- Suite completa de tests unitarios (mínimo 50 tests)
- Suite de tests de integración (mínimo 20 tests)
- Colección Postman exportada (mínimo 40 requests)
- Tests Cypress funcionales (mínimo 5 escenarios)

#### 4. Infraestructura

- `docker-compose.yml` funcional
- Configuraciones de DNS (archivos de zona)
- Configuraciones de LDAP (archivos . ldif)
- Configuración de Nginx (nginx.conf)
- Scripts de inicialización de BD (init.sql, seed.sql)
- Archivo `.env. example` con variables de entorno documentadas

#### 5. Reportes

- Reporte de cobertura de código (JaCoCo HTML o Coverlet HTML)
- Reporte de tests de API (Newman HTML)
- Screenshots/videos de tests E2E (Cypress)

---

### 🎯 Criterios de Evaluación

| Criterio             | Peso | Descripción                                              |
| -------------------- | ---- | -------------------------------------------------------- |
| **Funcionalidad**    | 25%  | El sistema cumple todos los requisitos funcionales       |
| **Testing**          | 30%  | Cobertura, calidad y variedad de tests                   |
| **Arquitectura**     | 15%  | Diseño limpio, separación de responsabilidades, patrones |
| **Infraestructura**  | 15%  | Configuración correcta de servicios, orquestación        |
| **Documentación**    | 10%  | Claridad, completitud, código comentado                  |
| **Buenas Prácticas** | 5%   | Código limpio, convenciones, commits Git                 |

#### Desglose de "Testing" (30%)

- **Tests unitarios (10%)**:
  - Cobertura > 80%
  - Mínimo 50 tests
  - Casos positivos y negativos
  - Uso correcto de mocks

- **Tests de integración (8%)**:
  - Mínimo 20 tests
  - Uso de Testcontainers
  - Validaciones de BD real
  - Transaccionalidad

- **Tests de API (7%)**:
  - Mínimo 40 requests
  - Colección Postman completa y organizada
  - Validaciones robustas con pm.test()
  - Ejecución exitosa con Newman

- **Tests E2E (5%)**:
  - Mínimo 5 escenarios completos
  - Flujos críticos cubiertos
  - Selectores resilientes (data-cy)
  - Ejecución exitosa en Docker

---

### 💡 Consejos y Recomendaciones

#### Planificación
1. **Empezar por el backend**: Modelo de datos → Repositorios → Servicios → Controllers
2. **Testear mientras desarrollas**: No dejes los tests para el final
3. **Infraestructura primero**: Asegúrate de que LDAP y PostgreSQL funcionan antes de integrar
4. **Iteraciones pequeñas**: Haz commits frecuentes, prueba cada feature antes de continuar

#### Testing
- **Tests unitarios**: Enfócate en la lógica de negocio (servicios)
- **Tests de integración**: Verifica interacciones con BD
- **Tests de API**: Documenta y valida el contrato de la API
- **Tests E2E**: Solo los flujos más críticos (no testees cada botón)

#### Errores Comunes a Evitar

❌ **Hardcodear IPs** en lugar de usar DNS
❌ **No verificar healthchecks** antes de levantar servicios dependientes
❌ **Ignorar manejo de errores** en el backend
❌ **Tests que dependen del orden de ejecución**
❌ **No limpiar datos entre tests**
❌ **Passwords en texto plano** en repositorios (usar . env y . env.example)
❌ **No documentar usuarios de prueba**
❌ **Frontend sin feedback visual** (loading, errores)

---


¡Buena suerte con el proyecto! 🚀📚