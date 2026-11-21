# Guía 2: CRUD y organización de la API

**Evidencias:** GA2-AA1-EV01, GA2-AA1-EV02, GA2-AA2-EV03 y GA2-AA3-EV04.
**Fecha del informe:** 13 de noviembre de 2026.
Esta guía se entregó en el repositorio [`tienda-api`](https://github.com/robledocordoba123-cmyk/tienda-api); aquí queda su resultado integrado al proyecto.

## Qué se aprendió

- **CRUD** y su método HTTP: Crear → POST (201), Leer → GET (200), Actualizar → PUT (200), Eliminar → DELETE (200).
- **Pydantic:** una clase que hereda de `BaseModel` define los campos del cuerpo de la petición; si falta un campo o el tipo no coincide, FastAPI responde 422.
- **APIRouter:** cada recurso tiene su archivo; `main.py` solo los conecta con `include_router`. `prefix` evita repetir el inicio de la ruta y `tags` agrupa los endpoints en `/docs`.

## Estructura

```
main.py
routers/
├── __init__.py       # vacío: convierte routers en paquete
├── productos.py
└── categorias.py
```

## Endpoints (CRUD de productos y categorías)

| Operación | Productos | Categorías |
|-----------|-----------|------------|
| Listar | `GET /productos` | `GET /categorias` |
| Obtener uno | `GET /productos/{id}` | `GET /categorias/{id}` |
| Crear | `POST /productos` (201) | `POST /categorias` (201) |
| Actualizar | `PUT /productos/{id}` | `PUT /categorias/{id}` |
| Eliminar | `DELETE /productos/{id}` | `DELETE /categorias/{id}` |

El id lo asigna el servidor (el más alto + 1). Si el recurso no existe responde 404.

## Pruebas de las categorías

| Operación | Dato enviado | Código |
|-----------|--------------|--------|
| GET /categorias | Ninguno | 200 |
| GET /categorias/2 | id 2 | 200 |
| POST /categorias | nombre: Almacenamiento | 201 |
| PUT /categorias/4 | nombre: Discos y memorias | 200 |
| DELETE /categorias/4 | id 4 | 200 |
| GET /categorias/99 | id que no existe | 404 |
| POST /categorias | `titulo` en lugar de `nombre` | 422 |

## Evidencias

Capturas en [`capturas/guia-2`](../capturas/guia-2/).
