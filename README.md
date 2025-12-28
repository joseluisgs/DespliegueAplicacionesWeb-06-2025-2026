# Despliegue de Aplicaciones Web - 06 - Verificación y Validación

Tema 06. Verificación y Validación. 2DAW. Curso 2025-2026.

![imagen](https://github.com/joseluisgs/DespliegueAplicacionesWeb-00-2024-2025/raw/master/images/despliegue.png)

- [Despliegue de Aplicaciones Web - 06 - Verificación y Validación](#despliegue-de-aplicaciones-web---06---verificación-y-validación)
- [Contenido en Youtube](#contenido-en-youtube)
  - [1. Introducción: La Cultura del QA en el Despliegue](#1-introducción-la-cultura-del-qa-en-el-despliegue)
    - [¿Por qué importa la Verificación y Validación?](#por-qué-importa-la-verificación-y-validación)
    - [Verificación vs Validación](#verificación-vs-validación)
    - [La Pirámide de Tests](#la-pirámide-de-tests)
      - [Distribución Recomendada](#distribución-recomendada)
    - [El Coste del Error en Producción](#el-coste-del-error-en-producción)
    - [Testing en el Contexto del Despliegue](#testing-en-el-contexto-del-despliegue)
  - [2. Pruebas Unitarias y Dobles de Prueba](#2-pruebas-unitarias-y-dobles-de-prueba)
    - [¿Qué es una Prueba Unitaria?](#qué-es-una-prueba-unitaria)
      - [Características de una Buena Prueba Unitaria](#características-de-una-buena-prueba-unitaria)
    - [Dobles de Prueba: La Terminología Correcta](#dobles-de-prueba-la-terminología-correcta)
    - [2.1. Java con Gradle (Kotlin DSL) y JUnit 5](#21-java-con-gradle-kotlin-dsl-y-junit-5)
      - [🛠️ Paso a Paso:  Configuración Inicial del Proyecto](#️-paso-a-paso--configuración-inicial-del-proyecto)
      - [Código de Ejemplo: Sistema de Gestión de Usuarios](#código-de-ejemplo-sistema-de-gestión-de-usuarios)
      - [Tests Unitarios con JUnit 5 y Mockito](#tests-unitarios-con-junit-5-y-mockito)
      - [Conceptos Clave de Mockito](#conceptos-clave-de-mockito)
      - [Ejecutar las Pruebas](#ejecutar-las-pruebas)
    - [2. 2. C# \& .NET:  Testing con NUnit y Moq](#2-2-c--net--testing-con-nunit-y-moq)
      - [🛠️ Paso a Paso:  Configuración del Proyecto .NET](#️-paso-a-paso--configuración-del-proyecto-net)
      - [Código de Ejemplo con C# 14](#código-de-ejemplo-con-c-14)
      - [Tests con NUnit y Moq](#tests-con-nunit-y-moq)
      - [Conceptos Clave de Moq](#conceptos-clave-de-moq)
      - [Ejecutar las Pruebas](#ejecutar-las-pruebas-1)
    - [2. 3.  Cobertura de Código](#2-3--cobertura-de-código)
      - [Tipos de Cobertura](#tipos-de-cobertura)
      - [JaCoCo para Java (con Gradle)](#jacoco-para-java-con-gradle)
      - [🛠️ Paso a Paso:  Instalación de JaCoCo Plugin en IntelliJ IDEA](#️-paso-a-paso--instalación-de-jacoco-plugin-en-intellij-idea)
      - [Coverlet para .NET](#coverlet-para-net)
      - [Interpretación del Reporte Coverlet](#interpretación-del-reporte-coverlet)
  - [3. Integración Real con Testcontainers](#3-integración-real-con-testcontainers)
    - [3.1. El Fin de los Mocks en Bases de Datos](#31-el-fin-de-los-mocks-en-bases-de-datos)
      - [El Problema con los Mocks de BD](#el-problema-con-los-mocks-de-bd)
      - [La Solución:  Testcontainers](#la-solución--testcontainers)
    - [3.2. Implementación en Spring Boot (Java)](#32-implementación-en-spring-boot-java)
      - [🛠️ Paso a Paso: Configuración del Proyecto](#️-paso-a-paso-configuración-del-proyecto)
      - [Código de la Aplicación](#código-de-la-aplicación)
      - [Tests de Integración con Testcontainers](#tests-de-integración-con-testcontainers)
      - [Características Avanzadas de Testcontainers](#características-avanzadas-de-testcontainers)
    - [3.3.  Implementación en .NET](#33--implementación-en-net)
      - [🛠️ Paso a Paso:  Configuración del Proyecto](#️-paso-a-paso--configuración-del-proyecto)
      - [Código de la Aplicación](#código-de-la-aplicación-1)
      - [Tests de Integración con Testcontainers](#tests-de-integración-con-testcontainers-1)
      - [Ejecutar los Tests](#ejecutar-los-tests)
  - [4. Automatización de APIs (Postman y Newman)](#4-automatización-de-apis-postman-y-newman)
    - [4.1. Guía Completa de Postman](#41-guía-completa-de-postman)
      - [🛠️ Paso a Paso:  Instalación y Configuración](#️-paso-a-paso--instalación-y-configuración)
      - [Creación de Requests con Variables](#creación-de-requests-con-variables)
      - [Validación de Esquemas JSON Avanzada](#validación-de-esquemas-json-avanzada)
      - [Scripts Pre-request (Preparación)](#scripts-pre-request-preparación)
      - [Pruebas de Errores (Casos Negativos)](#pruebas-de-errores-casos-negativos)
      - [Collection-level Tests (Tests Globales)](#collection-level-tests-tests-globales)
      - [Variables de Entorno:  Desarrollo vs Producción](#variables-de-entorno--desarrollo-vs-producción)
    - [4. 2. Newman: CLI para Automatización](#4-2-newman-cli-para-automatización)
      - [🛠️ Paso a Paso:  Instalación y Uso de Newman](#️-paso-a-paso--instalación-y-uso-de-newman)
      - [Ejecutar Tests con Newman](#ejecutar-tests-con-newman)
      - [Opciones Avanzadas de Newman](#opciones-avanzadas-de-newman)
      - [Script de Automatización Completo](#script-de-automatización-completo)
      - [Newman en Docker](#newman-en-docker)
      - [Integración con GitHub Actions](#integración-con-github-actions)
      - [Buenas Prácticas con Newman](#buenas-prácticas-con-newman)
  - [5. Validación de Interfaz con Cypress](#5-validación-de-interfaz-con-cypress)
    - [5.1. Fundamentos de Cypress](#51-fundamentos-de-cypress)
      - [Diferencias clave:  Cypress vs Selenium](#diferencias-clave--cypress-vs-selenium)
      - [🛠️ Paso a Paso:  Instalación y Configuración](#️-paso-a-paso--instalación-y-configuración-1)
    - [Selectores Inteligentes en Cypress](#selectores-inteligentes-en-cypress)
      - [Jerarquía de Selectores (de mejor a peor)](#jerarquía-de-selectores-de-mejor-a-peor)
      - [Ejemplo de HTML preparado para testing:](#ejemplo-de-html-preparado-para-testing)
      - [Comandos de Selección en Cypress](#comandos-de-selección-en-cypress)
    - [Comandos de Acción Fundamentales](#comandos-de-acción-fundamentales)
      - [Interacción con Formularios](#interacción-con-formularios)
      - [Navegación y URLs](#navegación-y-urls)
      - [Interacción Avanzada](#interacción-avanzada)
    - [Aserciones Más Usadas](#aserciones-más-usadas)
    - [5. 2.  Flujos E2E:  Login hasta Persistencia](#5-2--flujos-e2e--login-hasta-persistencia)
    - [5.3. Ejemplo:  Buscar en Wikipedia con Cypress](#53-ejemplo--buscar-en-wikipedia-con-cypress)
    - [5.4. Dockerización:  Ejecución en Modo Headless](#54-dockerización--ejecución-en-modo-headless)
      - [🛠️ Paso a Paso:  Cypress en Docker](#️-paso-a-paso--cypress-en-docker)
    - [Comandos Personalizados (Custom Commands)](#comandos-personalizados-custom-commands)
  - [6: Servicios de Red e Infraestructura](#6-servicios-de-red-e-infraestructura)
    - [Introducción:  La Capa Invisible del Despliegue](#introducción--la-capa-invisible-del-despliegue)
    - [6.1. DNS con BIND9](#61-dns-con-bind9)
      - [¿Qué es DNS?](#qué-es-dns)
      - [Jerarquía DNS](#jerarquía-dns)
      - [Tipos de Registros DNS Principales](#tipos-de-registros-dns-principales)
      - [🛠️ Paso a Paso: Configuración de BIND9 en Docker](#️-paso-a-paso-configuración-de-bind9-en-docker)
      - [Iniciar y Verificar el Servidor DNS](#iniciar-y-verificar-el-servidor-dns)
      - [Tests DNS con dig, nslookup y host](#tests-dns-con-dig-nslookup-y-host)
      - [Tests desde contenedor cliente](#tests-desde-contenedor-cliente)
      - [Integración con Aplicaciones](#integración-con-aplicaciones)
    - [6. 2. Servicios de Directorio:  LDAP y Active Directory](#6-2-servicios-de-directorio--ldap-y-active-directory)
      - [¿Qué es LDAP?](#qué-es-ldap)
      - [Conceptos Fundamentales](#conceptos-fundamentales)
      - [🛠️ Paso a Paso: OpenLDAP + phpLDAPadmin](#️-paso-a-paso-openldap--phpldapadmin)
      - [Poblar el Directorio LDAP](#poblar-el-directorio-ldap)
      - [Acceder a phpLDAPadmin](#acceder-a-phpldapadmin)
      - [Tests de LDAP con ldapsearch](#tests-de-ldap-con-ldapsearch)
    - [6. 3. Laboratorio: Autenticación LDAP en Aplicación](#6-3-laboratorio-autenticación-ldap-en-aplicación)
      - [Implementación en Spring Boot](#implementación-en-spring-boot)
      - [Implementación en ASP.NET Core](#implementación-en-aspnet-core)
  - [7. Orquestación Final](#7-orquestación-final)
    - [Introducción:  Integrando Todos los Componentes](#introducción--integrando-todos-los-componentes)
    - [7.1. El Gran Escenario: Arquitectura Completa](#71-el-gran-escenario-arquitectura-completa)
      - [Diagrama de la Arquitectura](#diagrama-de-la-arquitectura)
      - [Red y Resolución de Nombres](#red-y-resolución-de-nombres)
    - [7.2. Implementación con Spring Boot](#72-implementación-con-spring-boot)
      - [🛠️ Paso a Paso:  Proyecto Completo](#️-paso-a-paso--proyecto-completo)
    - [7. 3.  Ejecución y Verificación](#7-3--ejecución-y-verificación)
- [Autor](#autor)
  - [Contacto](#contacto)
  - [Licencia de uso](#licencia-de-uso)


# Contenido en Youtube

- [Podcast](https://youtu.be/IrFU6U_d7YI)
- [Resumen](https://youtu.be/TbotPkOe2hk)
- [Lista de Reproducción](https://www.youtube.com/watch?v=HX2gSuX0oow&list=PLGIH-7eZDbVxu55hmqqdQE-Ba6FdPoO-Z)


---

## 1. Introducción: La Cultura del QA en el Despliegue

### ¿Por qué importa la Verificación y Validación?

En el mundo del desarrollo de software moderno, **desplegar no es suficiente**. Una aplicación puede compilar correctamente, ejecutarse sin errores evidentes y aún así no cumplir con las expectativas del usuario o contener fallos críticos que solo aparecen en producción. 

La **Verificación y Validación** (V&V) son dos pilares fundamentales que garantizan no solo que el software funcione, sino que funcione **correctamente** y **como se espera**. 

### Verificación vs Validación

Aunque a menudo se utilizan indistintamente, estos términos tienen significados distintos:

| Concepto         | Pregunta Clave                                   | Enfoque                                                            |
| ---------------- | ------------------------------------------------ | ------------------------------------------------------------------ |
| **Verificación** | ¿Estamos construyendo el producto correctamente? | Comprueba que el software cumple con las especificaciones técnicas |
| **Validación**   | ¿Estamos construyendo el producto correcto?      | Verifica que el software satisface las necesidades del usuario     |

**Ejemplo práctico:**

Imagina que desarrollas un sistema de login: 

- **Verificación**: ¿El método `hashPassword()` utiliza SHA-256 como especifica la documentación técnica? 
- **Validación**: ¿El usuario puede acceder a su cuenta de forma intuitiva y segura?

### La Pirámide de Tests

La industria del software ha consolidado un modelo conceptual conocido como **la Pirámide de Tests**, que establece la proporción ideal de tipos de pruebas:

```
                    /\
                   /  \
                  / E2E \
                 /--------\
                /          \
               / Integración \
              /--------------\
             /                \
            /    Unitarias     \
           /____________________\
```

#### Distribución Recomendada

1. **Pruebas Unitarias (70%)**: Rápidas, aisladas, enfocadas en funciones individuales
2. **Pruebas de Integración (20%)**: Verifican la comunicación entre componentes
3. **Pruebas E2E (10%)**: Simulan el comportamiento completo del usuario

### El Coste del Error en Producción

Los estudios de la industria demuestran que **el coste de corregir un bug crece exponencialmente** según la fase en que se detecta:

| Fase de Detección | Coste Relativo | Tiempo de Corrección        |
| ----------------- | -------------- | --------------------------- |
| Desarrollo        | 1x             | Minutos                     |
| Testing           | 10x            | Horas                       |
| Staging           | 50x            | Días                        |
| Producción        | 100x-1000x     | Semanas + Daño reputacional |

💡 **Nota del Profesor**: Un bug detectado en producción no solo requiere tiempo de desarrollo para corregirse, sino que involucra reuniones de crisis, análisis de impacto, comunicación con clientes afectados, posible compensación y pérdida de confianza.  Por eso, invertir en testing es **siempre** rentable.

### Testing en el Contexto del Despliegue

En esta unidad no nos limitaremos a escribir tests aislados.  Vamos a integrar la verificación y validación en el **ciclo completo de despliegue**, utilizando:

- **Docker** para entornos reproducibles
- **Testcontainers** para pruebas con infraestructura real
- **Automatización** de tests en todos los niveles
- **Orquestación** de servicios complejos

Al finalizar esta unidad, serás capaz de diseñar y ejecutar una estrategia de testing completa que garantice la calidad desde el código hasta la producción.

---

## 2. Pruebas Unitarias y Dobles de Prueba

### ¿Qué es una Prueba Unitaria? 

Una **prueba unitaria** verifica el comportamiento de una **unidad mínima de código** (típicamente una función o método) de forma **aislada**, sin dependencias externas como bases de datos, APIs o sistemas de archivos.

#### Características de una Buena Prueba Unitaria

- ✅ **Rápida**: Se ejecuta en milisegundos
- ✅ **Aislada**:  No depende de otras pruebas ni del orden de ejecución
- ✅ **Repetible**: Produce el mismo resultado siempre
- ✅ **Auto-verificable**: Pasa o falla sin intervención manual
- ✅ **Oportuna**: Se escribe junto al código (idealmente antes con TDD)

### Dobles de Prueba: La Terminología Correcta

Comúnmente se usa "mock" para referirse a cualquier objeto falso en tests, pero existen **distinciones importantes**:

| Tipo      | Propósito                           | Comportamiento                             |
| --------- | ----------------------------------- | ------------------------------------------ |
| **Dummy** | Rellena parámetros que no se usan   | No hace nada                               |
| **Stub**  | Proporciona respuestas predefinidas | Devuelve valores fijos                     |
| **Spy**   | Registra cómo se le invoca          | Objeto real con capacidad de inspección    |
| **Mock**  | Verifica que se llame correctamente | Espera invocaciones específicas            |
| **Fake**  | Implementación simplificada         | Tiene lógica funcional (ej: BD en memoria) |

---

### 2.1. Java con Gradle (Kotlin DSL) y JUnit 5

#### 🛠️ Paso a Paso:  Configuración Inicial del Proyecto

**1.  Estructura del Proyecto**

```
proyecto-java-tests/
├── build.gradle. kts
├── settings.gradle.kts
├── src/
│   ├── main/
│   │   └── java/
│   │       └── com/
│   │           └── example/
│   │               ├── service/
│   │               │   └── UserService.java
│   │               ├── repository/
│   │               │   └── UserRepository.java
│   │               └── model/
│   │                   └── User.java
│   └── test/
│       └── java/
│           └── com/
│               └── example/
│                   └── service/
│                       └── UserServiceTest.java
```

**2. Configuración de Gradle (build.gradle.kts)**

```kotlin
plugins {
    java
    jacoco
}

group = "com.example"
version = "1.0.0"

java {
    toolchain {
        languageVersion. set(JavaLanguageVersion.of(21))
    }
}

repositories {
    mavenCentral()
}

dependencies {
    // Dependencias de producción
    implementation("org.springframework.boot:spring-boot-starter-data-jpa: 3.3.0")
    implementation("org.springframework.boot:spring-boot-starter-web:3.3.0")
    
    // Dependencias de testing
    testImplementation(platform("org.junit:junit-bom:5.10.2"))
    testImplementation("org.junit.jupiter:junit-jupiter")
    testImplementation("org. junit.jupiter:junit-jupiter-params")
    testImplementation("org.mockito:mockito-core:5.11.0")
    testImplementation("org.mockito:mockito-junit-jupiter:5.11.0")
    testImplementation("org.assertj:assertj-core:3.25.3")
}

tasks.test {
    useJUnitPlatform()
    
    testLogging {
        events("passed", "skipped", "failed")
        exceptionFormat = org.gradle.api.tasks.testing.logging.TestExceptionFormat. FULL
        showStandardStreams = false
    }
    
    finalizedBy(tasks.jacocoTestReport)
}

jacoco {
    toolVersion = "0.8.11"
}

tasks.jacocoTestReport {
    dependsOn(tasks.test)
    
    reports {
        xml.required. set(true)
        html.required.set(true)
        csv.required.set(false)
    }
    
    classDirectories.setFrom(
        files(classDirectories.files.map {
            fileTree(it) {
                exclude(
                    "**/config/**",
                    "**/entity/**",
                    "**/dto/**",
                    "**/*Application. class"
                )
            }
        })
    )
}

tasks.jacocoTestCoverageVerification {
    violationRules {
        rule {
            limit {
                minimum = "0.80".toBigDecimal()
            }
        }
        
        rule {
            element = "CLASS"
            limit {
                counter = "LINE"
                value = "COVEREDRATIO"
                minimum = "0.75".toBigDecimal()
            }
            excludes = listOf(
                "*. config.*",
                "*.entity.*",
                "*.dto.*"
            )
        }
    }
}
```

**settings.gradle.kts**

```kotlin
rootProject.name = "proyecto-java-tests"
```

#### Código de Ejemplo: Sistema de Gestión de Usuarios

**User.java**

```java
package com.example.model;

import java.time.LocalDateTime;
import java.util.Objects;

public class User {
    private Long id;
    private String username;
    private String email;
    private String password;
    private boolean active;
    private LocalDateTime createdAt;

    public User() {
        this.createdAt = LocalDateTime.now();
        this.active = true;
    }

    public User(String username, String email, String password) {
        this();
        this.username = username;
        this.email = email;
        this.password = password;
    }

    // Getters y Setters
    public Long getId() { return id; }
    public void setId(Long id) { this.id = id; }

    public String getUsername() { return username; }
    public void setUsername(String username) { this.username = username; }

    public String getEmail() { return email; }
    public void setEmail(String email) { this.email = email; }

    public String getPassword() { return password; }
    public void setPassword(String password) { this.password = password; }

    public boolean isActive() { return active; }
    public void setActive(boolean active) { this.active = active; }

    public LocalDateTime getCreatedAt() { return createdAt; }
    public void setCreatedAt(LocalDateTime createdAt) { this.createdAt = createdAt; }

    @Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (o == null || getClass() != o.getClass()) return false;
        User user = (User) o;
        return Objects.equals(id, user.id) && 
               Objects.equals(username, user.username);
    }

    @Override
    public int hashCode() {
        return Objects.hash(id, username);
    }
}
```

**UserRepository.java (Interfaz)**

```java
package com.example.repository;

import com.example.model.User;
import java.util.Optional;

public interface UserRepository {
    User save(User user);
    Optional<User> findById(Long id);
    Optional<User> findByUsername(String username);
    Optional<User> findByEmail(String email);
    void deleteById(Long id);
    boolean existsByUsername(String username);
    boolean existsByEmail(String email);
}
```

**UserService.java**

```java
package com.example.service;

import com.example.model.User;
import com.example.repository.UserRepository;

import java.security.MessageDigest;
import java.security.NoSuchAlgorithmException;
import java.util.Base64;
import java.util. Optional;

public class UserService {
    
    private final UserRepository userRepository;
    private final EmailValidator emailValidator;
    
    public UserService(UserRepository userRepository, EmailValidator emailValidator) {
        this.userRepository = userRepository;
        this.emailValidator = emailValidator;
    }
    
    /**
     * Registra un nuevo usuario en el sistema
     * @return El usuario registrado con ID asignado
     * @throws IllegalArgumentException si los datos no son válidos
     * @throws UserAlreadyExistsException si el username o email ya existen
     */
    public User registerUser(String username, String email, String password) {
        // Validaciones de entrada
        validateUsername(username);
        validatePassword(password);
        
        if (! emailValidator.isValid(email)) {
            throw new IllegalArgumentException("Email formato inválido");
        }
        
        // Verificar que no exista
        if (userRepository.existsByUsername(username)) {
            throw new UserAlreadyExistsException("Username ya existe:  " + username);
        }
        
        if (userRepository. existsByEmail(email)) {
            throw new UserAlreadyExistsException("Email ya registrado: " + email);
        }
        
        // Crear usuario con password hasheado
        User user = new User(username, email, hashPassword(password));
        
        return userRepository.save(user);
    }
    
    /**
     * Autentica un usuario
     * @return Optional con el usuario si las credenciales son válidas
     */
    public Optional<User> authenticate(String username, String password) {
        Optional<User> userOpt = userRepository.findByUsername(username);
        
        if (userOpt.isEmpty()) {
            return Optional.empty();
        }
        
        User user = userOpt.get();
        
        if (!user.isActive()) {
            return Optional.empty();
        }
        
        String hashedPassword = hashPassword(password);
        if (user.getPassword().equals(hashedPassword)) {
            return Optional. of(user);
        }
        
        return Optional.empty();
    }
    
    /**
     * Desactiva un usuario (borrado lógico)
     */
    public void deactivateUser(Long userId) {
        Optional<User> userOpt = userRepository.findById(userId);
        
        if (userOpt.isPresent()) {
            User user = userOpt.get();
            user.setActive(false);
            userRepository.save(user);
        }
    }
    
    // Métodos privados de utilidad
    
    private void validateUsername(String username) {
        if (username == null || username.trim().isEmpty()) {
            throw new IllegalArgumentException("Username no puede estar vacío");
        }
        
        if (username.length() < 3) {
            throw new IllegalArgumentException("Username debe tener al menos 3 caracteres");
        }
        
        if (username.length() > 20) {
            throw new IllegalArgumentException("Username no puede superar 20 caracteres");
        }
        
        if (! username.matches("^[a-zA-Z0-9_]+$")) {
            throw new IllegalArgumentException("Username solo puede contener letras, números y guion bajo");
        }
    }
    
    private void validatePassword(String password) {
        if (password == null || password.isEmpty()) {
            throw new IllegalArgumentException("Password no puede estar vacío");
        }
        
        if (password.length() < 8) {
            throw new IllegalArgumentException("Password debe tener al menos 8 caracteres");
        }
    }
    
    private String hashPassword(String password) {
        try {
            MessageDigest digest = MessageDigest.getInstance("SHA-256");
            byte[] hash = digest.digest(password.getBytes());
            return Base64.getEncoder().encodeToString(hash);
        } catch (NoSuchAlgorithmException e) {
            throw new RuntimeException("Error al hashear password", e);
        }
    }
    
    // Clases de excepción personalizadas
    
    public static class UserAlreadyExistsException extends RuntimeException {
        public UserAlreadyExistsException(String message) {
            super(message);
        }
    }
}
```

**EmailValidator.java**

```java
package com.example.service;

public interface EmailValidator {
    boolean isValid(String email);
}
```

#### Tests Unitarios con JUnit 5 y Mockito

**UserServiceTest.java**

```java
package com.example.service;

import com.example.model.User;
import com.example.repository.UserRepository;
import com.example.service.UserService. UserAlreadyExistsException;
import org.junit.jupiter.api.BeforeEach;
import org. junit.jupiter.api.DisplayName;
import org.junit. jupiter.api. Nested;
import org.junit. jupiter.api.Test;
import org.junit.jupiter.api. extension.ExtendWith;
import org.junit.jupiter.params.ParameterizedTest;
import org.junit.jupiter.params.provider.ValueSource;
import org.junit.jupiter.params.provider.NullAndEmptySource;
import org. mockito.ArgumentCaptor;
import org.mockito. Captor;
import org.mockito.InjectMocks;
import org. mockito.Mock;
import org.mockito.junit.jupiter. MockitoExtension;

import java.util.Optional;

import static org.assertj.core.api.Assertions.*;
import static org.mockito.ArgumentMatchers.*;
import static org.mockito.Mockito.*;

@ExtendWith(MockitoExtension.class)
@DisplayName("UserService - Pruebas Unitarias")
class UserServiceTest {

    @Mock
    private UserRepository userRepository;

    @Mock
    private EmailValidator emailValidator;

    @InjectMocks
    private UserService userService;

    @Captor
    private ArgumentCaptor<User> userCaptor;

    @Nested
    @DisplayName("Registro de Usuarios")
    class RegisterUser {

        @Test
        @DisplayName("Debe registrar usuario exitosamente con datos válidos")
        void shouldRegisterUserSuccessfully() {
            // Given
            String username = "john_doe";
            String email = "john@example.com";
            String password = "SecurePass123";

            when(emailValidator.isValid(email)).thenReturn(true);
            when(userRepository. existsByUsername(username)).thenReturn(false);
            when(userRepository.existsByEmail(email)).thenReturn(false);
            when(userRepository.save(any(User.class))).thenAnswer(invocation -> {
                User user = invocation.getArgument(0);
                user.setId(1L);
                return user;
            });

            // When
            User result = userService.registerUser(username, email, password);

            // Then
            assertThat(result).isNotNull();
            assertThat(result.getId()).isEqualTo(1L);
            assertThat(result.getUsername()).isEqualTo(username);
            assertThat(result. getEmail()).isEqualTo(email);
            assertThat(result.isActive()).isTrue();
            
            // Verificar que el password fue hasheado (no es igual al original)
            assertThat(result.getPassword()).isNotEqualTo(password);
            assertThat(result.getPassword()).isNotEmpty();

            // Verificar interacciones
            verify(emailValidator).isValid(email);
            verify(userRepository).existsByUsername(username);
            verify(userRepository).existsByEmail(email);
            verify(userRepository).save(any(User.class));
        }

        @Test
        @DisplayName("Debe capturar el usuario guardado con todos sus campos")
        void shouldCaptureUserWithAllFields() {
            // Given
            String username = "jane_smith";
            String email = "jane@example.com";
            String password = "MyPassword99";

            when(emailValidator.isValid(email)).thenReturn(true);
            when(userRepository.existsByUsername(username)).thenReturn(false);
            when(userRepository. existsByEmail(email)).thenReturn(false);

            // When
            userService.registerUser(username, email, password);

            // Then
            verify(userRepository).save(userCaptor.capture());
            User capturedUser = userCaptor.getValue();

            assertThat(capturedUser.getUsername()).isEqualTo(username);
            assertThat(capturedUser.getEmail()).isEqualTo(email);
            assertThat(capturedUser.isActive()).isTrue();
            assertThat(capturedUser.getCreatedAt()).isNotNull();
        }

        @ParameterizedTest
        @NullAndEmptySource
        @ValueSource(strings = {"  ", "\t", "\n"})
        @DisplayName("Debe rechazar usernames vacíos o en blanco")
        void shouldRejectEmptyUsernames(String invalidUsername) {
            // When & Then
            assertThatThrownBy(() -> userService.registerUser(invalidUsername, "test@example.com", "password123"))
                    .isInstanceOf(IllegalArgumentException.class)
                    .hasMessageContaining("Username no puede estar vacío");

            verifyNoInteractions(userRepository);
        }

        @ParameterizedTest
        @ValueSource(strings = {"ab", "a", "xy"})
        @DisplayName("Debe rechazar usernames menores a 3 caracteres")
        void shouldRejectShortUsernames(String shortUsername) {
            // When & Then
            assertThatThrownBy(() -> userService.registerUser(shortUsername, "test@example. com", "password123"))
                    .isInstanceOf(IllegalArgumentException.class)
                    . hasMessageContaining("debe tener al menos 3 caracteres");
        }

        @Test
        @DisplayName("Debe rechazar usernames mayores a 20 caracteres")
        void shouldRejectLongUsernames() {
            // Given
            String longUsername = "a".repeat(21);

            // When & Then
            assertThatThrownBy(() -> userService.registerUser(longUsername, "test@example.com", "password123"))
                    .isInstanceOf(IllegalArgumentException.class)
                    .hasMessageContaining("no puede superar 20 caracteres");
        }

        @ParameterizedTest
        @ValueSource(strings = {"user name", "user-name", "user@name", "user. name", "user#123"})
        @DisplayName("Debe rechazar usernames con caracteres inválidos")
        void shouldRejectInvalidCharactersInUsername(String invalidUsername) {
            // When & Then
            assertThatThrownBy(() -> userService.registerUser(invalidUsername, "test@example.com", "password123"))
                    .isInstanceOf(IllegalArgumentException.class)
                    .hasMessageContaining("solo puede contener letras, números y guion bajo");
        }

        @ParameterizedTest
        @NullAndEmptySource
        @DisplayName("Debe rechazar passwords vacías")
        void shouldRejectEmptyPasswords(String invalidPassword) {
            // When & Then
            assertThatThrownBy(() -> userService.registerUser("validuser", "test@example.com", invalidPassword))
                    .isInstanceOf(IllegalArgumentException.class)
                    .hasMessageContaining("Password no puede estar vacío");
        }

        @ParameterizedTest
        @ValueSource(strings = {"short", "1234567", "abc123"})
        @DisplayName("Debe rechazar passwords menores a 8 caracteres")
        void shouldRejectShortPasswords(String shortPassword) {
            // When & Then
            assertThatThrownBy(() -> userService.registerUser("validuser", "test@example.com", shortPassword))
                    .isInstanceOf(IllegalArgumentException.class)
                    .hasMessageContaining("debe tener al menos 8 caracteres");
        }

        @Test
        @DisplayName("Debe rechazar email con formato inválido")
        void shouldRejectInvalidEmailFormat() {
            // Given
            String invalidEmail = "not-an-email";
            when(emailValidator.isValid(invalidEmail)).thenReturn(false);

            // When & Then
            assertThatThrownBy(() -> userService.registerUser("validuser", invalidEmail, "password123"))
                    .isInstanceOf(IllegalArgumentException.class)
                    .hasMessageContaining("Email formato inválido");

            verify(emailValidator).isValid(invalidEmail);
            verifyNoMoreInteractions(userRepository);
        }

        @Test
        @DisplayName("Debe lanzar excepción si username ya existe")
        void shouldThrowExceptionIfUsernameExists() {
            // Given
            String existingUsername = "existing_user";
            when(emailValidator.isValid(anyString())).thenReturn(true);
            when(userRepository. existsByUsername(existingUsername)).thenReturn(true);

            // When & Then
            assertThatThrownBy(() -> userService.registerUser(existingUsername, "new@example.com", "password123"))
                    .isInstanceOf(UserAlreadyExistsException.class)
                    . hasMessageContaining("Username ya existe");

            verify(userRepository).existsByUsername(existingUsername);
            verify(userRepository, never()).save(any());
        }

        @Test
        @DisplayName("Debe lanzar excepción si email ya existe")
        void shouldThrowExceptionIfEmailExists() {
            // Given
            String existingEmail = "existing@example.com";
            when(emailValidator. isValid(existingEmail)).thenReturn(true);
            when(userRepository. existsByUsername(anyString())).thenReturn(false);
            when(userRepository.existsByEmail(existingEmail)).thenReturn(true);

            // When & Then
            assertThatThrownBy(() -> userService.registerUser("newuser", existingEmail, "password123"))
                    .isInstanceOf(UserAlreadyExistsException.class)
                    .hasMessageContaining("Email ya registrado");

            verify(userRepository).existsByEmail(existingEmail);
            verify(userRepository, never()).save(any());
        }
    }

    @Nested
    @DisplayName("Autenticación de Usuarios")
    class Authenticate {

        @Test
        @DisplayName("Debe autenticar usuario con credenciales correctas")
        void shouldAuthenticateWithValidCredentials() {
            // Given
            String username = "john_doe";
            String password = "SecurePass123";
            
            User existingUser = new User(username, "john@example.com", hashPassword(password));
            existingUser.setId(1L);
            existingUser.setActive(true);

            when(userRepository.findByUsername(username)).thenReturn(Optional.of(existingUser));

            // When
            Optional<User> result = userService.authenticate(username, password);

            // Then
            assertThat(result).isPresent();
            assertThat(result.get().getUsername()).isEqualTo(username);
            verify(userRepository).findByUsername(username);
        }

        @Test
        @DisplayName("Debe rechazar autenticación con password incorrecta")
        void shouldRejectAuthenticationWithWrongPassword() {
            // Given
            String username = "john_doe";
            String correctPassword = "SecurePass123";
            String wrongPassword = "WrongPassword";

            User existingUser = new User(username, "john@example.com", hashPassword(correctPassword));
            existingUser.setId(1L);

            when(userRepository.findByUsername(username)).thenReturn(Optional.of(existingUser));

            // When
            Optional<User> result = userService.authenticate(username, wrongPassword);

            // Then
            assertThat(result).isEmpty();
        }

        @Test
        @DisplayName("Debe rechazar autenticación de usuario inexistente")
        void shouldRejectAuthenticationForNonExistentUser() {
            // Given
            when(userRepository.findByUsername(anyString())).thenReturn(Optional.empty());

            // When
            Optional<User> result = userService.authenticate("nonexistent", "password123");

            // Then
            assertThat(result).isEmpty();
        }

        @Test
        @DisplayName("Debe rechazar autenticación de usuario inactivo")
        void shouldRejectAuthenticationForInactiveUser() {
            // Given
            String username = "inactive_user";
            String password = "SecurePass123";

            User inactiveUser = new User(username, "inactive@example.com", hashPassword(password));
            inactiveUser.setId(1L);
            inactiveUser.setActive(false);

            when(userRepository.findByUsername(username)).thenReturn(Optional.of(inactiveUser));

            // When
            Optional<User> result = userService.authenticate(username, password);

            // Then
            assertThat(result).isEmpty();
        }
    }

    @Nested
    @DisplayName("Desactivación de Usuarios")
    class DeactivateUser {

        @Test
        @DisplayName("Debe desactivar usuario existente")
        void shouldDeactivateExistingUser() {
            // Given
            Long userId = 1L;
            User user = new User("john_doe", "john@example.com", "hashedpass");
            user.setId(userId);
            user.setActive(true);

            when(userRepository.findById(userId)).thenReturn(Optional.of(user));

            // When
            userService.deactivateUser(userId);

            // Then
            verify(userRepository).findById(userId);
            verify(userRepository).save(userCaptor.capture());

            User savedUser = userCaptor.getValue();
            assertThat(savedUser.isActive()).isFalse();
        }

        @Test
        @DisplayName("No debe hacer nada si el usuario no existe")
        void shouldDoNothingIfUserDoesNotExist() {
            // Given
            Long userId = 999L;
            when(userRepository.findById(userId)).thenReturn(Optional.empty());

            // When
            userService.deactivateUser(userId);

            // Then
            verify(userRepository).findById(userId);
            verify(userRepository, never()).save(any());
        }
    }

    // Método auxiliar para tests
    private String hashPassword(String password) {
        try {
            java.security.MessageDigest digest = java.security.MessageDigest.getInstance("SHA-256");
            byte[] hash = digest.digest(password.getBytes());
            return java.util.Base64.getEncoder().encodeToString(hash);
        } catch (Exception e) {
            throw new RuntimeException(e);
        }
    }
}
```

#### Conceptos Clave de Mockito

**Anotaciones Principales:**

```java
@Mock  // Crea un mock (objeto simulado) de la clase
@Spy   // Crea un spy (objeto real con capacidad de verificación)
@InjectMocks  // Crea instancia real e inyecta los mocks automáticamente
@Captor  // Captura argumentos pasados a métodos
```

**Stubbing (Definir Comportamiento):**

```java
// Retornar valor específico
when(mock.metodo(argumento)).thenReturn(valor);

// Lanzar excepción
when(mock.metodo()).thenThrow(new RuntimeException());

// Retornar diferentes valores en llamadas sucesivas
when(mock.metodo()).thenReturn(valor1, valor2, valor3);

// Usar Answer para lógica personalizada
when(mock.metodo()).thenAnswer(invocation -> {
    String arg = invocation.getArgument(0);
    return "Procesado: " + arg;
});
```

**Verificación:**

```java
// Verificar que se llamó
verify(mock).metodo();

// Verificar número de veces
verify(mock, times(2)).metodo();
verify(mock, never()).metodo();
verify(mock, atLeastOnce()).metodo();

// Verificar con argument matchers
verify(mock).metodo(eq("valor"), anyInt(), any(User.class));

// Verificar orden de llamadas
InOrder inOrder = inOrder(mock1, mock2);
inOrder.verify(mock1).metodo1();
inOrder.verify(mock2).metodo2();
```

💡 **Nota del Profesor**: Un error común es usar `when()` con métodos void. Para métodos void usa:  `doNothing().when(mock).metodoVoid()` o `doThrow().when(mock).metodoVoid()`.

#### Ejecutar las Pruebas

```bash
# Ejecutar todos los tests
./gradlew test

# Ejecutar tests con informe detallado
./gradlew test --info

# Ejecutar solo una clase de test
./gradlew test --tests UserServiceTest

# Ejecutar tests y generar reporte de cobertura
./gradlew test jacocoTestReport
```

El reporte HTML de cobertura estará en:  `build/reports/jacoco/test/html/index.html`

---

### 2. 2. C# & .NET:  Testing con NUnit y Moq

#### 🛠️ Paso a Paso:  Configuración del Proyecto .NET

**1. Crear la Estructura del Proyecto**

```bash
# Crear solución
dotnet new sln -n UserManagementSystem

# Crear proyecto de biblioteca de clases
dotnet new classlib -n UserManagement. Core
dotnet sln add UserManagement.Core/UserManagement.Core.csproj

# Crear proyecto de tests
dotnet new nunit -n UserManagement.Tests
dotnet sln add UserManagement.Tests/UserManagement.Tests.csproj

# Agregar referencia del proyecto de tests al proyecto principal
cd UserManagement.Tests
dotnet add reference ../UserManagement.Core/UserManagement.Core.csproj
cd ..
```

**2. Estructura Final**

```
UserManagementSystem/
├── UserManagementSystem.sln
├── UserManagement.Core/
│   ├── UserManagement.Core.csproj
│   ├── Models/
│   │   └── User.cs
│   ├── Repositories/
│   │   └── IUserRepository.cs
│   ├── Services/
│   │   ├── UserService.cs
│   │   └── IEmailValidator.cs
│   └── Exceptions/
│       └── UserAlreadyExistsException. cs
└── UserManagement.Tests/
    ├── UserManagement. Tests.csproj
    ├── Services/
    │   └── UserServiceTests.cs
    └── Usings.cs
```

**3. Configuración del Proyecto Principal (UserManagement.Core. csproj)**

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>net10.0</TargetFramework>
    <LangVersion>14. 0</LangVersion>
    <ImplicitUsings>enable</ImplicitUsings>
    <Nullable>enable</Nullable>
  </PropertyGroup>

</Project>
```

**4. Configuración del Proyecto de Tests (UserManagement.Tests.csproj)**

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>net10.0</TargetFramework>
    <LangVersion>14.0</LangVersion>
    <ImplicitUsings>enable</ImplicitUsings>
    <Nullable>enable</Nullable>
    <IsPackable>false</IsPackable>
    <IsTestProject>true</IsTestProject>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="coverlet.collector" Version="6.0.0">
      <IncludeAssets>runtime; build; native; contentfiles; analyzers; buildtransitive</IncludeAssets>
      <PrivateAssets>all</PrivateAssets>
    </PackageReference>
    <PackageReference Include="FluentAssertions" Version="6.12.0" />
    <PackageReference Include="Microsoft.NET. Test.Sdk" Version="17.11.0" />
    <PackageReference Include="Moq" Version="4.20.70" />
    <PackageReference Include="NUnit" Version="4.1.0" />
    <PackageReference Include="NUnit. Analyzers" Version="4.2.0">
      <IncludeAssets>runtime; build; native; contentfiles; analyzers; buildtransitive</IncludeAssets>
      <PrivateAssets>all</PrivateAssets>
    </PackageReference>
    <PackageReference Include="NUnit3TestAdapter" Version="4.5.0" />
  </ItemGroup>

  <ItemGroup>
    <ProjectReference Include="..\UserManagement.Core\UserManagement.Core.csproj" />
  </ItemGroup>

</Project>
```

#### Código de Ejemplo con C# 14

**User.cs (aprovechando Primary Constructors de C# 14)**

```csharp
namespace UserManagement.Core.Models;

public class User(string username, string email, string password)
{
    public long?  Id { get; set; }
    public string Username { get; set; } = username;
    public string Email { get; set; } = email;
    public string Password { get; set; } = password;
    public bool IsActive { get; set; } = true;
    public DateTime CreatedAt { get; init; } = DateTime.UtcNow;

    // Constructor sin parámetros para compatibilidad con ORMs
    public User() : this(string.Empty, string.Empty, string.Empty)
    {
    }
}
```

**IUserRepository.cs**

```csharp
namespace UserManagement.Core.Repositories;

using Models;

public interface IUserRepository
{
    User Save(User user);
    User?  FindById(long id);
    User? FindByUsername(string username);
    User? FindByEmail(string email);
    void DeleteById(long id);
    bool ExistsByUsername(string username);
    bool ExistsByEmail(string email);
}
```

**IEmailValidator.cs**

```csharp
namespace UserManagement.Core.Services;

public interface IEmailValidator
{
    bool IsValid(string email);
}
```

**UserAlreadyExistsException.cs**

```csharp
namespace UserManagement.Core.Exceptions;

public class UserAlreadyExistsException(string message) : Exception(message);
```

**UserService.cs**

```csharp
namespace UserManagement.Core.Services;

using System. Security.Cryptography;
using System.Text;
using Models;
using Repositories;
using Exceptions;

public class UserService(IUserRepository userRepository, IEmailValidator emailValidator)
{
    private readonly IUserRepository _userRepository = userRepository 
        ?? throw new ArgumentNullException(nameof(userRepository));
    private readonly IEmailValidator _emailValidator = emailValidator 
        ?? throw new ArgumentNullException(nameof(emailValidator));

    /// <summary>
    /// Registra un nuevo usuario en el sistema
    /// </summary>
    /// <returns>El usuario registrado con ID asignado</returns>
    /// <exception cref="ArgumentException">Si los datos no son válidos</exception>
    /// <exception cref="UserAlreadyExistsException">Si el username o email ya existen</exception>
    public User RegisterUser(string username, string email, string password)
    {
        // Validaciones de entrada
        ValidateUsername(username);
        ValidatePassword(password);

        if (! _emailValidator.IsValid(email))
        {
            throw new ArgumentException("Email formato inválido", nameof(email));
        }

        // Verificar que no exista
        if (_userRepository.ExistsByUsername(username))
        {
            throw new UserAlreadyExistsException($"Username ya existe: {username}");
        }

        if (_userRepository. ExistsByEmail(email))
        {
            throw new UserAlreadyExistsException($"Email ya registrado: {email}");
        }

        // Crear usuario con password hasheado
        var user = new User(username, email, HashPassword(password));

        return _userRepository.Save(user);
    }

    /// <summary>
    /// Autentica un usuario
    /// </summary>
    /// <returns>El usuario si las credenciales son válidas, null en caso contrario</returns>
    public User?  Authenticate(string username, string password)
    {
        var user = _userRepository.FindByUsername(username);

        if (user is null || !user.IsActive)
        {
            return null;
        }

        var hashedPassword = HashPassword(password);
        return user.Password == hashedPassword ? user : null;
    }

    /// <summary>
    /// Desactiva un usuario (borrado lógico)
    /// </summary>
    public void DeactivateUser(long userId)
    {
        var user = _userRepository.FindById(userId);

        if (user is not null)
        {
            user.IsActive = false;
            _userRepository.Save(user);
        }
    }

    // Métodos privados de validación

    private static void ValidateUsername(string username)
    {
        if (string.IsNullOrWhiteSpace(username))
        {
            throw new ArgumentException("Username no puede estar vacío", nameof(username));
        }

        if (username.Length < 3)
        {
            throw new ArgumentException(
                "Username debe tener al menos 3 caracteres", 
                nameof(username));
        }

        if (username. Length > 20)
        {
            throw new ArgumentException(
                "Username no puede superar 20 caracteres", 
                nameof(username));
        }

        if (!System.Text.RegularExpressions.Regex.IsMatch(username, @"^[a-zA-Z0-9_]+$"))
        {
            throw new ArgumentException(
                "Username solo puede contener letras, números y guion bajo", 
                nameof(username));
        }
    }

    private static void ValidatePassword(string password)
    {
        if (string.IsNullOrEmpty(password))
        {
            throw new ArgumentException("Password no puede estar vacío", nameof(password));
        }

        if (password.Length < 8)
        {
            throw new ArgumentException(
                "Password debe tener al menos 8 caracteres", 
                nameof(password));
        }
    }

    private static string HashPassword(string password)
    {
        var bytes = SHA256.HashData(Encoding. UTF8.GetBytes(password));
        return Convert.ToBase64String(bytes);
    }
}
```

#### Tests con NUnit y Moq

**Usings.cs (para simplificar imports)**

```csharp
global using NUnit.Framework;
global using Moq;
global using FluentAssertions;
global using UserManagement.Core.Models;
global using UserManagement. Core.Services;
global using UserManagement. Core.Repositories;
global using UserManagement. Core.Exceptions;
```

**UserServiceTests.cs**

```csharp
namespace UserManagement.Tests. Services;

[TestFixture]
[Category("UnitTests")]
public class UserServiceTests
{
    private Mock<IUserRepository> _userRepositoryMock = null!;
    private Mock<IEmailValidator> _emailValidatorMock = null!;
    private UserService _userService = null! ;

    [SetUp]
    public void Setup()
    {
        _userRepositoryMock = new Mock<IUserRepository>();
        _emailValidatorMock = new Mock<IEmailValidator>();
        _userService = new UserService(_userRepositoryMock. Object, _emailValidatorMock.Object);
    }

    [TearDown]
    public void TearDown()
    {
        _userRepositoryMock. Reset();
        _emailValidatorMock.Reset();
    }

    #region RegisterUser Tests

    [Test]
    [Category("RegisterUser")]
    public void RegisterUser_WithValidData_ShouldRegisterSuccessfully()
    {
        // Arrange
        const string username = "john_doe";
        const string email = "john@example.com";
        const string password = "SecurePass123";

        _emailValidatorMock.Setup(x => x.IsValid(email)).Returns(true);
        _userRepositoryMock. Setup(x => x.ExistsByUsername(username)).Returns(false);
        _userRepositoryMock.Setup(x => x.ExistsByEmail(email)).Returns(false);
        _userRepositoryMock. Setup(x => x.Save(It.IsAny<User>()))
            .Returns((User u) => { u.Id = 1L; return u; });

        // Act
        var result = _userService.RegisterUser(username, email, password);

        // Assert
        result.Should().NotBeNull();
        result.Id.Should().Be(1L);
        result.Username.Should().Be(username);
        result.Email. Should().Be(email);
        result.IsActive.Should().BeTrue();
        result.Password.Should().NotBe(password); // Debe estar hasheado
        result.Password.Should().NotBeNullOrEmpty();

        // Verificar llamadas
        _emailValidatorMock.Verify(x => x.IsValid(email), Times.Once);
        _userRepositoryMock.Verify(x => x.ExistsByUsername(username), Times.Once);
        _userRepositoryMock.Verify(x => x. ExistsByEmail(email), Times.Once);
        _userRepositoryMock.Verify(x => x.Save(It.IsAny<User>()), Times.Once);
    }

    [Test]
    [Category("RegisterUser")]
    public void RegisterUser_WithValidData_ShouldSaveUserWithCorrectFields()
    {
        // Arrange
        const string username = "jane_smith";
        const string email = "jane@example.com";
        const string password = "MyPassword99";

        _emailValidatorMock.Setup(x => x. IsValid(email)).Returns(true);
        _userRepositoryMock.Setup(x => x. ExistsByUsername(username)).Returns(false);
        _userRepositoryMock.Setup(x => x.ExistsByEmail(email)).Returns(false);

        User?  capturedUser = null;
        _userRepositoryMock. Setup(x => x.Save(It.IsAny<User>()))
            .Callback<User>(u => capturedUser = u)
            .Returns((User u) => u);

        // Act
        _userService.RegisterUser(username, email, password);

        // Assert
        capturedUser.Should().NotBeNull();
        capturedUser! .Username.Should().Be(username);
        capturedUser. Email.Should().Be(email);
        capturedUser.IsActive.Should().BeTrue();
        capturedUser.CreatedAt.Should().BeCloseTo(DateTime.UtcNow, TimeSpan.FromSeconds(5));
    }

    [Test]
    [TestCase(null)]
    [TestCase("")]
    [TestCase("  ")]
    [TestCase("\t")]
    [TestCase("\n")]
    [Category("RegisterUser")]
    public void RegisterUser_WithEmptyUsername_ShouldThrowArgumentException(string?  invalidUsername)
    {
        // Act
        Action act = () => _userService.RegisterUser(invalidUsername!, "test@example.com", "password123");

        // Assert
        act.Should().Throw<ArgumentException>()
            .WithMessage("*Username no puede estar vacío*")
            .And.ParamName.Should().Be("username");

        _userRepositoryMock. VerifyNoOtherCalls();
    }

    [Test]
    [TestCase("ab")]
    [TestCase("a")]
    [TestCase("xy")]
    [Category("RegisterUser")]
    public void RegisterUser_WithShortUsername_ShouldThrowArgumentException(string shortUsername)
    {
        // Act
        Action act = () => _userService.RegisterUser(shortUsername, "test@example. com", "password123");

        // Assert
        act.Should().Throw<ArgumentException>()
            .WithMessage("*debe tener al menos 3 caracteres*");
    }

    [Test]
    [Category("RegisterUser")]
    public void RegisterUser_WithLongUsername_ShouldThrowArgumentException()
    {
        // Arrange
        var longUsername = new string('a', 21);

        // Act
        Action act = () => _userService.RegisterUser(longUsername, "test@example.com", "password123");

        // Assert
        act.Should().Throw<ArgumentException>()
            .WithMessage("*no puede superar 20 caracteres*");
    }

    [Test]
    [TestCase("user name")]
    [TestCase("user-name")]
    [TestCase("user@name")]
    [TestCase("user. name")]
    [TestCase("user#123")]
    [Category("RegisterUser")]
    public void RegisterUser_WithInvalidCharactersInUsername_ShouldThrowArgumentException(
        string invalidUsername)
    {
        // Act
        Action act = () => _userService.RegisterUser(invalidUsername, "test@example.com", "password123");

        // Assert
        act. Should().Throw<ArgumentException>()
            .WithMessage("*solo puede contener letras, números y guion bajo*");
    }

    [Test]
    [TestCase(null)]
    [TestCase("")]
    [Category("RegisterUser")]
    public void RegisterUser_WithEmptyPassword_ShouldThrowArgumentException(string? invalidPassword)
    {
        // Act
        Action act = () => _userService.RegisterUser("validuser", "test@example.com", invalidPassword!);

        // Assert
        act.Should().Throw<ArgumentException>()
            .WithMessage("*Password no puede estar vacío*")
            .And.ParamName.Should().Be("password");
    }

    [Test]
    [TestCase("short")]
    [TestCase("1234567")]
    [TestCase("abc123")]
    [Category("RegisterUser")]
    public void RegisterUser_WithShortPassword_ShouldThrowArgumentException(string shortPassword)
    {
        // Act
        Action act = () => _userService.RegisterUser("validuser", "test@example.com", shortPassword);

        // Assert
        act.Should().Throw<ArgumentException>()
            .WithMessage("*debe tener al menos 8 caracteres*");
    }

    [Test]
    [Category("RegisterUser")]
    public void RegisterUser_WithInvalidEmailFormat_ShouldThrowArgumentException()
    {
        // Arrange
        const string invalidEmail = "not-an-email";
        _emailValidatorMock. Setup(x => x.IsValid(invalidEmail)).Returns(false);

        // Act
        Action act = () => _userService.RegisterUser("validuser", invalidEmail, "password123");

        // Assert
        act.Should().Throw<ArgumentException>()
            .WithMessage("*Email formato inválido*")
            .And.ParamName.Should().Be("email");

        _emailValidatorMock. Verify(x => x.IsValid(invalidEmail), Times.Once);
        _userRepositoryMock. VerifyNoOtherCalls();
    }

    [Test]
    [Category("RegisterUser")]
    public void RegisterUser_WithExistingUsername_ShouldThrowUserAlreadyExistsException()
    {
        // Arrange
        const string existingUsername = "existing_user";
        _emailValidatorMock.Setup(x => x.IsValid(It.IsAny<string>())).Returns(true);
        _userRepositoryMock.Setup(x => x.ExistsByUsername(existingUsername)).Returns(true);

        // Act
        Action act = () => _userService.RegisterUser(existingUsername, "new@example.com", "password123");

        // Assert
        act.Should().Throw<UserAlreadyExistsException>()
            .WithMessage("*Username ya existe*");

        _userRepositoryMock.Verify(x => x.ExistsByUsername(existingUsername), Times.Once);
        _userRepositoryMock.Verify(x => x.Save(It.IsAny<User>()), Times.Never);
    }

    [Test]
    [Category("RegisterUser")]
    public void RegisterUser_WithExistingEmail_ShouldThrowUserAlreadyExistsException()
    {
        // Arrange
        const string existingEmail = "existing@example. com";
        _emailValidatorMock.Setup(x => x.IsValid(existingEmail)).Returns(true);
        _userRepositoryMock. Setup(x => x.ExistsByUsername(It.IsAny<string>())).Returns(false);
        _userRepositoryMock. Setup(x => x.ExistsByEmail(existingEmail)).Returns(true);

        // Act
        Action act = () => _userService.RegisterUser("newuser", existingEmail, "password123");

        // Assert
        act.Should().Throw<UserAlreadyExistsException>()
            .WithMessage("*Email ya registrado*");

        _userRepositoryMock. Verify(x => x.ExistsByEmail(existingEmail), Times.Once);
        _userRepositoryMock.Verify(x => x.Save(It.IsAny<User>()), Times.Never);
    }

    #endregion

    #region Authenticate Tests

    [Test]
    [Category("Authenticate")]
    public void Authenticate_WithValidCredentials_ShouldReturnUser()
    {
        // Arrange
        const string username = "john_doe";
        const string password = "SecurePass123";
        var hashedPassword = HashPasswordForTest(password);

        var existingUser = new User(username, "john@example.com", hashedPassword)
        {
            Id = 1L,
            IsActive = true
        };

        _userRepositoryMock.Setup(x => x.FindByUsername(username)).Returns(existingUser);

        // Act
        var result = _userService.Authenticate(username, password);

        // Assert
        result.Should().NotBeNull();
        result!.Username.Should().Be(username);
        _userRepositoryMock.Verify(x => x.FindByUsername(username), Times.Once);
    }

    [Test]
    [Category("Authenticate")]
    public void Authenticate_WithWrongPassword_ShouldReturnNull()
    {
        // Arrange
        const string username = "john_doe";
        const string correctPassword = "SecurePass123";
        const string wrongPassword = "WrongPassword";

        var existingUser = new User(username, "john@example.com", HashPasswordForTest(correctPassword))
        {
            Id = 1L,
            IsActive = true
        };

        _userRepositoryMock.Setup(x => x.FindByUsername(username)).Returns(existingUser);

        // Act
        var result = _userService. Authenticate(username, wrongPassword);

        // Assert
        result. Should().BeNull();
    }

    [Test]
    [Category("Authenticate")]
    public void Authenticate_WithNonExistentUser_ShouldReturnNull()
    {
        // Arrange
        _userRepositoryMock.Setup(x => x.FindByUsername(It.IsAny<string>())).Returns((User?)null);

        // Act
        var result = _userService.Authenticate("nonexistent", "password123");

        // Assert
        result. Should().BeNull();
    }

    [Test]
    [Category("Authenticate")]
    public void Authenticate_WithInactiveUser_ShouldReturnNull()
    {
        // Arrange
        const string username = "inactive_user";
        const string password = "SecurePass123";

        var inactiveUser = new User(username, "inactive@example.com", HashPasswordForTest(password))
        {
            Id = 1L,
            IsActive = false
        };

        _userRepositoryMock.Setup(x => x.FindByUsername(username)).Returns(inactiveUser);

        // Act
        var result = _userService.Authenticate(username, password);

        // Assert
        result.Should().BeNull();
    }

    #endregion

    #region DeactivateUser Tests

    [Test]
    [Category("DeactivateUser")]
    public void DeactivateUser_WithExistingUser_ShouldSetIsActiveToFalse()
    {
        // Arrange
        const long userId = 1L;
        var user = new User("john_doe", "john@example.com", "hashedpass")
        {
            Id = userId,
            IsActive = true
        };

        _userRepositoryMock.Setup(x => x.FindById(userId)).Returns(user);

        User? savedUser = null;
        _userRepositoryMock.Setup(x => x.Save(It.IsAny<User>()))
            .Callback<User>(u => savedUser = u)
            .Returns((User u) => u);

        // Act
        _userService. DeactivateUser(userId);

        // Assert
        _userRepositoryMock.Verify(x => x.FindById(userId), Times.Once);
        _userRepositoryMock. Verify(x => x.Save(It.IsAny<User>()), Times.Once);

        savedUser.Should().NotBeNull();
        savedUser!.IsActive.Should().BeFalse();
    }

    [Test]
    [Category("DeactivateUser")]
    public void DeactivateUser_WithNonExistentUser_ShouldNotCallSave()
    {
        // Arrange
        const long userId = 999L;
        _userRepositoryMock.Setup(x => x.FindById(userId)).Returns((User?)null);

        // Act
        _userService.DeactivateUser(userId);

        // Assert
        _userRepositoryMock.Verify(x => x.FindById(userId), Times.Once);
        _userRepositoryMock. Verify(x => x.Save(It.IsAny<User>()), Times.Never);
    }

    #endregion

    #region Helper Methods

    private static string HashPasswordForTest(string password)
    {
        var bytes = System.Security.Cryptography.SHA256.HashData(
            System.Text.Encoding. UTF8.GetBytes(password));
        return Convert.ToBase64String(bytes);
    }

    #endregion
}
```

#### Conceptos Clave de Moq

**Configuración de Mocks:**

```csharp
// Setup básico
mock.Setup(x => x.Method(param)).Returns(value);

// Setup con It.IsAny<T>()
mock.Setup(x => x.Method(It.IsAny<string>())).Returns(value);

// Setup con condiciones
mock.Setup(x => x.Method(It.Is<int>(i => i > 0))).Returns(value);

// Setup con callback
mock.Setup(x => x.Method(It.IsAny<User>()))
    .Callback<User>(u => Console.WriteLine(u.Username))
    .Returns((User u) => u);
```

**Verificación:**

```csharp
// Verificar llamada
mock.Verify(x => x.Method(), Times.Once);

// Otras opciones de Times
Times.Never
Times.AtLeastOnce
Times.AtMost(n)
Times.Between(min, max, Range. Inclusive)

// Verificar que NO se llamaron otros métodos
mock. VerifyNoOtherCalls();
```

💡 **Nota del Profesor**: FluentAssertions mejora significativamente la legibilidad de las aserciones.  Compara `Assert.AreEqual(expected, actual)` con `actual.Should().Be(expected)`. La segunda es más natural de leer.

#### Ejecutar las Pruebas

```bash
# Ejecutar todos los tests
dotnet test

# Ejecutar con detalle
dotnet test --logger "console;verbosity=detailed"

# Ejecutar tests de una categoría específica
dotnet test --filter "Category=RegisterUser"

# Ejecutar con cobertura de código
dotnet test --collect:"XPlat Code Coverage"
```

---

### 2. 3.  Cobertura de Código

La **cobertura de código** mide qué porcentaje del código fuente es ejecutado por las pruebas.  Es una métrica útil pero **no es sinónimo de calidad**. 

#### Tipos de Cobertura

| Tipo                   | Qué Mide                          | Ejemplo          |
| ---------------------- | --------------------------------- | ---------------- |
| **Line Coverage**      | % de líneas ejecutadas            | 85% de líneas    |
| **Branch Coverage**    | % de ramas condicionales probadas | If/else, switch  |
| **Method Coverage**    | % de métodos invocados            | 20 de 25 métodos |
| **Statement Coverage** | % de sentencias ejecutadas        | Similar a líneas |

💡 **Nota del Profesor**: 100% de cobertura NO garantiza código libre de bugs. Lo importante es la **calidad** de las pruebas, no solo la cantidad de líneas ejecutadas.

---

#### JaCoCo para Java (con Gradle)

Ya configuramos JaCoCo en el `build.gradle. kts` anterior.  Veamos cómo interpretar el reporte:

**Generar reporte:**

```bash
./gradlew test jacocoTestReport
```

**Ubicación del reporte:** `build/reports/jacoco/test/html/index.html`


```
├── index.html (Vista general del proyecto)
├── com.example.service/
│   └── UserService.html (Detalle de cada clase)
└── . resources/ (Estilos CSS)
```

**Interpretación de Colores:**

- 🟢 **Verde**: Línea ejecutada por los tests
- 🔴 **Rojo**: Línea NO ejecutada
- 🟡 **Amarillo**:  Rama parcialmente cubierta (ej: solo el `if`, no el `else`)

**Ejemplo de Lectura del Reporte:**

```
Package: com.example.service
┌────────────────┬──────────┬─────────┬──────────┬─────────┐
│     Element    │ Missed   │ Covered │   Total  │ Coverage│
├────────────────┼──────────┼─────────┼──────────┼─────────┤
│ Instructions   │    42    │   358   │   400    │   89%   │
│ Branches       │    8     │    34   │    42    │   81%   │
│ Lines          │    12    │    88   │   100    │   88%   │
│ Methods        │    1     │    14   │    15    │   93%   │
│ Classes        │    0     │    5    │     5    │  100%   │
└────────────────┴──────────┴─────────┴──────────┴─────────┘
```

**Configuración de Umbrales Mínimos:**

En nuestro `build.gradle.kts` ya incluimos verificación de cobertura:

```kotlin
tasks.jacocoTestCoverageVerification {
    violationRules {
        rule {
            limit {
                minimum = "0.80".toBigDecimal() // 80% mínimo global
            }
        }
        
        rule {
            element = "CLASS"
            limit {
                counter = "LINE"
                value = "COVEREDRATIO"
                minimum = "0.75".toBigDecimal() // 75% por clase
            }
            excludes = listOf(
                "*. config.*",
                "*.entity.*",
                "*.dto.*"
            )
        }
    }
}
```

**Integrar verificación en el build:**

```kotlin
tasks.check {
    dependsOn(tasks.jacocoTestCoverageVerification)
}
```

Ahora, `./gradlew check` fallará si la cobertura está por debajo del umbral. 

#### 🛠️ Paso a Paso:  Instalación de JaCoCo Plugin en IntelliJ IDEA

1. **Abrir IntelliJ IDEA** y navegar al proyecto
2. **Ir a Settings/Preferences** (Ctrl+Alt+S / Cmd+,)
3. **Plugins** → Buscar "JaCoCo"
4. **Instalar "Coverage"** (ya viene integrado en versiones recientes)
5. **Ejecutar tests con cobertura:**
   - Click derecho en carpeta `test`
   - Seleccionar "Run Tests with Coverage"
6. **Ver resultados:** Panel lateral mostrará cobertura por paquete/clase

**Atajos útiles:**
- `Ctrl+Alt+F6` (Windows/Linux) / `Cmd+Alt+F6` (Mac): Run with Coverage
- En el editor, las líneas se colorean según cobertura

💡 **Nota del Profesor**: El plugin de IntelliJ muestra la cobertura en tiempo real mientras editas, lo cual es extremadamente útil para identificar rápidamente código no probado.

---

#### Coverlet para .NET

**🛠️ Paso a Paso: Configuración Completa**

Ya agregamos `coverlet.collector` en el `.csproj`. Ahora configuremos reportes HTML:

**1. Instalar ReportGenerator (herramienta global):**

```bash
dotnet tool install -g dotnet-reportgenerator-globaltool
```

**2. Ejecutar tests con cobertura:**

```bash
dotnet test --collect:"XPlat Code Coverage"
```

Esto genera archivos `coverage.cobertura.xml` en: 
```
UserManagement. Tests/TestResults/{guid}/coverage.cobertura.xml
```

**3. Generar reporte HTML:**

```bash
reportgenerator \
  -reports:"**/coverage.cobertura.xml" \
  -targetdir:"coveragereport" \
  -reporttypes: Html
```

**4. Abrir el reporte:**

```bash
# Windows
start coveragereport/index.html

# Linux
xdg-open coveragereport/index.html

# macOS
open coveragereport/index.html
```

**Script Automatizado (crear archivo `test-coverage.sh` o `test-coverage.ps1`):**

**PowerShell (Windows):**

```powershell
# test-coverage.ps1
Write-Host "Ejecutando tests con cobertura..." -ForegroundColor Green

# Limpiar reportes anteriores
Remove-Item -Path "TestResults" -Recurse -ErrorAction SilentlyContinue
Remove-Item -Path "coveragereport" -Recurse -ErrorAction SilentlyContinue

# Ejecutar tests
dotnet test --collect:"XPlat Code Coverage" --results-directory:"./TestResults"

if ($LASTEXITCODE -ne 0) {
    Write-Host "Tests fallaron" -ForegroundColor Red
    exit 1
}

# Generar reporte
Write-Host "Generando reporte HTML..." -ForegroundColor Green
reportgenerator `
    -reports:"TestResults/**/coverage.cobertura.xml" `
    -targetdir:"coveragereport" `
    -reporttypes:Html

Write-Host "Reporte generado en coveragereport/index.html" -ForegroundColor Green
Start-Process "coveragereport/index.html"
```

**Bash (Linux/macOS):**

```bash
#!/bin/bash
# test-coverage.sh

echo "Ejecutando tests con cobertura..."

# Limpiar reportes anteriores
rm -rf TestResults coveragereport

# Ejecutar tests
dotnet test --collect:"XPlat Code Coverage" --results-directory:"./TestResults"

if [ $? -ne 0 ]; then
    echo "Tests fallaron"
    exit 1
fi

# Generar reporte
echo "Generando reporte HTML..."
reportgenerator \
    -reports:"TestResults/**/coverage.cobertura.xml" \
    -targetdir:"coveragereport" \
    -reporttypes:Html

echo "Reporte generado en coveragereport/index. html"
xdg-open coveragereport/index.html 2>/dev/null || open coveragereport/index.html
```

**Configuración Avanzada con coverlet.msbuild:**

Para más control, instala el paquete MSBuild:

```bash
cd UserManagement.Tests
dotnet add package coverlet.msbuild
```

**Ejecutar con umbrales:**

```bash
dotnet test /p:CollectCoverage=true \
            /p:CoverletOutputFormat=cobertura \
            /p: Threshold=80 \
            /p:ThresholdType=line \
            /p:ThresholdStat=total
```

Esto fallará si la cobertura de líneas es menor al 80%.

**Excluir archivos de la cobertura:**

```bash
dotnet test /p:CollectCoverage=true \
            /p: Exclude="[*]*. Migrations.*,[*]*.Program,[*]*. Startup"
```

#### Interpretación del Reporte Coverlet

El reporte HTML generado por ReportGenerator tiene una estructura similar a JaCoCo:

**Vista General:**

```
Summary
┌─────────────────┬─────────┬─────────┬──────────┐
│    Metric       │ Covered │  Total  │ Coverage │
├─────────────────┼─────────┼─────────┼──────────┤
│ Line Coverage   │   456   │   520   │  87. 69%  │
│ Branch Coverage │   89    │   110   │  80.91%  │
│ Method Coverage │   45    │   52    │  86.54%  │
└─────────────────┴─────────┴─────────┴──────────┘
```

**Vista de Clase (UserService. cs):**

```csharp
public class UserService
{
    // ✅ Cubierto por:  RegisterUser_WithValidData_ShouldRegisterSuccessfully
    public User RegisterUser(string username, string email, string password)
    {
        ✅ ValidateUsername(username);
        ✅ ValidatePassword(password);
        
        ✅ if (! _emailValidator.IsValid(email))
        {
            ✅ throw new ArgumentException("Email formato inválido");
        }
        
        ✅ if (_userRepository.ExistsByUsername(username))
        {
            ✅ throw new UserAlreadyExistsException($"Username ya existe");
        }
        
        ✅ var user = new User(username, email, HashPassword(password));
        ✅ return _userRepository.Save(user);
    }
    
    // ❌ NO cubierto - ningún test verifica este método
    private void LogAuditEvent(string action)
    {
        ❌ _auditLogger.Log($"Action: {action}");
    }
}
```

💡 **Nota del Profesor**: Los métodos privados no probados pueden ser: 
1. **Código muerto** que debería eliminarse
2. **Lógica que debería ser pública** para poder testearla
3. **Código implícitamente probado** a través de métodos públicos (en cuyo caso la cobertura los marcará como cubiertos)

---

## 3. Integración Real con Testcontainers

### 3.1. El Fin de los Mocks en Bases de Datos

#### El Problema con los Mocks de BD

Hasta ahora hemos mockeado los repositorios, lo cual es perfecto para **pruebas unitarias**.  Pero los mocks tienen limitaciones significativas:

| Aspecto           | Con Mocks     | Con BD Real               |
| ----------------- | ------------- | ------------------------- |
| **Consultas SQL** | No se prueban | Se ejecutan realmente     |
| **Constraints**   | No se validan | Se verifican (FK, UNIQUE) |
| **Transacciones** | Simuladas     | Comportamiento real       |
| **Performance**   | No se mide    | Detectable                |
| **Dialecto SQL**  | Ignorado      | Específico del motor      |

**Ejemplo de Bug NO Detectado con Mocks:**

```java
// Repository con bug sutil
public List<User> findActiveUsers() {
    return entityManager.createQuery(
        "SELECT u FROM User u WHERE u.active = 1", // ❌ Bug: active es boolean, no int
        User.class
    ).getResultList();
}

// Test unitario con mock - PASA ✅ (no ejecuta SQL)
@Test
void testFindActiveUsers() {
    when(repository.findActiveUsers()).thenReturn(List.of(user1, user2));
    List<User> result = service.getActiveUsers();
    assertThat(result).hasSize(2); // ✅ Pasa con mock
}

// Realidad en producción - FALLA ❌
// org.hibernate.exception.SQLGrammarException: could not execute query
```

#### La Solución:  Testcontainers

**Testcontainers** es una biblioteca Java (con ports para . NET, Go, Python, Node.js, etc.) que permite ejecutar **contenedores Docker desde los tests**, proporcionando:

- ✅ Bases de datos reales (PostgreSQL, MySQL, MongoDB, etc.)
- ✅ Colas de mensajes (RabbitMQ, Kafka)
- ✅ Servicios externos (Redis, Elasticsearch)
- ✅ Navegadores (Selenium)
- ✅ Cualquier cosa que tenga imagen Docker

**Ventajas Clave:**

1. **Aislamiento**: Cada test suite tiene su propia BD limpia
2. **Realismo**: Comportamiento idéntico a producción
3. **Portabilidad**: Funciona en cualquier máquina con Docker
4. **Automatización**: Se gestiona todo desde código

💡 **Nota del Profesor**: Testcontainers revolucionó el testing de integración. Antes necesitábamos BD instaladas localmente, scripts de setup complejos y limpieza manual. Ahora todo es automático y reproducible.

---

### 3.2. Implementación en Spring Boot (Java)

#### 🛠️ Paso a Paso: Configuración del Proyecto

**1. Actualizar `build.gradle.kts` con dependencias de integración:**

```kotlin
plugins {
    java
    jacoco
    id("org.springframework.boot") version "3.3.0"
    id("io.spring.dependency-management") version "1.1.5"
}

group = "com.example"
version = "1.0.0"

java {
    toolchain {
        languageVersion. set(JavaLanguageVersion.of(21))
    }
}

repositories {
    mavenCentral()
}

dependencies {
    // Spring Boot
    implementation("org. springframework.boot:spring-boot-starter-data-jpa")
    implementation("org.springframework.boot:spring-boot-starter-web")
    implementation("org.springframework.boot:spring-boot-starter-validation")
    
    // PostgreSQL
    runtimeOnly("org.postgresql:postgresql")
    
    // Testing
    testImplementation("org. springframework.boot:spring-boot-starter-test")
    testImplementation(platform("org.testcontainers:testcontainers-bom:1.19.8"))
    testImplementation("org.testcontainers:testcontainers")
    testImplementation("org.testcontainers:junit-jupiter")
    testImplementation("org.testcontainers:postgresql")
    
    testImplementation("org.junit.jupiter:junit-jupiter")
    testImplementation("org. mockito:mockito-core: 5.11.0")
    testImplementation("org.assertj:assertj-core:3.25.3")
}

tasks.test {
    useJUnitPlatform()
}
```

**2. Estructura del Proyecto:**

```
proyecto-spring-testcontainers/
├── src/
│   ├── main/
│   │   ├── java/com/example/
│   │   │   ├── UserApplication.java
│   │   │   ├── entity/
│   │   │   │   └── UserEntity.java
│   │   │   ├── repository/
│   │   │   │   └── UserRepository.java
│   │   │   ├── service/
│   │   │   │   └── UserService. java
│   │   │   └── dto/
│   │   │       └── CreateUserRequest.java
│   │   └── resources/
│   │       └── application.yml
│   └── test/
│       ├── java/com/example/
│       │   ├── integration/
│       │   │   └── UserServiceIntegrationTest.java
│       │   └── repository/
│       │       └── UserRepositoryTest.java
│       └── resources/
│           └── application-test.yml
```

#### Código de la Aplicación

**UserEntity.java**

```java
package com.example.entity;

import jakarta.persistence.*;
import java.time.LocalDateTime;
import java.util.Objects;

@Entity
@Table(name = "users", uniqueConstraints = {
    @UniqueConstraint(name = "uk_username", columnNames = "username"),
    @UniqueConstraint(name = "uk_email", columnNames = "email")
})
public class UserEntity {
    
    @Id
    @GeneratedValue(strategy = GenerationType. IDENTITY)
    private Long id;
    
    @Column(nullable = false, length = 20)
    private String username;
    
    @Column(nullable = false, length = 100)
    private String email;
    
    @Column(nullable = false)
    private String password;
    
    @Column(nullable = false)
    private Boolean active = true;
    
    @Column(name = "created_at", nullable = false, updatable = false)
    private LocalDateTime createdAt;
    
    @PrePersist
    protected void onCreate() {
        createdAt = LocalDateTime.now();
    }
    
    // Constructors
    public UserEntity() {}
    
    public UserEntity(String username, String email, String password) {
        this.username = username;
        this.email = email;
        this.password = password;
    }
    
    // Getters y Setters
    public Long getId() { return id; }
    public void setId(Long id) { this.id = id; }
    
    public String getUsername() { return username; }
    public void setUsername(String username) { this.username = username; }
    
    public String getEmail() { return email; }
    public void setEmail(String email) { this.email = email; }
    
    public String getPassword() { return password; }
    public void setPassword(String password) { this.password = password; }
    
    public Boolean getActive() { return active; }
    public void setActive(Boolean active) { this.active = active; }
    
    public LocalDateTime getCreatedAt() { return createdAt; }
    
    @Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (o == null || getClass() != o.getClass()) return false;
        UserEntity that = (UserEntity) o;
        return Objects.equals(id, that.id);
    }
    
    @Override
    public int hashCode() {
        return Objects.hash(id);
    }
}
```

**UserRepository.java (Spring Data JPA)**

```java
package com.example.repository;

import com.example.entity.UserEntity;
import org.springframework.data.jpa.repository.JpaRepository;
import org.springframework.data.jpa.repository.Query;
import org.springframework.stereotype.Repository;

import java.util.List;
import java.util.Optional;

@Repository
public interface UserRepository extends JpaRepository<UserEntity, Long> {
    
    Optional<UserEntity> findByUsername(String username);
    
    Optional<UserEntity> findByEmail(String email);
    
    boolean existsByUsername(String username);
    
    boolean existsByEmail(String email);
    
    @Query("SELECT u FROM UserEntity u WHERE u.active = true")
    List<UserEntity> findAllActive();
    
    @Query("SELECT u FROM UserEntity u WHERE u.username LIKE %: pattern%")
    List<UserEntity> searchByUsername(String pattern);
}
```

**application.yml**

```yaml
spring:
  application:
    name: user-management
  
  datasource:
    url:  ${DATABASE_URL:jdbc:postgresql://localhost:5432/userdb}
    username: ${DATABASE_USER:postgres}
    password: ${DATABASE_PASSWORD:postgres}
    driver-class-name: org. postgresql.Driver
  
  jpa:
    hibernate:
      ddl-auto: update
    show-sql: true
    properties:
      hibernate:
        format_sql: true
        dialect: org.hibernate.dialect.PostgreSQLDialect
```

**application-test.yml**

```yaml
spring:
  jpa:
    hibernate:
      ddl-auto: create-drop
    show-sql: true
```

#### Tests de Integración con Testcontainers

**AbstractIntegrationTest.java (Clase Base)**

```java
package com.example.integration;

import org.springframework.boot.test.context.SpringBootTest;
import org.springframework.boot.testcontainers.service. connection.ServiceConnection;
import org.springframework.test.context.ActiveProfiles;
import org.testcontainers.containers.PostgreSQLContainer;
import org.testcontainers.junit.jupiter.Container;
import org.testcontainers.junit. jupiter.Testcontainers;

@SpringBootTest
@Testcontainers
@ActiveProfiles("test")
public abstract class AbstractIntegrationTest {
    
    @Container
    @ServiceConnection
    static PostgreSQLContainer<?> postgres = new PostgreSQLContainer<>("postgres:16-alpine")
            .withDatabaseName("testdb")
            .withUsername("testuser")
            .withPassword("testpass");
}
```

💡 **Nota del Profesor**: La anotación `@ServiceConnection` de Spring Boot 3.1+ configura automáticamente el datasource usando los datos del contenedor.  Es una simplificación enorme comparada con versiones anteriores donde había que configurar manualmente las propiedades.

**UserRepositoryTest.java**

```java
package com.example.repository;

import com.example.entity. UserEntity;
import com.example.integration.AbstractIntegrationTest;
import org.junit.jupiter.api.BeforeEach;
import org. junit.jupiter.api.DisplayName;
import org.junit. jupiter.api.Test;
import org.springframework.beans.factory. annotation.Autowired;
import org.springframework.dao.DataIntegrityViolationException;

import java.util.List;
import java.util.Optional;

import static org.assertj.core.api.Assertions.*;

@DisplayName("UserRepository - Tests de Integración")
class UserRepositoryTest extends AbstractIntegrationTest {
    
    @Autowired
    private UserRepository userRepository;
    
    @BeforeEach
    void setUp() {
        userRepository.deleteAll();
    }
    
    @Test
    @DisplayName("Debe guardar usuario correctamente")
    void shouldSaveUser() {
        // Given
        UserEntity user = new UserEntity("john_doe", "john@example.com", "hashedpass");
        
        // When
        UserEntity saved = userRepository.save(user);
        
        // Then
        assertThat(saved.getId()).isNotNull();
        assertThat(saved.getUsername()).isEqualTo("john_doe");
        assertThat(saved.getCreatedAt()).isNotNull();
        assertThat(saved.getActive()).isTrue();
    }
    
    @Test
    @DisplayName("Debe encontrar usuario por username")
    void shouldFindByUsername() {
        // Given
        UserEntity user = new UserEntity("jane_smith", "jane@example. com", "hashedpass");
        userRepository.save(user);
        
        // When
        Optional<UserEntity> found = userRepository.findByUsername("jane_smith");
        
        // Then
        assertThat(found).isPresent();
        assertThat(found.get().getEmail()).isEqualTo("jane@example.com");
    }
    
    @Test
    @DisplayName("Debe retornar empty si username no existe")
    void shouldReturnEmptyIfUsernameNotFound() {
        // When
        Optional<UserEntity> found = userRepository.findByUsername("nonexistent");
        
        // Then
        assertThat(found).isEmpty();
    }
    
    @Test
    @DisplayName("Debe lanzar excepción con username duplicado")
    void shouldThrowExceptionOnDuplicateUsername() {
        // Given
        userRepository.save(new UserEntity("duplicate", "user1@example.com", "pass1"));
        
        // When & Then
        assertThatThrownBy(() -> {
            userRepository.save(new UserEntity("duplicate", "user2@example.com", "pass2"));
            userRepository.flush(); // Forzar la ejecución inmediata
        }).isInstanceOf(DataIntegrityViolationException.class);
    }
    
    @Test
    @DisplayName("Debe lanzar excepción con email duplicado")
    void shouldThrowExceptionOnDuplicateEmail() {
        // Given
        userRepository.save(new UserEntity("user1", "duplicate@example.com", "pass1"));
        
        // When & Then
        assertThatThrownBy(() -> {
            userRepository.save(new UserEntity("user2", "duplicate@example. com", "pass2"));
            userRepository.flush();
        }).isInstanceOf(DataIntegrityViolationException. class);
    }
    
    @Test
    @DisplayName("Debe verificar existencia de username correctamente")
    void shouldCheckUsernameExistence() {
        // Given
        userRepository.save(new UserEntity("existing", "test@example.com", "pass"));
        
        // When & Then
        assertThat(userRepository.existsByUsername("existing")).isTrue();
        assertThat(userRepository.existsByUsername("nonexistent")).isFalse();
    }
    
    @Test
    @DisplayName("Debe encontrar solo usuarios activos")
    void shouldFindOnlyActiveUsers() {
        // Given
        UserEntity active1 = new UserEntity("active1", "active1@example.com", "pass");
        UserEntity active2 = new UserEntity("active2", "active2@example.com", "pass");
        UserEntity inactive = new UserEntity("inactive", "inactive@example.com", "pass");
        inactive.setActive(false);
        
        userRepository.saveAll(List.of(active1, active2, inactive));
        
        // When
        List<UserEntity> activeUsers = userRepository.findAllActive();
        
        // Then
        assertThat(activeUsers)
            .hasSize(2)
            .extracting(UserEntity::getUsername)
            .containsExactlyInAnyOrder("active1", "active2");
    }
    
    @Test
    @DisplayName("Debe buscar usuarios por patrón en username")
    void shouldSearchByUsernamePattern() {
        // Given
        userRepository.saveAll(List.of(
            new UserEntity("john_doe", "john@example.com", "pass"),
            new UserEntity("jane_doe", "jane@example.com", "pass"),
            new UserEntity("bob_smith", "bob@example.com", "pass")
        ));
        
        // When
        List<UserEntity> results = userRepository.searchByUsername("doe");
        
        // Then
        assertThat(results)
            .hasSize(2)
            .extracting(UserEntity:: getUsername)
            .containsExactlyInAnyOrder("john_doe", "jane_doe");
    }
    
    @Test
    @DisplayName("Debe eliminar usuario correctamente")
    void shouldDeleteUser() {
        // Given
        UserEntity user = userRepository.save(new UserEntity("todelete", "delete@example. com", "pass"));
        Long userId = user.getId();
        
        // When
        userRepository. deleteById(userId);
        
        // Then
        assertThat(userRepository.findById(userId)).isEmpty();
    }
    
    @Test
    @DisplayName("Debe actualizar usuario correctamente")
    void shouldUpdateUser() {
        // Given
        UserEntity user = userRepository.save(new UserEntity("original", "original@example.com", "pass"));
        
        // When
        user.setEmail("updated@example. com");
        user.setActive(false);
        UserEntity updated = userRepository.save(user);
        
        // Then
        UserEntity found = userRepository.findById(user.getId()).orElseThrow();
        assertThat(found.getEmail()).isEqualTo("updated@example.com");
        assertThat(found.getActive()).isFalse();
        assertThat(found.getUsername()).isEqualTo("original"); // No cambió
    }
}
```

**UserServiceIntegrationTest.java (Test End-to-End de Servicio + Repositorio)**

```java
package com.example.integration;

import com.example.entity.UserEntity;
import com. example.repository.UserRepository;
import com.example.service.UserService;
import org.junit. jupiter.api.BeforeEach;
import org.junit.jupiter.api.DisplayName;
import org.junit.jupiter.api. Test;
import org.springframework. beans.factory.annotation.Autowired;
import org.springframework. dao.DataIntegrityViolationException;

import static org.assertj.core.api.Assertions.*;

@DisplayName("UserService - Tests de Integración Completos")
class UserServiceIntegrationTest extends AbstractIntegrationTest {
    
    @Autowired
    private UserService userService;
    
    @Autowired
    private UserRepository userRepository;
    
    @BeforeEach
    void setUp() {
        userRepository.deleteAll();
    }
    
    @Test
    @DisplayName("Debe registrar usuario y persistir en BD real")
    void shouldRegisterAndPersistUser() {
        // When
        UserEntity registered = userService.registerUser("integration_user", "int@example.com", "SecurePass123");
        
        // Then - Verificar que se persistió realmente
        assertThat(registered.getId()).isNotNull();
        
        // Buscar en BD para confirmar
        UserEntity fromDb = userRepository.findById(registered.getId()).orElseThrow();
        assertThat(fromDb.getUsername()).isEqualTo("integration_user");
        assertThat(fromDb.getEmail()).isEqualTo("int@example.com");
        assertThat(fromDb.getPassword()).isNotEqualTo("SecurePass123"); // Hasheado
        assertThat(fromDb.getActive()).isTrue();
    }
    
    @Test
    @DisplayName("Debe detectar username duplicado con constraint real de BD")
    void shouldDetectDuplicateUsernameWithRealConstraint() {
        // Given
        userService.registerUser("duplicate_user", "first@example.com", "password123");
        
        // When & Then - El constraint UNIQUE de PostgreSQL debe activarse
        assertThatThrownBy(() -> 
            userService.registerUser("duplicate_user", "second@example.com", "password456")
        ).isInstanceOf(DataIntegrityViolationException.class)
         .hasMessageContaining("uk_username");
    }
    
    @Test
    @DisplayName("Debe autenticar con password correcta hasheada en BD")
    void shouldAuthenticateWithCorrectHashedPassword() {
        // Given
        String rawPassword = "MySecurePassword99";
        userService.registerUser("auth_test", "auth@example.com", rawPassword);
        
        // When
        UserEntity authenticated = userService.authenticate("auth_test", rawPassword);
        
        // Then
        assertThat(authenticated).isNotNull();
        assertThat(authenticated.getUsername()).isEqualTo("auth_test");
    }
    
    @Test
    @DisplayName("Debe rechazar autenticación con password incorrecta")
    void shouldRejectAuthenticationWithWrongPassword() {
        // Given
        userService.registerUser("auth_test2", "auth2@example.com", "CorrectPassword");
        
        // When
        UserEntity result = userService.authenticate("auth_test2", "WrongPassword");
        
        // Then
        assertThat(result).isNull();
    }
    
    @Test
    @DisplayName("Debe desactivar usuario y persistir cambio")
    void shouldDeactivateAndPersist() {
        // Given
        UserEntity user = userService.registerUser("to_deactivate", "deact@example.com", "pass123");
        Long userId = user.getId();
        
        // When
        userService.deactivateUser(userId);
        
        // Then - Verificar en BD
        UserEntity fromDb = userRepository.findById(userId).orElseThrow();
        assertThat(fromDb.getActive()).isFalse();
    }
    
    @Test
    @DisplayName("Debe rechazar autenticación de usuario desactivado")
    void shouldRejectAuthenticationForDeactivatedUser() {
        // Given
        String password = "password123";
        UserEntity user = userService.registerUser("to_deactivate2", "deact2@example.com", password);
        userService.deactivateUser(user.getId());
        
        // When
        UserEntity result = userService.authenticate("to_deactivate2", password);
        
        // Then
        assertThat(result).isNull();
    }
}
```

#### Características Avanzadas de Testcontainers

**1. Reutilización de Contenedores:**

Por defecto, Testcontainers crea un nuevo contenedor para cada clase de test. Podemos optimizar esto: 

```java
@SpringBootTest
@Testcontainers
public abstract class AbstractIntegrationTest {
    
    @Container
    @ServiceConnection
    static PostgreSQLContainer<?> postgres = new PostgreSQLContainer<>("postgres:16-alpine")
            .withDatabaseName("testdb")
            .withUsername("testuser")
            .withPassword("testpass")
            .withReuse(true); // ⚠️ Requiere testcontainers. reuse. enable=true en ~/. testcontainers. properties
}
```

**2. Ejecutar scripts SQL de inicialización:**

```java
static PostgreSQLContainer<?> postgres = new PostgreSQLContainer<>("postgres: 16-alpine")
        .withInitScript("init-test-data.sql");
```

**3. Exponer puertos para debugging:**

```java
static PostgreSQLContainer<?> postgres = new PostgreSQLContainer<>("postgres:16-alpine")
        .withExposedPorts(5432)
        .withReuse(true);

@BeforeAll
static void logConnectionInfo() {
    System.out.println("PostgreSQL disponible en: " + 
        postgres.getHost() + ":" + postgres.getFirstMappedPort());
    System.out.println("JDBC URL: " + postgres.getJdbcUrl());
}
```

Esto permite conectarte con un cliente SQL externo durante los tests.

**4. Configuración de red para múltiples contenedores:**

```java
static Network network = Network.newNetwork();

static PostgreSQLContainer<?> postgres = new PostgreSQLContainer<>("postgres:16-alpine")
        .withNetwork(network)
        .withNetworkAliases("postgres-db");

static GenericContainer<?> redis = new GenericContainer<>("redis:7-alpine")
        .withNetwork(network)
        .withNetworkAliases("redis-cache")
        .withExposedPorts(6379);
```

💡 **Nota del Profesor**: Testcontainers maneja automáticamente la limpieza de contenedores.  Si un test falla, el contenedor se elimina igualmente.  Usa `withReuse(true)` solo en desarrollo local para acelerar tests repetidos.

---

### 3.3.  Implementación en .NET

#### 🛠️ Paso a Paso:  Configuración del Proyecto

**1. Instalar paquetes necesarios:**

```bash
cd UserManagement. Tests
dotnet add package Testcontainers.PostgreSql --version 3.8.0
dotnet add package Microsoft.AspNetCore.Mvc.Testing --version 10.0.0
dotnet add package Npgsql.EntityFrameworkCore. PostgreSQL --version 10.0.0
```

**2. Actualizar UserManagement.Core.csproj:**

```xml
<Project Sdk="Microsoft.NET. Sdk">
  <PropertyGroup>
    <TargetFramework>net10.0</TargetFramework>
    <LangVersion>14. 0</LangVersion>
    <Nullable>enable</Nullable>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Microsoft.EntityFrameworkCore" Version="10.0.0" />
    <PackageReference Include="Microsoft.EntityFrameworkCore.Design" Version="10.0.0" />
    <PackageReference Include="Npgsql.EntityFrameworkCore.PostgreSQL" Version="10.0.0" />
  </ItemGroup>
</Project>
```

**3. Estructura del Proyecto:**

```
UserManagementSystem/
├── UserManagement. Core/
│   ├── Data/
│   │   ├── UserDbContext.cs
│   │   └── Entities/
│   │       └── UserEntity.cs
│   ├── Repositories/
│   │   ├── IUserRepository.cs
│   │   └── UserRepository.cs
│   └── Services/
│       └── UserService.cs
└── UserManagement.Tests/
    ├── Integration/
    │   ├── IntegrationTestBase.cs
    │   ├── UserRepositoryIntegrationTests.cs
    │   └── UserServiceIntegrationTests.cs
    └── appsettings.Test.json
```

#### Código de la Aplicación

**UserEntity.cs**

```csharp
namespace UserManagement.Core.Data.Entities;

using System.ComponentModel.DataAnnotations;
using System.ComponentModel. DataAnnotations.Schema;

[Table("users")]
public class UserEntity
{
    [Key]
    [Column("id")]
    public long Id { get; set; }

    [Required]
    [MaxLength(20)]
    [Column("username")]
    public string Username { get; set; } = string.Empty;

    [Required]
    [MaxLength(100)]
    [Column("email")]
    public string Email { get; set; } = string.Empty;

    [Required]
    [Column("password")]
    public string Password { get; set; } = string.Empty;

    [Column("is_active")]
    public bool IsActive { get; set; } = true;

    [Column("created_at")]
    public DateTime CreatedAt { get; set; } = DateTime.UtcNow;
}
```

**UserDbContext.cs**

```csharp
namespace UserManagement.Core.Data;

using Microsoft.EntityFrameworkCore;
using Entities;

public class UserDbContext(DbContextOptions<UserDbContext> options) : DbContext(options)
{
    public DbSet<UserEntity> Users => Set<UserEntity>();

    protected override void OnModelCreating(ModelBuilder modelBuilder)
    {
        base.OnModelCreating(modelBuilder);

        modelBuilder.Entity<UserEntity>(entity =>
        {
            entity.HasIndex(e => e.Username)
                .IsUnique()
                .HasDatabaseName("uk_username");

            entity.HasIndex(e => e.Email)
                .IsUnique()
                .HasDatabaseName("uk_email");

            entity.Property(e => e.CreatedAt)
                .HasDefaultValueSql("CURRENT_TIMESTAMP");
        });
    }
}
```

**UserRepository.cs**

```csharp
namespace UserManagement.Core. Repositories;

using Data;
using Data.Entities;
using Microsoft. EntityFrameworkCore;

public class UserRepository(UserDbContext context) : IUserRepository
{
    private readonly UserDbContext _context = context ??  throw new ArgumentNullException(nameof(context));

    public UserEntity Save(UserEntity user)
    {
        if (user. Id == 0)
        {
            _context.Users.Add(user);
        }
        else
        {
            _context.Users.Update(user);
        }
        
        _context.SaveChanges();
        return user;
    }

    public UserEntity?  FindById(long id)
    {
        return _context.Users. Find(id);
    }

    public UserEntity? FindByUsername(string username)
    {
        return _context.Users.FirstOrDefault(u => u.Username == username);
    }

    public UserEntity? FindByEmail(string email)
    {
        return _context.Users.FirstOrDefault(u => u.Email == email);
    }

    public void DeleteById(long id)
    {
        var user = FindById(id);
        if (user is not null)
        {
            _context.Users.Remove(user);
            _context.SaveChanges();
        }
    }

    public bool ExistsByUsername(string username)
    {
        return _context. Users.Any(u => u. Username == username);
    }

    public bool ExistsByEmail(string email)
    {
        return _context.Users.Any(u => u.Email == email);
    }

    public List<UserEntity> FindAllActive()
    {
        return _context.Users.Where(u => u.IsActive).ToList();
    }
}
```

#### Tests de Integración con Testcontainers

**IntegrationTestBase.cs**

```csharp
namespace UserManagement.Tests. Integration;

using Core.Data;
using Microsoft.EntityFrameworkCore;
using Testcontainers.PostgreSql;

[TestFixture]
public abstract class IntegrationTestBase
{
    protected PostgreSqlContainer PostgresContainer = null!;
    protected UserDbContext DbContext = null!;

    [OneTimeSetUp]
    public async Task OneTimeSetup()
    {
        // Crear contenedor PostgreSQL
        PostgresContainer = new PostgreSqlBuilder()
            .WithImage("postgres:16-alpine")
            .WithDatabase("testdb")
            .WithUsername("testuser")
            .WithPassword("testpass")
            .Build();

        // Iniciar contenedor
        await PostgresContainer.StartAsync();

        // Crear contexto de BD
        var options = new DbContextOptionsBuilder<UserDbContext>()
            .UseNpgsql(PostgresContainer.GetConnectionString())
            .Options;

        DbContext = new UserDbContext(options);

        // Crear esquema de BD
        await DbContext.Database.EnsureCreatedAsync();
    }

    [SetUp]
    public async Task Setup()
    {
        // Limpiar datos antes de cada test
        await DbContext.Users.ExecuteDeleteAsync();
    }

    [OneTimeTearDown]
    public async Task OneTimeTearDown()
    {
        await DbContext. DisposeAsync();
        await PostgresContainer.DisposeAsync();
    }
}
```

**UserRepositoryIntegrationTests.cs**

```csharp
namespace UserManagement.Tests. Integration;

using Core.Data. Entities;
using Core. Repositories;
using Microsoft.EntityFrameworkCore;

[TestFixture]
[Category("Integration")]
public class UserRepositoryIntegrationTests : IntegrationTestBase
{
    private UserRepository _repository = null!;

    [SetUp]
    public new async Task Setup()
    {
        await base.Setup();
        _repository = new UserRepository(DbContext);
    }

    [Test]
    public void Save_WithNewUser_ShouldPersistToDatabase()
    {
        // Arrange
        var user = new UserEntity
        {
            Username = "john_doe",
            Email = "john@example.com",
            Password = "hashedpass"
        };

        // Act
        var saved = _repository.Save(user);

        // Assert
        saved.Id.Should().BeGreaterThan(0);
        saved.Username.Should().Be("john_doe");

        // Verificar en BD
        var fromDb = DbContext.Users.Find(saved. Id);
        fromDb.Should().NotBeNull();
        fromDb! .Email.Should().Be("john@example.com");
    }

    [Test]
    public void Save_WithDuplicateUsername_ShouldThrowDbUpdateException()
    {
        // Arrange
        _repository.Save(new UserEntity
        {
            Username = "duplicate",
            Email = "first@example.com",
            Password = "pass1"
        });

        var duplicate = new UserEntity
        {
            Username = "duplicate",
            Email = "second@example.com",
            Password = "pass2"
        };

        // Act & Assert
        Action act = () => _repository.Save(duplicate);

        act.Should().Throw<DbUpdateException>()
            .WithInnerException<Npgsql.PostgresException>()
            .Which. ConstraintName.Should().Be("uk_username");
    }

    [Test]
    public void FindByUsername_WithExistingUser_ShouldReturnUser()
    {
        // Arrange
        _repository.Save(new UserEntity
        {
            Username = "findme",
            Email = "find@example.com",
            Password = "pass"
        });

        // Act
        var found = _repository.FindByUsername("findme");

        // Assert
        found.Should().NotBeNull();
        found!.Email.Should().Be("find@example.com");
    }

    [Test]
    public void FindByUsername_WithNonExistent_ShouldReturnNull()
    {
        // Act
        var found = _repository.FindByUsername("nonexistent");

        // Assert
        found.Should().BeNull();
    }

    [Test]
    public void ExistsByUsername_ShouldWorkCorrectly()
    {
        // Arrange
        _repository. Save(new UserEntity
        {
            Username = "exists",
            Email = "exists@example.com",
            Password = "pass"
        });

        // Act & Assert
        _repository.ExistsByUsername("exists").Should().BeTrue();
        _repository.ExistsByUsername("notexists").Should().BeFalse();
    }

    [Test]
    public void FindAllActive_ShouldReturnOnlyActiveUsers()
    {
        // Arrange
        _repository.Save(new UserEntity
        {
            Username = "active1",
            Email = "active1@example.com",
            Password = "pass",
            IsActive = true
        });

        _repository.Save(new UserEntity
        {
            Username = "active2",
            Email = "active2@example. com",
            Password = "pass",
            IsActive = true
        });

        _repository.Save(new UserEntity
        {
            Username = "inactive",
            Email = "inactive@example.com",
            Password = "pass",
            IsActive = false
        });

        // Act
        var activeUsers = _repository.FindAllActive();

        // Assert
        activeUsers.Should().HaveCount(2);
        activeUsers. Should().OnlyContain(u => u.IsActive);
        activeUsers.Select(u => u.Username).Should().Contain(new[] { "active1", "active2" });
    }

    [Test]
    public void DeleteById_ShouldRemoveFromDatabase()
    {
        // Arrange
        var user = _repository.Save(new UserEntity
        {
            Username = "todelete",
            Email = "delete@example.com",
            Password = "pass"
        });

        var userId = user.Id;

        // Act
        _repository.DeleteById(userId);

        // Assert
        _repository.FindById(userId).Should().BeNull();
    }

    [Test]
    public void Update_ShouldPersistChanges()
    {
        // Arrange
        var user = _repository.Save(new UserEntity
        {
            Username = "original",
            Email = "original@example.com",
            Password = "pass"
        });

        // Act
        user.Email = "updated@example.com";
        user.IsActive = false;
        _repository.Save(user);

        // Assert
        var updated = _repository.FindById(user.Id);
        updated!.Email. Should().Be("updated@example. com");
        updated.IsActive.Should().BeFalse();
    }
}
```

**UserServiceIntegrationTests.cs**

```csharp
namespace UserManagement.Tests.Integration;

using Core.Data.Entities;
using Core.Repositories;
using Core.Services;
using Microsoft.EntityFrameworkCore;

[TestFixture]
[Category("Integration")]
public class UserServiceIntegrationTests : IntegrationTestBase
{
    private UserService _userService = null!;
    private UserRepository _userRepository = null! ;
    private Mock<IEmailValidator> _emailValidatorMock = null!;

    [SetUp]
    public new async Task Setup()
    {
        await base.Setup();
        
        _userRepository = new UserRepository(DbContext);
        _emailValidatorMock = new Mock<IEmailValidator>();
        _emailValidatorMock.Setup(v => v.IsValid(It. IsAny<string>())).Returns(true);
        
        _userService = new UserService(_userRepository, _emailValidatorMock.Object);
    }

    [Test]
    public void RegisterUser_ShouldPersistToRealDatabase()
    {
        // Act
        var registered = _userService.RegisterUser("integration_user", "int@example.com", "SecurePass123");

        // Assert
        registered. Id.Should().BeGreaterThan(0);

        // Verificar directamente en BD
        var fromDb = DbContext.Users.Find(registered.Id);
        fromDb.Should().NotBeNull();
        fromDb!.Username.Should().Be("integration_user");
        fromDb.Password.Should().NotBe("SecurePass123"); // Debe estar hasheado
    }

    [Test]
    public void RegisterUser_WithDuplicateUsername_ShouldThrowDueToRealConstraint()
    {
        // Arrange
        _userService.RegisterUser("duplicate", "first@example.com", "pass123");

        // Act & Assert
        Action act = () => _userService.RegisterUser("duplicate", "second@example.com", "pass456");

        act.Should().Throw<DbUpdateException>()
            .WithInnerException<Npgsql.PostgresException>()
            .Which.ConstraintName.Should().Be("uk_username");
    }

    [Test]
    public void Authenticate_WithCorrectPassword_ShouldReturnUser()
    {
        // Arrange
        const string password = "MySecurePassword99";
        _userService.RegisterUser("auth_test", "auth@example.com", password);

        // Act
        var authenticated = _userService.Authenticate("auth_test", password);

        // Assert
        authenticated.Should().NotBeNull();
        authenticated! .Username.Should().Be("auth_test");
    }

    [Test]
    public void Authenticate_WithWrongPassword_ShouldReturnNull()
    {
        // Arrange
        _userService.RegisterUser("auth_test2", "auth2@example.com", "CorrectPassword");

        // Act
        var result = _userService.Authenticate("auth_test2", "WrongPassword");

        // Assert
        result.Should().BeNull();
    }

    [Test]
    public void DeactivateUser_ShouldPersistChange()
    {
        // Arrange
        var user = _userService.RegisterUser("to_deactivate", "deact@example.com", "pass123");
        var userId = user.Id;

        // Act
        _userService.DeactivateUser(userId);

        // Assert
        var fromDb = DbContext.Users.Find(userId);
        fromDb!.IsActive.Should().BeFalse();
    }

    [Test]
    public void Authenticate_WithDeactivatedUser_ShouldReturnNull()
    {
        // Arrange
        const string password = "password123";
        var user = _userService.RegisterUser("to_deactivate2", "deact2@example. com", password);
        _userService.DeactivateUser(user.Id);

        // Act
        var result = _userService.Authenticate("to_deactivate2", password);

        // Assert
        result.Should().BeNull();
    }

    [Test]
    public void CompleteUserLifecycle_ShouldWorkEndToEnd()
    {
        // 1. Registrar
        var user = _userService. RegisterUser("lifecycle", "lifecycle@example.com", "Pass1234");
        user.Id.Should().BeGreaterThan(0);

        // 2. Autenticar
        var authenticated = _userService. Authenticate("lifecycle", "Pass1234");
        authenticated.Should().NotBeNull();

        // 3. Desactivar
        _userService.DeactivateUser(user.Id);

        // 4. Verificar que no puede autenticarse
        var afterDeactivation = _userService. Authenticate("lifecycle", "Pass1234");
        afterDeactivation.Should().BeNull();

        // 5. Verificar estado en BD
        var finalState = _userRepository.FindById(user.Id);
        finalState! .IsActive.Should().BeFalse();
    }
}
```

💡 **Nota del Profesor**:  Observa cómo en . NET usamos `[OneTimeSetUp]` para crear el contenedor una sola vez para toda la clase de tests, y `[SetUp]` para limpiar los datos antes de cada test individual.  Esto optimiza el tiempo de ejecución sin sacrificar el aislamiento entre tests.

#### Ejecutar los Tests

```bash
# Ejecutar todos los tests de integración
dotnet test --filter "Category=Integration"

# Ejecutar con logs detallados
dotnet test --filter "Category=Integration" --logger "console;verbosity=detailed"

# Verificar que Docker está corriendo
docker ps
```

**Salida esperada durante la ejecución:**

```
Starting container:  postgres:16-alpine
Container started:  5a3b2c1d... 
Running tests... 
✓ Save_WithNewUser_ShouldPersistToDatabase (245 ms)
✓ Save_WithDuplicateUsername_ShouldThrowDbUpdateException (189 ms)
...
Stopping container: 5a3b2c1d...
Container removed
```

---

## 4. Automatización de APIs (Postman y Newman)

### 4.1. Guía Completa de Postman

**Postman** es la herramienta líder para testing de APIs REST. Permite:
- Enviar requests HTTP de cualquier tipo (GET, POST, PUT, DELETE, etc.)
- Organizar requests en **colecciones**
- Automatizar tests con **scripts JavaScript**
- Usar **variables** para diferentes entornos (dev, staging, prod)
- Ejecutar tests desde CLI con **Newman**

#### 🛠️ Paso a Paso:  Instalación y Configuración

**1. Instalar Postman:**
- Descargar de:  https://www.postman.com/downloads/
- O usar la versión web: https://web.postman.com/

**2. Crear Workspace:**
```
File → New Workspace → 
Name: "UD6 - Testing APIs"
Type: Personal
```

**3. Estructura de una Colección:**

```
📁 User Management API
  📁 Auth
    ├── POST Register User
    ├── POST Login
    └── POST Logout
  📁 Users
    ├── GET List All Users
    ├── GET Get User by ID
    ├── PUT Update User
    └── DELETE Delete User
  📁 Admin
    └── POST Deactivate User
```

#### Creación de Requests con Variables

**Variables de Entorno - Crear "Local Development":**

```json
{
  "base_url": "http://localhost:8080",
  "api_version": "v1",
  "admin_token": "",
  "user_id": "",
  "username": "testuser_{{$timestamp}}",
  "email": "test{{$timestamp}}@example.com"
}
```

💡 **Nota del Profesor**: `{{$timestamp}}` es una variable dinámica de Postman que genera un timestamp Unix. Útil para crear datos únicos en cada ejecución y evitar colisiones.

**Request 1: POST Register User**

```
Method: POST
URL: {{base_url}}/api/{{api_version}}/users/register

Headers:
  Content-Type:  application/json

Body (raw JSON):
{
  "username": "{{username}}",
  "email":  "{{email}}",
  "password": "SecurePass123!"
}
```

**Tests Tab (Scripts de Validación):**

```javascript
// Test 1: Verificar código de estado
pm.test("Status code is 201 Created", function () {
    pm.response.to.have. status(201);
});

// Test 2: Verificar tiempo de respuesta
pm.test("Response time is less than 500ms", function () {
    pm.expect(pm.response.responseTime).to.be.below(500);
});

// Test 3: Verificar estructura del response
pm.test("Response has required fields", function () {
    const jsonData = pm.response.json();
    pm.expect(jsonData).to.have.property('id');
    pm.expect(jsonData).to.have.property('username');
    pm.expect(jsonData).to.have.property('email');
    pm.expect(jsonData).to.have.property('createdAt');
});

// Test 4: Verificar que el password NO se devuelve
pm.test("Password is not exposed in response", function () {
    const jsonData = pm.response.json();
    pm.expect(jsonData).to.not.have.property('password');
});

// Test 5: Validar tipos de datos
pm.test("ID is a number", function () {
    const jsonData = pm.response.json();
    pm.expect(jsonData. id).to.be.a('number');
});

pm.test("Username matches request", function () {
    const jsonData = pm.response.json();
    const requestData = JSON.parse(pm.request.body. raw);
    pm.expect(jsonData.username).to.eql(requestData.username);
});

// Test 6: Guardar user_id para requests posteriores
pm.test("Save user ID to environment", function () {
    const jsonData = pm.response.json();
    pm.environment.set("user_id", jsonData.id);
    console.log("User ID saved:", jsonData.id);
});
```

**Request 2: POST Login (Autenticación)**

```
Method: POST
URL: {{base_url}}/api/{{api_version}}/auth/login

Body (raw JSON):
{
  "username": "{{username}}",
  "password": "SecurePass123!"
}
```

**Tests:**

```javascript
pm.test("Status code is 200 OK", function () {
    pm.response.to.have.status(200);
});

pm.test("Response contains access token", function () {
    const jsonData = pm.response.json();
    pm.expect(jsonData).to.have.property('token');
    pm.expect(jsonData.token).to.not.be.empty;
});

pm.test("Token is valid JWT format", function () {
    const jsonData = pm.response.json();
    const jwtRegex = /^[A-Za-z0-9-_]+\.[A-Za-z0-9-_]+\.[A-Za-z0-9-_]+$/;
    pm. expect(jsonData.token).to.match(jwtRegex);
});

// Guardar token para requests autenticados
pm.test("Save token to environment", function () {
    const jsonData = pm.response.json();
    pm.environment.set("admin_token", jsonData.token);
    console.log("Token saved");
});
```

**Request 3: GET Get User by ID (Autenticado)**

```
Method: GET
URL: {{base_url}}/api/{{api_version}}/users/{{user_id}}

Headers:
  Authorization: Bearer {{admin_token}}
```

**Tests:**

```javascript
pm.test("Status code is 200 OK", function () {
    pm.response.to.have.status(200);
});

pm.test("User data is correct", function () {
    const jsonData = pm.response.json();
    pm.expect(jsonData. id).to.eql(parseInt(pm.environment.get("user_id")));
    pm.expect(jsonData.username).to.eql(pm.environment.get("username"));
});

pm.test("Response schema is valid", function () {
    const schema = {
        type: "object",
        required: ["id", "username", "email", "isActive", "createdAt"],
        properties: {
            id: { type: "number" },
            username: { type: "string", minLength: 3, maxLength: 20 },
            email: { type: "string", format: "email" },
            isActive: { type: "boolean" },
            createdAt: { type: "string", format: "date-time" }
        }
    };
    
    pm.response.to.have.jsonSchema(schema);
});
```

#### Validación de Esquemas JSON Avanzada

**Request 4: GET List All Users**

```
Method: GET
URL: {{base_url}}/api/{{api_version}}/users? page=1&size=10

Headers:
  Authorization: Bearer {{admin_token}}
```

**Tests con Validación de Schema:**

```javascript
pm.test("Status code is 200 OK", function () {
    pm.response.to.have.status(200);
});

pm.test("Response is an array", function () {
    const jsonData = pm.response. json();
    pm.expect(jsonData).to.be.an('array');
});

pm.test("All users have valid structure", function () {
    const jsonData = pm.response.json();
    
    jsonData.forEach(function(user) {
        pm.expect(user).to.have.all.keys('id', 'username', 'email', 'isActive', 'createdAt');
        pm.expect(user.id).to.be.a('number');
        pm.expect(user. username).to.be.a('string').and.to.have.lengthOf. at.least(3);
        pm.expect(user.email).to.match(/^[^\s@]+@[^\s@]+\.[^\s@]+$/);
        pm.expect(user.isActive).to.be.a('boolean');
    });
});

pm.test("List contains our test user", function () {
    const jsonData = pm.response.json();
    const testUserId = parseInt(pm.environment. get("user_id"));
    const userExists = jsonData.some(user => user.id === testUserId);
    pm.expect(userExists).to.be.true;
});
```

#### Scripts Pre-request (Preparación)

A veces necesitamos generar datos dinámicos ANTES de enviar el request:

**Pre-request Script en "POST Register User":**

```javascript
// Generar username único
const randomString = Math.random().toString(36).substring(7);
pm.environment.set("username", `user_${randomString}`);

// Generar email único
pm.environment. set("email", `${randomString}@testdomain.com`);

// Generar password complejo
function generatePassword() {
    const lowercase = 'abcdefghijklmnopqrstuvwxyz';
    const uppercase = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ';
    const numbers = '0123456789';
    const symbols = '!@#$%^&*';
    const allChars = lowercase + uppercase + numbers + symbols;
    
    let password = '';
    password += lowercase[Math.floor(Math.random() * lowercase.length)];
    password += uppercase[Math.floor(Math.random() * uppercase.length)];
    password += numbers[Math.floor(Math.random() * numbers.length)];
    password += symbols[Math.floor(Math.random() * symbols.length)];
    
    for (let i = 4; i < 12; i++) {
        password += allChars[Math.floor(Math.random() * allChars.length)];
    }
    
    return password. split('').sort(() => 0.5 - Math.random()).join('');
}

pm.environment.set("password", generatePassword());

console.log("Generated credentials:");
console.log("Username:", pm.environment.get("username"));
console.log("Email:", pm.environment.get("email"));
console.log("Password:", pm. environment.get("password"));
```

#### Pruebas de Errores (Casos Negativos)

**Request 5: POST Register User - Duplicate Username (Expected Failure)**

```
Method: POST
URL: {{base_url}}/api/{{api_version}}/users/register

Body (raw JSON):
{
  "username": "{{username}}",
  "email": "different_{{$timestamp}}@example.com",
  "password": "SecurePass123!"
}
```

**Tests:**

```javascript
pm.test("Status code is 409 Conflict", function () {
    pm.response.to.have.status(409);
});

pm.test("Error message indicates duplicate username", function () {
    const jsonData = pm.response. json();
    pm.expect(jsonData).to.have.property('error');
    pm.expect(jsonData.error).to.include('username');
    pm.expect(jsonData.error. toLowerCase()).to.match(/already exists|duplicate|taken/);
});

pm.test("Response has error structure", function () {
    const jsonData = pm.response.json();
    pm.expect(jsonData).to.have.property('error');
    pm.expect(jsonData).to.have.property('timestamp');
    pm.expect(jsonData).to.have.property('path');
});
```

**Request 6: POST Register User - Invalid Email**

```
Body (raw JSON):
{
  "username": "validuser_{{$timestamp}}",
  "email": "not-an-email",
  "password": "SecurePass123!"
}
```

**Tests:**

```javascript
pm.test("Status code is 400 Bad Request", function () {
    pm.response.to.have.status(400);
});

pm.test("Error indicates invalid email format", function () {
    const jsonData = pm.response.json();
    pm.expect(jsonData. error. toLowerCase()).to.match(/email|format|invalid/);
});
```

**Request 7: POST Register User - Short Password**

```
Body (raw JSON):
{
  "username": "validuser_{{$timestamp}}",
  "email": "valid{{$timestamp}}@example.com",
  "password": "short"
}
```

**Tests:**

```javascript
pm.test("Status code is 400 Bad Request", function () {
    pm.response.to.have.status(400);
});

pm.test("Error indicates password length requirement", function () {
    const jsonData = pm.response.json();
    pm.expect(jsonData.error.toLowerCase()).to.match(/password.*8|8.*characters/);
});
```

**Request 8: GET User - Unauthorized (No Token)**

```
Method: GET
URL: {{base_url}}/api/{{api_version}}/users/{{user_id}}

Headers:
  (Sin Authorization header)
```

**Tests:**

```javascript
pm.test("Status code is 401 Unauthorized", function () {
    pm.response.to.have.status(401);
});

pm.test("Error indicates missing authentication", function () {
    const jsonData = pm.response.json();
    pm.expect(jsonData. error. toLowerCase()).to.match(/unauthorized|token|authentication/);
});
```

#### Collection-level Tests (Tests Globales)

Puedes definir tests que se ejecuten para **todos** los requests de la colección:

**Configuración:**
1. Click derecho en la colección → **Edit**
2. Tab **Tests**

**Script Global:**

```javascript
// Verificar que todas las respuestas son JSON
pm.test("[Global] Content-Type is application/json", function () {
    pm.response.to.have.header("Content-Type");
    pm.expect(pm.response.headers. get("Content-Type")).to.include("application/json");
});

// Verificar headers de seguridad
pm.test("[Global] Security headers are present", function () {
    pm.response.to.have.header("X-Content-Type-Options");
    pm.response.to.have.header("X-Frame-Options");
});

// Log de todas las respuestas
console.log(`[${pm.info.requestName}] Status: ${pm. response.code} | Time: ${pm.response.responseTime}ms`);
```

#### Variables de Entorno:  Desarrollo vs Producción

**Environment "Local Development":**
```json
{
  "base_url":  "http://localhost:8080",
  "api_version": "v1",
  "timeout": 500
}
```

**Environment "Staging":**
```json
{
  "base_url": "https://staging-api.example.com",
  "api_version": "v1",
  "timeout": 2000
}
```

**Environment "Production":**
```json
{
  "base_url":  "https://api.example.com",
  "api_version":  "v1",
  "timeout": 3000
}
```

Cambiar entre ambientes:  Click en el dropdown superior derecho → Seleccionar entorno. 

💡 **Nota del Profesor**:  NUNCA guardes tokens o credenciales reales en entornos de Postman si usas workspaces compartidos. Usa variables locales o archivos de configuración externos.

---

### 4. 2. Newman: CLI para Automatización

**Newman** es el runner de línea de comandos de Postman.  Permite ejecutar colecciones en: 
- Pipelines CI/CD (GitHub Actions, GitLab CI, Jenkins)
- Contenedores Docker
- Scripts de automatización
- Pruebas de regresión programadas

#### 🛠️ Paso a Paso:  Instalación y Uso de Newman

**1. Instalar Newman globalmente:**

```bash
npm install -g newman
```

**Verificar instalación:**
```bash
newman --version
# newman/6.1.1
```

**2. Exportar Colección de Postman:**

En Postman:
1. Click derecho en la colección → **Export**
2. Seleccionar **Collection v2.1**
3. Guardar como `user-management-api.postman_collection.json`

**3. Exportar Environment:**

1. Click en el ícono de entornos (arriba derecha)
2. Click en los tres puntos junto a "Local Development"
3. **Export**
4. Guardar como `local-dev.postman_environment.json`

**4. Estructura del Proyecto:**

```
proyecto-api-tests/
├── collections/
│   └── user-management-api.postman_collection.json
├── environments/
│   ├── local-dev.postman_environment.json
│   ├── staging.postman_environment.json
│   └── production.postman_environment.json
├── reports/
│   └── (reportes generados)
├── run-tests.sh
└── Dockerfile
```

#### Ejecutar Tests con Newman

**Comando básico:**

```bash
newman run collections/user-management-api.postman_collection.json \
  -e environments/local-dev.postman_environment.json
```

**Salida esperada:**

```
┌─────────────────────────┬──────────────────┬──────────────────┐
│                         │         executed │           failed │
├─────────────────────────┼──────────────────┼──────────────────┤
│              iterations │                1 │                0 │
├─────────────────────────┼──────────────────┼──────────────────┤
│                requests │                8 │                0 │
├─────────────────────────┼──────────────────┼──────────────────┤
│            test-scripts │               16 │                0 │
├─────────────────────────┼──────────────────┼──────────────────┤
│      prerequest-scripts │                8 │                0 │
├─────────────────────────┼──────────────────┼──────────────────┤
│              assertions │               45 │                0 │
├─────────────────────────┴──────────────────┴──────────────────┤
│ total run duration: 2.3s                                      │
├───────────────────────────────────────────────────────────────┤
│ total data received: 1.24kB (approx)                          │
├───────────────────────────────────────────────────────────────┤
│ average response time: 285ms [min: 145ms, max: 456ms, s.d.: 98ms] │
└───────────────────────────────────────────────────────────────┘
```

#### Opciones Avanzadas de Newman

**1. Ejecutar con iteraciones múltiples:**

```bash
newman run collections/user-management-api.postman_collection.json \
  -e environments/local-dev.postman_environment.json \
  -n 10 \
  --delay-request 200
```

Esto ejecuta toda la colección 10 veces con 200ms de pausa entre requests.

**2. Ejecutar solo una carpeta específica:**

```bash
newman run collections/user-management-api.postman_collection.json \
  -e environments/local-dev.postman_environment. json \
  --folder "Auth"
```

**3. Generar reportes HTML:**

Instalar reporter HTML:
```bash
npm install -g newman-reporter-html
```

Ejecutar con reporte: 
```bash
newman run collections/user-management-api.postman_collection.json \
  -e environments/local-dev.postman_environment.json \
  -r html \
  --reporter-html-export reports/test-report.html
```

**4. Generar reportes JSON para CI/CD:**

```bash
newman run collections/user-management-api.postman_collection.json \
  -e environments/local-dev.postman_environment. json \
  -r json \
  --reporter-json-export reports/test-results.json
```

**5. Opciones de verbosidad:**

```bash
# Modo silencioso (solo errores)
newman run collection. json -e env.json --silent

# Modo completo con detalles de cada request
newman run collection.json -e env.json --verbose

# Sin colores (para logs de CI)
newman run collection.json -e env.json --no-color
```

**6. Bailout (detener en primer fallo):**

```bash
newman run collections/user-management-api.postman_collection.json \
  -e environments/local-dev. postman_environment.json \
  --bail
```

**7. Timeout personalizado:**

```bash
newman run collections/user-management-api. postman_collection.json \
  -e environments/local-dev.postman_environment.json \
  --timeout-request 10000
```

#### Script de Automatización Completo

**run-tests.sh (Linux/macOS):**

```bash
#!/bin/bash

# Colores para output
GREEN='\033[0;32m'
RED='\033[0;31m'
YELLOW='\033[1;33m'
NC='\033[0m' # No Color

# Configuración
COLLECTION="collections/user-management-api.postman_collection.json"
ENVIRONMENT="environments/local-dev. postman_environment.json"
REPORTS_DIR="reports"
TIMESTAMP=$(date +"%Y%m%d_%H%M%S")
REPORT_FILE="${REPORTS_DIR}/report_${TIMESTAMP}.html"
JSON_REPORT="${REPORTS_DIR}/results_${TIMESTAMP}.json"

# Crear directorio de reportes si no existe
mkdir -p "$REPORTS_DIR"

echo -e "${YELLOW}========================================${NC}"
echo -e "${YELLOW}  Iniciando Tests de API con Newman${NC}"
echo -e "${YELLOW}========================================${NC}"
echo ""

# Verificar que el backend está corriendo
echo -e "${YELLOW}Verificando que el backend está activo...${NC}"
if curl -s -o /dev/null -w "%{http_code}" http://localhost:8080/actuator/health | grep -q "200"; then
    echo -e "${GREEN}✓ Backend activo${NC}"
else
    echo -e "${RED}✗ Backend no responde en http://localhost:8080${NC}"
    echo -e "${RED}  Por favor inicia el backend antes de ejecutar los tests${NC}"
    exit 1
fi

echo ""

# Ejecutar Newman
echo -e "${YELLOW}Ejecutando colección de tests...${NC}"
newman run "$COLLECTION" \
  -e "$ENVIRONMENT" \
  -r html,json,cli \
  --reporter-html-export "$REPORT_FILE" \
  --reporter-json-export "$JSON_REPORT" \
  --color on \
  --delay-request 100

# Capturar código de salida
EXIT_CODE=$? 

echo ""
echo -e "${YELLOW}========================================${NC}"

# Evaluar resultado
if [ $EXIT_CODE -eq 0 ]; then
    echo -e "${GREEN}✓ TODOS LOS TESTS PASARON${NC}"
    echo -e "${GREEN}  Reporte HTML:  $REPORT_FILE${NC}"
    
    # Extraer métricas del JSON
    TOTAL_TESTS=$(jq '.run.stats.assertions. total' "$JSON_REPORT")
    FAILED_TESTS=$(jq '.run.stats.assertions.failed' "$JSON_REPORT")
    AVG_RESPONSE=$(jq '.run.timings.responseAverage' "$JSON_REPORT")
    
    echo ""
    echo -e "Métricas:"
    echo -e "  Total de aserciones: $TOTAL_TESTS"
    echo -e "  Aserciones fallidas: $FAILED_TESTS"
    echo -e "  Tiempo promedio de respuesta: ${AVG_RESPONSE}ms"
else
    echo -e "${RED}✗ ALGUNOS TESTS FALLARON${NC}"
    echo -e "${RED}  Revisa el reporte:  $REPORT_FILE${NC}"
fi

echo -e "${YELLOW}========================================${NC}"

exit $EXIT_CODE
```

**run-tests.ps1 (Windows PowerShell):**

```powershell
# Configuración
$COLLECTION = "collections\user-management-api.postman_collection.json"
$ENVIRONMENT = "environments\local-dev.postman_environment.json"
$REPORTS_DIR = "reports"
$TIMESTAMP = Get-Date -Format "yyyyMMdd_HHmmss"
$REPORT_FILE = "$REPORTS_DIR\report_$TIMESTAMP.html"
$JSON_REPORT = "$REPORTS_DIR\results_$TIMESTAMP.json"

# Crear directorio de reportes
New-Item -ItemType Directory -Force -Path $REPORTS_DIR | Out-Null

Write-Host "========================================" -ForegroundColor Yellow
Write-Host "  Iniciando Tests de API con Newman" -ForegroundColor Yellow
Write-Host "========================================" -ForegroundColor Yellow
Write-Host ""

# Verificar backend
Write-Host "Verificando que el backend está activo..." -ForegroundColor Yellow
try {
    $response = Invoke-WebRequest -Uri "http://localhost:8080/actuator/health" -Method Get -TimeoutSec 5
    if ($response.StatusCode -eq 200) {
        Write-Host "✓ Backend activo" -ForegroundColor Green
    }
} catch {
    Write-Host "✗ Backend no responde en http://localhost:8080" -ForegroundColor Red
    Write-Host "  Por favor inicia el backend antes de ejecutar los tests" -ForegroundColor Red
    exit 1
}

Write-Host ""

# Ejecutar Newman
Write-Host "Ejecutando colección de tests..." -ForegroundColor Yellow
newman run $COLLECTION `
  -e $ENVIRONMENT `
  -r html,json,cli `
  --reporter-html-export $REPORT_FILE `
  --reporter-json-export $JSON_REPORT `
  --color on `
  --delay-request 100

$EXIT_CODE = $LASTEXITCODE

Write-Host ""
Write-Host "========================================" -ForegroundColor Yellow

if ($EXIT_CODE -eq 0) {
    Write-Host "✓ TODOS LOS TESTS PASARON" -ForegroundColor Green
    Write-Host "  Reporte HTML: $REPORT_FILE" -ForegroundColor Green
    
    # Extraer métricas
    $jsonContent = Get-Content $JSON_REPORT | ConvertFrom-Json
    $totalTests = $jsonContent.run.stats.assertions.total
    $failedTests = $jsonContent.run.stats.assertions.failed
    $avgResponse = [math]::Round($jsonContent. run.timings.responseAverage, 2)
    
    Write-Host ""
    Write-Host "Métricas:"
    Write-Host "  Total de aserciones: $totalTests"
    Write-Host "  Aserciones fallidas: $failedTests"
    Write-Host "  Tiempo promedio de respuesta: ${avgResponse}ms"
} else {
    Write-Host "✗ ALGUNOS TESTS FALLARON" -ForegroundColor Red
    Write-Host "  Revisa el reporte: $REPORT_FILE" -ForegroundColor Red
}

Write-Host "========================================" -ForegroundColor Yellow

exit $EXIT_CODE
```

**Hacer ejecutable (Linux/macOS):**
```bash
chmod +x run-tests.sh
```

**Ejecutar:**
```bash
# Linux/macOS
./run-tests.sh

# Windows
.\run-tests.ps1
```

#### Newman en Docker

**Dockerfile:**

```dockerfile
FROM node:20-alpine

# Instalar Newman y reporters
RUN npm install -g newman newman-reporter-html newman-reporter-json

# Crear directorio de trabajo
WORKDIR /etc/newman

# Copiar colecciones y entornos
COPY collections/ ./collections/
COPY environments/ ./environments/

# Crear directorio para reportes
RUN mkdir -p reports

# Script de entrada
COPY docker-entrypoint.sh /usr/local/bin/
RUN chmod +x /usr/local/bin/docker-entrypoint.sh

ENTRYPOINT ["docker-entrypoint.sh"]
```

**docker-entrypoint.sh:**

```bash
#!/bin/sh

COLLECTION=${COLLECTION:-"collections/user-management-api.postman_collection. json"}
ENVIRONMENT=${ENVIRONMENT:-"environments/local-dev. postman_environment.json"}

echo "Running Newman with:"
echo "  Collection: $COLLECTION"
echo "  Environment: $ENVIRONMENT"
echo ""

newman run "$COLLECTION" \
  -e "$ENVIRONMENT" \
  -r html,json,cli \
  --reporter-html-export reports/report.html \
  --reporter-json-export reports/results.json \
  --color on \
  "$@"
```

**docker-compose.yml (para ejecutar tests contra servicios):**

```yaml
version: '3.8'

services:
  backend:
    image: user-management-api:latest
    ports:
      - "8080:8080"
    environment: 
      - SPRING_PROFILES_ACTIVE=test
      - DATABASE_URL=jdbc:postgresql://postgres:5432/testdb
    depends_on:
      - postgres
    healthcheck:
      test: ["CMD", "curl", "-f", "http://localhost:8080/actuator/health"]
      interval:  5s
      timeout: 3s
      retries: 10

  postgres:
    image: postgres:16-alpine
    environment:
      - POSTGRES_DB=testdb
      - POSTGRES_USER=testuser
      - POSTGRES_PASSWORD=testpass
    ports: 
      - "5432:5432"

  newman: 
    build: .
    environment:
      - COLLECTION=collections/user-management-api. postman_collection.json
      - ENVIRONMENT=environments/docker. postman_environment.json
    volumes:
      - ./reports:/etc/newman/reports
    depends_on:
      backend:
        condition: service_healthy
    command: ["--bail", "--delay-request", "200"]
```

**environments/docker.postman_environment. json:**

```json
{
  "id": "docker-env",
  "name": "Docker Environment",
  "values":  [
    {
      "key":  "base_url",
      "value":  "http://backend:8080",
      "enabled": true
    },
    {
      "key": "api_version",
      "value": "v1",
      "enabled": true
    }
  ]
}
```

**Ejecutar todo el stack:**

```bash
# Construir imágenes
docker-compose build

# Ejecutar tests
docker-compose up --abort-on-container-exit

# Ver resultados
ls -la reports/
```

**Limpiar después:**

```bash
docker-compose down -v
```

💡 **Nota del Profesor**:  Esta configuración es ideal para CI/CD.  Los tests se ejecutan en un entorno completamente aislado, reproducible y sin dependencias locales.  Cada pipeline execution arranca servicios limpios, ejecuta tests y destruye todo al finalizar.

#### Integración con GitHub Actions

**. github/workflows/api-tests.yml:**

```yaml
name: API Tests with Newman

on:
  push: 
    branches: [ main, develop ]
  pull_request: 
    branches: [ main ]

jobs:
  api-tests:
    runs-on: ubuntu-latest

    services:
      postgres:
        image: postgres:16-alpine
        env:
          POSTGRES_DB: testdb
          POSTGRES_USER: testuser
          POSTGRES_PASSWORD: testpass
        ports:
          - 5432:5432
        options: >-
          --health-cmd pg_isready
          --health-interval 10s
          --health-timeout 5s
          --health-retries 5

    steps:
      - name: Checkout code
        uses:  actions/checkout@v4

      - name: Set up Java 21
        uses: actions/setup-java@v4
        with: 
          java-version: '21'
          distribution: 'temurin'

      - name:  Build and start backend
        run: |
          ./gradlew bootJar
          java -jar build/libs/*. jar &
          sleep 30

      - name: Wait for backend to be ready
        run: |
          for i in {1..30}; do
            if curl -s http://localhost:8080/actuator/health | grep -q "UP"; then
              echo "Backend is ready"
              exit 0
            fi
            echo "Waiting for backend...  ($i/30)"
            sleep 2
          done
          echo "Backend failed to start"
          exit 1

      - name: Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: '20'

      - name: Install Newman
        run: npm install -g newman newman-reporter-htmlextra

      - name: Run API tests
        run: |
          newman run collections/user-management-api.postman_collection.json \
            -e environments/ci-cd.postman_environment.json \
            -r htmlextra,json,cli \
            --reporter-htmlextra-export reports/report.html \
            --reporter-json-export reports/results.json \
            --bail

      - name: Upload test reports
        if: always()
        uses: actions/upload-artifact@v4
        with:
          name: newman-reports
          path: reports/

      - name: Comment PR with results
        if: github.event_name == 'pull_request'
        uses: actions/github-script@v7
        with:
          script: |
            const fs = require('fs');
            const results = JSON.parse(fs.readFileSync('reports/results.json', 'utf8'));
            
            const stats = results.run.stats;
            const summary = `
            ## 🧪 API Test Results
            
            - **Requests:** ${stats.requests.total} (${stats.requests.failed} failed)
            - **Tests:** ${stats.assertions.total} (${stats.assertions.failed} failed)
            - **Average Response Time:** ${Math.round(results.run.timings.responseAverage)}ms
            
            ${stats.assertions.failed === 0 ? '✅ All tests passed!' : '❌ Some tests failed'}
            `;
            
            github.rest.issues.createComment({
              issue_number: context.issue. number,
              owner: context.repo.owner,
              repo: context.repo.repo,
              body: summary
            });
```

#### Buenas Prácticas con Newman

**1. Organización de colecciones:**
- Una colección por módulo/dominio
- Carpetas para agrupar requests relacionados
- Nombres descriptivos:  "POST User Registration - Valid Data"

**2. Gestión de secretos:**
```bash
# Usar variables de entorno del sistema
newman run collection.json \
  --env-var "api_key=$API_KEY" \
  --env-var "db_password=$DB_PASSWORD"
```

**3. Data-driven testing con archivos CSV:**

**users-data.csv:**
```csv
username,email,password
john_doe,john@example.com,SecurePass123!
jane_smith,jane@example.com,MyPassword99
bob_wilson,bob@example.com,BobPass2024! 
```

**Ejecutar:**
```bash
newman run collection.json \
  -d users-data.csv \
  -n 3
```

En los requests, usa `{{username}}`, `{{email}}`, `{{password}}` y Newman iterará sobre cada fila.

**4. Captura de métricas para análisis:**

```bash
newman run collection.json \
  -e env.json \
  -r json \
  --reporter-json-export results.json

# Extraer métricas con jq
cat results.json | jq '.run.stats'
cat results.json | jq '.run.timings'
cat results.json | jq '.run.executions[].response.responseTime' | jq -s 'add/length'
```

---

**🎯 Resumen del Bloque 3:**

✅ **Postman** permite diseñar, organizar y ejecutar tests de APIs con: 
- Variables de entorno para múltiples contextos
- Scripts de validación con `pm.test()`
- Aserciones sobre status, tiempos, estructura y contenido
- Pruebas de casos positivos y negativos

✅ **Newman** automatiza la ejecución de colecciones: 
- Desde línea de comandos
- En contenedores Docker
- En pipelines CI/CD
- Con reportes HTML/JSON

✅ **Estrategias clave:**
- Tests globales para verificaciones comunes
- Pre-request scripts para datos dinámicos
- Validación de esquemas JSON
- Tests de seguridad (headers, tokens)
- Integración con servicios mediante Docker Compose

💡 **Nota del Profesor Final del Bloque**:  La combinación Postman + Newman es estándar en la industria.  Aprende a escribir tests robustos en Postman y Newman los ejecutará consistentemente en cualquier entorno.  Esta es la base del testing automatizado de APIs en equipos profesionales.

---

## 5. Validación de Interfaz con Cypress

### 5.1. Fundamentos de Cypress

**Cypress** es un framework moderno de testing end-to-end (E2E) diseñado específicamente para aplicaciones web.  A diferencia de Selenium, Cypress ejecuta los tests **dentro del navegador**, proporcionando: 

- ✅ **Ejecución rápida**:  Sin drivers externos ni protocolos lentos
- ✅ **Debugging sencillo**: Snapshots en cada paso, DevTools integrado
- ✅ **Esperas automáticas**: No más `sleep()` o esperas explícitas
- ✅ **Time Travel**: Revisa cada comando ejecutado
- ✅ **Screenshots y videos**: Automáticos en fallos

#### Diferencias clave:  Cypress vs Selenium

| Aspecto           | Cypress                         | Selenium                           |
| ----------------- | ------------------------------- | ---------------------------------- |
| **Arquitectura**  | Corre dentro del navegador      | Controla navegador externamente    |
| **Lenguaje**      | JavaScript/TypeScript           | Múltiples (Java, Python, C#, etc.) |
| **Esperas**       | Automáticas e inteligentes      | Manuales (WebDriverWait)           |
| **Debugging**     | Interactivo con Time Travel     | Complejo, requiere breakpoints     |
| **Velocidad**     | Muy rápido                      | Más lento                          |
| **Cross-browser** | Chrome, Edge, Firefox, Electron | Todos los navegadores              |

💡 **Nota del Profesor**:  Cypress es ideal para aplicaciones modernas (React, Vue, Angular). Su filosofía es "developer-first":  tests fáciles de escribir y debuggear.  Selenium sigue siendo necesario para testing cross-browser exhaustivo o aplicaciones legacy.

---

#### 🛠️ Paso a Paso:  Instalación y Configuración

**1. Crear proyecto de testing:**

```bash
# Crear directorio
mkdir cypress-tests-user-management
cd cypress-tests-user-management

# Inicializar proyecto Node.js
npm init -y
```

**2. Instalar Cypress:**

```bash
npm install cypress --save-dev
```

**3. Abrir Cypress por primera vez:**

```bash
npx cypress open
```

Esto crea la estructura de carpetas: 

```
cypress-tests-user-management/
├── cypress/
│   ├── e2e/
│   │   └── (aquí van los tests)
│   ├── fixtures/
│   │   └── (datos de prueba JSON)
│   ├── support/
│   │   ├── commands.js (comandos personalizados)
│   │   └── e2e. js (configuración global)
│   └── screenshots/ (generados automáticamente)
│   └── videos/ (generados automáticamente)
├── cypress.config.js
├── package.json
└── node_modules/
```

**4. Configuración básica (cypress.config.js):**

```javascript
const { defineConfig } = require('cypress');

module.exports = defineConfig({
  e2e: {
    // URL base de la aplicación
    baseUrl:  'http://localhost:3000',
    
    // Viewport por defecto
    viewportWidth:  1280,
    viewportHeight: 720,
    
    // Tiempo de espera por defecto
    defaultCommandTimeout:  10000,
    
    // Captura de pantalla en fallos
    screenshotOnRunFailure: true,
    
    // Video de ejecución
    video: true,
    videoCompression: 32,
    
    // Configuración de reintentos
    retries: {
      runMode: 2,  // CI/CD
      openMode: 0  // Desarrollo local
    },
    
    // Variables de entorno
    env: {
      apiUrl: 'http://localhost:8080/api/v1',
      adminUsername: 'admin',
      adminPassword: 'Admin123!'
    },
    
    setupNodeEvents(on, config) {
      // Aquí puedes agregar plugins
      return config;
    },
  },
});
```

**5. Instalar dependencias adicionales (TypeScript support - opcional pero recomendado):**

```bash
npm install --save-dev typescript @cypress/webpack-preprocessor
```

**tsconfig.json:**

```json
{
  "compilerOptions": {
    "target": "es5",
    "lib": ["es5", "dom"],
    "types": ["cypress", "node"]
  },
  "include": ["cypress/**/*.ts"]
}
```

---

### Selectores Inteligentes en Cypress

La clave de tests E2E robustos está en usar **selectores resilientes** que no se rompan con cambios en el diseño. 

#### Jerarquía de Selectores (de mejor a peor)

1. **`data-cy` attributes** ⭐ (Mejor práctica)
2. **`data-test` attributes**
3. **IDs únicos** (`#user-form`)
4. **Clases específicas** (`.user-registration-form`)
5. **Texto visible** (`cy.contains('Submit')`)
6. **Selectores CSS complejos** ❌ (Frágiles)

#### Ejemplo de HTML preparado para testing:

```html
<div class="user-registration-page" data-cy="registration-page">
  <h1>User Registration</h1>
  
  <form data-cy="registration-form" id="user-form">
    <div class="form-group">
      <label for="username">Username</label>
      <input 
        type="text" 
        id="username" 
        name="username"
        data-cy="username-input"
        placeholder="Enter username"
      />
      <span class="error" data-cy="username-error"></span>
    </div>
    
    <div class="form-group">
      <label for="email">Email</label>
      <input 
        type="email" 
        id="email" 
        name="email"
        data-cy="email-input"
        placeholder="Enter email"
      />
      <span class="error" data-cy="email-error"></span>
    </div>
    
    <div class="form-group">
      <label for="password">Password</label>
      <input 
        type="password" 
        id="password" 
        name="password"
        data-cy="password-input"
        placeholder="Enter password"
      />
      <span class="error" data-cy="password-error"></span>
    </div>
    
    <button 
      type="submit" 
      data-cy="submit-button"
      class="btn btn-primary"
    >
      Register
    </button>
  </form>
  
  <div class="alert alert-success" data-cy="success-message" style="display: none;">
    Registration successful! 
  </div>
  
  <div class="alert alert-danger" data-cy="error-message" style="display: none;">
    Registration failed. 
  </div>
</div>
```

#### Comandos de Selección en Cypress

```javascript
// Por data-cy (recomendado)
cy.get('[data-cy="username-input"]')

// Por ID
cy.get('#username')

// Por clase
cy.get('. user-registration-form')

// Por tipo de elemento
cy.get('input[type="email"]')

// Por texto visible
cy.contains('Register')
cy.contains('button', 'Register')

// Combinaciones
cy.get('[data-cy="registration-form"]').find('[data-cy="submit-button"]')

// Primer/último elemento
cy.get('. user-row').first()
cy.get('.user-row').last()

// Por índice
cy.get('.user-row').eq(2)

// Filtros
cy.get('. user-row').filter('.active')

// Hermanos
cy.get('[data-cy="username-input"]').siblings('label')

// Padres
cy.get('[data-cy="username-input"]').parent()
cy.get('[data-cy="username-input"]').parents('. form-group')

// Closest (padre más cercano que cumple selector)
cy.get('[data-cy="username-input"]').closest('form')
```

---

### Comandos de Acción Fundamentales

#### Interacción con Formularios

```javascript
describe('User Registration Form', () => {
  beforeEach(() => {
    // Visitar la página antes de cada test
    cy.visit('/register');
  });

  it('should fill and submit registration form', () => {
    // Escribir texto
    cy.get('[data-cy="username-input"]').type('john_doe');
    
    // Escribir con delay (simula usuario real)
    cy.get('[data-cy="email-input"]').type('john@example.com', { delay: 100 });
    
    // Escribir password (oculta de logs)
    cy.get('[data-cy="password-input"]').type('SecurePass123!', { log: false });
    
    // Limpiar y escribir de nuevo
    cy.get('[data-cy="username-input"]').clear().type('jane_doe');
    
    // Click en botón
    cy.get('[data-cy="submit-button"]').click();
    
    // Verificar resultado
    cy.get('[data-cy="success-message"]').should('be.visible');
  });

  it('should handle select dropdown', () => {
    cy.visit('/profile');
    
    // Seleccionar por valor
    cy.get('[data-cy="country-select"]').select('ES');
    
    // Seleccionar por texto visible
    cy.get('[data-cy="country-select"]').select('Spain');
    
    // Seleccionar por índice
    cy.get('[data-cy="country-select"]').select(2);
  });

  it('should handle checkboxes and radios', () => {
    // Marcar checkbox
    cy.get('[data-cy="terms-checkbox"]').check();
    
    // Desmarcar
    cy.get('[data-cy="newsletter-checkbox"]').uncheck();
    
    // Verificar estado
    cy.get('[data-cy="terms-checkbox"]').should('be.checked');
    
    // Radio buttons
    cy.get('[data-cy="gender-male"]').check();
    cy.get('[data-cy="gender-male"]').should('be.checked');
    cy.get('[data-cy="gender-female"]').should('not.be.checked');
  });

  it('should handle file uploads', () => {
    // Subir archivo desde fixtures
    cy.get('[data-cy="avatar-upload"]')
      .selectFile('cypress/fixtures/avatar. png');
    
    // Simular drag & drop
    cy.get('[data-cy="document-dropzone"]')
      .selectFile('cypress/fixtures/document. pdf', { 
        action: 'drag-drop' 
      });
  });
});
```

#### Navegación y URLs

```javascript
describe('Navigation Tests', () => {
  it('should navigate between pages', () => {
    cy.visit('/');
    
    // Click en link
    cy.get('[data-cy="register-link"]').click();
    
    // Verificar URL
    cy.url().should('include', '/register');
    
    // Navegar directamente
    cy.visit('/login');
    cy.url().should('eq', 'http://localhost:3000/login');
    
    // Botón atrás del navegador
    cy.go('back');
    cy.url().should('include', '/register');
    
    // Botón adelante
    cy.go('forward');
    
    // Recargar página
    cy.reload();
  });

  it('should handle redirects', () => {
    cy.visit('/protected-page');
    
    // Debe redirigir a login si no está autenticado
    cy.url().should('include', '/login');
  });
});
```

#### Interacción Avanzada

```javascript
describe('Advanced Interactions', () => {
  it('should handle hover effects', () => {
    cy.get('[data-cy="dropdown-menu"]').trigger('mouseover');
    cy.get('[data-cy="submenu"]').should('be.visible');
  });

  it('should handle double click', () => {
    cy.get('[data-cy="editable-field"]').dblclick();
    cy.get('[data-cy="edit-input"]').should('be.visible');
  });

  it('should handle right click (context menu)', () => {
    cy.get('[data-cy="file-item"]').rightclick();
    cy.get('[data-cy="context-menu"]').should('be.visible');
  });

  it('should handle keyboard events', () => {
    cy.get('[data-cy="search-input"]')
      .type('test query')
      .type('{enter}');
    
    // Teclas especiales
    cy.get('[data-cy="text-editor"]')
      .type('{ctrl}A')  // Select all
      .type('{del}');   // Delete
    
    // Combinaciones
    cy.get('[data-cy="input"]').type('{shift}{enter}');
  });

  it('should handle scrolling', () => {
    // Scroll a elemento
    cy.get('[data-cy="footer"]').scrollIntoView();
    
    // Scroll de la ventana
    cy.scrollTo('bottom');
    cy.scrollTo('top');
    cy.scrollTo(0, 500);  // x, y coordinates
    
    // Scroll dentro de contenedor
    cy.get('[data-cy="scrollable-list"]').scrollTo('bottom');
  });

  it('should handle focus', () => {
    cy.get('[data-cy="username-input"]').focus();
    cy.get('[data-cy="username-input"]').should('have.focus');
    
    cy.get('[data-cy="username-input"]').blur();
    cy.get('[data-cy="username-input"]').should('not.have.focus');
  });
});
```

---

### Aserciones Más Usadas

Cypress usa **Chai assertions** bajo el capó, con una sintaxis fluida:

```javascript
describe('Assertions Examples', () => {
  it('should demonstrate visibility assertions', () => {
    // Visible/Oculto
    cy.get('[data-cy="success-message"]').should('be.visible');
    cy.get('[data-cy="error-message"]').should('not.be.visible');
    cy.get('[data-cy="loading-spinner"]').should('not.exist');
  });

  it('should demonstrate text assertions', () => {
    // Texto exacto
    cy.get('[data-cy="welcome-message"]').should('have.text', 'Welcome!');
    
    // Contiene texto
    cy.get('[data-cy="description"]').should('contain', 'user');
    
    // Coincide con regex
    cy.get('[data-cy="email"]').should('match', /^[^\s@]+@[^\s@]+\.[^\s@]+$/);
  });

  it('should demonstrate attribute assertions', () => {
    // Tiene atributo
    cy.get('[data-cy="link"]').should('have.attr', 'href');
    
    // Atributo con valor específico
    cy.get('[data-cy="link"]').should('have.attr', 'href', '/profile');
    
    // Tiene clase
    cy.get('[data-cy="button"]').should('have.class', 'btn-primary');
    
    // ID
    cy.get('[data-cy="form"]').should('have.id', 'registration-form');
  });

  it('should demonstrate value assertions', () => {
    cy.get('[data-cy="username-input"]').should('have.value', 'john_doe');
    cy.get('[data-cy="email-input"]').should('not.have.value', '');
  });

  it('should demonstrate state assertions', () => {
    // Enabled/Disabled
    cy.get('[data-cy="submit-button"]').should('be.enabled');
    cy.get('[data-cy="submit-button"]').should('not.be.disabled');
    
    // Checked
    cy.get('[data-cy="terms-checkbox"]').should('be.checked');
    cy.get('[data-cy="newsletter-checkbox"]').should('not.be.checked');
    
    // Selected (select options)
    cy.get('[data-cy="country-select"] option: selected').should('have.text', 'Spain');
  });

  it('should demonstrate length assertions', () => {
    cy.get('. user-row').should('have.length', 5);
    cy.get('.user-row').should('have.length. greaterThan', 0);
    cy.get('.user-row').should('have.length.lessThan', 10);
  });

  it('should demonstrate CSS assertions', () => {
    cy.get('[data-cy="button"]')
      .should('have.css', 'background-color', 'rgb(0, 123, 255)');
    
    cy.get('[data-cy="error-text"]')
      .should('have.css', 'color', 'rgb(255, 0, 0)');
  });

  it('should chain multiple assertions', () => {
    cy.get('[data-cy="username-input"]')
      .should('be.visible')
      .and('have.attr', 'type', 'text')
      .and('have.attr', 'placeholder')
      .and('not.be.disabled');
  });

  it('should use custom assertions with then()', () => {
    cy.get('[data-cy="user-list"]').then($list => {
      // Acceso directo al elemento jQuery
      expect($list).to.have.length(3);
      expect($list. text()).to.include('John');
      
      // Aserciones complejas
      const users = $list.find('.user-name').toArray().map(el => el.textContent);
      expect(users).to.deep.equal(['John', 'Jane', 'Bob']);
    });
  });
});
```

💡 **Nota del Profesor**: La diferencia entre `.should()` y `.then()`:
- **`.should()`**: Reintenta automáticamente hasta que pase o se agote el timeout (es retry-able)
- **`.then()`**: Se ejecuta UNA vez con el valor en ese momento (no reintenta)

Usa `.should()` siempre que sea posible para aprovechar las esperas automáticas de Cypress.

---

### 5. 2.  Flujos E2E:  Login hasta Persistencia

Vamos a crear un test completo que simule el ciclo de vida real de un usuario:

**cypress/e2e/user-registration-flow.cy.js:**

```javascript
describe('Complete User Registration and Login Flow', () => {
  // Datos de prueba únicos para cada ejecución
  const timestamp = Date.now();
  const testUser = {
    username: `testuser_${timestamp}`,
    email: `test${timestamp}@example.com`,
    password: 'SecureTest123!'
  };

  before(() => {
    // Limpiar base de datos (requiere endpoint o comando personalizado)
    cy.request('POST', `${Cypress.env('apiUrl')}/test/reset-database`);
  });

  it('Step 1: Should navigate to registration page', () => {
    cy.visit('/');
    
    // Click en botón de registro
    cy.get('[data-cy="register-link"]').click();
    
    // Verificar que estamos en la página correcta
    cy.url().should('include', '/register');
    cy.get('[data-cy="registration-page"]').should('be.visible');
    cy.get('h1').should('contain', 'User Registration');
  });

  it('Step 2: Should show validation errors for empty form', () => {
    cy.visit('/register');
    
    // Intentar enviar formulario vacío
    cy.get('[data-cy="submit-button"]').click();
    
    // Verificar errores de validación
    cy.get('[data-cy="username-error"]')
      .should('be.visible')
      .and('contain', 'Username is required');
    
    cy.get('[data-cy="email-error"]')
      .should('be.visible')
      .and('contain', 'Email is required');
    
    cy.get('[data-cy="password-error"]')
      .should('be.visible')
      .and('contain', 'Password is required');
    
    // Verificar que no se creó el usuario
    cy.get('[data-cy="success-message"]').should('not.exist');
  });

  it('Step 3: Should show validation error for invalid email', () => {
    cy.visit('/register');
    
    cy.get('[data-cy="username-input"]').type('validuser');
    cy.get('[data-cy="email-input"]').type('not-an-email');
    cy.get('[data-cy="password-input"]').type('SecurePass123!');
    cy.get('[data-cy="submit-button"]').click();
    
    cy.get('[data-cy="email-error"]')
      .should('be.visible')
      .and('contain', 'Invalid email format');
  });

  it('Step 4: Should show validation error for short password', () => {
    cy.visit('/register');
    
    cy.get('[data-cy="username-input"]').type('validuser');
    cy.get('[data-cy="email-input"]').type('valid@example.com');
    cy.get('[data-cy="password-input"]').type('short');
    cy.get('[data-cy="submit-button"]').click();
    
    cy.get('[data-cy="password-error"]')
      .should('be.visible')
      .and('contain', 'at least 8 characters');
  });

  it('Step 5: Should successfully register new user', () => {
    cy.visit('/register');
    
    // Llenar formulario con datos válidos
    cy.get('[data-cy="username-input"]')
      .type(testUser. username)
      .should('have.value', testUser.username);
    
    cy.get('[data-cy="email-input"]')
      .type(testUser.email)
      .should('have.value', testUser.email);
    
    cy.get('[data-cy="password-input"]')
      .type(testUser.password, { log: false })
      .should('have.value', testUser.password);
    
    // Interceptar llamada API para verificar request
    cy.intercept('POST', '**/api/v1/users/register').as('registerRequest');
    
    // Enviar formulario
    cy.get('[data-cy="submit-button"]').click();
    
    // Esperar respuesta del servidor
    cy.wait('@registerRequest').then((interception) => {
      // Verificar que se envió el payload correcto
      expect(interception.request.body).to.deep.include({
        username: testUser. username,
        email: testUser.email
      });
      
      // Verificar respuesta exitosa
      expect(interception.response.statusCode).to.equal(201);
      expect(interception.response.body).to.have.property('id');
      expect(interception.response.body. username).to.equal(testUser.username);
      
      // Guardar ID para tests posteriores
      cy.wrap(interception.response.body. id).as('userId');
    });
    
    // Verificar mensaje de éxito
    cy. get('[data-cy="success-message"]')
      .should('be.visible')
      .and('contain', 'Registration successful');
    
    // Verificar que no hay errores
    cy.get('[data-cy="error-message"]').should('not.exist');
  });

  it('Step 6: Should prevent duplicate username registration', () => {
    cy.visit('/register');
    
    // Intentar registrar mismo username
    cy.get('[data-cy="username-input"]').type(testUser.username);
    cy.get('[data-cy="email-input"]').type(`different_${timestamp}@example.com`);
    cy.get('[data-cy="password-input"]').type('AnotherPass123!');
    
    cy.intercept('POST', '**/api/v1/users/register').as('duplicateRequest');
    cy.get('[data-cy="submit-button"]').click();
    
    cy.wait('@duplicateRequest').then((interception) => {
      expect(interception.response.statusCode).to.equal(409);
    });
    
    cy.get('[data-cy="error-message"]')
      .should('be.visible')
      .and('contain', 'Username already exists');
  });

  it('Step 7: Should navigate to login page', () => {
    cy.visit('/register');
    
    // Click en link a login
    cy.get('[data-cy="login-link"]').click();
    
    cy.url().should('include', '/login');
    cy.get('[data-cy="login-page"]').should('be.visible');
  });

  it('Step 8: Should fail login with wrong password', () => {
    cy.visit('/login');
    
    cy.get('[data-cy="username-input"]').type(testUser.username);
    cy.get('[data-cy="password-input"]').type('WrongPassword123!');
    
    cy.intercept('POST', '**/api/v1/auth/login').as('loginRequest');
    cy.get('[data-cy="login-button"]').click();
    
    cy.wait('@loginRequest').then((interception) => {
      expect(interception.response.statusCode).to.equal(401);
    });
    
    cy.get('[data-cy="error-message"]')
      .should('be.visible')
      .and('contain', 'Invalid credentials');
  });

  it('Step 9: Should successfully login', () => {
    cy.visit('/login');
    
    cy.get('[data-cy="username-input"]').type(testUser.username);
    cy.get('[data-cy="password-input"]').type(testUser.password, { log: false });
    
    cy.intercept('POST', '**/api/v1/auth/login').as('loginRequest');
    cy.get('[data-cy="login-button"]').click();
    
    cy.wait('@loginRequest').then((interception) => {
      expect(interception.response.statusCode).to.equal(200);
      expect(interception.response.body).to.have.property('token');
      
      // Guardar token
      const token = interception.response.body.token;
      cy.wrap(token).as('authToken');
      
      // Verificar que se guardó en localStorage o cookie
      cy.window().its('localStorage. authToken').should('exist');
    });
    
    // Verificar redirección a dashboard
    cy. url().should('include', '/dashboard');
    cy.get('[data-cy="dashboard-page"]').should('be.visible');
    
    // Verificar que se muestra el username
    cy.get('[data-cy="user-greeting"]')
      .should('contain', testUser.username);
  });

  it('Step 10: Should display user profile with correct data', () => {
    // Login primero (usando comando personalizado - ver más adelante)
    cy.loginViaUI(testUser.username, testUser.password);
    
    // Navegar a perfil
    cy.get('[data-cy="profile-link"]').click();
    
    cy.url().should('include', '/profile');
    
    // Verificar datos del usuario
    cy.get('[data-cy="profile-username"]')
      .should('contain', testUser.username);
    
    cy.get('[data-cy="profile-email"]')
      .should('contain', testUser.email);
    
    cy.get('[data-cy="profile-status"]')
      .should('contain', 'Active');
    
    cy.get('[data-cy="profile-created-date"]')
      .should('exist')
      .invoke('text')
      .should('match', /\d{4}-\d{2}-\d{2}/); // Formato de fecha
  });

  it('Step 11: Should update user profile', () => {
    cy.loginViaUI(testUser.username, testUser.password);
    cy.visit('/profile/edit');
    
    const newEmail = `updated_${timestamp}@example.com`;
    
    cy.get('[data-cy="email-input"]')
      .clear()
      .type(newEmail);
    
    cy.intercept('PUT', '**/api/v1/users/*').as('updateRequest');
    cy.get('[data-cy="save-button"]').click();
    
    cy.wait('@updateRequest').then((interception) => {
      expect(interception.response.statusCode).to.equal(200);
    });
    
    cy.get('[data-cy="success-message"]')
      .should('be.visible')
      .and('contain', 'Profile updated');
    
    // Verificar persistencia
    cy.reload();
    cy.get('[data-cy="profile-email"]').should('contain', newEmail);
  });

  it('Step 12: Should logout successfully', () => {
    cy.loginViaUI(testUser.username, testUser.password);
    
    cy.get('[data-cy="logout-button"]').click();
    
    // Verificar redirección a home
    cy.url().should('not.include', '/dashboard');
    cy.url().should('include', '/');
    
    // Verificar que el token fue eliminado
    cy.window().its('localStorage.authToken').should('not.exist');
    
    // Intentar acceder a página protegida
    cy.visit('/dashboard');
    
    // Debe redirigir a login
    cy.url().should('include', '/login');
  });

  it('Step 13: Should persist data after browser restart', () => {
    // Login
    cy.loginViaUI(testUser.username, testUser. password);
    
    // Crear algún dato
    cy.visit('/dashboard');
    cy.get('[data-cy="create-note-button"]').click();
    cy.get('[data-cy="note-title"]').type('Test Note');
    cy.get('[data-cy="note-content"]').type('This is a test note');
    cy.get('[data-cy="save-note-button"]').click();
    
    // Logout
    cy.get('[data-cy="logout-button"]').click();
    
    // Simular cierre de navegador (limpiar localStorage/cookies)
    cy.clearLocalStorage();
    cy.clearCookies();
    
    // Login de nuevo
    cy.loginViaUI(testUser.username, testUser.password);
    
    // Verificar que los datos persisten
    cy.visit('/dashboard');
    cy.get('[data-cy="note-list"]')
      .should('contain', 'Test Note');
  });

  after(() => {
    // Cleanup:  eliminar usuario de prueba
    cy.request({
      method: 'DELETE',
      url: `${Cypress.env('apiUrl')}/test/users/${testUser.username}`,
      failOnStatusCode: false
    });
  });
});
```

---

### 5.3. Ejemplo:  Buscar en Wikipedia con Cypress

Un ejemplo práctico para entender la interacción con sitios reales:

**cypress/e2e/wikipedia-search.cy. js:**

```javascript
describe('Wikipedia Search Functionality', () => {
  beforeEach(() => {
    // Visitar Wikipedia
    cy.visit('https://www.wikipedia.org');
  });

  it('should load Wikipedia homepage', () => {
    // Verificar elementos clave de la página
    cy.get('#www-wikipedia-org').should('be.visible');
    cy.get('. search-input').should('be.visible');
    
    // Verificar título
    cy.title().should('include', 'Wikipedia');
  });

  it('should search for "Cypress Testing" and navigate to article', () => {
    // Encontrar campo de búsqueda
    cy.get('#searchInput').should('be.visible').type('Cypress Testing');
    
    // Click en botón de búsqueda
    cy.get('button[type="submit"]').click();
    
    // Esperar a que cargue la página de resultados
    cy.url().should('include', 'wikipedia.org/wiki/');
    
    // Verificar que estamos en una página de artículo
    cy.get('#firstHeading').should('be.visible');
    
    // Verificar que el contenido está presente
    cy.get('#mw-content-text').should('exist');
  });

  it('should search with suggestions and select one', () => {
    // Escribir búsqueda
    cy.get('#searchInput').type('JavaScript');
    
    // Esperar a que aparezcan sugerencias
    cy.get('.suggestions-results').should('be.visible');
    
    // Verificar que hay sugerencias
    cy.get('.suggestions-result').should('have.length. greaterThan', 0);
    
    // Click en la primera sugerencia
    cy.get('.suggestions-result').first().click();
    
    // Verificar navegación
    cy.url().should('include', 'wikipedia.org/wiki/');
    cy.get('#firstHeading').should('exist');
  });

  it('should handle search with no results', () => {
    const randomString = 'xyzabc123impossible' + Date.now();
    
    cy.get('#searchInput').type(randomString);
    cy.get('button[type="submit"]').click();
    
    // Debe mostrar página de "no results"
    cy.contains('Search results').should('be.visible');
    cy.contains('There were no results matching the query').should('be.visible');
  });

  it('should navigate between language editions', () => {
    // Click en español
    cy.get('#js-link-box-es').click();
    
    // Verificar que estamos en la versión en español
    cy.url().should('include', 'es.wikipedia.org');
    cy.get('#searchInput').should('have.attr', 'placeholder').and('include', 'Buscar');
  });

  it('should use the search and verify article structure', () => {
    // Buscar un tema específico
    cy.get('#searchInput').type('Software testing{enter}');
    
    // Verificar estructura del artículo
    cy. get('#firstHeading').should('contain', 'Software testing');
    
    // Verificar tabla de contenidos
    cy.get('#toc').should('be.visible');
    cy.get('. toc-list').find('li').should('have.length. greaterThan', 3);
    
    // Click en una sección de la tabla de contenidos
    cy.get('. toc-list').find('a').first().click();
    
    // Verificar que el scroll funcionó (URL cambia con anchor)
    cy.url().should('include', '#');
  });

  it('should test responsive behavior', () => {
    // Cambiar a viewport móvil
    cy.viewport('iphone-x');
    
    // Verificar que el menú móvil existe
    cy.get('.menu-button').should('be.visible');
    
    // Buscar en móvil
    cy.get('#searchInput').type('Mobile web{enter}');
    
    // Verificar navegación
    cy.url().should('include', 'wikipedia.org/wiki/');
    
    // Restaurar viewport
    cy.viewport(1280, 720);
  });

  it('should verify external links behavior', () => {
    cy.get('#searchInput').type('Selenium (software){enter}');
    
    // Encontrar enlaces externos (tienen class specific o target)
    cy.get('#mw-content-text').find('a[rel="nofollow"]').first().then($link => {
      // Verificar que el link existe y tiene href
      expect($link).to.have.attr('href');
      
      // No hacer click real (evita salir del test)
      // En su lugar, verificar el atributo
      const href = $link.attr('href');
      expect(href).to.match(/^https?:\/\//);
    });
  });

  it('should test search with special characters', () => {
    const searches = [
      'C++ programming',
      'AT&T',
      'Björk',
      'São Paulo'
    ];

    searches.forEach(searchTerm => {
      cy. visit('https://www.wikipedia.org');
      cy.get('#searchInput').type(searchTerm + '{enter}');
      
      // Verificar que no hubo error
      cy.get('#firstHeading').should('be.visible');
      cy.url().should('include', 'wikipedia.org/wiki/');
    });
  });

  it('should verify search performance', () => {
    const startTime = Date.now();
    
    cy.get('#searchInput').type('Performance testing{enter}');
    
    cy.get('#firstHeading').should('be.visible').then(() => {
      const endTime = Date.now();
      const loadTime = endTime - startTime;
      
      // Verificar que cargó en menos de 3 segundos
      expect(loadTime).to.be.lessThan(3000);
      
      cy.log(`Page loaded in ${loadTime}ms`);
    });
  });
});
```

💡 **Nota del Profesor**: Este test de Wikipedia demuestra interacciones reales:  búsqueda, navegación, sugerencias, responsive design.  Nota cómo NO usamos `cy.wait(5000)` innecesarios; Cypress espera automáticamente a que los elementos estén disponibles. 

---

### 5.4. Dockerización:  Ejecución en Modo Headless

Para CI/CD y entornos de despliegue, necesitamos ejecutar Cypress en **modo headless** (sin interfaz gráfica) dentro de contenedores. 

#### 🛠️ Paso a Paso:  Cypress en Docker

**1. Estructura del Proyecto:**

```
cypress-docker/
├── cypress/
│   ├── e2e/
│   │   ├── user-flow.cy.js
│   │   └── wikipedia. cy.js
│   ├── fixtures/
│   ├── support/
│   │   ├── commands.js
│   │   └── e2e.js
├── cypress.config.js
├── package.json
├── Dockerfile
└── docker-compose. yml
```

**2. Dockerfile:**

```dockerfile
FROM cypress/included:13.6.3

# Crear directorio de trabajo
WORKDIR /e2e

# Copiar package files
COPY package*.json ./

# Instalar dependencias
RUN npm ci

# Copiar configuración de Cypress
COPY cypress.config.js ./

# Copiar tests y soporte
COPY cypress ./cypress

# Variables de entorno por defecto
ENV CYPRESS_baseUrl=http://webapp:3000
ENV CYPRESS_video=true
ENV CYPRESS_screenshotOnRunFailure=true

# Script de entrada
COPY docker-entrypoint.sh /usr/local/bin/
RUN chmod +x /usr/local/bin/docker-entrypoint.sh

ENTRYPOINT ["docker-entrypoint.sh"]
CMD ["cypress", "run"]
```

**docker-entrypoint.sh:**

```bash
#!/bin/bash
set -e

echo "================================================"
echo "  Cypress E2E Tests - Docker Execution"
echo "================================================"
echo ""
echo "Configuration:"
echo "  Base URL: ${CYPRESS_baseUrl}"
echo "  Browser: ${CYPRESS_browser:-electron}"
echo "  Spec: ${CYPRESS_spec:-all}"
echo ""

# Esperar a que la webapp esté disponible
if [ -n "$CYPRESS_baseUrl" ]; then
  echo "Waiting for application to be ready..."
  
  HOST=$(echo $CYPRESS_baseUrl | sed -e 's|^[^/]*//||' -e 's|/.*$||' -e 's|: .*$||')
  PORT=$(echo $CYPRESS_baseUrl | sed -e 's|^[^: ]*: ||' -e 's|/.*$||')
  
  timeout=60
  elapsed=0
  
  while !  nc -z $HOST ${PORT:-80}; do
    if [ $elapsed -ge $timeout ]; then
      echo "ERROR: Application not ready after ${timeout}s"
      exit 1
    fi
    echo "Waiting for $HOST:${PORT:-80}...  ($elapsed/$timeout)"
    sleep 2
    elapsed=$((elapsed + 2))
  done
  
  echo "Application is ready!"
  echo ""
fi

# Ejecutar Cypress
exec "$@"
```

**3. docker-compose.yml (con aplicación web):**

```yaml
version: '3.8'

services:
  webapp:
    image: user-management-frontend:latest
    ports:
      - "3000:3000"
    environment:
      - REACT_APP_API_URL=http://backend:8080/api/v1
    depends_on:
      backend:
        condition: service_healthy
    healthcheck:
      test: ["CMD", "curl", "-f", "http://localhost:3000"]
      interval: 5s
      timeout: 3s
      retries: 10

  backend:
    image: user-management-api:latest
    ports:
      - "8080:8080"
    environment:
      - SPRING_PROFILES_ACTIVE=test
      - DATABASE_URL=jdbc:postgresql://postgres:5432/testdb
      - DATABASE_USER=testuser
      - DATABASE_PASSWORD=testpass
    depends_on:
      postgres:
        condition: service_healthy
    healthcheck:
      test: ["CMD", "curl", "-f", "http://localhost:8080/actuator/health"]
      interval:  5s
      timeout: 3s
      retries: 15

  postgres:
    image:  postgres:16-alpine
    environment:
      - POSTGRES_DB=testdb
      - POSTGRES_USER=testuser
      - POSTGRES_PASSWORD=testpass
    healthcheck: 
      test: ["CMD-SHELL", "pg_isready -U testuser -d testdb"]
      interval: 5s
      timeout: 3s
      retries: 5

  cypress:
    build: .
    environment:
      - CYPRESS_baseUrl=http://webapp:3000
      - CYPRESS_apiUrl=http://backend:8080/api/v1
      - CYPRESS_video=true
      - CYPRESS_screenshotOnRunFailure=true
    volumes:
      # Montar carpetas de resultados para acceder desde host
      - ./cypress/videos:/e2e/cypress/videos
      - ./cypress/screenshots:/e2e/cypress/screenshots
      - ./cypress/results:/e2e/cypress/results
    depends_on:
      webapp:
        condition: service_healthy
      backend:
        condition:  service_healthy
    command: ["cypress", "run", "--browser", "electron", "--headless"]

networks:
  default:
    name: cypress-test-network
```

**4. cypress.config.js adaptado para Docker:**

```javascript
const { defineConfig } = require('cypress');

module.exports = defineConfig({
  e2e: {
    baseUrl: process.env.CYPRESS_baseUrl || 'http://localhost:3000',
    viewportWidth: 1280,
    viewportHeight: 720,
    defaultCommandTimeout: 10000,
    screenshotOnRunFailure: true,
    video: true,
    videoCompression: 15,
    
    // Configuración de reportes
    reporter: 'mochawesome',
    reporterOptions: {
      reportDir: 'cypress/results',
      overwrite: false,
      html: true,
      json: true,
      timestamp: 'mmddyyyy_HHMMss'
    },
    
    retries: {
      runMode:  2,
      openMode:  0
    },
    
    env: {
      apiUrl: process.env.CYPRESS_apiUrl || 'http://localhost:8080/api/v1'
    },
    
    setupNodeEvents(on, config) {
      // Eventos personalizados si es necesario
      return config;
    },
  },
});
```

**5. Instalar reporter mochawesome:**

```bash
npm install --save-dev mochawesome mochawesome-merge mochawesome-report-generator
```

**6. Scripts en package.json:**

```json
{
  "name": "cypress-docker-tests",
  "version": "1.0.0",
  "scripts": {
    "cy:open": "cypress open",
    "cy:run": "cypress run",
    "cy:run:chrome": "cypress run --browser chrome",
    "cy:run:firefox": "cypress run --browser firefox",
    "test:docker": "docker-compose up --build --abort-on-container-exit",
    "test:docker:clean": "docker-compose down -v && npm run test:docker",
    "report:merge": "mochawesome-merge cypress/results/*. json > cypress/results/report. json",
    "report:generate": "marge cypress/results/report.json -f report -o cypress/results",
    "report:full": "npm run report:merge && npm run report:generate"
  },
  "devDependencies": {
    "cypress": "^13.6.3",
    "mochawesome":  "^7.1.3",
    "mochawesome-merge": "^4.3.0",
    "mochawesome-report-generator": "^6.2.0"
  }
}
```

**7. Ejecutar tests:**

```bash
# Construir y ejecutar todo
docker-compose up --build

# Ejecutar y detener automáticamente al finalizar
docker-compose up --build --abort-on-container-exit

# Ver logs de Cypress específicamente
docker-compose logs -f cypress

# Limpiar y ejecutar de nuevo
docker-compose down -v
docker-compose up --build --abort-on-container-exit
```

**8. Resultados:**

Después de la ejecución: 

```
cypress/
├── videos/
│   ├── user-flow.cy.js. mp4
│   └── wikipedia.cy.js.mp4
├── screenshots/
│   └── user-flow.cy.js/
│       └── Step 5 -- Should successfully register new user (failed).png
├── results/
│   ├── report.html
│   └── report.json
```

**9. Generar reporte consolidado:**

```bash
npm run report:full
```

Abrir `cypress/results/report.html` en el navegador para ver un dashboard completo. 

---

### Comandos Personalizados (Custom Commands)

Para reutilizar lógica común entre tests:

**cypress/support/commands.js:**

```javascript
// Comando para login via UI
Cypress.Commands.add('loginViaUI', (username, password) => {
  cy.visit('/login');
  cy.get('[data-cy="username-input"]').type(username);
  cy.get('[data-cy="password-input"]').type(password, { log: false });
  cy.get('[data-cy="login-button"]').click();
  cy.url().should('include', '/dashboard');
});

// Comando para login via API (más rápido)
Cypress.Commands.add('loginViaAPI', (username, password) => {
  cy.request({
    method: 'POST',
    url: `${Cypress.env('apiUrl')}/auth/login`,
    body: { username, password }
  }).then((response) => {
    expect(response.status).to.eq(200);
    window.localStorage.setItem('authToken', response.body.token);
  });
});

// Comando para crear usuario via API
Cypress.Commands.add('createUser', (username, email, password) => {
  return cy.request({
    method: 'POST',
    url:  `${Cypress.env('apiUrl')}/users/register`,
    body: { username, email, password },
    failOnStatusCode: false
  });
});

// Comando para resetear base de datos
Cypress.Commands. add('resetDatabase', () => {
  cy.request('POST', `${Cypress.env('apiUrl')}/test/reset-database`);
});

// Comando para esperar a que un elemento deje de estar visible
Cypress.Commands.add('waitUntilHidden', (selector, timeout = 10000) => {
  cy.get(selector, { timeout }).should('not.exist');
});

// Comando para llenar formulario de registro
Cypress.Commands.add('fillRegistrationForm', (userData) => {
  cy.get('[data-cy="username-input"]').type(userData.username);
  cy.get('[data-cy="email-input"]').type(userData.email);
  cy.get('[data-cy="password-input"]').type(userData.password, { log: false });
});
```

**Uso en tests:**

```javascript
describe('User Tests with Custom Commands', () => {
  const testUser = {
    username: 'customuser',
    email: 'custom@example.com',
    password: 'CustomPass123!'
  };

  beforeEach(() => {
    cy.resetDatabase();
  });

  it('should register and login user', () => {
    cy.visit('/register');
    cy.fillRegistrationForm(testUser);
    cy.get('[data-cy="submit-button"]').click();
    
    // Login rápido via API
    cy.loginViaAPI(testUser.username, testUser.password);
    
    // Verificar que estamos logueados
    cy.visit('/dashboard');
    cy.get('[data-cy="dashboard-page"]').should('be.visible');
  });
});
```

---

**🎯 Resumen del Bloque 5:**

✅ **Cypress** es el framework moderno de elección para E2E testing: 
- Selectores inteligentes con `data-cy` attributes
- Comandos de acción intuitivos:  `type()`, `click()`, `select()`
- Aserciones fluidas con retry automático
- Debugging interactivo con Time Travel

✅ **Flujos E2E completos** simulan comportamiento real de usuarios:
- Registro → Validación → Login → Navegación → Persistencia
- Pruebas de casos positivos y negativos
- Intercepción de llamadas API con `cy.intercept()`

✅ **Dockerización para CI/CD:**
- Ejecución headless en contenedores
- Orquestación con `docker-compose`
- Generación automática de videos y screenshots
- Reportes HTML consolidados

✅ **Comandos personalizados** mejoran mantenibilidad:
- Reutilización de lógica común
- Login via UI o API
- Helpers para operaciones frecuentes

💡 **Consejo Final**:  Cypress revolucionó el E2E testing eliminando esperas arbitrarias y complicaciones de setup.  Aprovecha sus features automáticas y escribe tests que describan comportamiento de usuario, no implementación técnica.

---

## 6: Servicios de Red e Infraestructura

### Introducción:  La Capa Invisible del Despliegue

Hasta ahora hemos probado **código de aplicación**:  lógica de negocio, APIs, interfaces de usuario. Pero en entornos de producción reales, las aplicaciones dependen de **servicios de infraestructura** que son igualmente críticos: 

- **DNS**: Resolución de nombres de dominio
- **LDAP/Active Directory**: Autenticación y autorización centralizada
- **Certificados SSL/TLS**: Comunicación segura
- **Servicios de correo**:  SMTP para notificaciones
- **Proxies/Load Balancers**: Distribución de tráfico

En este bloque aprenderemos a **configurar, validar y probar** estos servicios usando Docker, con énfasis en DNS (BIND9) y servicios de directorio (OpenLDAP).

💡 **Nota del Profesor**: Estos servicios suelen ser "black boxes" para desarrolladores, pero entenderlos es fundamental para diagnosticar problemas en producción.  ¿Tu API falla porque el código está mal o porque no puede resolver el DNS del servidor de base de datos?  Esta unidad te da las herramientas para saberlo.

---

### 6.1. DNS con BIND9

#### ¿Qué es DNS?

El **Domain Name System (DNS)** es el "directorio telefónico" de Internet.  Traduce nombres legibles por humanos (`www.example.com`) a direcciones IP (`192.168.1.10`) que las máquinas entienden.

#### Jerarquía DNS

```
                        .  (root)
                         |
        +----------------+----------------+
        |                |                |
       com              org              es
        |                |                |
    +---+---+        +---+---+        +---+---+
    |       |        |       |        |       |
  example github   wikipedia          uc3m
    |
    +-------+-------+
    |       |       |
   www    api     mail
```

#### Tipos de Registros DNS Principales

| Tipo      | Propósito            | Ejemplo                                          |
| --------- | -------------------- | ------------------------------------------------ |
| **A**     | Mapea nombre a IPv4  | `www.example.com → 192.168.1.10`                 |
| **AAAA**  | Mapea nombre a IPv6  | `www.example.com → 2001:db8::1`                  |
| **CNAME** | Alias de otro nombre | `blog.example.com → www.example.com`             |
| **MX**    | Servidor de correo   | `example.com → mail.example.com` (priority:  10) |
| **TXT**   | Texto arbitrario     | Verificación de dominio, SPF, DKIM               |
| **NS**    | Servidor de nombres  | `example.com → ns1.example.com`                  |
| **PTR**   | Resolución inversa   | `10.1.168.192.in-addr.arpa → www.example.com`    |
| **SRV**   | Servicio específico  | `_ldap._tcp.example.com → ldap.example.com:389`  |

---

#### 🛠️ Paso a Paso: Configuración de BIND9 en Docker

**1. Estructura del Proyecto:**

```
dns-bind9/
├── docker-compose.yml
├── bind9/
│   ├── named.conf
│   ├── named.conf.options
│   ├── named.conf.local
│   └── zones/
│       ├── db.example.local
│       └── db.192.168.1
├── tests/
│   └── test-dns.sh
└── README.md
```

**2. docker-compose.yml:**

```yaml
version: '3.8'

services:
  bind9:
    image: ubuntu/bind9:latest
    container_name: dns-server
    hostname: ns1.example.local
    ports:
      - "53:53/tcp"
      - "53:53/udp"
      - "953:953/tcp"  # rndc (control remoto)
    volumes:
      - ./bind9/named.conf:/etc/bind/named.conf:ro
      - ./bind9/named.conf.options:/etc/bind/named.conf.options:ro
      - ./bind9/named.conf.local:/etc/bind/named.conf.local:ro
      - ./bind9/zones:/etc/bind/zones:ro
      - bind9-cache:/var/cache/bind
      - bind9-lib:/var/lib/bind
    environment:
      - TZ=Europe/Madrid
      - BIND9_USER=bind
    restart: unless-stopped
    networks:
      app-network:
        ipv4_address: 192.168.100.10

  # Cliente de prueba
  dns-client:
    image: alpine:latest
    container_name:  dns-client
    command: sleep infinity
    dns: 
      - 192.168.100.10  # Usar nuestro DNS
    networks:
      - app-network
    depends_on:
      - bind9

volumes:
  bind9-cache:
  bind9-lib: 

networks:
  app-network: 
    driver: bridge
    ipam:
      config:
        - subnet: 192.168.100.0/24
```

**3. named.conf (Configuración principal):**

```conf
// named.conf - Configuración principal de BIND9

include "/etc/bind/named.conf.options";
include "/etc/bind/named.conf.local";
```

**4. named.conf. options (Opciones globales):**

```conf
options {
    directory "/var/cache/bind";

    // Configuración de forwarding (reenvío a DNS externos)
    forwarders {
        8.8.8.8;        // Google DNS
        8.8.4.4;
        1.1.1.1;        // Cloudflare DNS
    };

    // Permitir consultas desde cualquier origen
    allow-query { any; };

    // Permitir recursión (necesario para ser DNS resolver)
    recursion yes;

    // Escuchar en todas las interfaces
    listen-on { any; };
    listen-on-v6 { any; };

    // Transferencias de zona (solo desde IPs autorizadas)
    allow-transfer { none; };

    // DNSSEC
    dnssec-validation auto;

    // Versión (ocultar por seguridad)
    version "not disclosed";

    // Logging
    querylog yes;
};

// Logging configuration
logging {
    channel default_log {
        file "/var/log/named/default.log" versions 3 size 5m;
        severity info;
        print-time yes;
        print-severity yes;
        print-category yes;
    };
    
    channel query_log {
        file "/var/log/named/query.log" versions 3 size 5m;
        severity info;
        print-time yes;
    };

    category default { default_log; };
    category queries { query_log; };
};
```

**5. named.conf.local (Zonas locales):**

```conf
// Zona directa:  example.local
zone "example.local" {
    type master;
    file "/etc/bind/zones/db.example.local";
    allow-update { none; };
    allow-query { any; };
};

// Zona inversa: 192.168.1.0/24
zone "1.168.192.in-addr.arpa" {
    type master;
    file "/etc/bind/zones/db.192.168.1";
    allow-update { none; };
    allow-query { any; };
};

// Zona para el entorno de pruebas
zone "testenv.local" {
    type master;
    file "/etc/bind/zones/db.testenv.local";
    allow-update { none; };
};
```

**6. zones/db.example.local (Archivo de zona directa):**

```conf
; Zona:  example.local
; Descripción: Dominio local para aplicaciones de prueba

$TTL    86400   ; TTL por defecto (24 horas)

@       IN      SOA     ns1.example.local. admin.example.local. (
                        2024010101  ; Serial (YYYYMMDDNN)
                        3600        ; Refresh (1 hora)
                        1800        ; Retry (30 minutos)
                        604800      ; Expire (1 semana)
                        86400 )     ; Negative Cache TTL (24 horas)

; Servidores de nombres
@       IN      NS      ns1.example.local. 

; Registro A para el propio servidor DNS
ns1     IN      A       192.168.1.10

; Servidor web principal
www     IN      A       192.168.1.20
web     IN      CNAME   www

; API backend
api     IN      A       192.168.1.30
api-v1  IN      CNAME   api
api-v2  IN      A       192.168.1.31

; Base de datos
db      IN      A       192.168.1.40
postgres IN     CNAME   db
mysql   IN      A       192.168.1.41

; Servicios de autenticación
ldap    IN      A       192.168.1.50
auth    IN      CNAME   ldap

; Servidor de correo
mail    IN      A       192.168.1.60
smtp    IN      CNAME   mail

; Registros MX (correo electrónico)
@       IN      MX      10 mail.example.local.

; Registros TXT (SPF, verificación de dominio)
@       IN      TXT     "v=spf1 mx a ip4:192.168.1.60 -all"
@       IN      TXT     "google-site-verification=abc123def456"

; Registro SRV para LDAP
_ldap._tcp  IN  SRV     0 5 389 ldap.example. local.
_ldaps._tcp IN  SRV     0 5 636 ldap.example.local.

; Registro para monitorización
monitor IN      A       192.168.1.70

; Load balancer
lb      IN      A       192.168.1.80

; Múltiples registros A para balanceo de carga round-robin
app     IN      A       192.168.1.100
app     IN      A       192.168.1.101
app     IN      A       192.168.1.102

; Wildcard para subdominios dinámicos
*.dev   IN      A       192.168.1.200
```

**7. zones/db.192.168.1 (Zona inversa - PTR records):**

```conf
; Zona inversa: 1.168.192.in-addr.arpa
; Permite resolución IP → nombre

$TTL    86400

@       IN      SOA     ns1.example.local. admin.example.local. (
                        2024010101
                        3600
                        1800
                        604800
                        86400 )

@       IN      NS      ns1.example.local.

; PTR records (resolución inversa)
10      IN      PTR     ns1.example.local. 
20      IN      PTR     www.example.local. 
30      IN      PTR     api.example.local.
31      IN      PTR     api-v2.example.local. 
40      IN      PTR     db.example.local.
50      IN      PTR     ldap.example.local.
60      IN      PTR     mail. example.local.
70      IN      PTR     monitor.example. local.
80      IN      PTR     lb.example.local. 
100     IN      PTR     app01.example.local.
101     IN      PTR     app02.example.local.
102     IN      PTR     app03.example.local.
```

**8. zones/db.testenv.local (Entorno de testing):**

```conf
; Zona: testenv.local
; Entorno específico para tests automatizados

$TTL    3600

@       IN      SOA     ns1.testenv.local. admin. testenv.local. (
                        2024010101
                        3600
                        1800
                        604800
                        3600 )

@       IN      NS      ns1.testenv.local.

ns1     IN      A       192.168.100.10

; Servicios de test
api     IN      A       192.168.100.20
db      IN      A       192.168.100.30
ldap    IN      A       192.168.100.40
webapp  IN      A       192.168.100.50

; Mock services
mock-payment    IN      A       192.168.100.60
mock-sms        IN      A       192.168.100.61
mock-email      IN      A       192.168.100.62
```

---

#### Iniciar y Verificar el Servidor DNS

**1. Levantar el servicio:**

```bash
docker-compose up -d
```

**2. Verificar logs:**

```bash
docker-compose logs -f bind9
```

Deberías ver: 

```
starting BIND 9.18.x
zone example.local/IN: loaded serial 2024010101
zone 1.168.192.in-addr.arpa/IN: loaded serial 2024010101
zone testenv.local/IN: loaded serial 2024010101
```

**3. Verificar que está escuchando:**

```bash
docker-compose exec bind9 netstat -tuln | grep :53
```

---

#### Tests DNS con dig, nslookup y host

**tests/test-dns.sh:**

```bash
#!/bin/bash

# Colores para output
GREEN='\033[0;32m'
RED='\033[0;31m'
YELLOW='\033[1;33m'
NC='\033[0m'

DNS_SERVER="127.0.0.1"
PASSED=0
FAILED=0

echo "=========================================="
echo "  DNS Server Testing Suite"
echo "=========================================="
echo ""

# Función para ejecutar test
run_test() {
    local description="$1"
    local command="$2"
    local expected="$3"
    
    echo -n "Testing:  $description... "
    
    result=$(eval "$command" 2>&1)
    
    if echo "$result" | grep -q "$expected"; then
        echo -e "${GREEN}✓ PASS${NC}"
        ((PASSED++))
        return 0
    else
        echo -e "${RED}✗ FAIL${NC}"
        echo "  Expected: $expected"
        echo "  Got:  $result"
        ((FAILED++))
        return 1
    fi
}

echo "=== Basic A Record Resolution ==="
run_test "www.example.local A record" \
    "dig @${DNS_SERVER} www.example.local +short" \
    "192.168.1.20"

run_test "api.example.local A record" \
    "dig @${DNS_SERVER} api.example.local +short" \
    "192.168.1.30"

run_test "db.example.local A record" \
    "dig @${DNS_SERVER} db. example.local +short" \
    "192.168.1.40"

echo ""
echo "=== CNAME Resolution ==="
run_test "web.example.local CNAME" \
    "dig @${DNS_SERVER} web.example.local +short" \
    "www.example.local"

run_test "postgres.example.local CNAME" \
    "dig @${DNS_SERVER} postgres.example.local +short" \
    "db.example.local"

echo ""
echo "=== MX Records ==="
run_test "example.local MX record" \
    "dig @${DNS_SERVER} example.local MX +short" \
    "10 mail.example.local"

echo ""
echo "=== TXT Records ==="
run_test "SPF TXT record" \
    "dig @${DNS_SERVER} example.local TXT +short" \
    "spf1"

echo ""
echo "=== SRV Records ==="
run_test "LDAP SRV record" \
    "dig @${DNS_SERVER} _ldap._tcp.example.local SRV +short" \
    "389 ldap.example.local"

echo ""
echo "=== PTR Records (Reverse Lookup) ==="
run_test "Reverse lookup 192.168.1.20" \
    "dig @${DNS_SERVER} -x 192.168.1.20 +short" \
    "www.example.local"

run_test "Reverse lookup 192.168.1.30" \
    "dig @${DNS_SERVER} -x 192.168.1.30 +short" \
    "api.example. local"

echo ""
echo "=== Round-Robin Load Balancing ==="
echo -n "Testing:  app.example.local has multiple A records... "
app_records=$(dig @${DNS_SERVER} app. example.local +short | wc -l)
if [ "$app_records" -eq 3 ]; then
    echo -e "${GREEN}✓ PASS${NC} (found 3 records)"
    ((PASSED++))
else
    echo -e "${RED}✗ FAIL${NC} (expected 3, found $app_records)"
    ((FAILED++))
fi

echo ""
echo "=== Wildcard Resolution ==="
run_test "Wildcard *.dev. example.local" \
    "dig @${DNS_SERVER} anything.dev.example.local +short" \
    "192.168.1.200"

run_test "Wildcard test123.dev.example.local" \
    "dig @${DNS_SERVER} test123.dev.example.local +short" \
    "192.168.1.200"

echo ""
echo "=== External DNS Forwarding ==="
run_test "Forward to external DNS (google.com)" \
    "dig @${DNS_SERVER} google. com +short | head -1" \
    "[0-9]"

echo ""
echo "=== DNS Server Info ==="
run_test "SOA record" \
    "dig @${DNS_SERVER} example.local SOA +short" \
    "ns1.example. local"

run_test "NS record" \
    "dig @${DNS_SERVER} example.local NS +short" \
    "ns1.example.local"

echo ""
echo "=== Zone Transfer (should be denied) ==="
echo -n "Testing: Zone transfer denial... "
transfer_result=$(dig @${DNS_SERVER} example.local AXFR 2>&1)
if echo "$transfer_result" | grep -q "Transfer failed"; then
    echo -e "${GREEN}✓ PASS${NC} (correctly denied)"
    ((PASSED++))
else
    echo -e "${RED}✗ FAIL${NC} (zone transfer should be denied)"
    ((FAILED++))
fi

echo ""
echo "=========================================="
echo "  Test Summary"
echo "=========================================="
echo -e "Passed: ${GREEN}${PASSED}${NC}"
echo -e "Failed: ${RED}${FAILED}${NC}"
echo "Total:   $((PASSED + FAILED))"
echo ""

if [ $FAILED -eq 0 ]; then
    echo -e "${GREEN}All tests passed!${NC}"
    exit 0
else
    echo -e "${RED}Some tests failed!${NC}"
    exit 1
fi
```

**Hacer ejecutable y correr:**

```bash
chmod +x tests/test-dns.sh
./tests/test-dns.sh
```

---

#### Tests desde contenedor cliente

```bash
# Entrar al contenedor cliente
docker-compose exec dns-client sh

# Instalar herramientas DNS
apk add --no-cache bind-tools

# Test básico
nslookup www.example.local

# Output esperado: 
# Server:    192.168.100.10
# Address:   192.168.100.10#53
# 
# Name:      www.example.local
# Address:   192.168.1.20

# Test con dig (más detallado)
dig www.example.local

# Test de todos los tipos de registros
dig example.local ANY

# Test específico de CNAME
dig web.example.local CNAME

# Test de MX
dig example.local MX

# Test de SRV
dig _ldap._tcp.example.local SRV

# Test de resolución inversa
dig -x 192.168.1.20
```

---

#### Integración con Aplicaciones

**Ejemplo: Spring Boot usando DNS interno**

**application.yml:**

```yaml
spring:
  datasource:
    # Usar DNS en lugar de IP
    url: jdbc:postgresql://db. example.local:5432/appdb
    username: appuser
    password: ${DB_PASSWORD}

  ldap:
    urls: ldap://ldap.example.local:389
    base:  dc=example,dc=local

  mail:
    host: mail.example.local
    port: 25

# Configuración de servicios externos
app:
  api:
    payment-service:  http://api.example.local/payment
    notification-service: http://api.example.local/notify
```

**docker-compose.yml de la aplicación:**

```yaml
version: '3.8'

services:
  app:
    image: my-spring-app: latest
    dns:
      - 192.168.100.10  # Nuestro servidor DNS
    networks:
      - app-network
    environment:
      - SPRING_PROFILES_ACTIVE=production
      - DB_PASSWORD=${DB_PASSWORD}
```

**Ejemplo:  . NET con DNS interno**

**appsettings.json:**

```json
{
  "ConnectionStrings": {
    "DefaultConnection": "Host=db.example.local;Database=appdb;Username=appuser;Password=secret"
  },
  "Services": {
    "AuthenticationService": "http://auth.example.local/api",
    "LdapServer": "ldap. example.local",
    "LdapPort": 389
  },
  "Email": {
    "SmtpServer": "mail.example.local",
    "SmtpPort": 25
  }
}
```

💡 **Nota del Profesor**:  Usar DNS en lugar de IPs hardcodeadas tiene ventajas enormes:
1. **Flexibilidad**: Cambias la IP en DNS, no en 50 archivos de configuración
2. **Portabilidad**: El mismo código funciona en dev, staging y producción
3. **Balanceo**:  Round-robin DNS para distribución de carga básica
4. **Legibilidad**: `db.example.local` es más claro que `192.168.1.40`

---

### 6. 2. Servicios de Directorio:  LDAP y Active Directory

#### ¿Qué es LDAP?

**LDAP (Lightweight Directory Access Protocol)** es un protocolo para acceder y mantener servicios de directorio distribuidos. Se usa principalmente para: 

- **Autenticación centralizada**: Single Sign-On (SSO)
- **Gestión de usuarios y grupos**
- **Directorio de empleados** (nombre, email, teléfono, departamento)
- **Autorización**:  Roles y permisos

#### Conceptos Fundamentales

**DIT (Directory Information Tree):**

```
dc=example,dc=com
│
├── ou=users
│   ├── uid=john.doe
│   ├── uid=jane.smith
│   └── uid=bob.wilson
│
├── ou=groups
│   ├── cn=developers
│   ├── cn=admins
│   └── cn=users
│
└── ou=services
    ├── cn=database
    └── cn=api
```

**Terminología LDAP:**

| Término         | Significado                                | Ejemplo                               |
| --------------- | ------------------------------------------ | ------------------------------------- |
| **DN**          | Distinguished Name (nombre único completo) | `uid=john,ou=users,dc=example,dc=com` |
| **RDN**         | Relative Distinguished Name                | `uid=john`                            |
| **dc**          | Domain Component                           | `dc=example`                          |
| **ou**          | Organizational Unit (unidad organizativa)  | `ou=users`                            |
| **cn**          | Common Name (nombre común)                 | `cn=developers`                       |
| **uid**         | User ID                                    | `uid=john.doe`                        |
| **objectClass** | Tipo de entrada                            | `inetOrgPerson`, `posixAccount`       |

**Atributos comunes:**

- `uid`: User ID
- `cn`: Common Name
- `sn`: Surname (apellido)
- `givenName`: Nombre de pila
- `mail`: Email
- `userPassword`: Password (hasheado)
- `memberOf`: Grupos a los que pertenece
- `member`: Miembros de un grupo

---

#### 🛠️ Paso a Paso: OpenLDAP + phpLDAPadmin

**1. Estructura del Proyecto:**

```
ldap-infrastructure/
├── docker-compose. yml
├── ldap/
│   ├── bootstrap.ldif
│   ├── users.ldif
│   └── groups.ldif
├── tests/
│   ├── test-ldap-auth.sh
│   └── test-ldap-search.sh
└── README.md
```

**2. docker-compose.yml:**

```yaml
version: '3.8'

services:
  openldap:
    image: osixia/openldap:1.5. 0
    container_name: openldap-server
    hostname: ldap.example.local
    environment:
      # Configuración base
      - LDAP_ORGANISATION=Example Company
      - LDAP_DOMAIN=example.local
      - LDAP_BASE_DN=dc=example,dc=local
      
      # Credenciales de administrador
      - LDAP_ADMIN_PASSWORD=admin_secret_password
      - LDAP_CONFIG_PASSWORD=config_secret_password
      
      # Configuración adicional
      - LDAP_RFC2307BIS_SCHEMA=true
      - LDAP_REMOVE_CONFIG_AFTER_SETUP=true
      - LDAP_TLS=false  # Deshabilitado para desarrollo
      
    ports:
      - "389:389"    # LDAP no seguro (dev only)
      - "636:636"    # LDAPS (SSL/TLS)
    volumes:
      - ldap-data:/var/lib/ldap
      - ldap-config:/etc/ldap/slapd.d
      - ./ldap:/container/service/slapd/assets/config/bootstrap/ldif/custom: ro
    networks:
      - app-network
    command: --copy-service --loglevel debug

  phpldapadmin:
    image: osixia/phpldapadmin:0.9.0
    container_name: phpldapadmin
    hostname: phpldapadmin.example.local
    environment:
      - PHPLDAPADMIN_LDAP_HOSTS=openldap
      - PHPLDAPADMIN_HTTPS=false
    ports:
      - "8090:80"
    depends_on:
      - openldap
    networks:
      - app-network

  # Aplicación de prueba que autentica contra LDAP
  ldap-test-app:
    build: ./test-app
    container_name: ldap-test-app
    environment: 
      - LDAP_URL=ldap://openldap:389
      - LDAP_BASE_DN=dc=example,dc=local
      - LDAP_BIND_DN=cn=admin,dc=example,dc=local
      - LDAP_BIND_PASSWORD=admin_secret_password
    ports:
      - "8080:8080"
    depends_on:
      - openldap
    networks:
      - app-network

volumes:
  ldap-data:
  ldap-config: 

networks:
  app-network: 
    driver: bridge
```

**3. ldap/bootstrap.ldif (Estructura inicial):**

```ldif
# Estructura base del directorio

# Unidad Organizativa para Usuarios
dn: ou=users,dc=example,dc=local
objectClass: organizationalUnit
ou: users
description: Usuarios de la organización

# Unidad Organizativa para Grupos
dn: ou=groups,dc=example,dc=local
objectClass:  organizationalUnit
ou: groups
description: Grupos de la organización

# Unidad Organizativa para Servicios
dn: ou=services,dc=example,dc=local
objectClass: organizationalUnit
ou: services
description: Cuentas de servicio

# Unidad Organizativa por Departamentos
dn: ou=departments,dc=example,dc=local
objectClass: organizationalUnit
ou: departments
description: Departamentos de la empresa

dn: ou=IT,ou=departments,dc=example,dc=local
objectClass: organizationalUnit
ou: IT
description:  Departamento de TI

dn: ou=HR,ou=departments,dc=example,dc=local
objectClass: organizationalUnit
ou:  HR
description: Recursos Humanos

dn: ou=Sales,ou=departments,dc=example,dc=local
objectClass:  organizationalUnit
ou: Sales
description: Departamento de Ventas
```

**4. ldap/users.ldif (Usuarios de prueba):**

```ldif
# Usuario 1: John Doe (Admin)
dn: uid=john.doe,ou=users,dc=example,dc=local
objectClass: inetOrgPerson
objectClass: posixAccount
objectClass: shadowAccount
uid: john.doe
cn: John Doe
sn: Doe
givenName: John
displayName: John Doe
mail:  john.doe@example.local
userPassword: {SSHA}hashed_password_here
uidNumber: 10001
gidNumber: 10001
homeDirectory: /home/john.doe
loginShell: /bin/bash
description: System Administrator
telephoneNumber: +34 600 111 222
title: Senior DevOps Engineer
departmentNumber: IT

# Usuario 2: Jane Smith (Developer)
dn: uid=jane.smith,ou=users,dc=example,dc=local
objectClass: inetOrgPerson
objectClass: posixAccount
objectClass: shadowAccount
uid:  jane.smith
cn: Jane Smith
sn: Smith
givenName: Jane
displayName: Jane Smith
mail: jane.smith@example.local
userPassword: {SSHA}hashed_password_here
uidNumber: 10002
gidNumber: 10002
homeDirectory: /home/jane.smith
loginShell: /bin/bash
description:  Full Stack Developer
telephoneNumber: +34 600 222 333
title: Senior Developer
departmentNumber: IT

# Usuario 3: Bob Wilson (User)
dn: uid=bob.wilson,ou=users,dc=example,dc=local
objectClass: inetOrgPerson
objectClass: posixAccount
objectClass: shadowAccount
uid:  bob.wilson
cn: Bob Wilson
sn: Wilson
givenName: Bob
displayName: Bob Wilson
mail: bob.wilson@example.local
userPassword: {SSHA}hashed_password_here
uidNumber: 10003
gidNumber: 10003
homeDirectory: /home/bob.wilson
loginShell: /bin/bash
description:  Sales Representative
telephoneNumber: +34 600 333 444
title: Account Manager
departmentNumber: Sales

# Usuario 4: Alice Johnson (HR)
dn: uid=alice.johnson,ou=users,dc=example,dc=local
objectClass: inetOrgPerson
objectClass: posixAccount
objectClass: shadowAccount
uid: alice.johnson
cn: Alice Johnson
sn: Johnson
givenName: Alice
displayName: Alice Johnson
mail: alice. johnson@example.local
userPassword: {SSHA}hashed_password_here
uidNumber: 10004
gidNumber: 10004
homeDirectory:  /home/alice.johnson
loginShell: /bin/bash
description: HR Manager
telephoneNumber: +34 600 444 555
title:  HR Manager
departmentNumber: HR

# Cuenta de servicio para la aplicación
dn: uid=app-service,ou=services,dc=example,dc=local
objectClass: inetOrgPerson
objectClass: simpleSecurityObject
uid: app-service
cn: Application Service Account
sn: Service
userPassword: {SSHA}service_password_here
description: Service account for application authentication
```

**5. ldap/groups.ldif (Grupos y membresías):**

```ldif
# Grupo:  Administradores
dn: cn=admins,ou=groups,dc=example,dc=local
objectClass: groupOfNames
cn: admins
description: System Administrators
member: uid=john.doe,ou=users,dc=example,dc=local

# Grupo: Desarrolladores
dn: cn=developers,ou=groups,dc=example,dc=local
objectClass: groupOfNames
cn: developers
description:  Software Developers
member: uid=john.doe,ou=users,dc=example,dc=local
member: uid=jane.smith,ou=users,dc=example,dc=local

# Grupo: Usuarios
dn: cn=users,ou=groups,dc=example,dc=local
objectClass: groupOfNames
cn: users
description: Regular Users
member: uid=john. doe,ou=users,dc=example,dc=local
member:  uid=jane.smith,ou=users,dc=example,dc=local
member: uid=bob.wilson,ou=users,dc=example,dc=local
member: uid=alice.johnson,ou=users,dc=example,dc=local

# Grupo: IT Department
dn: cn=it-team,ou=groups,dc=example,dc=local
objectClass:  groupOfNames
cn: it-team
description: IT Department Members
member: uid=john.doe,ou=users,dc=example,dc=local
member: uid=jane.smith,ou=users,dc=example,dc=local

# Grupo: HR Department
dn: cn=hr-team,ou=groups,dc=example,dc=local
objectClass: groupOfNames
cn: hr-team
description: Human Resources Team
member: uid=alice.johnson,ou=users,dc=example,dc=local

# Grupo: Sales Department
dn: cn=sales-team,ou=groups,dc=example,dc=local
objectClass: groupOfNames
cn: sales-team
description: Sales Team
member:  uid=bob.wilson,ou=users,dc=example,dc=local
```

---

#### Poblar el Directorio LDAP

**Levantar servicios:**

```bash
docker-compose up -d
```

**Generar contraseñas hasheadas:**

```bash
# Instalar slappasswd si no está disponible
docker-compose exec openldap slappasswd -s "Password123!"
# Output: {SSHA}8vUx9gJwP3Ub4zG... 
```

**Reemplazar en los archivos . ldif** las líneas `userPassword` con el hash generado. 

**Insertar datos con ldapadd:**

```bash
# Insertar usuarios
docker-compose exec openldap ldapadd -x \
  -D "cn=admin,dc=example,dc=local" \
  -w admin_secret_password \
  -f /container/service/slapd/assets/config/bootstrap/ldif/custom/users.ldif

# Insertar grupos
docker-compose exec openldap ldapadd -x \
  -D "cn=admin,dc=example,dc=local" \
  -w admin_secret_password \
  -f /container/service/slapd/assets/config/bootstrap/ldif/custom/groups.ldif
```

---

#### Acceder a phpLDAPadmin

1.  Abrir navegador:   `http://localhost:8090`
2. Login: 
   - **DN**: `cn=admin,dc=example,dc=local`
   - **Password**: `admin_secret_password`

Explorar la estructura del directorio visualmente. 

---

#### Tests de LDAP con ldapsearch

**tests/test-ldap-search.sh:**

```bash
#!/bin/bash

LDAP_HOST="localhost"
LDAP_PORT="389"
BASE_DN="dc=example,dc=local"
BIND_DN="cn=admin,$BASE_DN"
BIND_PW="admin_secret_password"

echo "=== LDAP Search Tests ==="
echo ""

# Test 1: Buscar todos los usuarios
echo "1. All users:"
ldapsearch -x -H ldap://$LDAP_HOST:$LDAP_PORT \
  -D "$BIND_DN" -w "$BIND_PW" \
  -b "ou=users,$BASE_DN" \
  "(objectClass=inetOrgPerson)" \
  uid cn mail

echo ""

# Test 2: Buscar usuario específico
echo "2. Find user john.doe:"
ldapsearch -x -H ldap://$LDAP_HOST:$LDAP_PORT \
  -D "$BIND_DN" -w "$BIND_PW" \
  -b "ou=users,$BASE_DN" \
  "(uid=john.doe)" \
  dn cn mail memberOf

echo ""

# Test 3: Buscar usuarios por departamento
echo "3. Users in IT department:"
ldapsearch -x -H ldap://$LDAP_HOST:$LDAP_PORT \
  -D "$BIND_DN" -w "$BIND_PW" \
  -b "ou=users,$BASE_DN" \
  "(departmentNumber=IT)" \
  uid cn title

echo ""

# Test 4: Buscar miembros de un grupo
echo "4. Members of developers group:"
ldapsearch -x -H ldap://$LDAP_HOST:$LDAP_PORT \
  -D "$BIND_DN" -w "$BIND_PW" \
  -b "cn=developers,ou=groups,$BASE_DN" \
  "(objectClass=groupOfNames)" \
  member

echo ""

# Test 5: Autenticación de usuario
echo "5. Test user authentication:"
ldapwhoami -x -H ldap://$LDAP_HOST:$LDAP_PORT \
  -D "uid=jane.smith,ou=users,$BASE_DN" \
  -w "Password123!"
```

---

### 6. 3. Laboratorio: Autenticación LDAP en Aplicación

Vamos a crear una aplicación que autentique usuarios contra nuestro servidor LDAP.

#### Implementación en Spring Boot

**1. Dependencias (build.gradle. kts):**

```kotlin
dependencies {
    implementation("org.springframework.boot:spring-boot-starter-web")
    implementation("org.springframework.boot:spring-boot-starter-security")
    implementation("org.springframework.ldap:spring-ldap-core")
    implementation("org.springframework.security:spring-security-ldap")
    
    // Para tests
    testImplementation("org. springframework.boot:spring-boot-starter-test")
    testImplementation("org.springframework.security:spring-security-test")
}
```

**2. Configuración (application.yml):**

```yaml
spring:
  ldap:
    urls: ldap://localhost:389
    base:  dc=example,dc=local
    username: cn=admin,dc=example,dc=local
    password: admin_secret_password
    
server:
  port: 8080

logging:
  level:
    org.springframework.security: DEBUG
    org.springframework. ldap: DEBUG
```

**3. Configuración de Seguridad:**

```java
package com.example.ldapauth. config;

import org.springframework. context.annotation.Bean;
import org.springframework.context.annotation. Configuration;
import org.springframework. ldap.core.support.BaseLdapPathContextSource;
import org.springframework. security.authentication.AuthenticationManager;
import org.springframework.security.config.annotation.web.builders.HttpSecurity;
import org.springframework.security.config.ldap.LdapBindAuthenticationManagerFactory;
import org.springframework. security.ldap.userdetails.PersonContextMapper;
import org.springframework. security.web.SecurityFilterChain;

@Configuration
public class SecurityConfig {

    @Bean
    public SecurityFilterChain securityFilterChain(HttpSecurity http) throws Exception {
        http
            .authorizeHttpRequests(auth -> auth
                .requestMatchers("/public/**", "/api/health").permitAll()
                .requestMatchers("/admin/**").hasRole("ADMINS")
                .requestMatchers("/api/**").hasRole("USERS")
                .anyRequest().authenticated()
            )
            .httpBasic()
            .and()
            .csrf().disable();  // Solo para desarrollo
        
        return http.build();
    }

    @Bean
    public AuthenticationManager authenticationManager(BaseLdapPathContextSource contextSource) {
        LdapBindAuthenticationManagerFactory factory = 
            new LdapBindAuthenticationManagerFactory(contextSource);
        
        // Patrón de búsqueda de usuarios
        factory.setUserDnPatterns("uid={0},ou=users");
        
        // Búsqueda de grupos
        factory.setUserSearchBase("ou=users");
        factory.setUserSearchFilter("(uid={0})");
        factory.setGroupSearchBase("ou=groups");
        factory.setGroupSearchFilter("(member={0})");
        factory.setGroupRoleAttribute("cn");
        
        return factory. createAuthenticationManager();
    }
}
```

**4. Controlador de prueba:**

```java
package com.example.ldapauth.controller;

import org.springframework.security. core.Authentication;
import org.springframework.security.core. GrantedAuthority;
import org.springframework.web.bind.annotation.*;

import java.util.HashMap;
import java.util.Map;
import java.util.stream. Collectors;

@RestController
@RequestMapping("/api")
public class AuthController {

    @GetMapping("/health")
    public Map<String, String> health() {
        return Map.of("status", "UP");
    }

    @GetMapping("/whoami")
    public Map<String, Object> whoami(Authentication authentication) {
        Map<String, Object> user = new HashMap<>();
        user.put("username", authentication.getName());
        user.put("authorities", authentication.getAuthorities().stream()
            .map(GrantedAuthority::getAuthority)
            .collect(Collectors. toList()));
        user.put("authenticated", authentication.isAuthenticated());
        return user;
    }

    @GetMapping("/user/profile")
    public Map<String, String> userProfile(Authentication authentication) {
        return Map.of(
            "message", "User profile",
            "user", authentication.getName()
        );
    }

    @GetMapping("/admin/dashboard")
    public Map<String, String> adminDashboard(Authentication authentication) {
        return Map.of(
            "message", "Admin dashboard",
            "admin", authentication.getName()
        );
    }
}
```

**5. Tests de integración:**

```java
package com.example.ldapauth;

import org.junit.jupiter. api.Test;
import org. springframework.beans.factory.annotation. Autowired;
import org. springframework.boot.test.autoconfigure.web.servlet.AutoConfigureMockMvc;
import org.springframework.boot.test.context.SpringBootTest;
import org.springframework.security.test.context.support.WithMockUser;
import org. springframework.test.web.servlet. MockMvc;

import static org.springframework.security. test.web.servlet.request. SecurityMockMvcRequestPostProcessors.httpBasic;
import static org. springframework.test.web.servlet. request.MockMvcRequestBuilders.get;
import static org. springframework.test.web.servlet. result.MockMvcResultMatchers.*;

@SpringBootTest
@AutoConfigureMockMvc
public class LdapAuthenticationIntegrationTest {

    @Autowired
    private MockMvc mockMvc;

    @Test
    public void healthEndpoint_ShouldBeAccessibleWithoutAuth() throws Exception {
        mockMvc.perform(get("/api/health"))
            .andExpect(status().isOk())
            .andExpect(jsonPath("$.status").value("UP"));
    }

    @Test
    public void whoami_WithoutAuth_ShouldReturn401() throws Exception {
        mockMvc.perform(get("/api/whoami"))
            .andExpect(status().isUnauthorized());
    }

    @Test
    public void whoami_WithValidLdapUser_ShouldReturnUserInfo() throws Exception {
        mockMvc.perform(get("/api/whoami")
                .with(httpBasic("john.doe", "Password123!")))
            .andExpect(status().isOk())
            .andExpect(jsonPath("$. username").value("john.doe"))
            .andExpect(jsonPath("$.authenticated").value(true))
            .andExpect(jsonPath("$. authorities").isArray());
    }

    @Test
    public void adminEndpoint_WithRegularUser_ShouldReturn403() throws Exception {
        mockMvc.perform(get("/api/admin/dashboard")
                .with(httpBasic("bob.wilson", "Password123!")))
            .andExpect(status().isForbidden());
    }

    @Test
    public void adminEndpoint_WithAdminUser_ShouldReturn200() throws Exception {
        mockMvc. perform(get("/api/admin/dashboard")
                .with(httpBasic("john.doe", "Password123!")))
            .andExpect(status().isOk())
            .andExpect(jsonPath("$. message").value("Admin dashboard"))
            .andExpect(jsonPath("$.admin").value("john.doe"));
    }

    @Test
    public void authenticate_WithInvalidCredentials_ShouldReturn401() throws Exception {
        mockMvc.perform(get("/api/whoami")
                .with(httpBasic("john.doe", "WrongPassword")))
            .andExpect(status().isUnauthorized());
    }

    @Test
    public void authenticate_WithNonExistentUser_ShouldReturn401() throws Exception {
        mockMvc.perform(get("/api/whoami")
                .with(httpBasic("nonexistent", "Password123!")))
            .andExpect(status().isUnauthorized());
    }
}
```

**6. Test manual con curl:**

```bash
# Health check (sin autenticación)
curl http://localhost:8080/api/health

# Whoami con usuario válido
curl -u john.doe:Password123! http://localhost:8080/api/whoami

# Perfil de usuario
curl -u jane.smith:Password123! http://localhost:8080/api/user/profile

# Admin dashboard (solo john.doe es admin)
curl -u john.doe:Password123! http://localhost:8080/api/admin/dashboard

# Admin dashboard con usuario no-admin (debería fallar)
curl -u bob.wilson:Password123! http://localhost:8080/api/admin/dashboard
```

---

#### Implementación en ASP.NET Core

**1. Crear proyecto:**

```bash
dotnet new webapi -n LdapAuthApp
cd LdapAuthApp
dotnet add package Novell.Directory.Ldap. NETStandard --version 3.6.0
```

**2. Servicio de autenticación LDAP:**

```csharp
// Services/LdapAuthenticationService.cs
using Novell.Directory.Ldap;

namespace LdapAuthApp.Services;

public interface ILdapAuthenticationService
{
    bool ValidateUser(string username, string password);
    LdapUser?  GetUser(string username);
}

public class LdapAuthenticationService : ILdapAuthenticationService
{
    private readonly string _ldapHost;
    private readonly int _ldapPort;
    private readonly string _baseDn;
    private readonly string _adminDn;
    private readonly string _adminPassword;

    public LdapAuthenticationService(IConfiguration configuration)
    {
        _ldapHost = configuration["Ldap:Host"] ?? "localhost";
        _ldapPort = int.Parse(configuration["Ldap:Port"] ??  "389");
        _baseDn = configuration["Ldap: BaseDn"] ?? "dc=example,dc=local";
        _adminDn = configuration["Ldap: AdminDn"] ?? "cn=admin,dc=example,dc=local";
        _adminPassword = configuration["Ldap:AdminPassword"] ?? "admin_secret_password";
    }

    public bool ValidateUser(string username, string password)
    {
        try
        {
            using var connection = new LdapConnection();
            connection.Connect(_ldapHost, _ldapPort);

            var userDn = $"uid={username},ou=users,{_baseDn}";
            connection.Bind(userDn, password);

            return connection.Bound;
        }
        catch (LdapException)
        {
            return false;
        }
    }

    public LdapUser? GetUser(string username)
    {
        try
        {
            using var connection = new LdapConnection();
            connection.Connect(_ldapHost, _ldapPort);
            connection.Bind(_adminDn, _adminPassword);

            var searchBase = $"ou=users,{_baseDn}";
            var searchFilter = $"(uid={username})";
            var searchResults = connection.Search(
                searchBase,
                LdapConnection.ScopeSub,
                searchFilter,
                new[] { "uid", "cn", "mail", "memberOf" },
                false
            );

            if (searchResults.HasMore())
            {
                var entry = searchResults.Next();
                return new LdapUser
                {
                    Username = entry. GetAttribute("uid")?.StringValue ?? string.Empty,
                    CommonName = entry.GetAttribute("cn")?.StringValue ?? string.Empty,
                    Email = entry. GetAttribute("mail")?.StringValue ?? string.Empty,
                    Groups = entry.GetAttribute("memberOf")?.StringValueArray?.ToList() ?? new List<string>()
                };
            }

            return null;
        }
        catch (LdapException ex)
        {
            Console.WriteLine($"LDAP Error: {ex.Message}");
            return null;
        }
    }
}

public record LdapUser
{
    public string Username { get; init; } = string.Empty;
    public string CommonName { get; init; } = string.Empty;
    public string Email { get; init; } = string.Empty;
    public List<string> Groups { get.  init; } = new();
}
```

**3. Controlador:**

```csharp
// Controllers/AuthController.cs
using Microsoft.AspNetCore.Mvc;
using LdapAuthApp.Services;

namespace LdapAuthApp. Controllers;

[ApiController]
[Route("api/[controller]")]
public class AuthController : ControllerBase
{
    private readonly ILdapAuthenticationService _ldapService;

    public AuthController(ILdapAuthenticationService ldapService)
    {
        _ldapService = ldapService;
    }

    [HttpPost("login")]
    public IActionResult Login([FromBody] LoginRequest request)
    {
        if (string.IsNullOrEmpty(request.Username) || string.IsNullOrEmpty(request.Password))
        {
            return BadRequest(new { error = "Username and password are required" });
        }

        bool isValid = _ldapService. ValidateUser(request.Username, request.Password);

        if (!isValid)
        {
            return Unauthorized(new { error = "Invalid credentials" });
        }

        var user = _ldapService.GetUser(request.Username);

        if (user == null)
        {
            return Unauthorized(new { error = "User not found" });
        }

        // Aquí normalmente generarías un JWT token
        return Ok(new
        {
            message = "Authentication successful",
            user = new
            {
                username = user.Username,
                name = user.CommonName,
                email = user.Email,
                groups = user.Groups
            }
        });
    }

    [HttpGet("user/{username}")]
    public IActionResult GetUser(string username)
    {
        var user = _ldapService.GetUser(username);

        if (user == null)
        {
            return NotFound(new { error = "User not found" });
        }

        return Ok(user);
    }
}

public record LoginRequest(string Username, string Password);
```

**4. Configuración (appsettings.json):**

```json
{
  "Ldap": {
    "Host": "localhost",
    "Port": "389",
    "BaseDn": "dc=example,dc=local",
    "AdminDn": "cn=admin,dc=example,dc=local",
    "AdminPassword": "admin_secret_password"
  },
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft.AspNetCore": "Warning"
    }
  }
}
```

**5. Registro de servicios (Program.cs):**

```csharp
using LdapAuthApp.Services;

var builder = WebApplication.CreateBuilder(args);

builder.Services.AddControllers();
builder.Services.AddEndpointsApiExplorer();
builder.Services.AddSwaggerGen();

// Registrar servicio LDAP
builder.Services.AddSingleton<ILdapAuthenticationService, LdapAuthenticationService>();

var app = builder.Build();

if (app.Environment.IsDevelopment())
{
    app.UseSwagger();
    app.UseSwaggerUI();
}

app.UseAuthorization();
app.MapControllers();

app.Run();
```

**6. Test con curl:**

```bash
# Login
curl -X POST http://localhost:5000/api/auth/login \
  -H "Content-Type: application/json" \
  -d '{"username": "john.doe", "password": "Password123!"}'

# Obtener información de usuario
curl http://localhost:5000/api/auth/user/jane.smith
```

---

**🎯 Resumen del Bloque 6:**

✅ **DNS (BIND9)** proporciona resolución de nombres: 
- Registros A, CNAME, MX, TXT, SRV, PTR
- Configuración de zonas directas e inversas
- Forwarding a DNS externos
- Tests con dig, nslookup, host

✅ **LDAP/OpenLDAP** centraliza autenticación:
- Estructura jerárquica (DIT)
- Usuarios, grupos y unidades organizativas
- Búsquedas con ldapsearch
- phpLDAPadmin para gestión visual

✅ **Integración con aplicaciones**:
- Spring Boot + Spring Security LDAP
- ASP.NET Core + Novell.Directory. Ldap
- Autenticación contra directorio
- Gestión de roles y grupos

💡 **Consejo Final**:  En producción, LDAP/Active Directory es estándar para empresas medianas-grandes.  Dominar estos conceptos te diferencia como profesional que entiende toda la stack de infraestructura, no solo código de aplicación.

---

## 7. Orquestación Final

### Introducción:  Integrando Todos los Componentes

Hasta ahora hemos trabajado con componentes aislados:
- Backend con base de datos (Bloque 2)
- Tests de API (Bloque 3/4)
- Tests E2E (Bloque 5)
- Infraestructura (DNS, LDAP) (Bloque 6)

En este bloque **orquestaremos todo** en un único sistema coherente que demuestre un entorno de producción realista, incluyendo:

- ✅ **Backend API** (Spring Boot o ASP.NET Core)
- ✅ **Base de datos** (PostgreSQL)
- ✅ **Frontend web** (React/Vue/Angular)
- ✅ **Servidor DNS** (BIND9)
- ✅ **Directorio LDAP** (OpenLDAP)
- ✅ **Reverse proxy** (Nginx)
- ✅ **Tests automatizados** (Newman + Cypress)
- ✅ **Monitorización** (healthchecks)

💡 **Nota del Profesor**: Este es el tipo de arquitectura que encontrarás en empresas reales. Docker Compose permite replicar localmente un entorno que en producción estaría distribuido en múltiples servidores.  Dominar esta orquestación es fundamental para DevOps. 

---

### 7.1. El Gran Escenario: Arquitectura Completa

#### Diagrama de la Arquitectura

```
┌─────────────────────────────────────────────────────────────┐
│                         Internet                             │
└──────────────────────┬──────────────────────────────────────┘
                       │
                       │ : 80, :443
                       ▼
            ┌──────────────────────┐
            │   Nginx (Reverse     │
            │      Proxy)          │
            └──────┬──────┬────────┘
                   │      │
         /: 80      │      │  /api: 8080
                   │      │
       ┌───────────▼──┐ ┌─▼──────────────┐
       │   Frontend   │ │   Backend API  │
       │   (React)    │ │  (Spring Boot) │
       │   : 3000      │ │     :8080      │
       └──────────────┘ └────┬───────────┘
                             │
                 ┌───────────┼───────────┐
                 │           │           │
           : 5432 ▼     : 389  ▼      :53  ▼
        ┌─────────┐ ┌─────────┐ ┌─────────┐
        │PostgreSQL│ │ OpenLDAP│ │  BIND9  │
        │   DB    │ │  Server │ │   DNS   │
        └─────────┘ └─────────┘ └─────────┘
                             │
                             │ phpLDAPadmin : 8090
                             ▼
                      ┌──────────────┐
                      │    Tests     │
                      │ Newman +     │
                      │   Cypress    │
                      └──────────────┘
```

#### Red y Resolución de Nombres

Todos los servicios estarán en una red Docker personalizada con nombres DNS internos: 

| Servicio     | Hostname                | IP (opcional)  | Puerto   |
| ------------ | ----------------------- | -------------- | -------- |
| Nginx        | proxy.example.local     | 192.168.200.10 | 80, 443  |
| Frontend     | webapp.example.local    | 192.168.200.20 | 3000     |
| Backend      | api.example.local       | 192.168.200.30 | 8080     |
| PostgreSQL   | db.example.local        | 192.168.200.40 | 5432     |
| OpenLDAP     | ldap.example.local      | 192.168.200.50 | 389, 636 |
| BIND9        | dns.example.local       | 192.168.200.10 | 53       |
| phpLDAPadmin | ldapadmin.example.local | 192.168.200.51 | 80       |

---

### 7.2. Implementación con Spring Boot

#### 🛠️ Paso a Paso:  Proyecto Completo

**1. Estructura del Proyecto:**

```
complete-system/
├── docker-compose.yml
├── . env
├── backend/
│   ├── Dockerfile
│   ├── build.gradle. kts
│   ├── src/
│   │   ├── main/
│   │   │   ├── java/com/example/app/
│   │   │   │   ├── Application.java
│   │   │   │   ├── config/
│   │   │   │   │   ├── SecurityConfig.java
│   │   │   │   │   └── LdapConfig.java
│   │   │   │   ├── controller/
│   │   │   │   │   ├── AuthController.java
│   │   │   │   │   ├── UserController.java
│   │   │   │   │   └── HealthController.java
│   │   │   │   ├── service/
│   │   │   │   │   └── UserService.java
│   │   │   │   ├── repository/
│   │   │   │   │   └── UserRepository.java
│   │   │   │   └── entity/
│   │   │   │       └── User.java
│   │   │   └── resources/
│   │   │       └── application.yml
│   │   └── test/
│   └── wait-for-it.sh
├── frontend/
│   ├── Dockerfile
│   ├── package.json
│   ├── public/
│   └── src/
│       ├── App.js
│       ├── components/
│       │   ├── Login.js
│       │   ├── Dashboard.js
│       │   └── UserList.js
│       └── services/
│           └── api.js
├── nginx/
│   ├── Dockerfile
│   └── nginx.conf
├── dns/
│   ├── named.conf
│   ├── named.conf.local
│   └── zones/
│       └── db.example.local
├── ldap/
│   ├── bootstrap.ldif
│   ├── users.ldif
│   └── groups.ldif
├── tests/
│   ├── postman/
│   │   └── api-tests.postman_collection.json
│   └── cypress/
│       ├── e2e/
│       │   └── complete-flow.cy.js
│       └── cypress.config.js
└── README.md
```

**2. Variables de Entorno (. env):**

```bash
# Database
POSTGRES_DB=appdb
POSTGRES_USER=appuser
POSTGRES_PASSWORD=SecureDbPass2024!
DATABASE_URL=jdbc:postgresql://db.example.local:5432/appdb

# LDAP
LDAP_DOMAIN=example.local
LDAP_ORGANISATION=Example Company
LDAP_ADMIN_PASSWORD=LdapAdminPass2024! 
LDAP_CONFIG_PASSWORD=LdapConfigPass2024!

# Application
SPRING_PROFILES_ACTIVE=production
JWT_SECRET=MyVerySecureJwtSecretKey2024!
API_BASE_URL=http://api.example.local:8080

# Frontend
REACT_APP_API_URL=http://localhost/api

# Timezone
TZ=Europe/Madrid
```

**3. docker-compose.yml (Completo):**

```yaml
version: '3.8'

services:
  # ============================================
  # DNS Server (BIND9)
  # ============================================
  dns:
    image: ubuntu/bind9:latest
    container_name: dns-server
    hostname: dns.example.local
    volumes:
      - ./dns/named.conf:/etc/bind/named.conf:ro
      - ./dns/named.conf.local:/etc/bind/named.conf.local:ro
      - ./dns/zones:/etc/bind/zones:ro
      - dns-cache:/var/cache/bind
    ports:
      - "53:53/udp"
      - "53:53/tcp"
    environment:
      - TZ=${TZ}
    networks:
      app-network:
        ipv4_address: 192.168.200.2
    restart: unless-stopped
    healthcheck:
      test: ["CMD", "dig", "@127.0.0.1", "example.local"]
      interval: 10s
      timeout: 5s
      retries: 3

  # ============================================
  # LDAP Server (OpenLDAP)
  # ============================================
  ldap:
    image: osixia/openldap:1.5.0
    container_name: ldap-server
    hostname: ldap.example.local
    environment:
      - LDAP_ORGANISATION=${LDAP_ORGANISATION}
      - LDAP_DOMAIN=${LDAP_DOMAIN}
      - LDAP_ADMIN_PASSWORD=${LDAP_ADMIN_PASSWORD}
      - LDAP_CONFIG_PASSWORD=${LDAP_CONFIG_PASSWORD}
      - LDAP_RFC2307BIS_SCHEMA=true
      - LDAP_TLS=false
    volumes:
      - ldap-data:/var/lib/ldap
      - ldap-config:/etc/ldap/slapd.d
      - ./ldap:/container/service/slapd/assets/config/bootstrap/ldif/custom: ro
    ports:
      - "389:389"
      - "636:636"
    networks:
      app-network: 
        ipv4_address:  192.168.200.50
    restart: unless-stopped
    healthcheck:
      test:  ["CMD", "ldapsearch", "-x", "-H", "ldap://localhost", "-b", "dc=example,dc=local", "-LLL"]
      interval: 10s
      timeout: 5s
      retries: 5

  # ============================================
  # LDAP Admin Interface (phpLDAPadmin)
  # ============================================
  ldapadmin:
    image: osixia/phpldapadmin:0.9.0
    container_name: ldap-admin
    hostname: ldapadmin.example.local
    environment:
      - PHPLDAPADMIN_LDAP_HOSTS=ldap. example.local
      - PHPLDAPADMIN_HTTPS=false
    ports:
      - "8090:80"
    depends_on:
      ldap:
        condition: service_healthy
    networks:
      - app-network
    restart: unless-stopped

  # ============================================
  # Database (PostgreSQL)
  # ============================================
  postgres:
    image: postgres:16-alpine
    container_name: postgres-db
    hostname: db.example.local
    environment:
      - POSTGRES_DB=${POSTGRES_DB}
      - POSTGRES_USER=${POSTGRES_USER}
      - POSTGRES_PASSWORD=${POSTGRES_PASSWORD}
      - TZ=${TZ}
    volumes:
      - postgres-data:/var/lib/postgresql/data
      - ./backend/init-db.sql:/docker-entrypoint-initdb.d/init. sql: ro
    ports:
      - "5432:5432"
    networks:
      app-network:
        ipv4_address: 192.168.200.40
    restart: unless-stopped
    healthcheck:
      test:  ["CMD-SHELL", "pg_isready -U ${POSTGRES_USER} -d ${POSTGRES_DB}"]
      interval: 5s
      timeout: 3s
      retries: 10

  # ============================================
  # Backend API (Spring Boot)
  # ============================================
  backend: 
    build:
      context: ./backend
      dockerfile: Dockerfile
    container_name: backend-api
    hostname: api.example.local
    environment:
      - SPRING_PROFILES_ACTIVE=${SPRING_PROFILES_ACTIVE}
      - SPRING_DATASOURCE_URL=${DATABASE_URL}
      - SPRING_DATASOURCE_USERNAME=${POSTGRES_USER}
      - SPRING_DATASOURCE_PASSWORD=${POSTGRES_PASSWORD}
      - SPRING_LDAP_URLS=ldap://ldap.example.local:389
      - SPRING_LDAP_BASE=dc=example,dc=local
      - SPRING_LDAP_USERNAME=cn=admin,dc=example,dc=local
      - SPRING_LDAP_PASSWORD=${LDAP_ADMIN_PASSWORD}
      - JWT_SECRET=${JWT_SECRET}
      - TZ=${TZ}
    ports:
      - "8080:8080"
    depends_on:
      postgres: 
        condition: service_healthy
      ldap:
        condition: service_healthy
    networks:
      app-network:
        ipv4_address: 192.168.200.30
    restart: unless-stopped
    healthcheck: 
      test: ["CMD", "curl", "-f", "http://localhost:8080/actuator/health"]
      interval:  10s
      timeout: 5s
      retries: 15
      start_period: 60s
    dns:
      - 192.168.200.2

  # ============================================
  # Frontend (React)
  # ============================================
  frontend:
    build:
      context: ./frontend
      dockerfile: Dockerfile
      args:
        - REACT_APP_API_URL=${REACT_APP_API_URL}
    container_name: frontend-app
    hostname: webapp.example.local
    environment:
      - NODE_ENV=production
    ports:
      - "3000:80"
    depends_on: 
      backend:
        condition: service_healthy
    networks:
      app-network:
        ipv4_address: 192.168.200.20
    restart: unless-stopped
    healthcheck:
      test: ["CMD", "curl", "-f", "http://localhost:80"]
      interval: 10s
      timeout: 5s
      retries: 5

  # ============================================
  # Reverse Proxy (Nginx)
  # ============================================
  nginx: 
    build:
      context: ./nginx
      dockerfile: Dockerfile
    container_name: nginx-proxy
    hostname: proxy.example.local
    ports:
      - "80:80"
      - "443:443"
    volumes:
      - ./nginx/nginx.conf:/etc/nginx/nginx.conf:ro
      - ./nginx/ssl:/etc/nginx/ssl:ro
    depends_on:
      frontend:
        condition: service_healthy
      backend:
        condition: service_healthy
    networks:
      app-network:
        ipv4_address: 192.168.200.10
    restart: unless-stopped
    healthcheck:
      test: ["CMD", "curl", "-f", "http://localhost/health"]
      interval: 10s
      timeout: 5s
      retries: 3
    dns:
      - 192.168.200.2

  # ============================================
  # API Tests (Newman)
  # ============================================
  newman:
    image: postman/newman:alpine
    container_name: api-tests
    volumes:
      - ./tests/postman:/etc/newman
      - ./tests/reports:/etc/newman/reports
    environment: 
      - API_BASE_URL=http://proxy.example.local/api
    depends_on:
      nginx:
        condition: service_healthy
    networks:
      - app-network
    command: >
      run /etc/newman/api-tests.postman_collection. json
      --environment /etc/newman/environment.json
      --reporters cli,json,html
      --reporter-json-export /etc/newman/reports/newman-report.json
      --reporter-html-export /etc/newman/reports/newman-report.html
      --bail
      --timeout-request 10000
    dns:
      - 192.168.200.2

  # ============================================
  # E2E Tests (Cypress)
  # ============================================
  cypress:
    build:
      context: ./tests/cypress
      dockerfile: Dockerfile
    container_name: e2e-tests
    environment:
      - CYPRESS_baseUrl=http://proxy.example.local
      - CYPRESS_apiUrl=http://api.example.local:8080
      - CYPRESS_video=true
    volumes:
      - ./tests/cypress/e2e:/e2e/cypress/e2e:ro
      - ./tests/cypress/fixtures:/e2e/cypress/fixtures:ro
      - ./tests/reports/cypress/videos:/e2e/cypress/videos
      - ./tests/reports/cypress/screenshots:/e2e/cypress/screenshots
    depends_on: 
      nginx:
        condition:  service_healthy
    networks: 
      - app-network
    command: ["cypress", "run", "--browser", "electron", "--headless"]
    dns:
      - 192.168.200.2

volumes:
  dns-cache:
  ldap-data:
  ldap-config:
  postgres-data: 

networks:
  app-network: 
    driver: bridge
    ipam:
      config: 
        - subnet: 192.168.200.0/24
```

---

**4. Backend Dockerfile:**

```dockerfile
FROM gradle:8. 5-jdk21 AS builder

WORKDIR /app

# Copiar archivos de configuración de Gradle
COPY build.gradle.kts settings.gradle.kts ./
COPY gradle ./gradle

# Descargar dependencias (cacheado)
RUN gradle dependencies --no-daemon

# Copiar código fuente
COPY src ./src

# Compilar aplicación
RUN gradle bootJar --no-daemon

# ============================================
# Imagen de producción
# ============================================
FROM eclipse-temurin:21-jre-alpine

WORKDIR /app

# Instalar utilidades
RUN apk add --no-cache curl bash

# Copiar JAR desde builder
COPY --from=builder /app/build/libs/*.jar app.jar

# Copiar script de espera
COPY wait-for-it.sh /wait-for-it.sh
RUN chmod +x /wait-for-it.sh

# Usuario no-root
RUN addgroup -g 1001 appgroup && \
    adduser -D -u 1001 -G appgroup appuser && \
    chown -R appuser:appgroup /app

USER appuser

EXPOSE 8080

HEALTHCHECK --interval=10s --timeout=5s --start-period=60s --retries=3 \
  CMD curl -f http://localhost:8080/actuator/health || exit 1

ENTRYPOINT ["java", "-XX:+UseContainerSupport", "-XX:MaxRAMPercentage=75. 0", "-jar", "app. jar"]
```

**5. Backend application.yml:**

```yaml
spring:
  application:
    name: user-management-api
  
  profiles:
    active: ${SPRING_PROFILES_ACTIVE:development}
  
  datasource: 
    url: ${SPRING_DATASOURCE_URL}
    username: ${SPRING_DATASOURCE_USERNAME}
    password: ${SPRING_DATASOURCE_PASSWORD}
    driver-class-name: org.postgresql.Driver
    hikari:
      maximum-pool-size: 10
      minimum-idle: 5
      connection-timeout: 30000
      idle-timeout: 600000
      max-lifetime: 1800000
  
  jpa:
    hibernate:
      ddl-auto:  update
    show-sql: false
    properties:
      hibernate: 
        dialect: org.hibernate. dialect.PostgreSQLDialect
        format_sql: true
        jdbc:
          batch_size: 20
  
  ldap:
    urls: ${SPRING_LDAP_URLS}
    base: ${SPRING_LDAP_BASE}
    username: ${SPRING_LDAP_USERNAME}
    password:  ${SPRING_LDAP_PASSWORD}

server:
  port: 8080
  compression:
    enabled: true
  error:
    include-message:  always
    include-stacktrace: on_param

management:
  endpoints:
    web:
      exposure:
        include: health,info,metrics,prometheus
  endpoint:
    health:
      show-details: always
      probes:
        enabled: true
  health:
    livenessState:
      enabled: true
    readinessState: 
      enabled: true

jwt:
  secret: ${JWT_SECRET}
  expiration: 86400000  # 24 horas en milisegundos

logging:
  level:
    root: INFO
    com.example.app: DEBUG
    org.springframework.security: INFO
    org.springframework.ldap: DEBUG
  pattern: 
    console: "%d{yyyy-MM-dd HH:mm:ss} - %msg%n"
```

**6. SecurityConfig. java (con LDAP + JWT):**

```java
package com.example.app.config;

import com.example.app.security.JwtAuthenticationFilter;
import com.example.app.security.JwtTokenProvider;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.ldap.core.support.BaseLdapPathContextSource;
import org.springframework. security.authentication.AuthenticationManager;
import org.springframework.security.config.annotation.web.builders.HttpSecurity;
import org.springframework.security.config.annotation.web.configuration.EnableWebSecurity;
import org. springframework.security.config.http.SessionCreationPolicy;
import org.springframework.security.config.ldap.LdapBindAuthenticationManagerFactory;
import org.springframework. security.web.SecurityFilterChain;
import org.springframework.security.web. authentication.UsernamePasswordAuthenticationFilter;
import org.springframework. web.cors.CorsConfiguration;
import org.springframework.web.cors.CorsConfigurationSource;
import org.springframework.web.cors.UrlBasedCorsConfigurationSource;

import java.util.Arrays;

@Configuration
@EnableWebSecurity
public class SecurityConfig {

    private final JwtTokenProvider jwtTokenProvider;

    public SecurityConfig(JwtTokenProvider jwtTokenProvider) {
        this.jwtTokenProvider = jwtTokenProvider;
    }

    @Bean
    public SecurityFilterChain securityFilterChain(HttpSecurity http) throws Exception {
        http
            .cors().and()
            .csrf().disable()
            .sessionManagement()
                .sessionCreationPolicy(SessionCreationPolicy.STATELESS)
            .and()
            .authorizeHttpRequests(auth -> auth
                .requestMatchers(
                    "/api/auth/**",
                    "/actuator/health/**",
                    "/actuator/info",
                    "/health",
                    "/api/public/**"
                ).permitAll()
                .requestMatchers("/api/admin/**").hasRole("ADMINS")
                .requestMatchers("/api/**").hasAnyRole("USERS", "ADMINS")
                .anyRequest().authenticated()
            )
            .addFilterBefore(
                new JwtAuthenticationFilter(jwtTokenProvider),
                UsernamePasswordAuthenticationFilter.class
            );

        return http.build();
    }

    @Bean
    public AuthenticationManager authenticationManager(BaseLdapPathContextSource contextSource) {
        LdapBindAuthenticationManagerFactory factory = 
            new LdapBindAuthenticationManagerFactory(contextSource);
        
        factory.setUserDnPatterns("uid={0},ou=users");
        factory.setUserSearchBase("ou=users");
        factory.setUserSearchFilter("(uid={0})");
        factory.setGroupSearchBase("ou=groups");
        factory.setGroupSearchFilter("(member={0})");
        factory.setGroupRoleAttribute("cn");
        
        return factory.createAuthenticationManager();
    }

    @Bean
    public CorsConfigurationSource corsConfigurationSource() {
        CorsConfiguration configuration = new CorsConfiguration();
        configuration.setAllowedOrigins(Arrays.asList(
            "http://localhost",
            "http://localhost:3000",
            "http://proxy.example.local",
            "http://webapp.example.local"
        ));
        configuration.setAllowedMethods(Arrays.asList("GET", "POST", "PUT", "DELETE", "OPTIONS"));
        configuration.setAllowedHeaders(Arrays.asList("*"));
        configuration.setAllowCredentials(true);
        configuration.setMaxAge(3600L);

        UrlBasedCorsConfigurationSource source = new UrlBasedCorsConfigurationSource();
        source.registerCorsConfiguration("/**", configuration);
        return source;
    }
}
```

**7. AuthController.java:**

```java
package com.example.app.controller;

import com.example.app.dto.LoginRequest;
import com.example.app.dto.LoginResponse;
import com.example.app.security.JwtTokenProvider;
import org.springframework.http.ResponseEntity;
import org.springframework.security. authentication.AuthenticationManager;
import org.springframework.security.authentication. UsernamePasswordAuthenticationToken;
import org.springframework.security. core.Authentication;
import org. springframework.security.core.AuthenticationException;
import org.springframework.security.core. GrantedAuthority;
import org.springframework.web.bind.annotation.*;

import java.util.stream.Collectors;

@RestController
@RequestMapping("/api/auth")
public class AuthController {

    private final AuthenticationManager authenticationManager;
    private final JwtTokenProvider jwtTokenProvider;

    public AuthController(
            AuthenticationManager authenticationManager,
            JwtTokenProvider jwtTokenProvider) {
        this.authenticationManager = authenticationManager;
        this.jwtTokenProvider = jwtTokenProvider;
    }

    @PostMapping("/login")
    public ResponseEntity<? > login(@RequestBody LoginRequest request) {
        try {
            Authentication authentication = authenticationManager.authenticate(
                new UsernamePasswordAuthenticationToken(
                    request.getUsername(),
                    request.getPassword()
                )
            );

            String token = jwtTokenProvider.generateToken(authentication);
            
            var roles = authentication.getAuthorities().stream()
                .map(GrantedAuthority::getAuthority)
                .collect(Collectors. toList());

            return ResponseEntity.ok(new LoginResponse(
                token,
                authentication.getName(),
                roles
            ));

        } catch (AuthenticationException e) {
            return ResponseEntity. status(401)
                .body(new ErrorResponse("Invalid credentials"));
        }
    }

    @PostMapping("/validate")
    public ResponseEntity<?> validateToken(@RequestHeader("Authorization") String authHeader) {
        try {
            String token = authHeader.replace("Bearer ", "");
            boolean isValid = jwtTokenProvider. validateToken(token);
            
            if (isValid) {
                String username = jwtTokenProvider.getUsernameFromToken(token);
                return ResponseEntity.ok(new TokenValidationResponse(true, username));
            } else {
                return ResponseEntity.status(401)
                    .body(new TokenValidationResponse(false, null));
            }
        } catch (Exception e) {
            return ResponseEntity.status(401)
                .body(new TokenValidationResponse(false, null));
        }
    }

    @GetMapping("/whoami")
    public ResponseEntity<? > whoami(Authentication authentication) {
        if (authentication == null || ! authentication.isAuthenticated()) {
            return ResponseEntity.status(401).body(new ErrorResponse("Not authenticated"));
        }

        return ResponseEntity.ok(new WhoAmIResponse(
            authentication.getName(),
            authentication.getAuthorities().stream()
                .map(GrantedAuthority::getAuthority)
                .collect(Collectors.toList())
        ));
    }

    // DTOs internos
    record ErrorResponse(String error) {}
    record TokenValidationResponse(boolean valid, String username) {}
    record WhoAmIResponse(String username, java.util.List<String> roles) {}
}
```

**8. HealthController.java:**

```java
package com.example.app.controller;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.actuate.health.Health;
import org.springframework.boot. actuate.health.HealthEndpoint;
import org.springframework. http.ResponseEntity;
import org.springframework.web.bind.annotation.GetMapping;
import org. springframework.web.bind.annotation. RestController;

import javax.sql.DataSource;
import java. sql.Connection;
import java. util.HashMap;
import java.util.Map;

@RestController
public class HealthController {

    @Autowired
    private DataSource dataSource;

    @GetMapping("/health")
    public ResponseEntity<Map<String, Object>> health() {
        Map<String, Object> health = new HashMap<>();
        health.put("status", "UP");
        health.put("timestamp", System.currentTimeMillis());
        
        // Check database
        try (Connection conn = dataSource.getConnection()) {
            health.put("database", "UP");
        } catch (Exception e) {
            health.put("database", "DOWN");
            health.put("status", "DEGRADED");
        }

        return ResponseEntity.ok(health);
    }

    @GetMapping("/api/health")
    public ResponseEntity<Map<String, String>> apiHealth() {
        return ResponseEntity.ok(Map.of(
            "status", "UP",
            "service", "user-management-api",
            "version", "1.0.0"
        ));
    }
}
```

**9. JwtTokenProvider.java:**

```java
package com.example.app.security;

import io.jsonwebtoken.*;
import io.jsonwebtoken.security.Keys;
import org.springframework.beans.factory.annotation.Value;
import org.springframework.security.core.Authentication;
import org.springframework.security.core. GrantedAuthority;
import org.springframework.stereotype.Component;

import javax.crypto.SecretKey;
import java.nio.charset.StandardCharsets;
import java.util. Date;
import java.util. stream.Collectors;

@Component
public class JwtTokenProvider {

    private final SecretKey secretKey;
    private final long validityInMilliseconds;

    public JwtTokenProvider(
            @Value("${jwt. secret}") String secret,
            @Value("${jwt.expiration}") long validityInMilliseconds) {
        this.secretKey = Keys.hmacShaKeyFor(secret. getBytes(StandardCharsets.UTF_8));
        this.validityInMilliseconds = validityInMilliseconds;
    }

    public String generateToken(Authentication authentication) {
        String username = authentication.getName();
        Date now = new Date();
        Date validity = new Date(now.getTime() + validityInMilliseconds);

        var roles = authentication.getAuthorities().stream()
            .map(GrantedAuthority::getAuthority)
            .collect(Collectors.toList());

        return Jwts.builder()
            .setSubject(username)
            .claim("roles", roles)
            .setIssuedAt(now)
            .setExpiration(validity)
            .signWith(secretKey, SignatureAlgorithm. HS512)
            .compact();
    }

    public String getUsernameFromToken(String token) {
        Claims claims = Jwts.parserBuilder()
            .setSigningKey(secretKey)
            .build()
            .parseClaimsJws(token)
            .getBody();

        return claims.getSubject();
    }

    public boolean validateToken(String token) {
        try {
            Jwts.parserBuilder()
                .setSigningKey(secretKey)
                .build()
                .parseClaimsJws(token);
            return true;
        } catch (JwtException | IllegalArgumentException e) {
            return false;
        }
    }
}
```

**10. JwtAuthenticationFilter.java:**

```java
package com.example.app.security;

import jakarta.servlet.FilterChain;
import jakarta.servlet.ServletException;
import jakarta.servlet.http.HttpServletRequest;
import jakarta.servlet.http.HttpServletResponse;
import org.springframework. security.authentication.UsernamePasswordAuthenticationToken;
import org.springframework.security.core.context.SecurityContextHolder;
import org.springframework.security.web.authentication.WebAuthenticationDetailsSource;
import org.springframework.web.filter.OncePerRequestFilter;

import java.io.IOException;
import java.util.ArrayList;

public class JwtAuthenticationFilter extends OncePerRequestFilter {

    private final JwtTokenProvider jwtTokenProvider;

    public JwtAuthenticationFilter(JwtTokenProvider jwtTokenProvider) {
        this.jwtTokenProvider = jwtTokenProvider;
    }

    @Override
    protected void doFilterInternal(
            HttpServletRequest request,
            HttpServletResponse response,
            FilterChain filterChain) throws ServletException, IOException {

        String authHeader = request.getHeader("Authorization");

        if (authHeader != null && authHeader.startsWith("Bearer ")) {
            String token = authHeader.substring(7);

            if (jwtTokenProvider. validateToken(token)) {
                String username = jwtTokenProvider. getUsernameFromToken(token);

                UsernamePasswordAuthenticationToken authentication =
                    new UsernamePasswordAuthenticationToken(
                        username,
                        null,
                        new ArrayList<>()
                    );

                authentication.setDetails(
                    new WebAuthenticationDetailsSource().buildDetails(request)
                );

                SecurityContextHolder.getContext().setAuthentication(authentication);
            }
        }

        filterChain.doFilter(request, response);
    }
}
```

---

**11. Frontend Dockerfile (React):**

```dockerfile
# Build stage
FROM node:20-alpine AS builder

WORKDIR /app

# Copiar package files
COPY package*.json ./

# Instalar dependencias
RUN npm ci --only=production

# Copiar código
COPY public ./public
COPY src ./src

# Argument para API URL
ARG REACT_APP_API_URL
ENV REACT_APP_API_URL=$REACT_APP_API_URL

# Build
RUN npm run build

# Production stage con Nginx
FROM nginx:alpine

# Copiar build de React
COPY --from=builder /app/build /usr/share/nginx/html

# Copiar configuración de Nginx
COPY nginx.conf /etc/nginx/conf.d/default.conf

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
```

**12. Nginx Configuration (nginx/nginx.conf):**

```nginx
user nginx;
worker_processes auto;
error_log /var/log/nginx/error.log warn;
pid /var/run/nginx.pid;

events {
    worker_connections 1024;
}

http {
    include /etc/nginx/mime.types;
    default_type application/octet-stream;

    log_format main '$remote_addr - $remote_user [$time_local] "$request" '
                    '$status $body_bytes_sent "$http_referer" '
                    '"$http_user_agent" "$http_x_forwarded_for"';

    access_log /var/log/nginx/access.log main;

    sendfile on;
    tcp_nopush on;
    tcp_nodelay on;
    keepalive_timeout 65;
    types_hash_max_size 2048;

    gzip on;
    gzip_vary on;
    gzip_min_length 1024;
    gzip_types text/plain text/css application/json application/javascript text/xml application/xml application/xml+rss text/javascript;

    # Upstream para el backend
    upstream backend_api {
        server api. example.local:8080 max_fails=3 fail_timeout=30s;
    }

    # Upstream para el frontend
    upstream frontend_app {
        server webapp.example.local:80 max_fails=3 fail_timeout=30s;
    }

    server {
        listen 80;
        server_name localhost proxy.example.local;

        client_max_body_size 10M;

        # Health check endpoint
        location /health {
            access_log off;
            return 200 "healthy\n";
            add_header Content-Type text/plain;
        }

        # Backend API
        location /api/ {
            proxy_pass http://backend_api/api/;
            
            proxy_set_header Host $host;
            proxy_set_header X-Real-IP $remote_addr;
            proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
            proxy_set_header X-Forwarded-Proto $scheme;
            
            # Timeouts
            proxy_connect_timeout 60s;
            proxy_send_timeout 60s;
            proxy_read_timeout 60s;
            
            # Buffer settings
            proxy_buffering on;
            proxy_buffer_size 4k;
            proxy_buffers 8 4k;
            proxy_busy_buffers_size 8k;
            
            # WebSocket support
            proxy_http_version 1.1;
            proxy_set_header Upgrade $http_upgrade;
            proxy_set_header Connection "upgrade";
        }

        # Actuator endpoints
        location /actuator/ {
            proxy_pass http://backend_api/actuator/;
            proxy_set_header Host $host;
            proxy_set_header X-Real-IP $remote_addr;
        }

        # Frontend app
        location / {
            proxy_pass http://frontend_app/;
            
            proxy_set_header Host $host;
            proxy_set_header X-Real-IP $remote_addr;
            proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
            
            # SPA routing support
            try_files $uri $uri/ /index.html;
        }

        # Cache static assets
        location ~* \.(js|css|png|jpg|jpeg|gif|ico|svg|woff|woff2|ttf|eot)$ {
            proxy_pass http://frontend_app;
            expires 1y;
            add_header Cache-Control "public, immutable";
        }

        # Security headers
        add_header X-Frame-Options "SAMEORIGIN" always;
        add_header X-Content-Type-Options "nosniff" always;
        add_header X-XSS-Protection "1; mode=block" always;
        add_header Referrer-Policy "no-referrer-when-downgrade" always;
    }
}
```

---

### 7. 3.  Ejecución y Verificación

**1. Levantar todo el sistema:**

```bash
# Asegurarse de que Docker está corriendo
docker --version
docker-compose --version

# Levantar servicios de infraestructura primero
docker-compose up -d dns ldap postgres

# Esperar a que estén saludables
docker-compose ps

# Levantar resto de servicios
docker-compose up -d backend frontend nginx

# Ver logs en tiempo real
docker-compose logs -f
```

**2. Verificar estado de todos los servicios:**

```bash
# Script de verificación
#!/bin/bash

echo "=== System Health Check ==="
echo ""

services=(
  "DNS: http://localhost:53"
  "LDAP:ldap://localhost:389"
  "PostgreSQL:postgresql://localhost:5432"
  "Backend: http://localhost:8080/actuator/health"
  "Frontend:http://localhost:3000"
  "Nginx:http://localhost/health"
  "phpLDAPadmin:http://localhost:8090"
)

for service in "${services[@]}"; do
  name=$(echo $service | cut -d:  -f1)
  url=$(echo $service | cut -d: -f2-)
  
  echo -n "Checking $name... "
  
  case $name in
    "DNS")
      if dig @localhost example.local +short > /dev/null 2>&1; then
        echo "✓ OK"
      else
        echo "✗ FAIL"
      fi
      ;;
    "LDAP")
      if ldapsearch -x -H ldap://localhost:389 -b "dc=example,dc=local" -LLL > /dev/null 2>&1; then
        echo "✓ OK"
      else
        echo "✗ FAIL"
      fi
      ;;
    "PostgreSQL")
      if docker-compose exec -T postgres pg_isready > /dev/null 2>&1; then
        echo "✓ OK"
      else
        echo "✗ FAIL"
      fi
      ;;
    *)
      if curl -sf "$url" > /dev/null 2>&1; then
        echo "✓ OK"
      else
        echo "✗ FAIL"
      fi
      ;;
  esac
done

echo ""
echo "=== Container Status ==="
docker-compose ps
```

**3. Ejecutar tests automatizados:**

```bash
# Tests de API con Newman
docker-compose up newman

# Tests E2E con Cypress
docker-compose up cypress

# Ver reportes
ls -la tests/reports/
```

**4. Acceso manual:**

```bash
# Frontend
open http://localhost

# Backend API directamente
curl http://localhost:8080/api/health

# A través de Nginx
curl http://localhost/api/health

# phpLDAPadmin
open http://localhost:8090

# Login test
curl -X POST http://localhost/api/auth/login \
  -H "Content-Type: application/json" \
  -d '{"username":"john. doe","password":"Password123!"}'
```

---

**🎯 Resumen del Bloque 7:**

✅ **Orquestación completa** con Docker Compose:
- 9 servicios interconectados
- Dependencias gestionadas con healthchecks
- Red personalizada con DNS interno
- Variables de entorno centralizadas

✅ **Servicios de infraestructura**:
- DNS (BIND9) para resolución de nombres
- LDAP (OpenLDAP) para autenticación
- PostgreSQL para persistencia
- Nginx como reverse proxy

✅ **Aplicación completa**:
- Backend Spring Boot con seguridad LDAP + JWT
- Frontend React (o similar)
- APIs RESTful documentadas
- Health checks en todos los niveles

✅ **Testing automatizado integrado**:
- Newman para tests de API
- Cypress para tests E2E
- Ejecución en el mismo docker-compose

💡 **Consejo Final**:  Este es un sistema de producción en miniatura.  Cada componente tiene un propósito específico y todos se comunican de forma orquestada. Dominar esta arquitectura te prepara para trabajar en equipos profesionales donde múltiples servicios deben funcionar juntos de forma confiable.

---



# Autor

Codificado con :sparkling_heart: por [José Luis González Sánchez](https://twitter.com/JoseLuisGS_)

[![Twitter](https://img.shields.io/twitter/follow/JoseLuisGS_?style=social)](https://twitter.com/JoseLuisGS_)
[![GitHub](https://img.shields.io/github/followers/joseluisgs?style=social)](https://github.com/joseluisgs)
[![GitHub](https://img.shields.io/github/stars/joseluisgs?style=social)](https://github.com/joseluisgs)

## Contacto

<p>
  Cualquier cosa que necesites házmelo saber por si puedo ayudarte 💬.
</p>
<p>
 <a href="https://joseluisgs.dev" target="_blank">
        <img src="https://joseluisgs.github.io/img/favicon.png" 
    height="30">
    </a>  &nbsp;&nbsp;
    <a href="https://github.com/joseluisgs" target="_blank">
        <img src="https://distreau.com/github.svg" 
    height="30">
    </a> &nbsp;&nbsp;
        <a href="https://twitter.com/JoseLuisGS_" target="_blank">
        <img src="https://i.imgur.com/U4Uiaef.png" 
    height="30">
    </a> &nbsp;&nbsp;
    <a href="https://www.linkedin.com/in/joseluisgonsan" target="_blank">
        <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/c/ca/LinkedIn_logo_initials.png/768px-LinkedIn_logo_initials.png" 
    height="30">
    </a>  &nbsp;&nbsp;
    <a href="https://g.dev/joseluisgs" target="_blank">
        <img loading="lazy" src="https://googlediscovery.com/wp-content/uploads/google-developers.png" 
    height="30">
    </a>  &nbsp;&nbsp;
<a href="https://www.youtube.com/@joseluisgs" target="_blank">
        <img loading="lazy" src="https://upload.wikimedia.org/wikipedia/commons/e/ef/Youtube_logo.png" 
    height="30">
    </a>  
</p>

## Licencia de uso

Este repositorio y todo su contenido está licenciado bajo licencia **Creative Commons**, si desea saber más, vea
la [LICENSE](https://joseluisgs.dev/docs/license/). Por favor si compartes, usas o modificas este proyecto cita a su
autor, y usa las mismas condiciones para su uso docente, formativo o educativo y no comercial.

<a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/4.0/"><img alt="Licencia de Creative Commons" style="border-width:0" src="https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png" /></a><br /><span xmlns:dct="http://purl.org/dc/terms/" property="dct:title">
JoseLuisGS</span>
by <a xmlns:cc="http://creativecommons.org/ns#" href="https://joseluisgs.dev/" property="cc:attributionName" rel="cc:attributionURL">
José Luis González Sánchez</a> is licensed under
a <a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/4.0/">Creative Commons
Reconocimiento-NoComercial-CompartirIgual 4.0 Internacional License</a>.<br />Creado a partir de la obra
en <a xmlns:dct="http://purl.org/dc/terms/" href="https://github.com/joseluisgs" rel="dct:source">https://github.com/joseluisgs</a>.