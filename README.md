# Sistema de Gestión de Reservas - Gimnasio UdeM

EPlataforma integral para la reserva de cupos en el gimnasio de la Universidad de Medellín, diseñada como una Aplicación Web Progresiva para optimizar el aforo y eliminar las esperas manuales.

## Arquitectura del Sistema
El proyecto utiliza una arquitectura desacoplada y containerizada:
* [Backend](./backend): ADjango 4.2 + Django Rest Framework.
* [Database](./database): Diseño NoSQL en MongoDB.
* [Frontend](./frontend): IReact 18 + Vite (PWA).

## Requisitos Previos
* [Docker](https://www.docker.com/) y Docker Compose instalados.
* Node.js 18+ (para desarrollo local sin contenedores).
* Python 3.11+ (para desarrollo local sin contenedores).

## Inicio Rápido con Docker
1. Clona el repositorio.
2. Crea los archivos `.env` en `/backend` y `/frontend`.
3. Ejecuta el comando:
```bash
docker-compose up --build