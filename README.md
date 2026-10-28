# Cloud Web App Deployment

## 📌 Project Overview

This project demonstrates the complete process of developing a simple web application and deploying it on an AWS EC2 Linux server.

The application was first created locally using **Visual Studio Code**, uploaded to **GitHub**, and then deployed to an **AWS EC2 Ubuntu server** using **Apache Web Server**.

### Deployment Flow

```text
VS Code
   ↓
HTML / CSS / JavaScript
   ↓
Git & GitHub
   ↓
AWS EC2 Ubuntu Server
   ↓
Apache Web Server
   ↓
Live Web Application
```

---

# 🎯 Task

The objective of this project was to:

* Build a basic web application.
* Use HTML, CSS and JavaScript.
* Store the project on GitHub.
* Create a Linux server using AWS EC2.
* Configure network access using an AWS Security Group.
* Connect to the Linux server using SSH.
* Install and configure Apache Web Server.
* Deploy the application on the EC2 server.
* Access and test the application through a public IP address.

---

# 🛠️ Technologies Used

* HTML5
* CSS3
* JavaScript
* Visual Studio Code
* Git
* GitHub
* AWS EC2
* Ubuntu Server
* Apache2
* SSH
* Linux Command Line

---

# 📁 Project Structure

```text
cloud-web-app-deployment/
│
└── app/
    ├── index.html
    ├── style.css
    └── script.js
```

---

# Step 1 — Create the Web Application

## 📍 Where I worked

**Windows PC → Visual Studio Code**

I created the web application locally using HTML, CSS and JavaScript.

### `index.html`

The HTML file contains the structure of the web page.

It includes:

* Project title
* Introduction
* Test Application button
* Linux section
* Networking section
* Cloud section
* Footer

### `style.css`

The CSS file was used to:

* Design the page
* Add colors
* Add spacing
* Create cards
* Style the button
* Make the website responsive

### `script.js`

JavaScript was used to create a simple interactive button.

When the user clicks **Test Application**, it displays:

```text
Application is working successfully!
```

---

# Step 2 — Test the Application Locally

## 📍 Where I worked

**Visual Studio Code**

I opened the `index.html` file in the browser and checked that:

* The page loaded correctly.
* CSS styling worked.
* The cards were displayed.
* The JavaScript button worked.

---

# Step 3 — Create Git Repository

## 📍 Where I worked

**Windows CMD / Terminal**

I opened Command Prompt and moved to my project folder.

Example:

```cmd
cd "C:\Users\Tejas\OneDrive\Desktop\cloud-web-app-deployment"
```

I initialized Git:

```cmd
git init
```

I checked the Git status:

```cmd
git status
```

---

# Step 4 — Configure Git

## 📍 Where I worked

**Windows CMD**

I configured my Git username:

```cmd
git config --global user.name "Tejas Kondhalkar"
```

I configured my Git email:

```cmd
git config --global user.email "YOUR_GIT_EMAIL"
```

Then I checked the Git configuration:

```cmd
git config --global --list
```

---

# Step 5 — Add and Commit the Project

## 📍 Where I worked

**Windows CMD**

I added the application files:

```cmd
git add .
```

Then I created the first commit:

```cmd
git commit -m "Add initial cloud web application"
```

I checked the repository status:

```cmd
git status
```

---

# Step 6 — Connect Local Repository to GitHub

## 📍 Where I worked

**Windows CMD + GitHub**

I created the GitHub repository:

```text
cloud-web-app-deployment
```

Then I connected my local Git repository to GitHub:

```cmd
git remote add origin https://github.com/Tejaskondhalkar-2003/cloud-web-app-deployment.git
```

I changed the branch name to `main`:

```cmd
git branch -M main
```

Then I pushed the project:

```cmd
git push -u origin main
```

The repository is available on GitHub:

```text
https://github.com/Tejaskondhalkar-2003/cloud-web-app-deployment
```

---

# Step 7 — Create AWS EC2 Instance

## 📍 Where I worked

**AWS Management Console → EC2**

