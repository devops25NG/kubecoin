<div align="center">

<h1>KubeCoin Project (App + Delivery)</h1>

<p><strong>Full-stack source with Docker Compose, Kubernetes env manifests, and Jenkins pipeline</strong></p>

![Compose](https://img.shields.io/badge/Docker%20Compose-Local%20Stack-0ea5e9?style=for-the-badge)
![Kubernetes](https://img.shields.io/badge/Kubernetes-dev%20%7C%20test%20%7C%20prod-2563eb?style=for-the-badge)
![Jenkins](https://img.shields.io/badge/Jenkins-CI%2FCD-1d4ed8?style=for-the-badge)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-init.sql-4338ca?style=for-the-badge)

</div>

---

## Overview

This repository contains:

- `backend/` service source
- `frontend/` service source
- `docker-compose.yml` for local full-stack run
- `k8s/dev`, `k8s/test`, `k8s/prod` manifests
- `Jenkinsfile` for branch-based pipeline deployment

## CI/CD Branch Mapping

| Branch | Kubernetes Namespace |
|---|---|
| `dev` | `dev` |
| `test` | `test` |
| `main` | `prod` |

Pipeline flow:

1. checkout
2. docker login
3. build images
4. push images
5. deploy manifests
6. rollout status checks

## Local Run (Compose)

```bash
docker compose up -d --build
docker compose ps
```

Frontend is exposed on `http://localhost:3000`.

## Kubernetes Apply (Example)

```bash
kubectl apply -f k8s/dev/
```

## Folder Guide

| Path | Purpose |
|---|---|
| `backend/` | Flask backend service |
| `frontend/` | React frontend service |
| `k8s/dev` | dev manifests |
| `k8s/test` | test manifests |
| `k8s/prod` | prod manifests |
| `init.sql` | DB schema/bootstrap |
