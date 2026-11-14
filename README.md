# Cloud Computing & DevOps Internship — Codomax Digital Solutions

This repository documents the practical work and learning completed during the **Codomax Virtual Internship 2026 — Cloud Computing & DevOps** track.

**Internship:** Cloud Computing & DevOps  
**Intern:** Tejas Kondhalkar  
**Repository:** https://github.com/Tejaskondhalkar-2003/cloud-web-app-deployment

The README is organized according to the six modules in the Codomax internship tracker. Each module has its own objective, steps, commands, verification notes, and learning outcomes.

---

# Module 01 — Cloud Computing Foundations
**Duration:** Day 1–Day 5

## 1. Objective
Understand cloud computing fundamentals, service models, deployment models, regions, availability zones, virtualization, core cloud services, security, scalability, elasticity, and pricing.

## 2. Step 1 — Understand Cloud Computing
Cloud computing provides on-demand access to computing resources—such as servers, storage, databases, networking, and software—over a network. Resources can be provisioned when required and scaled according to demand.

## 3. Step 2 — Learn Cloud Service Models

| Model | Meaning | Example use |
|---|---|---|
| IaaS | Infrastructure as a Service; virtual machines, networks, and storage are managed by the provider while the user manages the operating system and applications | AWS EC2 |
| PaaS | Platform as a Service; a managed platform for building and running applications | AWS Elastic Beanstalk |
| SaaS | Software as a Service; a complete application delivered over the internet | Web-based email and collaboration software |

## 4. Step 3 — Learn Cloud Deployment Models
- **Public cloud:** Infrastructure offered to multiple customers by a cloud provider.
- **Private cloud:** Cloud infrastructure dedicated to one organization.
- **Hybrid cloud:** A combination of private infrastructure and public cloud services.

## 5. Step 4 — Understand Regions and Availability Zones
- A **Region** is a separate geographic area where a cloud provider operates.
- An **Availability Zone (AZ)** is an isolated location within a Region.
- Deploying across multiple Availability Zones can improve application availability and resilience.

## 6. Step 5 — Explore Virtualization and Core Cloud Concepts
- **Virtualization:** Allows multiple virtual machines to run on physical infrastructure.
- **Compute:** Processing resources used to run applications.
- **Storage:** Services used to store files, objects, and application data.
- **Networking:** Virtual networks, IP addresses, routing, and security controls.
- **IAM:** Identity and Access Management for controlling access to resources.
- **Scalability:** Increasing or decreasing resources to meet demand.
- **Elasticity:** Automatically or dynamically adjusting resources as demand changes.
- **Pricing:** Understanding usage-based billing, free-tier limits, and resource cleanup.

## 7. Step 6 — Explore AWS Core Services
The AWS console and services relevant to the internship project include:

| Service | Purpose |
|---|---|
| Amazon EC2 | Virtual servers for hosting applications |
| Amazon S3 | Object storage |
| Amazon VPC | Isolated virtual networking |
| AWS IAM | Identity, roles, and permissions |
| Amazon CloudWatch | Metrics, logs, and alarms |
| AWS Systems Manager | Managing and running commands on supported instances |

These services are explored further and applied in the practical modules below.

## 8. Step 7 — Cloud Services Exploration Diagram

```text
                 Cloud Platform (AWS)
                         |
       +-----------------+-----------------+
       |                 |                 |
     Compute           Storage          Networking
       |                 |                 |
      EC2                S3                VPC
       |                                   |
       +-----------------+-----------------+
                         |
                    Security
                         |
                        IAM
                         |
                    Monitoring
                         |
                    CloudWatch
```

## 9. Learning Outcomes
- Understood IaaS, PaaS, and SaaS.
- Learned public, private, and hybrid cloud models.
- Understood Regions and Availability Zones.
- Explored virtualization and common cloud capabilities.
- Identified the purpose of key AWS services used in later modules.

---

# Module 02 — Linux, Networking & Cloud Infrastructure
**Duration:** Day 6–Day 10

## 1. Objective
Practice Linux server administration, SSH access, IP and port concepts, DNS and firewall fundamentals, and secure cloud server deployment.

## 2. Step 1 — Create an AWS EC2 Linux Server
**Where:** AWS Management Console → EC2

The project server was created with the following configuration:

| Setting | Configuration |
|---|---|
| Instance name | `cloud-web-app-server` |
| Operating system | Ubuntu Server 24.04 LTS |
| Instance type | `t3.micro` |
| Architecture | 64-bit |
| Region | US East (N. Virginia) |
| Availability Zone | `us-east-1c` |

## 3. Step 2 — Create an SSH Key Pair
**Where:** AWS Console → EC2 → Key Pairs

An EC2 key pair was created for secure SSH authentication. The private `.pem` key was kept outside the public GitHub repository.