I created a new EC2 instance.

### Instance configuration

| Setting           | Configuration           |
| ----------------- | ----------------------- |
| Instance Name     | cloud-web-app-server    |
| Operating System  | Ubuntu Server 24.04 LTS |
| Instance Type     | t3.micro                |
| Architecture      | 64-bit                  |
| Region            | US East (N. Virginia)   |
| Availability Zone | us-east-1c              |

The instance was launched successfully.

---

# Step 8 — Create SSH Key Pair

## 📍 Where I worked

**AWS Console → EC2 → Key Pairs**

---

# Step 9 — Configure Security Group

## 📍 Where I worked

**AWS Console → EC2 → Security Groups**

I configured inbound rules to allow the required traffic.

### SSH

```text
Type: SSH
Protocol: TCP
Port: 22
Source: My IP
```

SSH is required to connect to the Ubuntu server.

### HTTP

```text
Type: HTTP
Protocol: TCP
Port: 80
Source: Anywhere
```

HTTP is required so users can access the website through a browser.

---

# Step 10 — Connect to EC2 Using SSH

## 📍 Where I worked

**Windows CMD**

I opened Command Prompt.

I moved to the Downloads folder where the `.pem` key was saved:

```cmd
cd %USERPROFILE%\Downloads
```

I checked the key:

```cmd
dir *.pem
```

Then I connected to the Ubuntu EC2 server:

```cmd
ssh -i "" ubuntu@
```

For example:

```cmd
ssh -i "" ubuntu@
```

When SSH asked:

```text
Are you sure you want to continue connecting?
```

I entered:

```text
yes
```

After successful authentication, I received an Ubuntu terminal prompt similar to:

```text
ubuntu@ip xxx-xx-xx-xx:~$
```

This confirmed that I was connected to the EC2 Linux server.

---

# Step 11 — Update Ubuntu

## 📍 Where I worked

**SSH Terminal connected to AWS EC2**

I updated the Ubuntu package information:

```bash
sudo apt update
```

Then I upgraded installed packages:

```bash
sudo apt upgrade -y
```

---

# Step 12 — Install Apache Web Server

## 📍 Where I worked

**AWS EC2 SSH Terminal**

I installed Apache:

```bash
sudo apt install apache2 -y
```

Then I checked the Apache service:

```bash
sudo systemctl status apache2
```

The service showed:

```text
Active: active (running)
```

This confirmed that Apache was running successfully.

---

# Step 13 — Test Apache Locally

## 📍 Where I worked

**AWS EC2 SSH Terminal**

I tested Apache from inside the server:

```bash
curl http://localhost
```

Apache returned HTML content, confirming that the web server was working.

---

# Step 14 — Test Apache From the Internet

## 📍 Where I worked

**Windows Web Browser**

I opened the EC2 public IP address:

```text
http://<>
```

The Apache default page appeared.

This confirmed that:

```text
Internet
   ↓
AWS EC2
   ↓
Security Group
   ↓
Port 80
   ↓
Apache
```

was working correctly.

---

# Step 15 — Download GitHub Repository to EC2

## 📍 Where I worked

**AWS EC2 SSH Terminal**

I moved to the temporary directory:

```bash
cd /tmp
```

I cloned my GitHub repository:

```bash
git clone https://github.com/Tejaskondhalkar-2003/cloud-web-app-deployment.git
```

I checked the application files:

```bash
ls /tmp/cloud-web-app-deployment/app
```

The output contained:

```text
index.html
script.js
style.css
```

This confirmed that the application was successfully downloaded to the EC2 server.

---

# Step 16 — Deploy Application to Apache

## 📍 Where I worked

**AWS EC2 SSH Terminal**

Apache serves website files from:

```text
/var/www/html/
```

I copied my application files into the Apache web directory:

```bash
sudo cp /tmp/cloud-web-app-deployment/app/* /var/www/html/
```

I restarted Apache:

```bash
sudo systemctl restart apache2
```

---

# Step 17 — Test the Deployed Application

## 📍 Where I worked

