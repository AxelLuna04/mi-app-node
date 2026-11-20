# 🎓 API de Estudiantes con CI/CD

API REST sencilla para administrar estudiantes, hecha como práctica de **integración y despliegue continuo (CI/CD)** con Docker, GitHub Actions y Jenkins.

## ✨ Qué hace

CRUD de estudiantes guardados en MongoDB. Cada estudiante tiene `matricula`, `nombre`, `carrera` y `edad`.

| Método | Ruta | Descripción |
|---|---|---|
| `GET` | `/api/estudiantes` | Lista todos los estudiantes |
| `GET` | `/api/estudiantes/:matricula` | Obtiene un estudiante |
| `POST` | `/api/estudiantes` | Registra un estudiante |
| `PUT` | `/api/estudiantes/:matricula` | Actualiza un estudiante |
| `PATCH` | `/api/estudiantes/:matricula` | Actualiza solo la edad |
| `DELETE` | `/api/estudiantes/:matricula` | Elimina un estudiante |

## 🔄 Pipeline de CI/CD

- **GitHub Actions** (`.github/workflows/ci.yml`): en cada push a `main` instala dependencias, corre las pruebas y, si pasan, construye la imagen de Docker y la publica en Docker Hub.
- **Jenkins** (`Jenkinsfile`): clona el repositorio, construye la imagen y despliega la API junto con MongoDB usando Docker Compose.

## 🧰 Tecnologías

Node.js, Express, MongoDB con Mongoose, Docker, Docker Compose, GitHub Actions y Jenkins.

## ⚙️ Cómo correrlo

Con Docker:

```bash
docker-compose up -d --build
```

La API queda en `http://localhost:3001/api/estudiantes`.

Sin Docker (necesitas MongoDB corriendo):

```bash
npm install
MONGODB_URI=mongodb://localhost:27017/estudiantesdb node app.js
```

La API queda en `http://localhost:3000/api/estudiantes`.
