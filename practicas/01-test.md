- [Bloque 1: Introducción y Cultura de QA](#bloque-1-introducción-y-cultura-de-qa)
- [Bloque 2: Pruebas Unitarias y Dobles de Prueba](#bloque-2-pruebas-unitarias-y-dobles-de-prueba)
- [Bloque 3: Cobertura de Código](#bloque-3-cobertura-de-código)
- [Bloque 4: Integración con Testcontainers](#bloque-4-integración-con-testcontainers)
- [Bloque 5: Automatización de APIs (Postman y Newman)](#bloque-5-automatización-de-apis-postman-y-newman)
- [Bloque 6: Validación de Interfaz con Playwright](#bloque-6-validación-de-interfaz-con-playwright)
- [Bloque 7: Servicios de Red e Infraestructura](#bloque-7-servicios-de-red-e-infraestructura)
- [Bloque 8: Orquestación Final](#bloque-8-orquestación-final)



### Bloque 1: Introducción y Cultura de QA

1. ¿Qué pregunta define el concepto de **Verificación**?
   a) ¿Estamos construyendo el producto correcto?
   b) ¿Estamos construyendo el producto correctamente?
   c) ¿El cliente está satisfecho con el diseño?
   d) ¿La aplicación es rentable para la empresa?

2. En el contexto de V&V, la **Validación** se enfoca en:
   a) Cumplir con las especificaciones técnicas.
   b) Verificar que el software satisfaga las necesidades del usuario.
   c) Comprobar que el método `hashPassword()` use el algoritmo correcto.
   d) Analizar el tiempo de compilación del código.

3. Según la **Pirámide de Tests**, ¿qué porcentaje de pruebas deberían ser **unitarias**?
   a) 10%
   b) 20%
   c) 50%
   d) 70%

4. Las pruebas que simulan el comportamiento completo del usuario final se denominan:
   a) Pruebas Unitarias.
   b) Pruebas de Integración.
   c) Pruebas E2E (End-to-End).
   d) Pruebas de Humo.

5. ¿Cuál es el coste relativo de corregir un bug detectado en la fase de **Producción** comparado con la de Desarrollo?
   a) 1x
   b) 10x
   c) 50x
   d) 100x-1000x

6. Un beneficio de invertir en testing es evitar el daño reputacional y la pérdida de confianza.
   a) Verdadero.
   b) Falso.
   c) Solo si se detecta en Staging.
   d) Solo si la empresa es grande.

7. ¿Qué herramienta se menciona para crear **entornos reproducibles** en el despliegue?
   a) Selenium.
   b) Docker.
   c) Postman.
   d) JaCoCo.

8. Las pruebas de integración verifican la comunicación entre componentes del sistema.
   a) Verdadero, y representan el 20% de la pirámide.
   b) Falso, son el 70% de la pirámide.
   c) Verdadero, pero solo se hacen manualmente.
   d) Falso, solo verifican funciones individuales.

9. ¿Cuál de estos factores NO aumenta el coste de un error en producción?
   a) Análisis de impacto.
   b) Reuniones de crisis.
   c) Escritura de código en fase de desarrollo.
   d) Compensación a clientes afectados.

10. El objetivo de la V&V es garantizar que el software funcione correctamente y...
    a) Sea visualmente atractivo.
    b) Como se espera según las necesidades del usuario.
    c) Utilice la última versión de Java.
    d) No tenga comentarios en el código.

### Bloque 2: Pruebas Unitarias y Dobles de Prueba

11. Una **prueba unitaria** debe verificar el comportamiento de:
    a) Toda la infraestructura de red.
    b) Una unidad mínima de código de forma aislada.
    c) La conexión con la base de datos real.
    d) El balanceador de carga.

12. ¿Cuál es una característica de una **buena** prueba unitaria?
    a) Depender de otras pruebas para ejecutarse.
    b) Ser lenta para asegurar precisión.
    c) Ser auto-verificable (pasa o falla sin intervención).
    d) Usar una base de datos externa.

13. Un objeto que se usa para rellenar parámetros que no se utilizan realmente en el test es un:
    a) Mock.
    b) Stub.
    c) Dummy.
    d) Spy.

