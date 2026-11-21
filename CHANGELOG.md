# Historial de cambios

Cada guía agrega funciones al mismo proyecto. Lo más reciente va primero.

## Guía 3: seguridad (GA3-AA3-EV04)

- Nuevo `seguridad.py`: hashing con bcrypt, creación y validación de tokens JWT (30 min), dependencias `obtener_usuario_actual` (401) y `requerir_admin` (403).
- Nuevo `routers/auth.py`: `POST /auth/login`, `POST /auth/registro` (rol `cliente`) y `GET /auth/yo`.
- `routers/productos.py` y `routers/categorias.py`: POST y PUT exigen token; DELETE exige rol admin; los GET siguen públicos.
- `main.py` conecta el router `auth`.
- Nuevas dependencias: `PyJWT`, `bcrypt`, `python-multipart`.
- README y carpeta `docs/` actualizados; capturas de seguridad en `capturas/guia-3/`.

## Guía 2: CRUD y organización (GA2-AA3-EV04)

- El proyecto pasa de un solo `main.py` a routers: `routers/productos.py` y `routers/categorias.py`.
- CRUD completo (POST, PUT, DELETE) con modelos Pydantic (`ProductoEntrada`, `CategoriaEntrada`); el id lo asigna el servidor.
- Los endpoints de lectura de la Guía 1 `/buscar` y `/categorias` (lista de nombres) se reemplazan por el CRUD de categorías.
- Esta guía se entregó en el repositorio `tienda-api`; su código quedó integrado aquí.

## Guía 1: mini-API de catálogo (GA1-AA3-EV04)

- API de solo lectura en un único `main.py`: `/`, `/productos`, `/productos/{id}`, `/categorias` y `/buscar`.
- Productos en una lista en memoria. Disponible con `git checkout guia-1`.
