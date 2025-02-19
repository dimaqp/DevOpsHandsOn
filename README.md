# DevOps Hands-On Project

This project involves developing and deploying a Flask-based REST API application with database integration, containerization, automation, and infrastructure as code. The project is divided into three phases:

- **PART 1**: Application & Containerization
- **PART 2**: Infrastructure & Configuration Management
- **PART 3**: CI/CD & Automation

## PART 1: Application Development & Containerization

### Goal:
Build a Python Flask REST API, integrate a PostgreSQL database, and containerize the application using Docker.

### Tasks:

#### Flask Application Development:
- Create `app.py` for the main API logic.
- Implement models in `models.py` for entities such as Users, Accounts, and Transactions.
- Add views for authentication, account management, and transactions.
- Set up unit tests in the `tests/` directory.

#### Database Integration (PostgreSQL):
- Define the database schema for users, accounts, and transactions.
- Implement user authentication with password hashing.
- Store credentials securely (initially in `.env` file).

#### Containerization:
- Write a `Dockerfile` to package the Flask application into a container.
- Implement `wait-for-postgres.sh` to ensure the app waits for DB readiness during startup.
- Use Docker Compose to define both Flask and PostgreSQL services.
- Test the application locally with `docker-compose up`.

---

## PART 2: Infrastructure & Configuration Management

### Goal:
Define infrastructure as code using Terraform and configure systems with Ansible.

### Tasks:

#### Terraform for Infrastructure:
- Define the networking setup, including VPC and subnets.
- Configure security groups and IAM roles for proper access control.
- Deploy a PostgreSQL instance (first locally, later on the cloud).
- Deploy the application as a containerized service.

#### Ansible for Configuration Management:
- Automate the setup of monitoring tools like Prometheus and Grafana.
- Configure services for logging, monitoring, and alerting.

---

## PART 3: CI/CD & Automation

In this part, we will implement continuous integration and continuous delivery pipelines to automate testing, building, and deployment.

### Goal:
Set up automated workflows for code testing, building container images, and deploying them to an environment of choice (local or cloud).

### Tasks:
- Implement CI pipeline for running unit tests on code changes.
- Build container images and push them to a Docker registry.
- Set up CD pipeline for deploying the application to production using Kubernetes or Docker Swarm.

---
