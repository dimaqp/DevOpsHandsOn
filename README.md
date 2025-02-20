# DevOps Hands-On Project

This project develops and deploys a Flask-based REST API with integrated PostgreSQL, containerization, infrastructure as code, and CI/CD pipelines.

## Table of Contents
- [Overview](#overview)
- [Part 1: Application & Containerization](#part-1-application--containerization)
    - [Flask App Development](#flask-app-development)
    - [Database Integration](#database-integration)
    - [Containerization](#containerization)
- [Part 2: Infrastructure & Configuration Management](#part-2-infrastructure--configuration-management)
    - [Terraform Setup](#terraform-setup)
    - [Ansible Configuration](#ansible-configuration)
- [Part 3: CI/CD & Automation](#part-3-cicd--automation)

## Overview
The project is structured into three parts:
1. Application development and containerization.
2. Infrastructure and configuration management.
3. CI/CD pipeline implementation for automated testing, building, and deployment.

## Part 1: Application & Containerization

### Flask App Development
- **app.py**: Primary API logic.
- **models.py**: Defining entities such as Users, Accounts, and Transactions.
- **Views**: Handling authentication, account management, and transactions.
- **Tests**: Located in the `tests/` directory for unit testing.

### Database Integration
- **PostgreSQL Schema**: Tables for users, accounts, and transactions.
- **Authentication**: Secure user authentication with password hashing.
- **Configuration**: Initial credentials stored in `.env` file.

### Containerization
- **Dockerfile**: Creates a containerized Flask application.
- **wait-for-postgres.sh**: Script to ensure database readiness before starting the app.
- **Docker Compose**: Defines services for Flask and PostgreSQL.
- **Local Testing**: Run with `docker-compose up`.

## Part 2: Infrastructure & Configuration Management

### Terraform Setup
- **Networking**: Configures VPC, subnets, and security groups.
- **IAM Roles**: Establishes proper access control.
- **Deployment**: Sets up a PostgreSQL instance and deploys the containerized service.

### Ansible Configuration
- **Monitoring**: Automates setup for Prometheus and Grafana.
- **Logging & Alerts**: Configures services for comprehensive monitoring and alerting.

## Part 3: CI/CD & Automation

### CI/CD Goals
- **Continuous Integration**: Automates running unit tests on every code change.
- **Container Build**: Automates building Docker images and pushing to a registry.
- **Continuous Delivery**: Deploys the application automatically using Kubernetes or Docker Swarm.

---