14. ¿Qué tipo de doble de prueba tiene **lógica funcional**, como una base de datos en memoria?
    a) Fake.
    b) Stub.
    c) Mock.
    d) Spy.

15. El propósito de un **Mock** es principalmente:
    a) Proporcionar respuestas predefinidas fijas.
    b) Registrar cómo se invoca a un objeto real.
    c) Verificar que se realicen llamadas específicas correctamente.
    d) No hacer nada y solo ocupar espacio.

16. En **Mockito**, ¿qué anotación se utiliza para crear un objeto simulado?
    a) `@InjectMocks`
    b) `@Mock`
    c) `@Test`
    d) `@Spy`

17. Para definir el comportamiento de un método que devuelve un valor en Mockito, se usa:
    a) `verify().method()`
    b) `doNothing().when()`
    c) `when().thenReturn()`
    d) `Assert.assertEquals()`

18. Si un método es **void** y queremos que lance una excepción en Mockito, debemos usar:
    a) `when().thenReturn()`
    b) `doThrow().when()`
    c) `verify()`
    d) `assertThrows()`

19. En .NET, la librería que mejora la legibilidad de las aserciones (ej: `actual.Should().Be(expected)`) es:
    a) NUnit.
    b) Moq.
    c) FluentAssertions.
    d) Coverlet.

20. En las pruebas unitarias con **NUnit**, el atributo para marcar un método de prueba es:
    a) `[Test]`
    b) `[Fact]`
    c) `[Mock]`
    d) `[SetUp]`

21. Una prueba unitaria debe ser **repetible**, lo que significa que:
    a) Se debe copiar el código en varios archivos.
    b) Debe producir siempre el mismo resultado.
    c) Solo se puede ejecutar una vez al día.
    d) Necesita que el programador la revise manualmente.

22. El concepto de **Stubbing** consiste en:
    a) Validar el esquema JSON.
    b) Definir el comportamiento de un mock para devolver valores fijos.
    c) Ejecutar un contenedor de Docker.
    d) Borrar la base de datos después de cada test.

23. ¿Qué hace un **Spy** que no haga un Mock?
    a) No permite lógica interna.
    b) Es un objeto real con capacidad de inspección.
    c) Solo devuelve valores nulos.
    d) Requiere conexión a internet.

24. ¿Cuándo es el momento "oportuno" para escribir una prueba unitaria?
    a) Tres meses después de desplegar.
    b) Junto al código, o antes con TDD.
    c) Solo cuando el cliente encuentra un fallo.
    d) Nunca, si el código compila.

25. Un error común mencionado en las fuentes es usar `when()` con:
    a) Métodos que devuelven un String.
    b) Métodos de tipo void.
    c) Métodos asíncronos.
    d) Variables estáticas.

### Bloque 3: Cobertura de Código

26. La **cobertura de código** mide:
    a) La velocidad del servidor.
    b) El porcentaje de código fuente ejecutado por las pruebas.
    c) El número de programadores trabajando en el proyecto.
    d) La cantidad de comentarios por línea de código.

27. ¿Qué tipo de cobertura mide qué ramas condicionales (if/else) se han probado?
    a) Line Coverage.
    b) Branch Coverage.
    c) Method Coverage.
    d) Statement Coverage.

28. Tener un **100% de cobertura** garantiza que el código está libre de errores.
    a) Verdadero.
    b) Falso, lo importante es la calidad de las pruebas.
    c) Solo si se usa JaCoCo.
    d) Solo si se usa en .NET.

29. En el reporte de **JaCoCo**, el color amarillo indica:
    a) Línea totalmente ejecutada.
    b) Línea no ejecutada.
    c) Rama parcialmente cubierta (ej: solo el if).
    d) El test ha fallado.

30. ¿Qué herramienta se utiliza para medir la cobertura en proyectos **.NET**?
    a) JaCoCo.
    b) Coverlet.
    c) Newman.
    d) Cypress.

### Bloque 4: Integración con Testcontainers

