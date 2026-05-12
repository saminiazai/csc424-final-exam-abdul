# CSC424 Final Exam — Containerized Full Stack Application

## Overview

This project demonstrates a containerized full stack web application using:

- React + Vite frontend
- ASP.NET backend API
- Nginx reverse proxy
- Docker Compose orchestration
- Docker multi-stage builds

The application was containerized as part of a DevOps modernization workflow for automated deployments and scalable infrastructure.

---

# DevOps Setup

## Run the application locally

From the project root directory run:

```bash
docker compose up --build -d
```

---

## Application URLs

Frontend:
```text
http://localhost
```

Backend API:
```text
http://localhost/api/ping
```

---

## Services

### Frontend
- Built using React + Vite
- Served through an Nginx container
- Multi-stage Docker build used to reduce final image size

### Backend
- ASP.NET minimal API
- Containerized using multi-stage Docker builds
- Exposes API endpoint:
  - `/api/ping`

### Nginx Reverse Proxy
- Routes frontend traffic from `/`
- Routes backend API traffic from `/api/`
- Only service exposed publicly on port 80

---

# Docker Compose

The stack uses Docker Compose to:
- build containers
- create shared networking
- start all services together

Services included:
- frontend
- backend
- nginx

---

# CI/CD Pipeline

The CI/CD pipeline is designed to:
- trigger automatically on push to `main`
- build Docker images
- push images to a container registry
- deploy updated containers to a QA server using SSH

Secrets such as:
- Docker Hub credentials
- SSH private keys

are stored securely using GitHub Secrets.

---

# Local Verification

Successful verification includes:

Frontend:
```text
http://localhost
```

Backend:
```text
http://localhost/api/ping
```

Expected API response:

```json
{"status":"ok","message":"pong"}
```