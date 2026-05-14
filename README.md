# TeamFlow API

Production-ready SaaS backend built with FastAPI, PostgreSQL, SQLAlchemy, JWT authentication, workspace permissions, task management, invitations, refresh tokens, Docker, and CI/CD.

---

# Features

## Authentication

* JWT access tokens
* Refresh tokens
* Secure password hashing
* Login/logout system
* Protected routes

## Workspace System

* Multi-workspace architecture
* Workspace membership table
* Roles:

  * owner
  * admin
  * member
* Role-based permissions

## Projects & Tasks

* Project management
* Task management
* Task status
* Task priorities
* Task due dates
* Task comments
* Task assignment

## Invitations

* Email invitations
* Invitation tokens
* Invitation acceptance flow

## Pagination

Pagination on all list endpoints.

## DevOps

* Docker
* Docker Compose
* Alembic migrations
* GitHub Actions CI
* PostgreSQL
* Ruff linting
* Pytest

## Deployment Ready

Supports:

* Render
* Railway
* Fly.io
* AWS

---

# Tech Stack

* Python 3.11+
* FastAPI
* PostgreSQL
* SQLAlchemy 2.x
* Alembic
* Pydantic v2
* JWT
* Docker
* Pytest
* GitHub Actions

---

# Project Structure

```text
teamflow-api/
├── app/
├── alembic/
├── tests/
├── .github/
├── Dockerfile
├── docker-compose.yml
├── requirements.txt
├── .env
└── README.md
```

---

# Installation

## 1. Clone Repository

```bash
git clone https://github.com/Mboy75/teamflow-api2.git
cd teamflow-api
```

## 2. Create Virtual Environment

```bash
python3 -m venv .venv
source .venv/bin/activate
```

## 3. Install Dependencies

```bash
pip install --upgrade pip
pip install -r requirements.txt
```

---

# Environment Variables

Create `.env`

```env
ENV=dev
PROJECT_NAME=TeamFlow API
API_V1_STR=/api/v1

DATABASE_URL=postgresql+psycopg2://postgres:postgres@localhost:5432/teamflow

SECRET_KEY=change-this-secret-key
ACCESS_TOKEN_EXPIRE_MINUTES=30
REFRESH_TOKEN_EXPIRE_DAYS=30
ALGORITHM=HS256

BACKEND_CORS_ORIGINS=http://localhost:3000
FRONTEND_URL=http://localhost:3000
```

---

# Run PostgreSQL with Docker

```bash
docker compose up -d
```

---

# Database Migrations

Create migration:

```bash
alembic revision --autogenerate -m "initial schema"
```

Run migrations:

```bash
alembic upgrade head
```

---

# Run Development Server

```bash
uvicorn app.main:app --reload
```

Open:

```text
http://127.0.0.1:8000/docs
```

---

# Running Tests

```bash
pytest
```

Coverage:

```bash
pytest --cov=app
```

---

# API Endpoints

## Auth

```text
POST   /api/v1/auth/register
POST   /api/v1/auth/login
POST   /api/v1/auth/refresh
POST   /api/v1/auth/logout
GET    /api/v1/auth/me
```

## Users

```text
GET    /api/v1/users/me
PATCH  /api/v1/users/me
```

## Workspaces

```text
POST   /api/v1/workspaces
GET    /api/v1/workspaces
GET    /api/v1/workspaces/{workspace_id}
PATCH  /api/v1/workspaces/{workspace_id}
DELETE /api/v1/workspaces/{workspace_id}
```

## Projects

```text
POST   /api/v1/projects/workspaces/{workspace_id}/projects
GET    /api/v1/projects/workspaces/{workspace_id}/projects
GET    /api/v1/projects/{project_id}
PATCH  /api/v1/projects/{project_id}
DELETE /api/v1/projects/{project_id}
```

## Tasks

```text
POST   /api/v1/projects/{project_id}/tasks
GET    /api/v1/projects/{project_id}/tasks
GET    /api/v1/tasks/{task_id}
PATCH  /api/v1/tasks/{task_id}
DELETE /api/v1/tasks/{task_id}
```

## Comments

```text
POST   /api/v1/tasks/{task_id}/comments
GET    /api/v1/tasks/{task_id}/comments
PATCH  /api/v1/tasks/comments/{comment_id}
DELETE /api/v1/tasks/comments/{comment_id}
```

---

# Git Workflow

## Initialize Git

```bash
git init
```

## First Commit

```bash
git add .
git commit -m "initial backend setup"
```

## Connect GitHub Repository

```bash
git remote add origin https://github.com/Mboy75/teamflow-api2.git
```

## Push

```bash
git branch -M main
git push -u origin main
```

---

# Docker Commands

## Start Containers

```bash
docker compose up --build
```

## Stop Containers

```bash
docker compose down
```

---

# CI/CD

GitHub Actions automatically:

* installs dependencies
* runs linting
* runs tests
* validates migrations

Workflow file:

```text
.github/workflows/ci.yml
```

---

# Deployment

## Render

Start command:

```bash
alembic upgrade head && uvicorn app.main:app --host 0.0.0.0 --port $PORT
```

## Railway

Supports automatic deploy from GitHub.

## Fly.io

```bash
fly launch
fly deploy
```

## AWS

Recommended services:

* EC2
* RDS PostgreSQL
* Nginx
* Docker

---

# Security

* Password hashing with bcrypt
* JWT authentication
* Refresh token rotation
* Role-based permissions
* Protected workspace access
* SQLAlchemy ORM

---

# Future Improvements

* WebSockets
* Real-time notifications
* File uploads
* Activity logs
* Stripe billing
* Teams analytics
* Background jobs with Celery
* Redis caching

---

# License

MIT License

---

# Author

Built by Massi 