31. ¿Cuál es el problema principal de usar **Mocks** para simular bases de datos?
    a) Son muy lentos.
    b) No validan constraints como FK o UNIQUE reales.
    c) Requieren instalar Docker.
    d) Solo funcionan con Java.

32. **Testcontainers** permite ejecutar contenedores Docker desde:
    a) El navegador únicamente.
    b) El código de los propios tests.
    c) La terminal de Linux exclusivamente.
    d) El panel de control de Windows.

33. Una ventaja clave de Testcontainers es el **aislamiento**, lo que significa que:
    a) El desarrollador trabaja solo.
    b) Cada test suite tiene su propia base de datos limpia.
    c) La aplicación no necesita red.
    d) El código no se comparte con el equipo.

34. ¿Qué tecnología es **necesaria** para que Testcontainers funcione?
    a) Kubernetes.
    b) Docker.
    c) VirtualBox.
    d) Jenkins.

35. En Spring Boot 3.1+, la anotación que simplifica la conexión al contenedor es:
    a) `@MockBean`
    b) `@ServiceConnection`
    c) `@TestPropertySource`
    d) `@Autowired`

36. Por defecto, Testcontainers crea un contenedor nuevo para:
    a) Cada línea de código.
    b) Cada clase de test.
    c) Cada vez que el ordenador se reinicia.
    d) Solo si el test falla.

37. ¿Para qué sirve la opción `withReuse(true)` en Testcontainers?
    a) Para borrar la imagen de Docker.
    b) Para acelerar los tests en desarrollo local reutilizando contenedores.
    c) Para compartir la base de datos con producción.
    d) Para que el código sea más legible.

38. Los tests de integración con Testcontainers aseguran un comportamiento idéntico a:
    a) El entorno de desarrollo de juguete.
    b) El entorno de producción.
    c) Una hoja de Excel.
    d) Los requerimientos del cliente por escrito.

39. En .NET, ¿qué método se suele usar para limpiar los datos antes de cada test individual?
    a) `[OneTimeSetUp]`
    b) `[SetUp]`
    c) `[TearDown]`
    d) `[CleanUp]`

40. ¿Qué sucede con los contenedores de Testcontainers si un test falla?
    a) Se quedan encendidos para siempre.
    b) Se eliminan automáticamente igual que si pasara.
    c) Se bloquea el ordenador.
    d) Se envían a la papelera de reciclaje.

41. Testcontainers permite probar no solo bases de datos, sino también:
    a) Colas de mensajes (RabbitMQ, Kafka).
    b) Servicios externos como Redis.
    c) Navegadores para Selenium.
    d) Todas las anteriores son correctas.

42. ¿Qué ventaja ofrece Testcontainers respecto al "Dialecto SQL"?
    a) Ignora el dialecto por completo.
    b) Permite probar comportamientos específicos del motor real.
    c) Traduce SQL a Java automáticamente.
    d) No permite usar SQL.

43. ¿Cómo se puede inicializar la base de datos en Testcontainers con un script específico?
    a) Copiando y pegando en la terminal.
    b) Con el método `withInitScript()`.
    c) No se puede inicializar.
    d) Escribiendo el script en el README.

44. ¿Qué es el "Fin de los Mocks en Bases de Datos"?
    a) Una ley que prohíbe los mocks.
    b) El cambio hacia el uso de infraestructura real para pruebas de integración.
    c) Que los mocks ya no existen en Java.
    d) Que las bases de datos ya no necesitan tests.

45. En .NET, para usar PostgreSQL con Testcontainers se necesita el paquete:
    a) `Testcontainers.PostgreSql`
    b) `Docker.Net.Postgres`
    c) `EntityFrameWork.Containers`
    d) `Microsoft.Testing.Containers`

### Bloque 5: Automatización de APIs (Postman y Newman)

46. ¿Qué herramienta se utiliza para ejecutar colecciones de Postman desde la **línea de comandos**?
    a) Postman CLI.
    b) Newman.
    c) Docker Desktop.
    d) Git Bash.

