# Flask Docker CI/CD Demo

## Project Overview

This repository contains a simple Flask web application packaged in Docker and built with a Jenkins pipeline. The app serves a single route and demonstrates a basic Python web app workflow, including dependency management, automated testing, Docker image creation, and container deployment.

## Architecture

```
Developer
      │
      ▼
GitHub Repository
      │
      ▼
 Jenkins
      │
 ┌────┼──────────┐
 │Clone Code     │
 │Install Packages
 │Run Tests
 │Docker Build
 │Deploy
 └────┼──────────┘
      │
      ▼
 Docker Container
      │
      ▼
 Flask Application
```

- `app.py`: Flask application entrypoint.
- `requirements.txt`: Python dependencies.
- `Dockerfile`: Builds a Docker image for the app.
- `tests/test_app.py`: Unit test for the Flask home route.
- `Jenkinsfile`: CI/CD pipeline definition.

The application runs in a container exposing port `10000`, and Jenkins orchestrates the build, test, Docker image creation, and runtime container launch.

## Features

- Lightweight Flask web app
- Automated unit test with `pytest`
- Dockerized deployment
- Jenkins pipeline for CI/CD
- Simple, reproducible build and run workflow

## Screenshots

> Add screenshots of the running app, Jenkins job, or Docker container output here.

If you'd like to include actual images, add them to the repository and reference them using Markdown:

```markdown
![App Home Page](screenshots/home-page.png)
![Jenkins Pipeline](screenshots/jenkins-pipeline.png)
```

## Jenkins Pipeline

The `Jenkinsfile` defines the following stages:

1. `Clone` - clones the repository.
2. `Install Dependencies` - installs Python dependencies from `requirements.txt`.
3. `Run Tests` - runs `pytest`.
4. `Build Docker Image` - builds the Docker image named `flask-demo`.
5. `Run Container` - stops any existing container named `flask-demo`, removes it, and runs a new one exposing port `10000`.

## Docker Commands

Build the Docker image:

```bash
docker build -t flask-demo .
```

Run the app container:

```bash
docker run -d -p 10000:10000 --name flask-demo flask-demo
```

Stop the container:

```bash
docker stop flask-demo
```

Remove the container:

```bash
docker rm flask-demo
```

View logs:

```bash
docker logs flask-demo
```

## Deployment Steps

1. Clone the repository:

```bash
git clone https://github.com/rohanengineeringpathx/pyproject.git
cd pyproject
```

2. Install Python dependencies locally:

```bash
pip install -r requirements.txt
```

3. Run tests:

```bash
pytest
```

4. Build the Docker image:

```bash
docker build -t flask-demo .
```

5. Run the Docker container:

```bash
docker run -d -p 10000:10000 --name flask-demo flask-demo
```

6. Open the app in a browser:

```text
http://localhost:10000/
```

---

This README provides a clean, professional overview and makes the repository easier to understand for reviewers and collaborators.