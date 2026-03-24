Gym UdeM - Backend API (Django + MongoDB)
Este es el núcleo lógico del Sistema de Gestión de Reservas del Gimnasio de la Universidad de Medellín. Provee una API REST para la autenticación de usuarios institucionales y el control de aforo en tiempo real utilizando una arquitectura desacoplada y containerizada.

Tecnologías y Versiones
Lenguaje: Python 3.11-slim.
Framework Web: Django 4.2.7.
API Toolkit: Django Rest Framework 3.14.0.
Base de Datos: MongoDB (vía PyMongo 4.6.0).
Contenedores: Docker & Docker Compose.

🛠️ Instalación y Configuración Local
1. Clonar el Repositorio
Bash
git clone https://github.com/tu-usuario/gym-reserva-project.git
cd gym-reserva-project/backend

2. Configurar Variables de Entorno
Crea un archivo .env en la raíz de la carpeta backend/ con los siguientes datos:
Fragmento de código
SECRET_KEY=tu_clave_secreta_de_django
DEBUG=True
MONGO_URI=mongodb://localhost:27017
MONGO_DB=gym_udem

3. Ejecución con Docker (Recomendado)
El proyecto está configurado para arrancar automáticamente con todas sus dependencias:

Bash
# Desde la raíz del proyecto
docker-compose up --build
Este comando instalará las dependencias de Python, ejecutará las migraciones iniciales y encenderá el servidor en el puerto 8000.

🔌 Documentación de la API (Endpoints)
La API está organizada bajo el prefijo /api/.

## 🔌 Documentación de la API (Endpoints)

| Método | Endpoint | Descripción | Requisito Relacionado |
| :--- | :--- | :--- | :--- |
| **POST** | `/api/auth/register/` | Registro de usuarios con correo institucional. | [cite_start]RF01 [cite: 48] |
| **POST** | `/api/auth/login/` | Inicio de sesión y validación de credenciales. | [cite_start]RF01 [cite: 48] |
| **GET** | `/api/slots/` | Consulta de bloques horarios (pares) y cupos. | [cite_start]RF03 [cite: 51] |
| **POST** | `/api/reservations/` | Crea una reserva y descuenta cupo en MongoDB. | [cite_start]RF04 [cite: 52] |
| **GET** | `/api/reservations/` | Lista las reservas activas de un estudiante. | [cite_start]RF02 [cite: 49] |
| **DELETE** | `/api/reservations/<id>/` | Cancela reserva y libera cupo inmediatamente. | [cite_start]RF06 [cite: 54] |

Seguridad y Reglas de Negocio
Hash de Contraseñas: Se utiliza PBKDF2 con SHA-256 y salt de 32 bytes para el almacenamiento seguro de credenciales.

Validación de Dominio: Restricción estricta a correos institucionales de la Universidad de Medellín.

Atomicidad: Las actualizaciones de cupos se realizan mediante operadores $inc para evitar inconsistencias de aforo en accesos concurrentes.

🗄️ Diseño de Base de Datos (MongoDB)
Se mantienen las especificaciones originales del diseño de documentos:

Colecciones Principales

users: Estudiantes, entrenadores y administradores.

schedules: Horarios disponibles de lunes a viernes (06:00 a 16:00).

reservations: Vinculación usuario-horario con estado de asistencia.

[!TIP]
Para probar la API: Puedes usar herramientas como Postman o Insomnia apuntando a http://localhost:8000/api/slots/ una vez que el contenedor de Docker esté corriendo.