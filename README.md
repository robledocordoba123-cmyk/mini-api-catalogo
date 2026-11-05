# Mini-API de Catálogo

API de solo lectura para el catálogo de una tienda virtual, hecha con **FastAPI** como reto de la Guía 1 (evidencia GA1-AA3-EV04).
Por ahora los productos se guardan en una lista en memoria dentro de `main.py`; todavía no usa base de datos.

**Aprendices:** Manuela Córdoba Robledo y Davier Andrés Quinto Bejarano. Ficha 3229209, ADSO (SENA)

## Requisitos

- Python 3.10 o superior
- pip

## Instalación

1. Clonar el repositorio y entrar a la carpeta:

   ```bash
   git clone https://github.com/robledocordoba123-cmyk/mini-api-catalogo.git
   cd mini-api-catalogo
   ```

2. Crear y activar el entorno virtual:

   ```bash
   python -m venv venv

   # Windows
   venv\Scripts\activate

   # Linux / macOS
   source venv/bin/activate
   ```

3. Instalar las dependencias:

   ```bash
   pip install -r requirements.txt
   ```

## Ejecución

```bash
uvicorn main:app --reload
```

La API queda en `http://127.0.0.1:8000`.

- Documentación interactiva (Swagger UI): `http://127.0.0.1:8000/docs`
- Documentación de lectura (ReDoc): `http://127.0.0.1:8000/redoc`

## Endpoints

| Método | Ruta | Qué hace |
|--------|------|----------|
| GET | `/` | Mensaje de bienvenida |
| GET | `/productos` | Lista completa de productos |
| GET | `/productos/{producto_id}` | Devuelve el producto con ese id. Si no existe responde **404** |
| GET | `/categorias` | Lista de categorías distintas (sin repetir) |
| GET | `/buscar?nombre=texto` | Productos cuyo nombre contiene el texto (no distingue mayúsculas) |

### Ejemplos

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

Las capturas de cada endpoint probado con **Try it out** en `/docs` están en la carpeta [`capturas/`](capturas/).
