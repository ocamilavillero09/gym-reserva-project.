Gym UdeM - Frontend (PWA con React + Vite)
Esta es la interfaz de usuario del Sistema de Reservas del Gimnasio UdeM. Está desarrollada como una Aplicación Web Progresiva (PWA), permitiendo a los estudiantes una experiencia nativa desde sus dispositivos móviles para gestionar sus entrenamientos.

Tecnologías y Versiones
Framework: React 18 (Hooks y Componentes Funcionales).
Herramienta de Construcción: Vite (Optimizado para desarrollo rápido).
Lenguaje: JavaScript (JSX).
Entorno de Ejecución: Node.js 18-alpine (vía Docker).
Estado Global: React useState y useEffect para sincronización con la API.

Configuración y Ejecución
1. Variables de Entorno
Crea un archivo .env en la raíz de la carpeta frontend/ para conectar con tu Backend:
Fragmento de código
VITE_API_URL=http://localhost:8000/api

2. Ejecución Local (Sin Docker)
Bash
npm install
npm run dev
Importante: La aplicación corre por defecto en el puerto 5173. Si intentas acceder por el puerto 3000, verás un error de conexión.
Accede mediante: http://localhost:5173.

3. Ejecución con Docker
Bash
docker build -t gym-frontend .
docker run -p 5173:5173 gym-frontend

Estructura de la Aplicación (src/)
Carpeta / Archivo	Función
components/	Contiene los elementos visuales (Login, Dashboard, Navbar, MyReservations).
services/api.js	Capa de servicio que gestiona todas las peticiones fetch al backend de Django.
App.jsx	Orquestador principal de la lógica, manejo de rutas internas y sistema de notificaciones (Toast).
index.jsx	Punto de entrada que renderiza la aplicación en el DOM.

Características Destacadas
Diseño Mobile-First: Interfaz limpia y minimalista utilizando el color institucional (#CC0000).

Sistema de Notificaciones: Toasts personalizados para confirmar acciones (reservas, cancelaciones) o mostrar errores de validación.

Actualización Atómica: Al reservar o cancelar, la interfaz refresca los datos globalmente sin recargar la página, manteniendo la consistencia del aforo.

Validación Institucional: El formulario de acceso restringe el ingreso solo a dominios @udem.edu.co o @soyudemedellin.edu.co.

Notas sobre la PWA
Para instalar la aplicación en un dispositivo móvil:
Asegúrate de que el backend y frontend estén corriendo en la misma red.
Accede a la IP de tu máquina desde el celular.
Selecciona "Añadir a la pantalla de inicio" en el menú del navegador.