## 4. Step 3 — Configure the Security Group
**Where:** AWS Console → EC2 → Security Groups

The inbound rules used for the web server were:

| Type | Protocol | Port | Source / purpose |
|---|---|---:|---|
| SSH | TCP | 22 | Restricted to my IP for administration |
| HTTP | TCP | 80 | Public web access |

Only required inbound access should be allowed. SSH should not be exposed to all IP addresses.

## 5. Step 4 — Connect to Ubuntu Using SSH
**Where:** Windows CMD / PowerShell

Move to the folder containing the downloaded key:

```cmd
cd %USERPROFILE%\Downloads
dir *.pem
```

Connect using the actual key filename and current EC2 public IPv4 address:

```bash
ssh -i "YOUR_KEY_FILE.pem" ubuntu@YOUR_EC2_PUBLIC_IP
```

Replace both placeholders with the correct local key filename and EC2 address. Never publish the private key.

When prompted to trust the host, verify the host and enter `yes` to continue.

## 6. Step 5 — Update Ubuntu
**Where:** EC2 SSH terminal

```bash
sudo apt update
sudo apt upgrade -y
```

These commands refresh package information and install available updates.

## 7. Step 6 — Install and Check Apache
```bash
sudo apt install apache2 -y
sudo systemctl status apache2
```

The Apache service was checked for an `active (running)` status.

## 8. Step 7 — Test Server Connectivity
From the EC2 terminal:

```bash
curl http://localhost
```

From a browser, open the current EC2 public IPv4 address using HTTP:

```text
http://YOUR_EC2_PUBLIC_IP
```

A successful response confirms that the web server can be reached through the configured network path and security-group rule.

## 9. Step 8 — Linux and Networking Commands Practiced

```bash
pwd
ls -la
cd /path/to/directory
whoami
ip addr
ip route
ss -tuln
ps aux
sudo systemctl status apache2
sudo systemctl restart apache2
curl -I http://localhost
```

The commands above are useful for checking the current directory, files, user, network interfaces, routes, listening ports, processes, services, and HTTP responses.

## 10. Security Notes
- Keep SSH access restricted to a trusted source IP.
- Keep private SSH keys outside GitHub.
- Allow only the ports required by the application.
- Do not commit AWS credentials or other secrets.
- Check the current public IP in the EC2 console before connecting.

## 11. Learning Outcomes
- Practiced Linux package and service management.
- Created an Ubuntu EC2 instance.
- Used SSH to access a cloud Linux server.
- Configured inbound network access with a security group.
- Practiced basic IP, route, port, process, and connectivity checks.

---

# Module 03 — Cloud Services & Web App Deployment
**Duration:** Day 11–Day 15

## 1. Objective
Explore cloud compute, storage, networking, IAM, and monitoring services, then develop and deploy a web application to cloud compute infrastructure.

## 2. Step 1 — Develop the Web Application Locally

**Where:** Windows PC → Visual Studio Code

I created a simple responsive website using HTML, CSS, and JavaScript.

### Project files

```text
app/
├── index.html
├── style.css
└── script.js
```

- `index.html` defines the page structure and content.
- `style.css` controls the layout, colors, cards, spacing, and responsive design.
- `script.js` adds interaction to the Test Application button.

The button displays the message:

```text
Application is working successfully!
```

## 3. Step 2 — Test the Application Locally

Open `app/index.html` in a browser and verify:

1. The page loads without errors.
2. CSS styling and layout display correctly.
3. The application content and cards are visible.
4. The JavaScript button displays the success message.

## 4. Step 3 — Initialize Git and Track the Project

**Where:** Windows PowerShell / CMD

Move to the project directory. Example:

```powershell
cd "C:\Users\Tejas\Documents\Cloud-DevOps\cloud-web-app-deployment"
git init
git status
```

Configure Git identity if it has not already been configured:

```bash
git config --global user.name "Tejas Kondhalkar"
git config --global user.email "YOUR_GIT_EMAIL"
```

Stage and commit the application:

```bash
git add .
git commit -m "Add cloud web application"
```

## 5. Step 4 — Push the Application to GitHub

Create the repository on GitHub, then connect the local project:

```bash
git remote add origin https://github.com/Tejaskondhalkar-2003/cloud-web-app-deployment.git
git branch -M main
git push -u origin main
```

If the remote named `origin` already exists, check it with `git remote -v` rather than adding it again.

## 6. Step 5 — Clone the Repository on EC2

**Where:** Ubuntu EC2 SSH terminal

```bash
cd /tmp
git clone https://github.com/Tejaskondhalkar-2003/cloud-web-app-deployment.git
ls /tmp/cloud-web-app-deployment/app
```

Confirm that `index.html`, `style.css`, and `script.js` are present.

