# Jenkins CI/CD Demo

A beginner-friendly Continuous Integration and Continuous Deployment (CI/CD) project using Jenkins, Docker, Git, and GitHub.

## Project Overview

This project demonstrates how Jenkins can automatically retrieve source code from GitHub, build a Docker image, run basic tests, and deploy a simple website in a Docker container.

## Technologies Used

- **Jenkins** — automates the pipeline.
- **Git and GitHub** — source control and code hosting.
- **Docker** — packages and runs the website.
- **Nginx** — serves the website.
- **Linux** — development environment.

## Project Structure

```text
jenkins-cicd-demo/
├── app/
│   └── index.html
├── Dockerfile
├── Jenkinsfile
└── README.md
```

## Pipeline Stages

1. **Checkout:** retrieves the source code from GitHub.
2. **Build:** builds a Docker image for the website.
3. **Test:** checks that the website file exists and contains the expected title.
4. **Deploy:** runs the website in a Docker container.

## Run the Website Locally

Build the Docker image:

```bash
docker build -t jenkins-cicd-demo:local .
```

Run the container:

```bash
docker run -d --name jenkins-demo-test -p 8081:80 jenkins-cicd-demo:local
```

Open [http://localhost:8081](http://localhost:8081) in your browser.

To stop and remove the test container:

```bash
docker rm -f jenkins-demo-test
```

## Jenkins Configuration

Create a Jenkins Pipeline job using **Pipeline script from SCM**.

- **SCM:** Git
- **Repository URL:** `https://github.com/SaMoscus/jenkins-cicd-demo.git`
- **Branch:** `*/main`
- **Script Path:** `Jenkinsfile`

The pipeline requires Docker CLI access and permission to communicate with the Docker daemon.

## Learning Objectives

- Understand CI/CD pipeline stages.
- Store pipeline instructions in a `Jenkinsfile`.
- Build and run Docker images.
- Integrate Jenkins with GitHub.
- Practice basic deployment automation.

## Author

SaMoscus

**Project status:** Learning project — Jenkins pipeline testing and deployment.

