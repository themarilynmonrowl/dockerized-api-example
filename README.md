# Dockerized API Example (FastAPI + PostgreSQL)

A minimal FastAPI app with PostgreSQL and SQLAlchemy, fully containerized with Docker Compose.
Includes a small items CRUD, health check, tests, and a CI workflow template.

## Features
- FastAPI app with `/health` and `/items` CRUD
- PostgreSQL database via Docker Compose
- SQLAlchemy ORM (sync) with automatic table creation on startup
- `.env` for configuration + `init.sql` example
- Pytest unit tests (using SQLite in-memory + dependency override)
- GitHub Actions CI (install + run tests)

## Quickstart

```bash
cp .env.example .env
docker compose up --build
# http://localhost:8080/docs
```

### Useful Commands
```bash
docker compose down
docker compose down -v
```

## Project Structure
```
dockerized-api-example/
├─ app/
│  ├─ __init__.py
│  ├─ main.py
│  ├─ db.py
│  ├─ models.py
│  └─ schemas.py
├─ tests/
│  └─ test_app.py
├─ .github/workflows/ci.yml
├─ Dockerfile
├─ docker-compose.yml
├─ docker-compose.env-cmd.yml
├─ docker-compose.python-main.yml
├─ exercises/
│  ├─ ex1_alpine_git/
│  └─ ex2_nginx_ubuntu/
├─ init.sql
├─ .env.example
├─ requirements.txt
├─ .gitignore
└─ README.md
```

---

## Compose Variants (Two Ways to Run)

- Variant i (**env + command**):
  ```bash
  docker compose -f docker-compose.env-cmd.yml up --build
  ```

- Variant ii (**python __main__**):
  ```bash
  docker compose -f docker-compose.python-main.yml up --build
  ```

Both variants declare a **named network** `app_net` and use **named volumes** (`db_data`, `app_static`).

## Exercises

- `exercises/ex1_alpine_git/` — Alpine image with Git; build, tag, run, attach, verify `git --version`.
- `exercises/ex2_nginx_ubuntu/` — Ubuntu 18.04 + Nginx serving a custom index.html.
