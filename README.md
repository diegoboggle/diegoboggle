<div align="center">

# ¡Hola! Soy Diego Villegas 👋

</div>

<div align="center">
  <p><strong>Estudiante de Ingeniería en Informática en Duoc UC | Desarrollador full-stack y de aplicaciones móviles</strong></p>
  <p>Basado en Quilpué, Chile</p>
</div>

---

### 💻 Tecnologías

Me enfoco en escribir código limpio y de alto rendimiento en toda la pila tecnológica: desde interfaces web modernas hasta *backends* robustos y aplicaciones móviles nativas.

* **Backend y sistemas:** Java, Spring Boot, Spring Security, Spring Cloud (Gateway, Config Server, Eureka), JWT, Resilience4j, C++, Python
* **Frontend y aplicaciones móviles:** React, TypeScript, Tailwind CSS, Kotlin, Jetpack Compose
* **Datos e infraestructura:** PostgreSQL, Docker, Maven, Railway, Render, JUnit 5, Mockito

---

### 🏆 Proyectos destacados

* **[Nance E-Commerce System]**
  Solución *full-stack* completa. El backend está desarrollado con **Java Spring Boot**, con autenticación JWT robusta y Spring Security. El frontend es una SPA altamente responsiva, construida con **React, TypeScript y Tailwind CSS**, con gestión de estado para los flujos de carrito y proceso de compra.

* **[PawSchedule]**
  Aplicación nativa para Android, desarrollada íntegramente con **Kotlin** y paradigmas modernos de interfaz mediante **Jetpack Compose**. Implementa *Clean Architecture* y consume servicios REST externos mediante Retrofit para una gestión fluida de las citas de mascotas.

* **[Sistema Distribuido de Gestión de Mascotas y Clínicas Veterinarias]**
  Arquitectura robusta de microservicios desarrollada con **Java 21, Spring Boot 3.2.5 y Spring Cloud 2023.0.1**. Implementa patrones de diseño como API Gateway, Config Server, Eureka Service Discovery y Circuit Breaker (Resilience4j) para garantizar la tolerancia a fallos. Todo el proyecto aplica estrictamente el patrón Controller-Service-Repository (CSR) y los principios de *Clean Code*. *(Detalle completo más abajo 👇)*

---

#### 🐾 Sistema Distribuido de Gestión de Mascotas y Clínicas Veterinarias

**Equipo de desarrollo (estudiantes)**
- Tomás Silva
- Diego Boggle

**Microservicios implementados**

El ecosistema cuenta con un total de 14 microservicios desacoplados que garantizan la separación de responsabilidades:

| Servicio | Puerto local | Descripción |
|---|---|---|
| ms-config-server | 8888 | Servidor centralizado de configuración nativa. |
| ms-eureka | 8761 | Servicio de registro y descubrimiento de servicios (Netflix Eureka). |
| apigateway | 8080 | Puerta de entrada única (Spring Cloud Gateway) con filtro global JWT. |
| ms-auth | Dinámico | Generación de JWT y cifrado de contraseñas con BCrypt. |
| ms-usuario | Dinámico | Gestión de usuarios (dueños de mascotas). |
| ms-mascotas | Dinámico | Gestión y registro de mascotas. |
| ms-veterinaria | Dinámico | Gestión de veterinarios. |
| ms-citas | Dinámico | Agenda y programación de citas médicas. |
| ms-historial | Dinámico | Gestión de las historias clínicas de las mascotas. |
| ms-vacunas | Dinámico | Registro de vacunación. |
| ms-notificaciones | Dinámico | Envío de notificaciones. |
| ms-recordatorios | Dinámico | Generación de recordatorios de citas y vacunas. |
| ms-reportes | Dinámico | Generación de reportes administrativos. |
| ms-facturacion | Dinámico | Generación de cobros (si aplica). |

> **Nota:** todos los microservicios de dominio (usuarios, mascotas, etc.) se inician en puertos dinámicos (`server.port=0`) y se comunican a través del Gateway.

**Rutas principales del API Gateway**

El API Gateway es la única entrada expuesta al exterior (puerto 8080).

| Funcionalidad | Ruta en el Gateway |
|---|---|
| Inicio de sesión y JWT | `POST http://localhost:8080/api/v1/auth/login` |
| Usuarios | `GET/POST http://localhost:8080/api/v1/usuarios` |
| Mascotas | `GET/POST http://localhost:8080/api/v1/mascotas` |

**Documentación Swagger/OpenAPI**

La documentación interactiva de la API está integrada nativamente en los microservicios. Puedes acceder a ella localmente (asegúrate de que el microservicio esté en ejecución en el puerto correspondiente, o hazlo a través del Gateway):

- Usuarios y autenticación (Swagger UI): `http://localhost:<PUERTO_DEL_SERVICIO>/swagger-ui.html`

Los controladores y los DTO están completamente documentados con descripciones, ejemplos de solicitud y respuesta, y códigos de estado HTTP.

**Instrucciones de ejecución**

*Entorno local (desarrollo)*

Para levantar el ecosistema localmente, asegúrate de tener JDK 21 y PostgreSQL (con las bases de datos db_usuarios, db_mascotas, etc., creadas según corresponda).

1. Levantar el Config Server:
   ```bash
   cd ms-config-server
   ./mvnw spring-boot:run
   ```
2. Levantar el Eureka Server:
   ```bash
   cd ../ms-eureka
   ./mvnw spring-boot:run
   ```
3. Levantar los microservicios de dominio (por ejemplo, ms-usuario, ms-auth, ms-mascotas):
   ```bash
   cd ../ms-usuario
   ./mvnw spring-boot:run
   ```
4. Levantar el API Gateway (debe ser el último):
   ```bash
   cd ../apigateway
   ./mvnw spring-boot:run
   ```

*Despliegue remoto (Railway/Render/Docker)*

Para desplegar este ecosistema en la nube (por ejemplo, en Railway):

1. Levantar un servicio de base de datos PostgreSQL en la plataforma de nube elegida y obtener la URL JDBC (`postgresql://user:pass@host:port/dbname`).
2. Configurar la variable de entorno `SPRING_CONFIG_IMPORT=optional:configserver:<URL_DEL_CONFIG_SERVER_PUBLICO>` en cada microservicio desplegado.
3. Desplegar los servicios conectando cada repositorio a Railway o Render, mediante el Dockerfile proporcionado en la raíz de cada microservicio, o bien el Buildpack de Maven con Java 21.

**Pruebas unitarias**

El proyecto cuenta con una cobertura de pruebas robusta que valida las reglas de negocio, el manejo de excepciones y las validaciones. Las pruebas están implementadas con JUnit 5 y Mockito.

Para ejecutar las pruebas de un microservicio:
```bash
cd ms-usuario
./mvnw test
```

---

### 🚀 Actualmente explorando

* Escalado de arquitecturas *backend* y patrones de microservicios.
* Hilos virtuales de Java y programación concurrente.
* Programación de hardware nativo con C++ y sistemas embebidos.

---

### 📫 Conectemos

Abierto a conversar sobre arquitectura limpia, *frameworks* modernos y proyectos de código abierto.

- 📧 Correo electrónico: [diego.villegas.alfaro@gmail.com](mailto:diego.villegas.alfaro@gmail.com)
