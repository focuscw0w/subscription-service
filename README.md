# Subscription Service

A Go web application for managing subscription plans with user registration, authentication, and automated email notifications.

## Tech Stack

- **Go** – backend + server-side rendered templates (`html/template`)
- **PostgreSQL** – database (users, plans, `user_plans` bindings)
- **Redis** – session store ([scs](https://github.com/alexedwards/scs))
- **Chi** – HTTP router
- **MailHog** – local SMTP for email testing
- **gofpdf** – PDF manual generation

## Features

- User registration and account activation via email
- Login / logout with session management
- Subscription plan selection and activation
- Automatic invoice and PDF manual delivery upon subscribing
- Protected routes via authentication middleware

## Getting Started

### Prerequisites

- Go 1.27+
- Docker & Docker Compose

### 1. Start infrastructure

```bash
docker compose up -d
```

Starts PostgreSQL (`:5432`), Redis (`:6379`), and MailHog (SMTP `:1025`, UI `:8025`).

### 2. Run the application

```bash
make run
```

The app runs at `http://localhost`.

### Available commands

| Command        | Description                    |
|----------------|--------------------------------|
| `make build`   | Compile the binary             |
| `make run`     | Build + run in background      |
| `make stop`    | Stop the running application   |
| `make restart` | Restart the application        |
| `make test`    | Run tests                      |
| `make clean`   | Clean build artifacts          |

## Project Structure

```
├── cmd/web/            # Main application (handlers, routes, middleware, templates)
├── data/               # Data models (User, Plan) and DB logic
├── pdf/                # PDF manual template
├── docker-compose.yaml # PostgreSQL, Redis, MailHog
└── Makefile            # Build, run, test commands
```

## Tests

```bash
make test
```
