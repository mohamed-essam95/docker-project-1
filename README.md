## Overview

This project is a simple **Docker‑based full‑stack application** consisting of:

- **frontend**: static site served by Nginx on port `80`
- **backend**: Node.js REST API on port `3001`
- **db**: PostgreSQL 15 database

Everything is orchestrated via `docker-compose.yml`.

## Prerequisites

- **Docker** (Engine or Desktop)
- **Docker Compose** (v2+; usually included with recent Docker installations)

## Running the stack

From the project root:

```bash
docker compose up -d --build
```

This will:

- build the `backend` image
- start `frontend`, `backend`, and `db` services

### Access the application

- **Frontend**: `http://localhost`
- **Backend API base URL**: `http://localhost:3001`

## Services

| Service  | Port | Description                |
| -------- | ---- | -------------------------- |
| frontend | 80   | Nginx serving static files |
| backend  | 3001 | Node.js REST API           |
| db       | 5432 | PostgreSQL database        |

## API Endpoints

- `GET /api/health` – health check used by Docker healthchecks
- `GET /api/items` – list all items
- `POST /api/items` – create a new item

## Environment variables

### Backend (`backend/.env`)

| Variable       | Default | Description                  |
| -------------- | ------- | ---------------------------- |
| `PORT`         | 3001    | API port                     |
| `DATABASE_URL` | –       | PostgreSQL connection string |

### Database (from `docker-compose.yml`)

| Variable            | Default | Description       |
| ------------------- | ------- | ----------------- |
| `POSTGRES_USER`     | app     | Database user     |
| `POSTGRES_PASSWORD` | secret  | Database password |
| `POSTGRES_DB`       | myapp   | Database name     |

## Stopping the stack

```bash
docker compose down
```

To remove the persistent Postgres volume as well:

```bash
docker compose down -v
```