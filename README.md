📚 Biblioteca Personal – API RESTful con FastAPI

Este proyecto es un sistema completo de gestión de libros, usuarios y reseñas, construido con FastAPI e implementando principios REST, autenticación con tokens Bearer, control de rol administrador y un frontend integrado en HTML/CSS/JS servido desde la misma API.

Incluye características como:

Gestión completa de libros (CRUD).

Sistema de usuarios con registro e inicio de sesión.

Autenticación mediante tokens Bearer.

Reseñas por libro.

Biblioteca personal para cada usuario.

Panel de administración para gestión de catálogo.

Observers (patrón Observer) que registran eventos del sistema.

Interfaz visual integrada.

🚀 Tecnologías utilizadas

Python 3.10+

FastAPI

Pydantic

Uvicorn

HTML + CSS + JavaScript

Patrón Facade

Patrón Observer

Sistema de autenticación con HTTPBearer

📦 Instalación
1. Clona el repositorio
git clone https://github.com/tu-usuario/tu-repo.git
cd tu-repo

2. Crea un entorno virtual
python -m venv venv
source venv/bin/activate   # Linux / macOS
venv\Scripts\activate      # Windows

3. Instala dependencias
pip install fastapi uvicorn


(Si agregas un requirements.txt, cámbialo por pip install -r requirements.txt)

▶️ Ejecución del servidor
uvicorn main:app --reload


Luego visita:

http://localhost:8000


La interfaz web ya viene incluida ⭐

También puedes acceder a la documentación automática:

Swagger UI:
http://localhost:8000/docs

Redoc:
http://localhost:8000/redoc

👤 Usuario administrador por defecto

El sistema crea un admin automáticamente:

Email	Contraseña	Rol
admin@biblioteca.com
	admin123	admin

Este usuario puede:

Crear libros

Editar libros

Eliminar libros

Administrar el catálogo

🔐 Autenticación

La API usa HTTP Bearer Token.

Inicia sesión:

POST /api/v1/auth/login


Devuelve un token:

{
  "token": "abc123...",
  "rol": "admin"
}


Usa el token en tus peticiones:

Authorization: Bearer <token>

📘 Endpoints Principales
Libros
Método	Endpoint	Descripción
GET	/api/v1/libros	Listar libros
POST	/api/v1/libros	Crear libro (solo admin)
GET	/api/v1/libros/{id}	Obtener libro
PUT	/api/v1/libros/{id}	Actualizar libro (admin)
DELETE	/api/v1/libros/{id}	Eliminar libro (admin)
Reseñas
Método	Endpoint	Descripción
GET	/api/v1/libros/{id}/reseñas	Listar reseñas
POST	/api/v1/libros/{id}/reseñas	Crear reseña
Usuarios
Método	Endpoint	Descripción
POST	/api/v1/usuarios	Registrar usuario
POST	/api/v1/auth/login	Iniciar sesión
GET	/api/v1/auth/me	Información del usuario autenticado
Biblioteca personal
Método	Endpoint
GET	/api/v1/usuarios/me/biblioteca
POST	/api/v1/usuarios/me/biblioteca/{id}
DELETE	/api/v1/usuarios/me/biblioteca/{id}
🏗️ Arquitectura del proyecto

Este sistema aplica varios patrones:

✔️ Facade

Toda la lógica de gestión de libros, usuarios y reseñas está centralizada en:

LibraryFacade

✔️ Observer

Cada acción genera eventos como:

LIBRO_CREADO

LIBRO_ELIMINADO

RESEÑA_AGREGADA

USUARIO_REGISTRADO

Observers incluidos:

LogObserver

EmailObserver

Estos imprimen notificaciones simuladas.

🎨 Interfaz gráfica incluida

En la ruta raíz / se sirve una UI en HTML/CSS/JS que permite:

Iniciar sesión

Registrar usuarios

Ver catálogo global

Agregar libros a la biblioteca personal

Ver detalles y reseñas

Añadir reseñas

Panel administrativo (si eres admin)

No necesitas frontend externo. Todo está integrado.

📁 Estructura simple del proyecto
📦 proyecto
 └── main.py


Todo está contenido en un solo archivo para facilidad de uso y despliegue.

🚀 Despliegue en Render (opcional)

Crea un archivo start en el panel:

uvicorn main:app --host 0.0.0.0 --port $PORT


Selecciona:

Runtime: Python

Version: Python 3.10+

Build Command:

pip install -r requirements.txt


Start Command:

uvicorn main:app --host 0.0.0.0 --port $PORT

❤️ Autor

Proyecto desarrollado por Dayana Ovalle (Tú)
API RESTful + interfaz visual creada con FastAPI y JavaScript.
