# 🚀 Production-Style CI/CD Pipeline with GitHub Actions, Docker & AWS EC2

A production-style Continuous Integration and Continuous Deployment (CI/CD) pipeline for a Flask application using GitHub Actions, Docker, Docker Hub, and AWS EC2.

Every push to the `main` branch automatically runs tests, builds a Docker image, pushes it to Docker Hub, and deploys the latest application to an AWS EC2 instance.

## Architecture

> **Architecture diagram coming soon**

## Features

- ✅ Automated testing with Pytest
- ✅ Docker containerization
- ✅ GitHub Actions CI/CD pipeline
- ✅ Docker Hub image registry
- ✅ Automatic deployment to AWS EC2
- ✅ Docker Compose deployment
- ✅ Immutable Docker image tags using Git commit SHA
- ✅ Secure secret management with GitHub Secrets

## Tech Stack

| Technology | Purpose |
|------------|---------|
| Python | Application language |
| Flask | Web framework |
| Pytest | Automated testing |
| Docker | Containerization |
| Docker Compose | Container orchestration |
| GitHub Actions | CI/CD automation |
| Docker Hub | Container registry |
| AWS EC2 | Application hosting |
| Git | Version control |

## Project Structure

```text
.
├── .github/
│   └── workflows/
│       └── main.yml
├── nginx/
├── app.py
├── Dockerfile
├── docker-compose.yml
├── requirements.txt
├── test.py
└── README.md
```

## CI/CD Workflow

```text
Developer
    │
git push
    │
    ▼
GitHub Repository
    │
    ▼
GitHub Actions
    │
    ├──────────────┐
    │              │
Run Tests      Build Docker Image
    │              │
    └──────┬───────┘
           ▼
      Docker Hub
           │
           ▼
      SSH to EC2
           │
           ▼
 Docker Compose Deployment
           │
           ▼
 Flask Application
```

## Deployment Process

Every push to the `main` branch triggers the following workflow:

1. Source code is checked out.
2. Python dependencies are installed.
3. Automated tests are executed using Pytest.
4. A Docker image is built.
5. The image is tagged with both:
   - `latest`
   - the Git commit SHA
6. Images are pushed to Docker Hub.
7. GitHub Actions connects securely to AWS EC2 using SSH.
8. The EC2 instance pulls the new image.
9. Docker Compose restarts the application with the new version.

## Run Locally

Clone the repository:

```bash
git clone https://github.com/emmxy-ops/cicd-demo-cloned-.git
cd cicd-demo-cloned-
```

Build and run:

```bash
docker compose up --build
```

Visit:

```
http://localhost:5000
```

## Roadmap

- [x] Automated testing
- [x] Docker containerization
- [x] Docker Hub integration
- [x] AWS EC2 deployment
- [x] Git SHA image versioning
- [ ] Nginx reverse proxy
- [ ] HTTPS with Let's Encrypt
- [ ] Zero-downtime deployment
- [ ] Automated rollback
- [ ] Monitoring and logging