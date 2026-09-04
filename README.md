# Project Management SaaS API

A multi-tenant REST API for managing teams, projects, and tasks — a simplified Trello/Asana-style tool. Built with **FastAPI**, with asynchronous processing, caching, observability, and deployment on **AWS** managed with **Terraform**.

This is my second backend project and the point where all the architecture pieces I've been learning separately come together: task queues, caching, OAuth2 authentication, CI/CD, standardized API design, and production observability.

## 📌 Project goal

Unlike the previous project (focused on implementation quality over a simple domain), the goal here is to **correctly integrate real backend architecture pieces** on a domain with richer relationships: organizations, teams, projects, tasks, and permissions.

## ⚙️ Features

### Organizations and teams
- Each user belongs to one or more organizations (multi-tenant)
- Team management within an organization
- Role and permission system (owner, admin, member) — role-based access control (RBAC)

### Projects and tasks
- CRUD for projects within an organization
- CRUD for tasks within a project: title, description, status, priority, assignee, due date
- Kanban-style boards (configurable statuses: To Do / In Progress / Done)
- Task comments
- Task change history (basic audit trail)

### Notifications (asynchronous processing)
- Email notification when a task is assigned
- Automatic reminders for tasks approaching their due date (periodic tasks with Celery Beat)
- Weekly project report generation in the background, without blocking the user

### Invitations
- Invite users to an organization by email
- Invitation acceptance flow

## 🔒 Authentication and authorization

- OAuth2 with Authorization Code + PKCE flow
- JWT with access token and refresh token
- Resource-level authorization: a user can only operate on organizations/projects they belong to, according to their role

## 🚀 Architecture and performance

- **Celery + Redis** as the queue system for all asynchronous processing (emails, reports, reminders)
- **Redis as cache** on frequently-read endpoints (task listing for a project, organization dashboard)
- **Rate limiting** per user and per organization
- API designed following the [Zalando RESTful API Guidelines](https://opensource.zalando.com/restful-api-guidelines/): explicit versioning, consistent pagination, standardized error format, complete OpenAPI contract

## 🧪 Quality and reliability

- TDD with `pytest`, unit and integration test coverage
- Load testing with **Locust** on critical endpoints (task listing, task creation) to validate behavior under concurrency
- Full CI/CD with GitHub Actions: tests, linting, Docker image build, and automated deployment

## 📊 Observability

- Structured logging
- Traces and instrumentation with **OpenTelemetry**
- Basic metrics dashboard in Grafana Cloud (latency, error rate, throughput per endpoint)

## ☁️ Infrastructure

- Deployed on AWS managed as infrastructure as code with **Terraform**
- Docker containers, orchestrated as defined in the reference course (ECS/Fargate)

## 🛠️ Tech stack

| Category | Technology |
|---|---|
| Framework | FastAPI |
| Database | PostgreSQL |
| ORM | SQLAlchemy |
| Task queues | Celery + Redis |
| Cache | Redis |
| Authentication | OAuth2 (Authorization Code + PKCE) + JWT |
| Testing | Pytest + Locust |
| Observability | OpenTelemetry + Grafana |
| Infrastructure | Terraform + AWS (ECS/Fargate) |
| CI/CD | GitHub Actions |

## 📂 Project structure

```
project-management-saas-api/
├── app/
│   ├── api/                # Endpoints (routers), versioned
│   ├── models/              # SQLAlchemy models
│   ├── schemas/              # Pydantic schemas
│   ├── core/                 # Configuration, security, dependencies
│   ├── services/               # Business logic
│   ├── tasks/                    # Celery tasks
│   └── main.py
├── tests/
├── load_tests/              # Locust scenarios
├── infra/                     # Terraform
├── alembic/
├── docker-compose.yml
├── Dockerfile
└── requirements.txt
```

## 🏁 How to run the project

```bash
# Clone the repository
git clone https://github.com/DaniLoBerr/project-management-saas-api.git
cd project-management-saas-api

# Start the services (API + Celery worker + PostgreSQL + Redis)
docker-compose up --build

# Run migrations
docker-compose exec web alembic upgrade head

# Run tests
docker-compose exec web pytest

# Run load test
locust -f load_tests/locustfile.py
```

The interactive API documentation will be available at `http://localhost:8000/docs`.

## 🕓 Project evolution

Unlike the Expense Tracker, this project started out with Celery, Redis, OAuth2, CI/CD, and the API design guidelines already in place from the initial build — pieces I already had mastered from applying them in Project 1, including deployment on AWS. Even so, there were later phases of improvement on the already-running project:

| Phase | What was added | Motivated by |
|---|---|---|
| 1 | Initial build — organizations, teams, projects, tasks, async notifications, caching, OAuth2, CI/CD, standardized API design, and AWS deployment with Terraform | Everything learned up through Project 1 (Celery, Redis, OAuth2, CI/CD, Zalando Guidelines, Scalable FastAPI on AWS) |
| 2 | Load testing + optimizations on the detected bottlenecks, validated against the real AWS environment | Locust |
| 3 | OpenTelemetry instrumentation | OpenTelemetry |
| 4 | PostgreSQL index and query optimization | The Art of PostgreSQL |

## 📈 Project status

🚧 Actively in development — this README will be updated as the project progresses.

## 🗺️ Context

This project is part of my personal learning roadmap to become a Backend Engineer, which you can check out on my [GitHub profile](https://github.com/DaniLoBerr).
