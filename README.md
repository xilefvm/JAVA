# ☕ JAVA

### Proyectos backend con Java y el ecosistema Spring

Colección de proyectos backend construidos con **Java** y **Spring Boot**. Cada proyecto vive en su propia carpeta, con dependencias, configuración y documentación independientes.

---

## 📌 Índice

- [Proyectos](#-proyectos)
- [Stack de referencia](#-stack-de-referencia)
- [Arquitectura](#-arquitectura)
- [Estructura del repositorio](#-estructura-del-repositorio)
- [Requisitos](#-requisitos)
- [Inicio rápido](#-inicio-rápido)
- [Configuración](#-configuración)
- [Calidad y pruebas](#-calidad-y-pruebas)
- [Convenciones](#-convenciones)
- [Contribuir](#-contribuir)
- [Licencia](#-licencia)

---

## 🧭 Proyectos

| Proyecto | Descripción | Estado |
|----------|-------------|--------|
| *Por publicar* | Se añadirán aquí con su descripción y enlace | 🚧 En preparación |

> Cada proyecto nuevo añade una fila a esta tabla con su nombre, una línea de descripción y su estado (🚧 en preparación, ✅ estable, 🗄️ archivado).

---

## 🧰 Stack de referencia

| Área | Tecnologías |
|------|-------------|
| 🧠 **Lenguaje** | Java 21 o superior |
| ⚙️ **Framework** | Spring Boot · Spring Web MVC · Spring Validation |
| 🗃️ **Persistencia** | Spring Data JPA · Hibernate · Flyway |
| 🔐 **Seguridad** | Spring Security · JWT |
| 🗄️ **Bases de datos** | PostgreSQL · Oracle · H2 (solo pruebas) |
| 📡 **API** | REST · OpenAPI / Swagger UI |
| 🧪 **Testing** | JUnit 5 · Mockito · Testcontainers |
| 🐳 **Infraestructura** | Docker · Docker Compose |
| 🔧 **Build** | Maven · Gradle |

Cada proyecto declara sus versiones exactas en su `pom.xml`. Esta tabla es el stack de referencia del repositorio, no una lista de obligatorios.

---

## 🏗️ Arquitectura

Los proyectos siguen una arquitectura por capas:

```text
Cliente HTTP
    │
    ▼
Controller   →  recibe y valida la petición, devuelve la respuesta
    │
    ▼
Service      →  lógica de negocio
    │
    ▼
Repository   →  acceso a datos (Spring Data JPA / Hibernate)
    │
    ▼
Base de datos
```

Principios comunes:

- 🧩 Los controllers no contienen lógica de negocio.
- 🔄 Los DTO separan la API del modelo de dominio y de las entidades JPA.
- ⚠️ Los errores se devuelven con un formato único gestionado por un manejador global.
- 🛠️ La configuración sensible se externaliza en variables de entorno.

---

## 🗂️ Estructura del repositorio

```text
JAVA/
├── <proyecto>/          # Cada proyecto es independiente
│   ├── src/
│   ├── pom.xml
│   ├── Dockerfile       # Si aplica
│   └── README.md        # Documentación propia del proyecto
├── README.md            # Este archivo
└── LICENSE              # MIT
```

---

## ✅ Requisitos

- ☕ **JDK 17** o superior
- 📦 **Maven o Gradle**
- 🐳 **Docker** y **Docker Compose**, para la base de datos y los contenedores
- 🔑 Un cliente REST para probar la API (Postman, Bruno o `curl`)

---

## ⚡ Inicio rápido

```bash
# 1. Clonar el repositorio
git clone https://github.com/xilefvm/JAVA.git
cd JAVA

# 2. Entrar en el proyecto que quieras ejecutar
cd <nombre-del-proyecto>

# 3. Levantar la base de datos, si el proyecto la necesita
docker compose up -d

# 4. Ejecutar la aplicación
mvn spring-boot:run
```

Cuando la aplicación arranca, la documentación de la API suele estar en `http://localhost:8080/swagger-ui.html`. Cada proyecto indica en su README la URL y el puerto exactos.

---

## ⚙️ Configuración

Cada proyecto usa variables de entorno para los datos sensibles. Nunca se suben credenciales al repositorio.

| Variable | Descripción | Ejemplo |
|----------|-------------|---------|
| `DB_URL` | URL de la base de datos | `jdbc:postgresql://localhost:5432/app` |
| `DB_USER` | Usuario de la base de datos | `app` |
| `DB_PASSWORD` | Contraseña de la base de datos | `********` |
| `SERVER_PORT` | Puerto de la aplicación | `8080` |

Copia `.env.example` a `.env` en cada proyecto y rellena los valores. El archivo `.env` está excluido en `.gitignore`.

---

## 🧪 Calidad y pruebas

```bash
mvn test          # Tests unitarios
mvn verify        # Tests unitarios e integración
```

Los tests de integración usan Testcontainers, así que requieren Docker en ejecución.

Antes de abrir un Pull Request, comprueba que:

- ✅ `mvn verify` termina sin errores.
- 📏 El código sigue el estilo del proyecto.
- 📝 Los cambios en la API están reflejados en la documentación.

---

## 📐 Convenciones

- **Commits**: formato [Conventional Commits](https://www.conventionalcommits.org/es/v1.0.0/), por ejemplo `feat: añade endpoint de usuarios`.
- **Ramas**: `feature/<descripción>`, `fix/<descripción>`, `docs/<descripción>`.
- **Código**: nombres en inglés, comentarios en español cuando aporten contexto.
- **Versiones**: [SemVer](https://semver.org/lang/es/) por proyecto.

---

## 🤝 Contribuir

1. 🍴 Haz un fork del repositorio.
2. 🌿 Crea una rama desde `main`: `git checkout -b feature/mi-cambio`.
3. ✅ Ejecuta `mvn verify`.
4. 💾 Haz commit siguiendo las convenciones.
5. 🚀 Abre un Pull Request con una descripción clara del cambio y cómo probarlo.

---

## 📄 Licencia

Distribuido bajo la **Licencia MIT**. Consulta el archivo [LICENSE](./LICENSE) para más detalles.

---

<sub>Mantenido por **Fèlix** · Hecho con ☕ y Spring Boot.</sub>