**Windows Web Browser**

I opened:

```text
http://<>
```

The Apache default page was replaced by my own web application.

The deployed website displayed:

```text
Cloud Web App

Linux • Networking • Cloud Computing

Welcome to My Cloud Project
```

I also tested the **Test Application** button.

The JavaScript displayed:

```text
Application is working successfully!
```

This confirmed that the HTML, CSS and JavaScript were successfully deployed.

---

# 🔄 Complete Deployment Process

The complete process can be summarized as:

```text
1. Create Web Application
        ↓
2. Test in VS Code
        ↓
3. Initialize Git
        ↓
4. Commit Files
        ↓
5. Push to GitHub
        ↓
6. Create AWS EC2 Instance
        ↓
7. Configure Security Group
        ↓
8. Connect using SSH
        ↓
9. Update Ubuntu
        ↓
10. Install Apache
        ↓
11. Test Apache
        ↓
12. Clone GitHub Repository
        ↓
13. Copy Application to /var/www/html
        ↓
14. Restart Apache
        ↓
15. Open Public IP
        ↓
16. Test Live Application
```

---

# 🧰 Important Commands Used

## Git Commands

```bash
git init
git status
git add .
git commit -m "Add initial cloud web application"
git branch -M main
git remote add origin <GITHUB_REPOSITORY_URL>
git push -u origin main
```

## Linux / AWS Commands

```bash
sudo apt update
sudo apt upgrade -y
sudo apt install apache2 -y
sudo systemctl status apache2
sudo systemctl restart apache2
curl http://localhost
cd /tmp
git clone <GITHUB_REPOSITORY_URL>
ls /tmp/cloud-web-app-deployment/app
sudo cp /tmp/cloud-web-app-deployment/app/* /var/www/html/
```

## SSH Command

```bash
ssh -i "" ubuntu@<>
```

---

# 🔐 Security Considerations

The following security practices were followed:

* SSH access was restricted to my IP address.
* HTTP traffic was allowed through port 80.
* The private `.pem` key was not uploaded to GitHub.
* AWS credentials were not stored inside the project.
* Sensitive AWS information should not be included in screenshots or public documentation.

---

# 📚 What I Learned

Through this project, I learned how to:

* Build a basic web application.
* Use HTML, CSS and JavaScript.
* Use Git and GitHub for version control.
* Create and configure an AWS EC2 instance.
* Work with Ubuntu Linux.
* Connect to a cloud server using SSH.
* Configure AWS Security Groups.
* Install and manage Apache.
* Deploy a website on a Linux server.
* Clone a GitHub repository on an EC2 server.
* Serve web files using Apache.
* Test a live cloud-hosted application.

---

# 🚀 Project Result

The web application was successfully deployed on an **AWS EC2 Ubuntu server** using **Apache Web Server**.

The final architecture was:

```text
GitHub Repository
       ↓
AWS EC2 Ubuntu Server
       ↓
Apache Web Server
       ↓
HTML + CSS + JavaScript
       ↓
Live Web Application
```

---

# 👤 Author

**Tejas Kondhalkar**

Electronics & Telecommunication Engineering Graduate

Interests:

* Networking
* Cloud Computing
* Linux
* Cybersecurity
* AWS
* IT Infrastructure

GitHub:

https://github.com/Tejaskondhalkar-2003  








# Docker & Containerization

## Overview

This module demonstrates how to containerize a web application using Docker and Docker Compose.

### Technologies Used

* Docker Desktop
* Docker
* Dockerfile
* Docker Compose
* Nginx
* Git
* GitHub

---

# Step 1 — Verify Docker Installation

### Command

```bash
docker --version
```

### What it does

Displays the installed Docker version and confirms that Docker is available from the command line.

### Result

Docker was successfully installed and verified.

---

# Step 2 — Test Docker Installation

### Command

```bash
docker run hello-world
```

### What it does

Downloads the `hello-world` Docker image if it is not available locally, creates a container from that image, and runs it.

This is a basic test to confirm that Docker can:

