# lobo-post2-u11

**Programación Web — Unidad 11: Buenas Prácticas y Patrones de Diseño**  
**Post-Contenido 2 — Logging con SLF4J/Logback y Documentación con Swagger/OpenAPI**  
Estudiante: Farid Lobo | Código: 1152338  
GitHub: github.com/faridl28/lobo-post2-u11

---

## Descripción

Extensión del proyecto de catálogo de productos (Post-Contenido 1) que integra:

- **SLF4J + Logback**: registro de eventos con niveles apropiados (INFO, WARN, DEBUG) y rotación diaria de archivos de log.
- **springdoc-openapi**: documentación automática de la API REST con Swagger UI interactiva.

---

## Ejecución

```bash
git clone https://github.com/faridl28/lobo-post2-u11.git
cd lobo-post2-u11
mvn spring-boot:run
```

La aplicación inicia en **http://localhost:8081**

---
## Captura de pantalla

<img width="1365" height="723" alt="image" src="https://github.com/user-attachments/assets/5a6c1f7a-ac04-4f54-be11-a6ecd9967307" />


## Swagger UI

Accesible en: **http://localhost:8081/swagger-ui.html**  
JSON de la API: **http://localhost:8081/api-docs**

Muestra los 4 endpoints documentados con sus respuestas posibles:

| Método | Endpoint | Respuestas |
|--------|----------|------------|
| POST | `/api/productos` | 201, 400 |
| GET | `/api/productos` | 200 |
| GET | `/api/productos/{id}` | 200, 404 |
| DELETE | `/api/productos/{id}` | 204, 404 |

---

## Archivos de Log

Los logs se generan en la carpeta `logs/` del proyecto:

- **Archivo activo**: `logs/catalogo.log`
- **Rotación diaria**: `logs/catalogo.yyyy-MM-dd.log`
- **Historial**: 30 días

Para ver el contenido del log en PowerShell:
```powershell
Get-Content logs\catalogo.log
```

---

## Niveles de Logging

| Nivel | Uso |
|-------|-----|
| INFO | Operaciones exitosas (crear, eliminar) |
| WARN | Recurso no encontrado |
| DEBUG | Búsquedas y listados |

---

## Estructura relevante

```
src/main/
├── java/com/empresa/catalogo/
│   ├── CatalogoApplication.java      ← @OpenAPIDefinition
│   ├── controller/
│   │   └── ProductoController.java   ← @Tag, @Operation, @ApiResponse
│   ├── service/
│   │   └── ProductoServiceImpl.java  ← SLF4J Logger
│   └── dto/
│       └── ProductoRequestDTO.java   ← @Schema
└── resources/
    ├── application.properties
    └── logback-spring.xml            ← Appenders CONSOLA y ARCHIVO
```
