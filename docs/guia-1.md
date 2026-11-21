# Guía 1: APIs con FastAPI

**Evidencias:** GA1-AA1-EV01, GA1-AA1-EV02, GA1-AA2-EV03 y GA1-AA3-EV04.
**Fecha del informe:** 6 de noviembre de 2026.
**Código de esta guía:** `git checkout guia-1`.

## Qué se aprendió

- Una API es un intermediario: el cliente hace una petición HTTP y el servidor responde con JSON y un código de estado.
- FastAPI valida los tipos solo (responde 422 si no coinciden) y genera la documentación en `/docs`.
- **Parámetro de ruta** (`/productos/{id}`) identifica un recurso. **Parámetro de consulta** (`/buscar?nombre=...`) filtra o busca.

## Reto: mini-API de catálogo

API de solo lectura con los productos en una lista en memoria.

| Método y ruta | Qué hace |
|---------------|----------|
| `GET /` | Mensaje de bienvenida |
| `GET /productos` | Lista completa |
| `GET /productos/{producto_id}` | Un producto; 404 si no existe |
| `GET /categorias` | Categorías sin repetir |
| `GET /buscar?nombre=...` | Productos cuyo nombre contiene el texto, sin importar mayúsculas |

## Ejemplos

```
GET /productos/2
→ {"id": 2, "nombre": "Mouse gamer", "precio": 85000, "categoria": "Perifericos"}

GET /productos/abc
→ 422, porque producto_id debe ser un entero

GET /categorias
→ ["Perifericos", "Pantallas"]

GET /buscar?nombre=mouse
→ [{"id": 2, "nombre": "Mouse gamer", "precio": 85000, "categoria": "Perifericos"}]
```

## Evidencias

Capturas de las pruebas con *Try it out* en [`capturas/guia-1`](../capturas/guia-1/).
