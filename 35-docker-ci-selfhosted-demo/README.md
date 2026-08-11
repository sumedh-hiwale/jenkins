# 🚀 Docker CI Pipeline Using GitHub Actions and Self-Hosted Runner on AWS EC2

## 📌 Objective

Create a Docker Continuous Integration (CI) pipeline using GitHub Actions and a Self-Hosted Runner running on an AWS EC2 Ubuntu instance.

The workflow will:

✅ Build a Docker Image
✅ Push the Image to Docker Hub
✅ Pull the Image from Docker Hub
✅ Run a Docker Container automatically

---

# 🏗️ Architecture

```text
GitHub Repository
        │
        ▼
GitHub Actions Workflow
        │
        ▼
Self-Hosted Runner (AWS EC2 Ubuntu)
        │
        ▼
Docker Build
        │
        ▼
Docker Hub
        │
        ▼
Docker Pull
        │
        ▼
Docker Container Run
```

---

# 📋 Prerequisites

Before starting, ensure the following:

* GitHub Account
* Docker Hub Account
* AWS Account
* Ubuntu EC2 Instance
* Internet Connectivity
* GitHub Repository

---

# 🛠️ Step 1: Create GitHub Repository

1. Login to GitHub.
2. Click **New Repository**.
3. Repository Name:

```text
docker-ci-selfhosted-demo
```

4. Description:

```text
Creating a Docker CI setup using GitHub Actions on a Self-Hosted Runner
```

5. Select **Public Repository**.
6. Enable **README.md**.
7. Click **Create Repository**.

---

# ☁️ Step 2: Launch AWS EC2 Instance

Launch a new EC2 Instance with the following configuration:

| Setting        | Value          |
| -------------- | -------------- |
| AMI            | Ubuntu Server  |
| Instance Type  | t2.micro       |
| Security Group | Allow SSH (22) |
| Storage        | Default        |

Launch the instance and connect using EC2 Instance Connect.

---

# 🐳 Step 3: Install Docker on EC2

Update Packages

```bash
sudo apt update
```

Install Docker

```bash
sudo apt install docker.io -y
```

Start Docker

```bash
sudo systemctl start docker
sudo systemctl enable docker
```

Verify Docker

```bash
docker --version
```

---

# 👥 Step 4: Add Ubuntu User to Docker Group

```bash
sudo usermod -aG docker ubuntu
newgrp docker
```

Verify:

```bash
docker ps
```

---

# 🤖 Step 5: Configure GitHub Self-Hosted Runner

Navigate to:

```text
Repository
→ Settings
→ Actions
→ Runners
→ New Self-hosted Runner
```

Select:

```text
Linux
x64
```

Run the commands provided by GitHub on the EC2 instance.

Example:

```bash
mkdir actions-runner && cd actions-runner

curl -o actions-runner-linux-x64.tar.gz -L <runner-url>

tar xzf actions-runner-linux-x64.tar.gz

./config.sh --url <repository-url> --token <token>
```

Start Runner:

```bash
./run.sh
```

Runner Status:

```text
Connected to GitHub
Listening for Jobs
```

---

# ⚙️ Step 6: Install Runner as a Service

Stop Manual Runner:

```bash
Ctrl + C
```

Install Service:

```bash
sudo ./svc.sh install
```

Start Service:

```bash
sudo ./svc.sh start
```

Verify Status:

```bash
sudo ./svc.sh status
```

Expected Output:

```text
active (running)
```

---

# 🔐 Step 7: Configure GitHub Secrets

Navigate to:

```text
Repository
→ Settings
→ Secrets and Variables
→ Actions
```

Create the following secrets:

### Secret 1

```text
DOCKERHUB_USERNAME
```

Value:

```text
<your-dockerhub-username>
```

### Secret 2

```text
DOCKERHUB_TOKEN
```

Value:

```text
<your-dockerhub-access-token>
```

---

# 📄 Step 8: Create Dockerfile

Create a file named:

```text
Dockerfile
```

Content:

```dockerfile
FROM nginx:latest
COPY . /usr/share/nginx/html
EXPOSE 80
```

---

# 🚀 Step 9: Create GitHub Actions Workflow

Create:

```text
.github/workflows/docker-ci-selfhosted.yml
```

Content:

```yaml
name: Docker_CI_pipeline_on_self-hosted_runner

on:
  push:

jobs:
  docker:
    runs-on: self-hosted

    steps:
      - name: Checkout Code
        uses: actions/checkout@v4

      - name: Login to Docker Hub
        uses: docker/login-action@v3
        with:
          username: ${{ secrets.DOCKERHUB_USERNAME }}
          password: ${{ secrets.DOCKERHUB_TOKEN }}

      - name: Build Docker Image
        run: |
          docker build -t ${DOCKER_USER}/docker-ci-selfhosted-demo:latest .
        env:
          DOCKER_USER: ${{ secrets.DOCKERHUB_USERNAME }}

      - name: Push Docker Image
        run: |
          docker push ${DOCKER_USER}/docker-ci-selfhosted-demo:latest
        env:
          DOCKER_USER: ${{ secrets.DOCKERHUB_USERNAME }}

      - name: Pull Docker Image
        run: |
          docker pull ${DOCKER_USER}/docker-ci-selfhosted-demo:latest
        env:
          DOCKER_USER: ${{ secrets.DOCKERHUB_USERNAME }}

      - name: Run Docker Container
        run: |
          docker rm -f docker-ci-container || true
          docker run -d --name docker-ci-container -p 80:80 ${DOCKER_USER}/docker-ci-selfhosted-demo:latest
        env:
          DOCKER_USER: ${{ secrets.DOCKERHUB_USERNAME }}
```

---

# 📤 Step 10: Commit Changes

Commit Message:

```text
Add Docker CI pipeline for self-hosted runner
```

GitHub Actions workflow will automatically trigger.

---

# ✅ Step 11: Verify Workflow Execution

Navigate to:

```text
Repository
→ Actions
```

Expected Status:

```text
Success ✅
```

Workflow Steps:

```text
Checkout Code ✅
Docker Login ✅
Build Docker Image ✅
Push Docker Image ✅
Pull Docker Image ✅
Run Docker Container ✅
```

---

# 🔍 Step 12: Verify Docker Resources on EC2

List Images:

```bash
docker images
```

List Running Containers:

```bash
docker ps
```

Expected:

```text
docker-ci-container
```

should be running successfully.

---

# 🎯 Outcome

Successfully configured a Docker CI pipeline using GitHub Actions and a Self-Hosted Runner on AWS EC2.

The workflow automatically:

✅ Builds Docker Images

✅ Pushes Images to Docker Hub

✅ Pulls Images from Docker Hub

✅ Runs Docker Containers

✅ Uses AWS EC2 as a Self-Hosted GitHub Actions Runner

---

# 🏆 Conclusion

This project demonstrates how GitHub Actions can be integrated with a Self-Hosted Runner running on AWS EC2 to automate Docker image build, push, pull, and deployment activities, providing a complete Continuous Integration (CI) workflow.