47. En Postman, las variables de entorno permiten:
    a) Cambiar entre entornos (dev, staging, prod) sin modificar las requests.
    b) Guardar el historial de navegación.
    c) Comprar licencias de software.
    d) Cambiar el color de la interfaz.

48. ¿Qué variable dinámica de Postman genera un **timestamp** único?
    a) `{{randomInt}}`
    b) `{{$timestamp}}`
    c) `{{date_now}}`
    d) `{{unique_id}}`

49. Los scripts de validación en Postman se escriben en el lenguaje:
    a) Python.
    b) Java.
    c) JavaScript.
    d) PHP.

50. Para validar que una respuesta HTTP sea exitosa (200 OK) en Postman, se usa:
    a) `pm.response.to.have.status(200)`
    b) `assert status == 200`
    c) `expect(200).toBeOK()`
    d) `checkStatus(200)`

51. ¿Qué funcionalidad de Postman permite preparar datos **antes** de enviar una petición?
    a) Tests Tab.
    b) Pre-request Script.
    c) Environment Tab.
    d) Console.

52. ¿Dónde se definen los tests que se deben ejecutar para **todas** las peticiones de una colección?
    a) En cada request individualmente.
    b) En el nivel de carpeta solamente.
    c) En el nivel de colección (Edit -> Tests).
    d) No es posible hacer tests globales.

53. Newman se integra habitualmente en pipelines de:
    a) Diseño gráfico.
    b) CI/CD (GitHub Actions, Jenkins).
    c) Gestión de RRHH.
    d) Edición de video.

54. Para generar un **reporte HTML** con Newman, es necesario instalar:
    a) Un navegador nuevo.
    b) El paquete `newman-reporter-htmlextra`.
    c) Microsoft Word.
    d) Adobe Reader.

55. La opción `--bail` en Newman sirve para:
    a) Bailar cuando los tests pasan.
    b) Detener la ejecución en el primer fallo.
    c) Ignorar todos los errores.
    d) Ejecutar los tests en bucle infinito.

56. El concepto "Data-driven testing" en Newman permite usar archivos:
    a) .mp3
    b) .csv o .json con múltiples filas de datos.
    c) .exe
    d) .jpg

57. ¿Qué formato de archivo se usa para exportar colecciones de Postman para Newman?
    a) .zip
    b) .json
    c) .postman
    d) .txt

58. En Postman, la validación de esquemas JSON asegura que:
    a) La respuesta tenga la estructura y tipos de datos correctos.
    b) El servidor sea de tipo Linux.
    c) El usuario haya pagado la suscripción.
    d) La base de datos esté vacía.

59. ¿Cuál es una buena práctica recomendada para gestionar secretos en Postman/Newman?
    a) Subirlos a GitHub en el archivo de entorno.
    b) Escribirlos en el nombre de la colección.
    c) Usar variables locales o archivos de configuración externos no trackeados.
    d) No usar contraseñas.

60. ¿Cómo se ejecutan tests contra servicios orquestados en Docker usando Newman?
    a) No se puede, Newman no soporta Docker.
    b) Usando una imagen de Docker de Newman dentro de un `docker-compose.yml`.
    c) Ejecutando Newman en el ordenador del cliente.
    d) Enviando las colecciones por email.

- [Bloque 6: Validación de Interfaz con Playwright](#bloque-6-validación-de-interfaz-con-playwright)

### Bloque 6: Validación de Interfaz con Playwright

61. Una diferencia clave de Playwright frente a Cypress es que Playwright:
    a) Corre dentro del navegador.
    b) Ejecuta los tests fuera del proceso del navegador mediante protocolos nativos.
    c) Es mucho más lento.
    d) No soporta múltiples pestañas.

62. ¿Qué herramienta de Playwright permite grabar la ejecución para un análisis posterior (red, consola, snapshots)?
    a) Playwright Recorder.
    b) Trace Viewer.
    c) History Brush.
    d) Debugger Console.

63. Según las mejores prácticas de Playwright, ¿cuál es el mejor **selector** para elementos que no tienen roles de accesibilidad claros?
    a) ID (#user-form).
    b) Clases CSS (.btn-success).
    c) Atributos personalizados como `data-testid`.
    d) Etiquetas HTML (button).