1. Download an image
2. Create a container
3. Start the container
4. Run an application inside the container

### Result

The Docker installation successfully displayed the `Hello from Docker!` message.

---

# Step 3 — Check Docker Images

### Command

```bash
docker images
```

### What it does

Lists the Docker images currently available on the local computer.

### Result

The `hello-world` image was visible in the local image list.

---

# Step 4 — Check Docker Containers

### Command

```bash
docker ps -a
```

### What it does

Displays all Docker containers, including containers that are currently stopped.

### Result

The containers created while testing `hello-world` were displayed.

---

# Step 5 — Run an Nginx Container

### Command

```bash
docker run -d -p 8080:80 --name my-web-server nginx
```

### What it does

This command creates and starts an Nginx container.

Explanation:

* `docker run` → Creates and starts a container
* `-d` → Runs the container in detached/background mode
* `-p 8080:80` → Maps local port `8080` to container port `80`
* `--name my-web-server` → Gives the container a custom name
* `nginx` → Uses the Nginx Docker image

### Result

The Nginx web server was successfully accessed through:

```text
http://localhost:8080
```

---

# Step 6 — Create the Dockerfile

A file named `Dockerfile` was created in the project root.

### Dockerfile

```dockerfile
FROM nginx:alpine

COPY app/ /usr/share/nginx/html/

EXPOSE 80
```

### What each line does

#### `FROM nginx:alpine`

Uses the lightweight Nginx Alpine image as the base image.

#### `COPY app/ /usr/share/nginx/html/`

Copies the web application files from the local `app` directory into the directory where Nginx serves web content.

#### `EXPOSE 80`

Documents that the application inside the container uses port `80`.

---

# Step 7 — Build the Custom Docker Image

### Command

```bash
docker build -t cloud-web-app .
```

### What it does

Builds a Docker image using the Dockerfile in the current directory.

Explanation:

* `docker build` → Builds a Docker image
* `-t cloud-web-app` → Gives the image the name `cloud-web-app`
* `.` → Uses the current directory as the build context

### Result

A custom Docker image named:

```text
cloud-web-app
```

was successfully created.

---

# Step 8 — Check the Custom Image

### Command

```bash
docker images
```

### What it does

Displays all locally available Docker images.

### Result

The custom image was visible:

```text
cloud-web-app
```

---

# Step 9 — Run the Custom Web Application Container

### Command

```bash
docker run -d -p 8081:80 --name cloud-web-container cloud-web-app
```

### What it does

Creates and starts a container using the custom `cloud-web-app` image.

Explanation:

* `-d` → Runs in the background
* `-p 8081:80` → Maps local port `8081` to container port `80`
* `--name cloud-web-container` → Gives the container a name
* `cloud-web-app` → Uses the custom image

### Result

The web application was successfully accessed through:

```text
http://localhost:8081
```

---

# Step 10 — Check Running Containers

### Command

```bash
docker ps
```

### What it does

Displays currently running Docker containers.

### Result

The custom web container was shown as running.

---

# Step 11 — Inspect the Container

### Command

```bash
docker inspect cloud-web-container
```

### What it does

Displays detailed information about the container.

It can provide information about:

* Container configuration
* Network configuration
* Port mappings
* Mounts
* Environment
* Container state

### Result

The configuration of the custom web container was inspected successfully.

---

# Step 12 — Check Docker Networks

### Command

```bash
docker network ls
```

### What it does

Lists the Docker networks available on the system.

Docker networks allow containers to communicate with each other and with external networks.

### Result

The available Docker networks were displayed.

---

# Step 13 — Test Environment Variables

### Command

```bash
docker run --rm -e APP_ENV=development nginx:alpine env
```

### What it does

Runs a temporary Nginx container and passes an environment variable into it.

Explanation:

* `--rm` → Automatically removes the container after it exits
* `-e APP_ENV=development` → Creates the environment variable
* `nginx:alpine` → Uses the Nginx Alpine image
* `env` → Displays environment variables inside the container

### Result

The following variable was displayed:

```text
APP_ENV=development
```

