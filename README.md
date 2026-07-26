# 🚀 Flask CI/CD Pipeline Automation using Jenkins & Docker

![Python](https://img.shields.io/badge/Python-3.13-blue)
![Flask](https://img.shields.io/badge/Flask-3.0-black)
![Jenkins](https://img.shields.io/badge/Jenkins-CI%2FCD-orange)
![Docker](https://img.shields.io/badge/Docker-Containerization-blue)
![GitHub](https://img.shields.io/badge/GitHub-Code%20Repository-black)

---

## 📌 About This Project

While learning DevOps and automation, I built this project to understand how a real-world application moves from **development to deployment** using CI/CD practices.

The main objective of this project was to automate the complete deployment workflow of a Flask application.

Instead of manually installing dependencies, testing code, creating Docker images, and running containers, Jenkins automates the complete process.

This project demonstrates how modern software teams use **Continuous Integration and Continuous Deployment (CI/CD)** to deliver applications faster and more reliably.

---

# 🏗️ Project Workflow

```
Developer
    |
    | Push Code
    ↓
GitHub Repository
    |
    ↓
Jenkins CI/CD Pipeline
    |
    ├── Install Dependencies
    |
    ├── Run Automated Tests
    |
    ├── Build Docker Image
    |
    └── Deploy Docker Container
              |
              ↓
        Flask Application
```

---

# 🛠️ Tech Stack

| Technology | Purpose |
|------------|---------|
| Python | Backend Development |
| Flask | Web Application Framework |
| Jenkins | CI/CD Automation |
| Docker | Application Containerization |
| GitHub | Source Code Management |
| Pytest | Automated Testing |

---

# 📂 Project Structure

```
Flask-CICD
│
├── app.py                  # Flask Application
├── requirements.txt        # Python Dependencies
├── Dockerfile              # Docker Configuration
├── Jenkinsfile             # Jenkins Pipeline Script
├── Procfile
│
├── tests
│   └── test_app.py         # Test Cases
│
└── screenshots
    ├── jenkins-success.png
    ├── docker-container.png
    └── application-running.png
```

---

# ⚙️ CI/CD Pipeline Steps

## 1. Source Code Checkout

Jenkins automatically fetches the latest source code from GitHub.

```
GitHub Repository → Jenkins Workspace
```

---

## 2. Install Dependencies

Jenkins installs all required Python packages.

```bash
python -m pip install -r requirements.txt
```

---

## 3. Automated Testing

Before deployment, Jenkins runs automated tests using Pytest.

```bash
python -m pytest
```

Successful test result:

```
1 passed
```

---

## 4. Build Docker Image

After successful testing, Jenkins creates a Docker image.

```bash
docker build -t flask-demo .
```

---

## 5. Deploy Docker Container

Jenkins automatically stops the previous container and starts a new container.

```bash
docker stop flask-demo
docker rm flask-demo
docker run -d -p 10000:10000 --name flask-demo flask-demo
```

Application runs on:

```
http://localhost:10000
```

---

# 🐳 Docker Configuration

The application is containerized using Docker.

### Dockerfile

```dockerfile
FROM python:3.13-slim

WORKDIR /app

COPY requirements.txt .

RUN pip install -r requirements.txt

COPY . .

EXPOSE 10000

CMD ["python", "app.py"]
```

---

# 🔄 Jenkins Pipeline

The complete Jenkins pipeline automates:

```
Code Checkout
      ↓
Install Dependencies
      ↓
Run Tests
      ↓
Build Docker Image
      ↓
Deploy Container
```

---

# 📸 Project Screenshots

## Jenkins Pipeline Success

![Jenkins Pipeline](screenshots/jenkins-success.png)


## Docker Container Running

![Docker Container](screenshots/docker-container.png)


## Flask Application Running

![Flask Application](screenshots/application-running.png)

---

# 🚀 How to Run Locally

### Clone Repository

```bash
git clone https://github.com/rohanengineeringpathx/pyproject.git
```

### Navigate to Project Folder

```bash
cd pyproject
```

### Install Dependencies

```bash
pip install -r requirements.txt
```

### Run Flask Application

```bash
python app.py
```

Open browser:

```
http://localhost:10000
```

---

# 🧪 Running Tests

Execute:

```bash
python -m pytest
```

Expected output:

```
1 passed
```

---

# 📚 What I Learned

Building this project helped me understand practical DevOps concepts:

✅ Creating CI/CD pipelines using Jenkins  
✅ Integrating GitHub with Jenkins  
✅ Automating application testing  
✅ Containerizing applications using Docker  
✅ Managing Docker containers through automation  
✅ Debugging real-world deployment issues  

During development, I solved challenges related to:

- Python environment configuration
- Jenkins service permissions
- Docker PATH configuration
- Automated deployment workflow

---

# 🔮 Future Improvements

Some improvements I plan to add:

- Deploy application on AWS Cloud
- Push Docker images to Docker Hub
- Add Kubernetes deployment
- Add Jenkins webhook for automatic builds
- Add monitoring using Prometheus and Grafana

---

# 👨‍💻 Author

**Rohan Kumar**

B.Tech Computer Science Engineering

GitHub:
https://github.com/rohanengineeringpathx

LinkedIn:
https://www.linkedin.com/in/rohan-kumar-54b6823a4/

---

⭐ If you found this project useful, feel free to star the repository!
