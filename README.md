# Jenkins CI/CD Project

## Overview

This project demonstrates a simple CI/CD pipeline using Jenkins and Docker.  
The pipeline automatically builds a Docker image and deploys a container from the latest GitHub source code.

Jenkins is running inside a Docker container, and it uses the host machine’s Docker daemon to build and deploy images.

---

## Tech Stack

- Jenkins (Docker container)
- Docker
- GitHub
- Declarative Pipeline (Jenkinsfile)

---

## Jenkins Setup

Jenkins was started using Docker with Docker socket access:

```bash
docker run -d \
  --name jenkins \
  -p 9090:8080 \
  -p 50000:50000 \
  -u root \
  -v jenkins_home:/var/jenkins_home \
  -v /var/run/docker.sock:/var/run/docker.sock \
  -v /usr/bin/docker:/usr/bin/docker \
  jenkins/jenkins:lts

## Access Jenkins at

 http://localhost:9090

## Unlock Password
  
  docker exec jenkins cat /var/jenkins_home/secrets/initialAdminPassword