64. El comando para escribir texto en un campo de entrada en Playwright es:
    a) `page.write()`
    b) `page.fill()`
    c) `page.input()`
    d) `page.typeText()`

65. Las aserciones en Playwright se denominan "Web-First" porque:
    a) Son las primeras que se inventaron.
    b) Reintentan automáticamente la comprobación hasta que se cumple o agota el timeout.
    c) Solo funcionan en Chrome.
    d) Son instantáneas y no esperan.

66. Para simular un clic en un botón con el rol "button" y el nombre "Enviar", usaríamos:
    a) `page.click('Enviar')`
    b) `page.getByRole('button', { name: 'Enviar' }).click()`
    c) `page.send('Enviar')`
    d) `page.push('Enviar')`

67. Playwright permite ejecutar tests en modo **headless**, lo que significa:
    a) Sin conexión a internet.
    b) Sin interfaz gráfica del navegador (ideal para CI/CD).
    c) Sin código fuente.
    d) Sin usar el ratón.

68. ¿Qué comando se usa en Playwright para interceptar y modificar el tráfico de red?
    a) `page.intercept()`
    b) `page.route()`
    c) `page.request()`
    d) `page.mock()`

69. ¿Cómo se ejecutan los tests de Playwright de forma nativa en múltiples navegadores (Chromium, Firefox, WebKit)?
    a) Configurando los proyectos en el archivo de configuración.
    b) Instalando tres versiones de Playwright.
    c) No es posible, solo soporta Chrome.
    d) Usando una extensión de Selenium.

70. ¿Qué ventaja ofrece Playwright respecto a la asincronía?
    a) Hay que poner `sleep(5000)` en cada línea.
    b) Gestiona esperas automáticas (Auto-waiting) antes de cada acción.
    c) No permite asincronía.
    d) El programador debe usar `Thread.sleep()`.

71. En un entorno Docker, ¿por qué es útil Playwright?
    a) Para que la web cargue más rápido.
    b) Para ejecutar pruebas E2E en un entorno aislado con todos los navegadores instalados.
    c) Para sustituir al servidor web.
    d) Para minar datos.

72. ¿Qué hace el comando `page.goto('/')`?
    a) Cierra la aplicación.
    b) Navega a la URL base o absoluta indicada.
    c) Visita al equipo de desarrollo.
    d) Borra las cookies.

73. ¿Qué arquitectura utiliza Playwright para comunicarse con los navegadores de forma eficiente?
    a) HTTP Polling.
    b) Client-Side Injection.
    c) CDPs (Chrome DevTools Protocol) y equivalentes sobre WebSockets.
    d) Copiado de archivos.

74. Para verificar que un elemento **no** es visible, usaríamos:
    a) `expect(locator).toBeHidden()`
    b) `expect(locator).not.toBeVisible()`
    c) Ambas son correctas.
    d) `assert.missing()`

75. ¿Qué característica permite a Playwright probar aplicaciones que requieren múltiples contextos (ej: chat entre dos usuarios)?
    a) Soporte nativo para múltiples BrowserContexts independientes.
    b) Uso de marcos iframes únicamente.
    c) No es posible probar dos usuarios a la vez.
    d) Reiniciando el navegador en cada paso.

### Bloque 7: Servicios de Red e Infraestructura

76. ¿Qué significa el acrónimo **DNS**?
    a) Digital Network System.
    b) Domain Name System.
    c) Data Node Server.
    d) Direct Network Service.

77. El registro DNS tipo **A** sirve para mapear un nombre a una dirección:
    a) IPv6.
    b) IPv4.
    c) MAC.
    d) De correo.

78. ¿Cuál es el propósito de un registro **CNAME**?
    a) Definir el servidor de correo.
    b) Crear un alias de otro nombre de dominio.
    c) Definir la IP del servidor.
    d) Almacenar texto para seguridad.

79. El servidor DNS que se configura paso a paso en las fuentes es:
    a) Nginx.
    b) BIND9.
    c) OpenLDAP.
    d) Apache.

