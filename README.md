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


## Task 4: Setting up CI/CD Pipeline with Jenkins

This guide will walk you through the process of setting up Jenkins, installing necessary plugins, and creating a freestyle project to build a CI/CD pipeline for your application using a Dockerfile directly from your GitHub repository.



Prerequisites
 * Ensure you have Docker installed on your machine.
  * Have a GitHub repository with your application code and a Dockerfile
  
  ### Step 1: Install Jenkins
Follow the official Jenkins installation guide for your operating system: Jenkins Installation Guide(https://www.jenkins.io/doc/book/installing/)

### Step 2: Install Necessary Plugins
1.  Open Jenkins in your browser (http://localhost:8080 by default).

2.  Click on "Manage Jenkins" in the left sidebar.

3.  Select "Manage Plugins."

4.  Navigate to the "Available" tab.

5.  Search for and install the following plugins:
     GitHub Plugin
     Docker Plugin
6.  Restart Jenkins to apply the plugin changes.

### Step 3: Configure GitHub Integration
1. Go to "Manage Jenkins" > "Configure System."
2. Scroll down to the "GitHub" section.
3. Add your GitHub credentials and configure the necessary settings.

### Step 4: Create a Freestyle Project
1. Click on "New Item" on the Jenkins dashboard.
2. Enter a name for your project (e.g., "MyAppCI/CD").
3. Select "Freestyle project" and click "OK."

### Step 5: Configure Build Steps
1. In the project configuration, go to the "Build" section.

2. Click on "Add build step" and choose "Execute shell" or "Execute Windows batch command," depending on your environment.

3. Enter the build commands, including the Docker build command using your Dockerfile.

Example Shell Build Commands:

```
git clone https://github.com/yourusername/your-repo.git
cd your-repo
docker build -t your-image-name .
```
Example Windows Batch Build Commands:
```
git clone https://github.com/yourusername/your-repo.git
cd your-repo
docker build -t your-image-name .
```
4. Save the project configuration.

### Step 6: Triggering the CI/CD Pipeline
1. Open your project on the Jenkins dashboard.
2. Click on "Build Now" to manually trigger the CI/CD pipeline.

Congratulations! You've successfully set up a Jenkins freestyle project for building a CI/CD pipeline for your application using a Dockerfile from your GitHub repository. Adjust the configurations and commands as needed for your specific project requirements.


## Screenshots

https://drive.google.com/drive/folders/1-cRcHPP9UylF-ErYCfPXEQcEowyiUpDZ?usp=sharing






