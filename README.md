\# Frontend Despacho Dashboard



Aplicación web desarrollada en React + Vite + Tailwind CSS para la gestión de despachos y ventas de ITPCARGO™.



\## Tecnologías

\- React + Vite

\- Tailwind CSS

\- Docker (multi-stage build)

\- Nginx (servidor de producción)

\- GitHub Actions (CI/CD)



\## Requisitos previos

\- Docker Desktop instalado

\- Node.js 18 o superior



\## Cómo ejecutar localmente



\### Con Docker Compose

```bash

docker compose up -d

```

Accede en: http://localhost



\### Sin Docker

```bash

npm install

npm run dev

```

Accede en: http://localhost:5173



\## Variables de entorno

| Variable | Descripción |

|----------|-------------|

| No requiere variables de entorno para el frontend estático |



\## Estructura del proyecto

front\_despacho/

├── Dockerfile          # Multi-stage build (Node builder + Nginx)

├── docker-compose.yml  # Stack de servicios

├── nginx.conf          # Configuración del servidor web

├── .dockerignore       # Archivos excluidos del build

├── .github/

│   └── workflows/

│       └── cicd-frontend.yml  # Pipeline CI/CD

├── src/                # Código fuente React

└── public/             # Archivos estáticos



\## Pipeline CI/CD

El pipeline se activa automáticamente con cada push a la rama `deploy`:

1\. Construye la imagen Docker

2\. Publica en Docker Hub

3\. Despliega en EC2-Web via SSH



\## Infraestructura AWS

\- \*\*EC2-Web\*\*: Instancia pública (subred pública) — accesible desde Internet

\- \*\*Puerto expuesto\*\*: 80 (HTTP)

\- \*\*IP pública\*\*: 98.90.149.0



\## Persistencia de datos

El frontend es estático, no requiere volúmenes de persistencia.



\## Principios DevOps aplicados

\- \*\*Contenedorización\*\*: Dockerfile multi-stage con usuario no-root

\- \*\*CI/CD\*\*: Pipeline automatizado con GitHub Actions

\- \*\*Mínimo privilegio\*\*: Usuario `appuser` no-root dentro del contenedor

\- \*\*Optimización\*\*: Imagen final liviana con Nginx Alpine