## 7. Step 6 — Deploy the Website to the EC2 Web Server

The initial deployment exercise used Apache on Ubuntu. Apache serves website files from `/var/www/html/`.

```bash
sudo cp /tmp/cloud-web-app-deployment/app/* /var/www/html/
sudo systemctl restart apache2
sudo systemctl status apache2
```

## 8. Step 7 — Verify the Live Application

From the EC2 terminal:

```bash
curl -I http://localhost
```

From a browser, open the current EC2 public IPv4 address:

```text
http://YOUR_EC2_PUBLIC_IP
```

Verify that the web page, styling, and JavaScript interaction work.

## 9. Step 8 — Understand the AWS Services Used

| AWS service | Role in this project |
|---|---|
| EC2 | Runs the Ubuntu cloud server and web application |
| VPC | Provides the virtual network for cloud resources |
| Security Group | Controls inbound and outbound instance traffic |
| IAM | Controls identities, roles, and permissions |
| S3 | Object-storage service explored as part of AWS fundamentals |
| CloudWatch | Monitors EC2 metrics and alarms in Module 06 |

**Deployment clarification:** The Apache commands above document the initial web-server deployment exercise. The current capstone deployment uses Nginx inside Docker and Docker Compose, as documented in Modules 04–06. This project README does not claim a managed database integration is complete.

## 10. Learning Outcomes

- Created and tested an HTML, CSS, and JavaScript web application.
- Used Git and GitHub to track and store source code.
- Cloned the project onto an Ubuntu EC2 instance.
- Deployed the website to a Linux web-server directory.
- Tested local and public HTTP connectivity.
- Identified how AWS compute, networking, security, storage, and monitoring services fit into a deployment.

## 3. Step 2 — Download the Project to the EC2 Server
**Where:** EC2 SSH terminal

The GitHub repository was cloned to the server:

```bash
cd /tmp
git clone https://github.com/Tejaskondhalkar-2003/cloud-web-app-deployment.git
ls /tmp/cloud-web-app-deployment/app
```

The application directory contains the website files, including `index.html`, `style.css`, and `script.js`.

## 4. Step 3 — Deploy the Application to the Web Server
The initial EC2 deployment exercise used Apache's default web directory:

```bash
sudo cp /tmp/cloud-web-app-deployment/app/* /var/www/html/
sudo systemctl restart apache2
```

## 5. Step 4 — Verify the Deployed Website
Open the current EC2 public IPv4 address in a browser:

```text
http://YOUR_EC2_PUBLIC_IP
```

The website was checked for correct HTML content, CSS styling, and JavaScript button behavior. The application displayed a successful test message when the button was clicked.

## 6. Step 5 — Deployment Flow

```text
Local HTML / CSS / JavaScript
             |
             v
        Git & GitHub
             |
             v
       AWS EC2 Ubuntu
             |
             v
     Web Server (initially Apache)
             |
             v
      Live Web Application
```

## 7. Step 6 — Cloud Services Used in the Project
- **EC2:** Hosted the Ubuntu server and application.
- **VPC and Security Groups:** Provided network isolation and inbound traffic controls.
- **IAM:** Provided roles and permissions for AWS service access in the later deployment workflow.
- **CloudWatch:** Used for infrastructure monitoring in Module 06.
- **S3:** Explored as an AWS object-storage service.

**Implementation scope:** The verified live application described in the capstone section is served by Nginx in Docker on EC2. The Apache steps above document the initial server-deployment exercise. A managed database integration is not claimed as complete in this README.

## 8. Learning Outcomes
- Developed a basic web application.
- Used GitHub as the source repository.
- Deployed web files to an Ubuntu EC2 server.
- Tested the website through a public HTTP endpoint.
- Explored the role of AWS compute, storage, networking, IAM, and monitoring services.

---

# Module 04 — Docker & Containerization
**Duration:** Day 16–Day 20

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

---

# Module 05 — DevOps, CI/CD & Monitoring

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
curl -I http://localhost
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

The production Docker Compose configuration maps host port `80` to container port `80`. The EC2 public IPv4 address can change after a stop/start unless an Elastic IP is configured. Check the AWS EC2 console for the current address before sharing the live URL.












---

---

# Module 06 — Cloud & DevOps Capstone Project
**Duration:** Day 26–Day 30

## 1. Objective
Build, containerize, automate, deploy, and monitor a real web application by integrating cloud infrastructure, Git, Docker, CI/CD, monitoring, and managed database/authentication services where implemented.

## 2. Capstone Architecture

The verified deployment architecture for the current web application is:

```text
Developer
   |
   v
GitHub Repository
   |
   v
GitHub Actions
   |
   +---- CI: validate files and build Docker image
   |
   +---- CD: AWS OIDC authentication
                 |
                 v
          AWS Systems Manager
                 |
                 v
          AWS EC2 (Ubuntu)
                 |
                 v
          Docker Compose
                 |
                 v
          Nginx Container
                 |
                 v
          Live Web Application
                 |
                 v
        CloudWatch + Health Check
```

