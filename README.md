# Refresh Memory API

FastAPI service for the `refresh-memory` project.

## Requirements

- Python 3.12+
- Docker and Docker Compose, for containerized development

## Local Development

### 1. Create a virtual environment

```bash
python -m venv .venv
source .venv/bin/activate
```

### 2. Install dependencies

```bash
pip install -e .
```

### 3. Configure environment variables

```bash
cp .env.example .env
```

### 4. Start the API

```bash
uvicorn app.main:app --reload
```

The API will be available at:

```text
http://localhost:8000
```

## Docker Compose

Use Docker Compose when you want to run the API in a container without managing a local Python environment.

### Start the service

```bash
docker compose up --build
```

This builds the image if needed and starts the `api` service defined in `docker-compose.yml`.

### Run in the background

```bash
docker compose up --build -d
```

### View logs

```bash
docker compose logs -f api
```

### Stop the service

```bash
docker compose down
```

The containerized API is exposed at:

```text
http://localhost:8000
```

## Database Migrations

Start the PostgreSQL service:

```bash
docker compose up -d postgres
```

Check the current Alembic revision:

```bash
alembic current
```

Apply all pending migrations:

```bash
alembic upgrade head
```

## API Reference

Swagger UI:

```text
http://localhost:8000/docs
```

OpenAPI schema:

```text
http://localhost:8000/openapi.json
```

Health check:

```bash
curl http://localhost:8000/health
```