80. ¿Qué comando se usa para realizar pruebas de resolución DNS?
    a) `ping`
    b) `dig`
    c) `curl`
    d) `ldapsearch`

81. En Docker, usar DNS internos en lugar de IPs hardcodeadas permite:
    a) Que el código sea más lento.
    b) Portabilidad entre entornos (dev, staging, prod) sin cambios de código.
    c) Que no necesitemos internet.
    d) No tiene ninguna ventaja.

82. El registro DNS para definir servidores de correo se denomina:
    a) MX.
    b) TXT.
    c) NS.
    d) PTR.

83. La "resolución inversa" (IP a nombre) utiliza registros de tipo:
    a) A.
    b) PTR.
    c) SRV.
    d) AAAA.

84. ¿Qué puerto utiliza habitualmente el servicio DNS?
    a) 80
    b) 53
    c) 389
    d) 443

85. En BIND9, el archivo donde se definen las zonas locales se llama:
    a) `named.conf.options`
    b) `named.conf.local`
    c) `named.conf.global`
    d) `zones.txt`

86. ¿Qué significa **LDAP**?
    a) Logical Data Access Protocol.
    b) Lightweight Directory Access Protocol.
    c) Local Directory Auth Protocol.
    d) Link Data Access Point.

87. LDAP se utiliza principalmente para:
    a) Almacenar videos.
    b) Autenticación centralizada y gestión de usuarios.
    c) Acelerar la base de datos SQL.
    d) Enviar correos masivos.

88. El nombre único completo de una entrada en LDAP se llama:
    a) UID.
    b) DN (Distinguished Name).
    c) RDN.
    d) OU.

89. En LDAP, `ou` significa:
    a) Organization Unit.
    b) Output Unit.
    c) Only User.
    d) Open Union.

90. ¿Qué herramienta web se menciona para gestionar visualmente OpenLDAP?
    a) phpMyAdmin.
    b) phpLDAPadmin.
    c) LDAP Visualizer.
    d) Portainer.

91. El comando CLI para buscar información en un servidor LDAP es:
    a) `grep`
    b) `ldapsearch`
    c) `find-user`
    d) `dig`

92. ¿Qué atributo LDAP suele almacenar el ID de usuario?
    a) `cn`
    b) `uid`
    c) `sn`
    d) `mail`

93. Un servidor de directorio permite el **SSO**, que significa:
    a) Single Sign-On (Inicio de sesión único).
    b) System Security Option.
    c) Simple Software Operation.
    d) Single Server Output.

94. En el laboratorio de Spring Boot, la seguridad se integra con LDAP usando:
    a) Spring Security.
    b) Hibernate.
    c) Thymeleaf.
    d) Maven.

95. ¿Qué puerto usa LDAP de forma estándar (sin cifrar)?
    a) 53
    b) 389
    c) 636
    d) 3306

### Bloque 8: Orquestación Final

96. ¿Cuál es el propósito de **Docker Compose** en la orquestación final?
    a) Compilar el código Java.
    b) Replicar localmente un entorno de producción con múltiples servicios.
    c) Sustituir a los programadores.
    d) Crear presentaciones para el cliente.

97. ¿Qué servicio actúa habitualmente como **Reverse Proxy** para distribuir el tráfico?
    a) PostgreSQL.
    b) Nginx.
    c) BIND9.
    d) Newman.

98. Los **healthchecks** en Docker Compose sirven para:
    a) Ver si el programador está sano.
    b) Gestionar dependencias asegurando que un servicio esté listo antes que otro.
    c) Calcular el espacio en disco.
    d) No sirven para nada.

99. En una arquitectura orquestada, el backend suele comunicarse con la base de datos usando:
    a) El nombre del servicio como hostname (ej: `db.example.local`).
    b) La IP de la casa del profesor.
    c) Un cable USB.
    d) Señales de humo.

100. El bloque final de orquestación integra:
    a) Solo el código del backend.
    b) Backend, frontend, base de datos e infraestructura (DNS, LDAP).
    c) Únicamente los tests de Cypress.
    d) El manual de usuario.

---