This confirmed that environment variables can be passed into containers.

---

# Step 14 — Create a Docker Volume

### Command

```bash
docker volume create cloud-web-data
```

### What it does

Creates a Docker-managed volume named `cloud-web-data`.

Docker volumes can be used to store persistent data separately from the container's writable layer.

### Result

The volume was successfully created.

---

# Step 15 — Check Docker Volumes

### Command

```bash
docker volume ls
```

### What it does

Lists Docker volumes available on the system.

### Result

The following volume was displayed:

```text
cloud-web-data
```

---

# Step 16 — Create Docker Compose Configuration

A file named:

```text
docker-compose.yml
```

was created in the project root.

### Configuration

```yaml
services:
  web:
    build: .
    container_name: cloud-web-compose
    ports:
      - "8082:80"
    environment:
      APP_ENV: production
```

### What it does

Docker Compose defines how the web application should be built and run.

Explanation:

#### `build: .`

Builds the Docker image using the Dockerfile in the current directory.

#### `container_name: cloud-web-compose`

Sets the container name.

#### `ports`

Maps:

```text
localhost:8082 → container:80
```

#### `environment`

Sets:

```text
APP_ENV=production
```

inside the container.

---

# Step 17 — Validate Docker Compose Configuration

### Command

```bash
docker compose config
```

### What it does

Validates and displays the Docker Compose configuration after Docker processes the file.

This helps identify configuration or YAML errors before starting the application.

### Result

The Compose configuration was successfully validated.

---

# Step 18 — Start the Application Using Docker Compose

### Command

```bash
docker compose up -d
```

### What it does

Builds the required image and starts the services defined in `docker-compose.yml`.

Explanation:

* `docker compose` → Uses Docker Compose
* `up` → Creates and starts the services
* `-d` → Runs them in the background

### Result

The `cloud-web-compose` container was successfully started.

---

# Step 19 — Check Docker Compose Services

### Command

```bash
docker compose ps
```

### What it does

Displays the status of the services managed by Docker Compose.

### Result

The web service was shown as running with port mapping:

```text
8082 → 80
```

---

# Step 20 — Test the Docker Compose Web Application

The application was opened in a web browser:

```text
http://localhost:8082
```

### Result

The web application loaded successfully through Docker Compose.

---

# Step 21 — Stop Docker Compose Services

### Command

```bash
docker compose down
```

### What it does

Stops and removes the containers and network created by Docker Compose.

It is useful for cleaning up the running Compose environment.

---

# Step 22 — Start Docker Compose Again

### Command

```bash
docker compose up -d
```

### What it does

Creates/starts the Compose services again in detached mode.

### Result

The application started successfully again.

This verified that the application can be stopped and recreated using Docker Compose.

---

# Step 23 — Check Git Status

After completing the Docker work, Git was used to check the project status.

### Command

```bash
git status
```

### What it does

Shows:

* Current Git branch
* Changes
* Untracked files
* Staged files
* Whether the working tree is clean

Docker-related files included:

```text
Dockerfile
docker-compose.yml
.dockerignore
```

---

# Step 24 — Add Docker Files to Git

### Command

```bash
git add Dockerfile docker-compose.yml .dockerignore
```

### What it does

Stages the Docker-related files so they can be included in the next Git commit.

---

# Step 25 — Commit Docker Changes

### Command

```bash
git commit -m "Add Docker containerization"
```

### What it does

Creates a Git commit containing the staged Docker-related changes.

The commit provides a record of when the Docker implementation was added.

---

# Step 26 — Synchronize with GitHub

Before pushing, the local repository was synchronized with the existing GitHub repository.

### Command

```bash
git pull origin main --allow-unrelated-histories
```

### What it does

Downloads changes from the GitHub `main` branch and merges them into the local `main` branch.

The `--allow-unrelated-histories` option allows Git to merge histories that were not previously connected.

### Result

The existing GitHub files were successfully merged with the local Docker project.

---

# Step 27 — Check Git Status Again

### Command

```bash
git status
```

### Result

