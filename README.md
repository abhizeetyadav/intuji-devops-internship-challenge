# intuji-devops-internship-challenge

## CI/CD Pipeline with Docker and Jenkins

This repository contains scripts and configurations for setting up a CI/CD pipeline using Docker and Jenkins. The pipeline is designed to build and deploy a simple web application from a GitHub repository to Docker Hub.

## Task 1: Install Docker using VMs

To install Docker on a Linux machine, use the provided bash script.

```bash
#!/bin/bash

# Install Docker on a Linux machine
sudo apt-get update
sudo apt-get install -y docker.io

```
## Task 2: Build and Push Docker Image
### 2.1 Clone the GitHub Repository
Clone the php-hello-world repository.

```
git clone https://github.com/silarhi/php-hello-world.git
cd php-hello-world
```


### 2.2 Create Dockerfile and Push Image to Docker Hub
Create a Dockerfile to build a Docker image for the web application (using nginx, apache, or httpd). Push the image to Docker Hub.

Example Dockerfile:

```
FROM nginx:latest
COPY . /usr/share/nginx/html
EXPOSE 80
```

Build and push the Docker image:
```
docker build -t your-dockerhub-username/php-hello-world:latest .
docker push your-dockerhub-username/php-hello-world:latest
```

## Task 3: Create Docker-Compose File
Create a docker-compose.yml file for the application.
```
version: '3'
services:
  web:
    image: your-dockerhub-username/php-hello-world:latest
    ports:
      - "8080:80"
```

Replace your-dockerhub-username with your Docker Hub username.


## Task 4: Install Jenkins and Create CI/CD Pipeline
Install Jenkins and necessary plugins.

Create a freestyle project in Jenkins for the CI/CD pipeline. Configure the project to build artifacts using the Dockerfile directly from your GitHub repo.

## Screenshots

https://drive.google.com/drive/folders/1-cRcHPP9UylF-ErYCfPXEQcEowyiUpDZ?usp=sharing






