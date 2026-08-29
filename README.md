# Project Management SaaS API

A production-oriented project management SaaS API built with **Python and FastAPI**.

The project is designed to demonstrate the development of a maintainable backend application, progressing from a solid REST API foundation to authentication, authorization, multi-tenancy, automated testing, containerization, CI/CD, cloud deployment, and observability.

> **Project status: Planned — Development not started yet.**

---

## Overview

Project Management SaaS API is a multi-tenant project management platform designed around the needs of small teams and organizations.

Users will be able to create organizations, manage team members, create projects, organize tasks, collaborate through comments, and track changes through an audit history.

The main purpose of the project is not to reproduce every feature of a product such as Jira or Trello, but to use a realistic application domain to explore and demonstrate **professional backend engineering practices**.

The project will evolve progressively alongside a structured backend learning roadmap, with a focus on depth, maintainability, testing, reliability, and production deployment.

---

## Planned Features

### Authentication

* User registration
* User login
* Password hashing
* Token-based authentication
* User account management

### Organizations & Teams

* Create and manage organizations
* Organization membership
* Invitations
* Role-based access control
* Organization-level permissions

### Projects

* Create and manage projects
* Project members
* Project status
* Project metadata

### Tasks

* Create, update, and delete tasks
* Task assignment
* Task status
* Task priority
* Due dates
* Task filtering
* Sorting and pagination

### Collaboration

* Task comments
* User activity
* Notifications

### Audit & Traceability

* Audit log
* Track important user actions
* Track changes to relevant resources

---

## Backend Engineering Goals

The project will be used to explore and demonstrate backend concepts beyond basic CRUD operations.

Planned areas include:

* REST API design
* Authentication
* Authorization
* Multi-tenancy
* Business rules
* Relational data modelling
* Database transactions
* Concurrency
* Idempotency
* Pagination
* Filtering and sorting
* Background processing
* Error handling
* Security
* Reliability
* API documentation
* Observability

Advanced functionality will only be introduced when it is justified by the project's requirements and the corresponding learning stage.

---

## Technology Stack

The planned technology stack includes:

### Backend

* Python
* FastAPI
* Pydantic
* SQLAlchemy
* Alembic

### Database

* PostgreSQL

### Testing

* pytest
* HTTPX
* pytest-asyncio
* Unit testing
* Integration testing
* API testing
* TDD

### Development & DevOps

* Git
* GitHub
* Docker
* Docker Compose
* CI/CD
* Linux

### Cloud

* AWS

### Observability

* Application logging
* Health checks
* Monitoring
* Error tracking
* Request tracing where appropriate

> The final AWS architecture and advanced infrastructure decisions will be defined during the cloud-development stage of the project rather than being fixed prematurely.

---

## Architecture

The project will progressively adopt a maintainable backend architecture.

The initial direction is based on clear separation of responsibilities between API endpoints, business logic, data access, and infrastructure concerns.

A possible high-level structure is:

```text
Client
   │
   ▼
FastAPI
   │
   ├── Authentication / Authorization
   │
   ├── API Layer
   │
   ├── Service / Business Logic
   │
   └── Data Access
           │
           ▼
       PostgreSQL
```

The architecture will evolve as the project requirements become more complex.

Architecture decisions will be documented as the project develops.

---

## Testing Strategy

Testing will be treated as a core part of the development process rather than as a final project stage.

The planned testing strategy includes:

### Unit Tests

Testing isolated business logic and application components.

### Integration Tests

Testing interactions between application components and the database.

### API Tests

Testing HTTP endpoints, request validation, responses, authentication, and authorization.

### Edge Cases

Testing scenarios such as:

* Invalid input
* Missing resources
* Unauthorized access
* Duplicate operations
* Invalid state transitions
* Conflicting updates
* Invalid organization membership

The project will follow a **TDD-oriented approach** where appropriate.

---

## Docker

Docker will be used to provide reproducible development and testing environments.