The repository showed:

```text
Your branch is ahead of 'origin/main' by 2 commits.
nothing to commit, working tree clean
```

This confirmed that the local Docker changes were committed and ready to be pushed.

---

# Step 28 — Push Docker Work to GitHub

### Command

```bash
git push origin main
```

### What it does

Uploads the local commits from the `main` branch to the GitHub repository.

### Result

The Docker implementation was successfully pushed to GitHub.

---

# Final Project Structure

```text
cloud-web-app-deployment/
│
├── app/
│   ├── index.html
│   ├── script.js
│   └── style.css
│
├── Dockerfile
├── docker-compose.yml
├── .dockerignore
├── screenshots/
└── README.md
```

# Docker Workflow

```text
Web Application
      ↓
Dockerfile
      ↓
Docker Image
      ↓
Docker Container
      ↓
Port Mapping
      ↓
Docker Networking
      ↓
Environment Variables
      ↓
Docker Volume
      ↓
Docker Compose
      ↓
Running Web Application
```

# Key Learning Outcomes

After completing this module, I practiced:

* Docker installation and verification
* Docker images
* Docker containers
* Nginx containers
* Dockerfiles
* Building custom images
* Port mapping
* Container inspection
* Docker networking
* Environment variables
* Docker volumes
* Docker Compose
* Container lifecycle management
* Git version control
* Pushing Docker projects to GitHub

# Result

The web application was successfully containerized using Docker and Docker Compose and tested locally through different container configurations.

## Repository

GitHub Repository:

https://github.com/Tejaskondhalkar-2003/cloud-web-app-deployment









# Module 5 — DevOps CI/CD Pipeline

## 1. Objective

Implement a Continuous Integration and Continuous Deployment (CI/CD) pipeline using GitHub Actions to validate a web application, build its Docker image, and deploy updates to an AWS EC2 instance through AWS Systems Manager (SSM).

## 2. Tools and Technologies

- Git and GitHub
- GitHub Actions
- HTML, CSS, and JavaScript
- Docker and Docker Compose
- AWS EC2
- AWS Systems Manager (SSM)
- AWS IAM
- GitHub OIDC authentication

## 3. Project Workflow

1. Make changes to the application or project files.
2. Push the changes to the `main` branch on GitHub.
3. GitHub Actions starts the CI workflow.
4. The workflow checks the required application files.
5. JavaScript syntax and basic HTML structure are validated.
6. Docker builds the application image.
7. After successful testing, the deployment job authenticates with AWS using OIDC.
8. GitHub Actions sends deployment commands to EC2 through SSM.
9. EC2 pulls the latest code and rebuilds the application using Docker Compose.
10. The deployment result is checked in GitHub Actions.

## 4. Workflow File

Location:

`.github/workflows/ci-cd.yml`

This file defines the automated build, test, and deployment jobs.

## 5. CI — Continuous Integration

The CI job performs the following checks:

- Checks out the repository.
- Configures Node.js.
- Verifies that required HTML, CSS, and JavaScript files exist.
- Checks JavaScript syntax.
- Validates essential HTML tags.
- Builds the Docker image.

These checks help identify application and build errors before deployment.

## 6. CD — Continuous Deployment

The deployment job runs after the build-and-test job succeeds and is configured for pushes to `main`.

The deployment process:

1. Configures AWS credentials using GitHub OIDC.
2. Verifies the AWS identity.
3. Sends a command to the EC2 instance using AWS Systems Manager.
4. Pulls the latest repository changes.
5. Builds and starts the application using Docker Compose.
6. Checks the deployment command status and displays diagnostic output if it fails.

## 7. Important Docker Commands

### Check running containers

```bash
docker ps
```

### Check all containers

```bash
docker ps -a
```

### Validate Docker Compose configuration

```bash
docker compose config
```

### Build and start the application

```bash
docker compose up -d --build
```

### Check Compose service status

```bash
docker compose ps
```

### View application logs

```bash
docker compose logs --tail=50
```

### Test Nginx configuration