## 3. Step 1 — Review the Application and Source Repository
- Confirm the application source files are present in the `app/` directory.
- Confirm the Dockerfile and Compose configuration are in the repository root.
- Keep the GitHub repository updated with the completed project files.

Repository: https://github.com/Tejaskondhalkar-2003/cloud-web-app-deployment

## 4. Step 2 — Review the Container Configuration

### Dockerfile

```dockerfile
FROM nginx:alpine
COPY app/ /usr/share/nginx/html/
EXPOSE 80
```

### Docker Compose

```yaml
services:
  web:
    build: .
    container_name: cloud-web-compose
    ports:
      - "80:80"
    environment:
      APP_ENV: production
```

The current production configuration maps host port 80 to container port 80.

## 5. Step 3 — Review Automated Deployment
The GitHub Actions workflow is stored at:

```text
.github/workflows/ci-cd.yml
```

The workflow validates the application, builds the Docker image, authenticates to AWS using GitHub OIDC, and sends deployment commands to EC2 through Systems Manager.

## 6. Step 4 — Review Monitoring and Health Checks
The project includes:
- A CloudWatch CPU utilization alarm.
- A CloudWatch EC2 status-check alarm.
- A Bash website health-check script.
- A cron schedule that runs the check every minute.
- A log file at `/var/log/website-health.log`.

The detailed configuration and commands are documented in the monitoring section below.

## 7. Step 5 — Managed Database and Authentication Integration
The Codomax capstone objectives include managed database/authentication integration. The README does not currently record a verified, working managed database connection or end-to-end authentication flow. Amazon Cognito setup was explored, but it should only be marked complete after the user pool/app client and application sign-in flow are tested successfully. No database integration is claimed here.

## 8. Step 6 — Verify the Live Deployment

| Item | Verified configuration at the time of checking |
|---|---|
| EC2 instance | `cloud-web-app-server` |
| Instance type | `t3.micro` |
| AWS Region | `us-east-1` (N. Virginia) |
| Container | `cloud-web-compose` |
| Web server | Nginx |
| Host/container port | `80:80` |
| Public URL at last verification | `http://54.90.156.63/` |
| HTTP response | `200 OK` |

The website was opened successfully during verification. The EC2 public IPv4 address may change after a stop/start unless an Elastic IP is configured. Check the EC2 console for the current address before sharing the live link. The site uses HTTP, not HTTPS.

## 9. Step 7 — Final Capstone Deliverables

| Deliverable | README / project location |
|---|---|
| GitHub repository | Project repository linked above |
| Live deployment | EC2 public URL; verify current IP before submission |
| Dockerfile | `Dockerfile` |
| Docker Compose | `docker-compose.yml` |
| CI/CD workflow | `.github/workflows/ci-cd.yml` |
| Monitoring and health checks | CloudWatch alarms, Bash script, cron, and log |
| Architecture diagram | Capstone architecture above |
| Managed database/auth | Not yet documented as verified; update only after successful testing |

## 10. Capstone Result
The web application was containerized with Docker and Docker Compose, deployed to AWS EC2, automated through GitHub Actions and AWS Systems Manager, and monitored using CloudWatch alarms and a scheduled website health check.

---

## Module 06 — Monitoring Implementation Details

### AWS Monitoring and Health Checks

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

#### Current Live Deployment

The completed application is deployed on an Ubuntu 24.04 EC2 instance and served by Nginx inside a Docker container managed with Docker Compose.

| Item | Current configuration |
|---|---|
| EC2 instance | `cloud-web-app-server` |
| Instance type | `t3.micro` |
| AWS Region | `us-east-1` (N. Virginia) |
| Container | `cloud-web-compose` |
| Web server | Nginx |
| Host/container port | `80:80` |
| Application URL at the time of verification | `http://54.90.156.63/` |

The live URL was opened successfully and returned an HTTP `200 OK` response during verification. The public IP is automatically assigned and may change after an EC2 stop/start; verify the current IP in the EC2 console before sharing it. The site currently uses HTTP, not HTTPS.


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

---

# Project Repository and Final Notes

**GitHub:** https://github.com/Tejaskondhalkar-2003/cloud-web-app-deployment

**Author:** Tejas Kondhalkar  
Electronics & Telecommunication Engineering Graduate

**Areas practiced:** Cloud Computing, AWS, Linux, Networking, Docker, GitHub Actions, CI/CD, and monitoring.

**Security reminder:** Do not commit private keys, passwords, access tokens, or AWS credentials. Verify the current EC2 public IP before sharing the live website URL.