The development environment is expected to include:

```text
Application
    │
    └── FastAPI
          │
          └── PostgreSQL
```

Docker Compose will be used where appropriate to simplify local development.

---

## CI/CD

The project will progressively introduce CI/CD automation.

The intended workflow is:

```text
Git Push
   │
   ▼
Automated Checks
   │
   ├── Tests
   ├── Quality Checks
   └── Build
         │
         ▼
      Deployment
```

The final deployment workflow will depend on the AWS architecture selected during the cloud-development stage.

---

## AWS

One of the main objectives of this project is to take the application beyond local development and deploy it to AWS.

The cloud stage will focus on:

* Production deployment
* Application configuration
* Secrets management
* Database deployment
* Networking
* CI/CD
* Logging
* Monitoring
* Health checks
* Reliability

The final AWS architecture will be determined after completing the relevant cloud-learning stage.

---

## Development Roadmap

### Phase 0 — Project Definition

* [x] Define project concept
* [x] Define initial scope
* [x] Create repository
* [x] Document project goals
* [ ] Define initial requirements
* [ ] Define data model

### Phase 1 — Core API

* [ ] FastAPI application setup
* [ ] Project structure
* [ ] Configuration management
* [ ] Database integration
* [ ] SQLAlchemy models
* [ ] Alembic migrations
* [ ] Initial REST endpoints
* [ ] API documentation

### Phase 2 — Testing & TDD

* [ ] Testing infrastructure
* [ ] Unit tests
* [ ] Integration tests
* [ ] API tests
* [ ] Authentication tests
* [ ] Authorization tests
* [ ] TDD workflow

### Phase 3 — Application Features

* [ ] Users
* [ ] Authentication
* [ ] Organizations
* [ ] Team members
* [ ] Roles and permissions
* [ ] Projects
* [ ] Tasks
* [ ] Comments
* [ ] Filtering
* [ ] Sorting
* [ ] Pagination
* [ ] Audit logs
* [ ] Notifications

### Phase 4 — Production Engineering

* [ ] Docker
* [ ] Docker Compose
* [ ] CI/CD
* [ ] Environment configuration
* [ ] Security hardening
* [ ] Health checks
* [ ] Structured logging
* [ ] Observability

### Phase 5 — AWS Deployment

* [ ] AWS architecture
* [ ] Production infrastructure
* [ ] Database deployment
* [ ] Application deployment
* [ ] CI/CD deployment pipeline
* [ ] Secrets management
* [ ] Monitoring
* [ ] Production validation

### Phase 6 — Reliability & Scalability

* [ ] Performance analysis
* [ ] Database optimization
* [ ] Caching where justified
* [ ] Background processing
* [ ] Rate limiting where appropriate
* [ ] Concurrency considerations
* [ ] Idempotency
* [ ] Reliability improvements

---

## Project Principles

The project follows a few core principles:

### Quality over quantity

The goal is not to build as many features as possible.

A smaller system with solid architecture, meaningful tests, documentation, CI/CD, deployment, and observability is more valuable than a large collection of superficial features.

### Progressive complexity

New technologies and architectural patterns will be introduced when they solve an actual problem in the application.

Technology will not be added simply to increase the number of technologies listed in the repository.

### Evidence over claims

The repository will distinguish between:

* Planned
* In progress
* Implemented
* Tested
* Deployed

Features will only be described as completed once they actually exist in the codebase.

### Production mindset

The project will consider not only how to make the application work, but also how to:

* test it
* secure it
* deploy it
* monitor it
* debug it
* maintain it
* operate it reliably

---

## Project Status

**Current status: Planned**

Development will begin progressively following the backend learning roadmap.

The repository currently serves as the project's definition, roadmap, and technical planning space.

---

## Author

**Daniel López Berrocal**

Backend development · Python · FastAPI · REST APIs · PostgreSQL · Testing · Docker · AWS