```bash
docker exec cloud-web-compose nginx -t
```

### Test the local application endpoint

```bash
curl -I http://localhost:8082
```

## 8. AWS Configuration

The deployment uses:

- An Ubuntu EC2 instance.
- Docker and Docker Compose installed on the instance.
- An IAM instance role that allows Systems Manager access.
- An IAM deployment role assumed by GitHub Actions through OIDC.
- The GitHub repository secret `AWS_ROLE_ARN`.
- A security group that permits the required application traffic.

Sensitive credentials and private keys must never be committed to the repository.

## 9. How to Trigger the Pipeline

From the project directory on your computer, make a small change to a file.

Check the changes:

```bash
git status
```

Stage the change:

```bash
git add .
```

Commit the change:

```bash
git commit -m "Update CI/CD project"
```

Push the change:

```bash
git push origin main
```

Open the repository's **Actions** tab to monitor the workflow.

## 10. Verification and Results

The completed pipeline was verified through these checks:

- GitHub Actions build-and-test job succeeded.
- Docker image build succeeded.
- AWS authentication and SSM deployment job succeeded.
- The Docker container was running on EC2.
- Nginx configuration validation succeeded.
- A local HTTP request returned `200 OK`.
- The live application opened successfully in a browser.

## 11. Troubleshooting

| Issue | What to check |
|---|---|
| Workflow fails during testing | Review the build-and-test logs. |
| AWS authentication fails | Check the OIDC provider, IAM trust policy, and `AWS_ROLE_ARN` secret. |
| SSM command fails | Check the EC2 instance's SSM status, IAM permissions, and command output. |
| Git reports dubious ownership | Verify repository ownership and Git safe-directory configuration. |
| Docker container is not running | Inspect `docker ps -a` and the Compose logs. |
| Website does not open | Check the current EC2 public IP, security group, port mapping, and network configuration. |

## 12. Learning Outcomes

- Understanding CI/CD concepts.
- Automating application validation with GitHub Actions.
- Building Docker images in a CI workflow.
- Deploying applications to AWS EC2.
- Using AWS Systems Manager for remote deployment.
- Configuring GitHub OIDC authentication with AWS IAM.
- Troubleshooting deployment and connectivity issues.

## 13. Repository

GitHub repository:

https://github.com/Tejaskondhalkar-2003/cloud-web-app-deployment

The application uses the configured host port `8082`. Its public IP address can change, so the current endpoint should be checked in the AWS EC2 console.












---




# Module 6 — AWS Monitoring and Health Checks

## 1. Objective

The objective of this module is to monitor the health and performance of the Cloud Web App deployed on AWS EC2 using Amazon CloudWatch and a custom website health-check script.

This module helps identify EC2 status-check failures, monitor CPU utilization, and verify that the web application is responding to HTTP requests.

## 2. Tools and Technologies

- Amazon EC2
- Amazon CloudWatch
- CloudWatch Alarms
- Ubuntu Linux
- Docker and Docker Compose
- Nginx
- Bash scripting
- Cron scheduling
- GitHub Actions

## 3. Monitoring Architecture

```text
                 AWS EC2 Instance
                        |
             +----------+----------+
             |                     |
       CloudWatch Alarms      Website Health Check
             |                     |
       +-----+------+          Cron Scheduler
       |            |               |
   CPUUtilization  StatusCheckFailed |
       |            |               |
       +-----+------+          Health Check Log
             |
       Monitor EC2 Health
```

## 4. CloudWatch CPU Utilization Alarm

A CloudWatch alarm was created to monitor the CPU utilization of the EC2 instance.

### Configuration

| Setting | Value |
|---|---|
| Alarm name | `cloud-web-app-server-high-cpu` |
| Namespace | `AWS/EC2` |
| Metric | `CPUUtilization` |
| Statistic | Average |
| Period | 5 minutes |
| Threshold | Greater than 80 |
| Evaluation | 1 out of 1 datapoint |

### Purpose

The alarm monitors CPU usage and enters the alarm state when the configured threshold is exceeded.

This helps identify unusually high CPU utilization on the EC2 instance.

## 5. EC2 Status Check Alarm

A second CloudWatch alarm was configured to monitor EC2 instance health.

### Configuration

| Setting | Value |
|---|---|
| Alarm name | `cloud-web-app-server-status-check-failed` |
| Namespace | `AWS/EC2` |
| Metric | `StatusCheckFailed` |
| Statistic | Maximum |
| Period | 5 minutes |
| Threshold | Greater than or equal to 1 |
| Evaluation | 1 out of 1 datapoint |

### Purpose

The `StatusCheckFailed` metric monitors EC2 system and instance status checks.

A value of `1` indicates a failed status check. The alarm helps detect infrastructure or instance-level problems.

## 6. Website Health Check Script

A Bash script was created on the EC2 instance to check whether the local Nginx web application responds to HTTP requests.

### Script location

```text
/usr/local/bin/website-health-check.sh
```

### Script

```bash
#!/bin/bash

if curl -fsS --max-time 10 http://localhost/ > /dev/null; then
    echo "$(date -Is) Website UP - HTTP check passed"
else
    echo "$(date -Is) Website DOWN - HTTP check failed"
    exit 1
fi
```

### How it works

1. Sends an HTTP request to the local website.
2. Waits for a response, with a maximum request time of 10 seconds.
3. Displays a success message when the HTTP request succeeds.
4. Displays a failure message and returns a non-zero exit code if the request fails.

### Make the script executable

```bash
sudo chmod +x /usr/local/bin/website-health-check.sh
```

### Run the health check manually

```bash
sudo /usr/local/bin/website-health-check.sh
```

### Example successful output

```text
2026-10-28T06:38:02+00:00 Website UP - HTTP check passed
```

The successful result confirms that the local web application responded to the HTTP check at the time of testing.

## 7. Schedule Automatic Health Checks

Cron was configured to execute the health-check script every minute and append the results to a log file.

### Cron configuration

```cron
* * * * * /usr/local/bin/website-health-check.sh >> /var/log/website-health.log 2>&1
```

### Log file

```text
/var/log/website-health.log
```

### Verify the scheduled job

```bash
sudo crontab -l
```

### View recent health-check results

```bash
sudo tail -n 10 /var/log/website-health.log
```

The log records successful checks and any HTTP check failures.

**Note:** This script checks the website locally on the EC2 instance. It does not independently verify public internet accessibility or send notifications. CloudWatch alarm notifications require an appropriate notification action to be configured.

## 8. Monitoring Verification

The monitoring configuration was checked using the AWS Management Console and the EC2 terminal.

Verification included:

- CloudWatch CPU utilization alarm created.
- CloudWatch EC2 status-check alarm created.
- Website health-check script executed successfully.
- HTTP check returned `Website UP - HTTP check passed`.
- Cron schedule configured for automatic execution.
- Health-check output written to the log file.

## 9. Important Commands

### Run the health check

```bash
sudo /usr/local/bin/website-health-check.sh
```

### Check the cron schedule

```bash
sudo crontab -l
```

### View health-check logs

```bash
sudo tail -n 10 /var/log/website-health.log
```

### Check Docker containers

```bash
sudo docker ps
```

### Check application logs

```bash
sudo docker compose logs --tail=50
```

## 10. Learning Outcomes

Through this module, I practiced:

- Creating Amazon CloudWatch alarms.
- Monitoring EC2 CPU utilization.
- Monitoring EC2 system and instance status checks.
- Writing a Bash health-check script.
- Testing HTTP responses using `curl`.
- Scheduling recurring tasks using cron.
- Recording monitoring results in a log file.
- Understanding the difference between application health checks and infrastructure monitoring.

## 11. Result

Basic monitoring was configured for the Cloud Web App deployed on AWS EC2.

CloudWatch alarms were created for CPU utilization and EC2 status-check failures. A Bash script was also created to test the local website, with cron scheduling and log output configured for recurring checks.



These components provide a foundation for monitoring the health and availability of the deployed application.




