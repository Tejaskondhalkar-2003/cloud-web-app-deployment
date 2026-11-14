# Cloud Computing & DevOps Internship — Codomax Digital Solutions

This repository documents the practical work, exercises, and learning completed during the **Codomax Virtual Internship 2026 — Cloud Computing & DevOps** program.

**Internship:** Cloud Computing & DevOps  
**Intern:** Tejas Kondhalkar  
**Organization:** Codomax Digital Solutions  
**Repository:** [cloud-web-app-deployment](https://github.com/Tejaskondhalkar-2003/cloud-web-app-deployment)

The internship is organized into six modules covering cloud computing fundamentals, Linux and networking, cloud services, Docker, DevOps automation, and a cloud deployment capstone project.

---

# Module 01 — Cloud Computing Foundations

**Duration:** Day 1–Day 5

## 1. Objective

Understand cloud computing fundamentals, cloud service models, deployment models, regions, availability zones, virtualization, core cloud services, security, scalability, elasticity, and pricing.

## 2. Step 1 — Understand Cloud Computing

Cloud computing provides on-demand access to computing resources such as servers, storage, databases, networking, and software over the internet.

Instead of purchasing and maintaining physical infrastructure, organizations can use cloud platforms to provision resources according to their requirements.

### Key characteristics

- On-demand resource availability.
- Pay-as-you-go pricing.
- Scalability and elasticity.
- Resource sharing.
- Access to services over a network.
- Flexible infrastructure management.

## 3. Step 2 — Learn Cloud Service Models

| Model | Full Form | Description | Example |
|---|---|---|---|
| IaaS | Infrastructure as a Service | Provides virtual servers, storage, and networking. | Amazon EC2 |
| PaaS | Platform as a Service | Provides a managed platform to develop and deploy applications. | AWS Elastic Beanstalk |
| SaaS | Software as a Service | Provides ready-to-use applications over the internet. | Web-based email |

### Understanding the models

- **IaaS:** The cloud provider manages the physical infrastructure, while the customer manages the operating system and applications.
- **PaaS:** The provider manages the infrastructure and platform, allowing developers to focus on application development.
- **SaaS:** The provider manages the complete application, which users access through the internet.

## 4. Step 3 — Learn Cloud Deployment Models

- **Public Cloud:** Cloud infrastructure provided over the internet and shared across multiple customers.
- **Private Cloud:** Cloud infrastructure dedicated to a single organization.
- **Hybrid Cloud:** A combination of private infrastructure and public cloud services.

## 5. Step 4 — Understand Regions and Availability Zones

- **Region:** A geographical area where a cloud provider operates its infrastructure.
- **Availability Zone:** An isolated location within a Region containing cloud infrastructure.
- **High Availability:** Deploying resources across multiple Availability Zones can improve service availability and resilience.

## 6. Step 5 — Understand Virtualization and Core Concepts

| Concept | Description |
|---|---|
| Virtualization | Allows multiple virtual machines to run on physical infrastructure. |
| Compute | Processing resources used to run applications. |
| Storage | Services used to store files and application data. |
| Networking | Virtual networks, IP addresses, routing, and connectivity. |
| IAM | Identity and Access Management for controlling resource access. |
| Scalability | Increasing or decreasing resources to meet requirements. |
| Elasticity | Dynamically adjusting resources according to demand. |
| Cloud Pricing | Understanding usage-based billing and resource costs. |

## 7. Step 6 — Explore AWS Core Services

The following AWS services were explored as part of cloud fundamentals:

| AWS Service | Purpose |
|---|---|
| Amazon EC2 | Provides virtual servers in the cloud. |
| Amazon S3 | Provides scalable object storage. |
| Amazon VPC | Provides isolated virtual networking. |
| AWS IAM | Manages users, roles, and permissions. |
| Amazon CloudWatch | Monitors metrics, logs, and alarms. |
| AWS Systems Manager | Helps manage and operate cloud instances. |

## 8. Step 7 — Cloud Services Exploration Diagram

```text
                  AWS Cloud Platform
                         |
        +----------------+----------------+
        |                |                |
     Compute           Storage         Networking
        |                |                |
       EC2               S3               VPC
        |                                 |
        +----------------+----------------+
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

- Understood the fundamentals of cloud computing.
- Learned IaaS, PaaS, and SaaS service models.
- Understood public, private, and hybrid cloud deployment models.
- Learned Regions and Availability Zones.
- Explored virtualization and cloud infrastructure.
- Identified the purpose of common AWS services.
- Understood scalability, elasticity, and cloud pricing.

---

# Module 02 — Linux, Networking & Cloud Infrastructure

**Duration:** Day 6–Day 10

## 1. Objective

Learn Linux command-line operations, file and directory management, SSH connectivity, IP addressing, ports, DNS, firewall fundamentals, and cloud server deployment.

## 2. Step 1 — Create an AWS EC2 Linux Instance

**Platform:** AWS Management Console

An Ubuntu Linux virtual server was created using Amazon EC2.

### EC2 Configuration

| Setting | Configuration |
|---|---|
| Instance Name | `cloud-web-app-server` |
| Operating System | Ubuntu Server 24.04 LTS |
| Instance Type | `t3.micro` |
| Architecture | 64-bit |
| AWS Region | US East (N. Virginia) |
| Availability Zone | `us-east-1c` |

Amazon EC2 provides scalable virtual computing resources in the AWS Cloud.

## 3. Step 2 — Create an SSH Key Pair

**Navigation:** AWS Console → EC2 → Key Pairs

An SSH key pair was created to authenticate securely with the Ubuntu instance.

- The public key is associated with the EC2 instance.
- The private `.pem` key is used to establish SSH access.
- The private key must be stored securely.
- Private keys must never be uploaded to a public GitHub repository.

## 4. Step 3 — Configure the EC2 Security Group

**Navigation:** AWS Console → EC2 → Security Groups

The following inbound rules were configured for the web server:

| Type | Protocol | Port | Purpose |
|---|---|---|---|
| SSH | TCP | 22 | Remote administration from a trusted IP |
| HTTP | TCP | 80 | Accessing the web application |

Security groups act as virtual firewalls that control inbound and outbound traffic for AWS resources.

**Security practice:** SSH access should be restricted to a trusted IP address instead of being opened to everyone.

## 5. Step 4 — Connect to Ubuntu Using SSH

**Platform:** Windows PowerShell / CMD

Locate the downloaded private key:

```powershell
cd $env:USERPROFILE\Downloads
Get-ChildItem *.pem
```

Connect to the EC2 instance:

```bash
ssh -i "YOUR_KEY_FILE.pem" ubuntu@YOUR_EC2_PUBLIC_IP
```

Replace the placeholders with the actual private key filename and current EC2 public IPv4 address.

After connecting, the Ubuntu terminal can be used to manage the server remotely.

## 6. Step 5 — Update the Ubuntu Server

Run the following commands inside the EC2 terminal:

```bash
sudo apt update
sudo apt upgrade -y
```

**Explanation:**

- `apt update` refreshes the package information.
- `apt upgrade -y` installs available package updates.

Keeping the server updated helps maintain security and stability.

## 7. Step 6 — Install and Check Apache Web Server

Install Apache:

```bash
sudo apt install apache2 -y
```

Check the service:

```bash
sudo systemctl status apache2
```

The Apache service was checked for an `active (running)` status.

## 8. Step 7 — Test Server Connectivity

Test the web server locally from the EC2 terminal:

```bash
curl http://localhost
```

Check the HTTP response:

```bash
curl -I http://localhost
```

Open the EC2 public IPv4 address in a web browser:

```text
http://YOUR_EC2_PUBLIC_IP
```

A successful response confirms that the web server is responding through the configured network path.

## 9. Step 8 — Practice Linux Commands

| Command | Purpose |
|---|---|
| `pwd` | Displays the current directory. |
| `ls -la` | Lists files, including hidden files. |
| `cd` | Changes the directory. |
| `whoami` | Displays the current user. |
| `mkdir` | Creates a directory. |
| `touch` | Creates an empty file. |
| `cat` | Displays file contents. |
| `chmod` | Changes file permissions. |
| `ps aux` | Displays running processes. |
| `ip addr` | Displays network interfaces and IP addresses. |
| `ip route` | Displays routing information. |
| `ss -tuln` | Displays listening TCP and UDP ports. |
| `systemctl status apache2` | Checks Apache service status. |
| `curl -I http://localhost` | Checks an HTTP response. |

## 10. Step 9 — Understand Networking Fundamentals

The following networking concepts were studied:

- **IP Addressing:** Identifies devices and network interfaces.
- **DNS:** Translates domain names into IP addresses.
- **Ports:** Identify services running on a system.
- **Firewall:** Controls network traffic.
- **Security Groups:** Control access to AWS resources.
- **SSH:** Provides secure remote terminal access.
- **HTTP:** Protocol used to transfer web content.

## 11. Security Best Practices

- Keep SSH access restricted to a trusted IP.
- Never share private SSH keys.
- Allow only required network ports.
- Avoid committing credentials and passwords to GitHub.
- Regularly update the operating system.
- Check the current EC2 public IP before connecting.

## 12. Learning Outcomes

- Created an Ubuntu EC2 instance.
- Practiced SSH connectivity.
- Updated and managed a Linux server.
- Installed and checked Apache.
- Practiced Linux CLI commands.
- Learned basic IP addressing and networking.
- Configured AWS security-group rules.
- Tested local and public HTTP connectivity.

---

# Module 03 — Cloud Services & Web App Deployment

**Duration:** Day 11–Day 15

## 1. Objective

Explore cloud compute, storage, networking, IAM, and monitoring services. Develop a web application and deploy it on cloud infrastructure.

## 2. Step 1 — Develop a Web Application

**Platform:** Windows PC with Visual Studio Code

A simple responsive web application was developed using:

- HTML
- CSS
- JavaScript

### Project Structure

```text
app/
├── index.html
├── style.css
└── script.js
```

### File Descriptions

| File | Purpose |
|---|---|
| `index.html` | Defines the structure and content of the web page. |
| `style.css` | Controls the design, layout, colors, and responsiveness. |
| `script.js` | Adds JavaScript functionality and user interaction. |

The application includes a test button that displays:

```text
Application is working successfully!
```

## 3. Step 2 — Test the Application Locally

Open `app/index.html` in a web browser.

Verify the following:

1. The website loads correctly.
2. The HTML content is visible.
3. CSS styling is applied.
4. The page layout displays correctly.
5. The JavaScript test button works.

## 4. Step 3 — Initialize Git

Open PowerShell and navigate to the project directory:

```powershell
cd "C:\Users\Tejas\Documents\Cloud-DevOps\cloud-web-app-deployment"
```

Initialize Git:

```bash
git init
git status
```

Configure Git identity if required:

```bash
git config --global user.name "Tejas Kondhalkar"
git config --global user.email "YOUR_GIT_EMAIL"
```

Add and commit the project files:

```bash
git add .
git commit -m "Add cloud web application"
```

## 5. Step 4 — Push the Application to GitHub

Connect the local repository to GitHub:

```bash
git remote add origin https://github.com/Tejaskondhalkar-2003/cloud-web-app-deployment.git
git branch -M main
git push -u origin main
```

If the `origin` remote already exists, check it first:

```bash
git remote -v
```

The GitHub repository stores the project source code and tracks changes.

## 6. Step 5 — Clone the Repository on EC2

Connect to the Ubuntu EC2 instance using SSH.

Clone the repository:

```bash
cd /tmp
git clone https://github.com/Tejaskondhalkar-2003/cloud-web-app-deployment.git
```

Check the application files:

```bash
ls /tmp/cloud-web-app-deployment/app
```

Verify that the HTML, CSS, and JavaScript files are present.

## 7. Step 6 — Deploy the Website Using Apache

The initial web deployment exercise used Apache on Ubuntu.

Apache's default web directory is:

```text
/var/www/html/
```

Copy the application files:

```bash
sudo cp /tmp/cloud-web-app-deployment/app/* /var/www/html/
```

Restart Apache:

```bash
sudo systemctl restart apache2
```

Check Apache status:

```bash
sudo systemctl status apache2
```

## 8. Step 7 — Verify the Deployed Application

From the EC2 terminal:

```bash
curl -I http://localhost
```

From a browser:

```text
http://YOUR_EC2_PUBLIC_IP
```

Verify that the application loads and that its CSS and JavaScript functionality work correctly.

## 9. Step 8 — Understand AWS Services Used

| AWS Service | Role |
|---|---|
| Amazon EC2 | Hosts the Ubuntu cloud server and web application. |
| Amazon VPC | Provides virtual networking. |
| Security Groups | Control inbound and outbound traffic. |
| AWS IAM | Manages identities, roles, and permissions. |
| Amazon S3 | Provides object storage. |
| Amazon CloudWatch | Monitors infrastructure metrics and alarms. |

## 10. Deployment Architecture

```text
       Web Application
        HTML / CSS / JS
               |
               v
          Git Repository
               |
               v
             GitHub
               |
               v
         AWS EC2 Ubuntu
               |
               v
        Apache Web Server
               |
               v
        Live Web Application
```

**Deployment clarification:** The Apache steps document the initial web-server deployment exercise. The current capstone application is deployed using Nginx inside Docker and Docker Compose, as documented in Modules 04–06.

## 11. Learning Outcomes

- Developed a basic web application.
- Practiced HTML, CSS, and JavaScript.
- Used Git for version control.
- Created and updated a GitHub repository.
- Cloned source code onto an EC2 instance.
- Deployed web files using Apache.
- Tested HTTP connectivity.
- Understood how cloud compute, storage, networking, IAM, and monitoring services support an application deployment.

---

# Module 04 — Docker & Containerization

**Duration:** Day 16–Day 20

## 1. Objective

Understand containerization and Docker architecture. Learn Docker images, containers, Dockerfiles, port mapping, networking, environment variables, volumes, and Docker Compose.

## 2. Tools and Technologies

- Docker Desktop
- Docker
- Dockerfile
- Docker Compose
- Nginx
- Git
- GitHub

## 3. Step 1 — Verify Docker Installation

Check the Docker version:

```bash
docker --version
```

Check Docker Compose:

```bash
docker compose version
```

These commands verify that Docker and Docker Compose are available.

## 4. Step 2 — Test Docker Installation

Run the test container:

```bash
docker run hello-world
```

This command downloads the image if required, creates a container, and executes it.

The `Hello from Docker!` message confirms that Docker can run a container successfully.

## 5. Step 3 — Explore Docker Images

Display available images:

```bash
docker images
```

Docker images are read-only templates used to create containers.

## 6. Step 4 — Explore Docker Containers

Display all containers:

```bash
docker ps -a
```

Display only running containers:

```bash
docker ps
```

A container is an isolated running instance created from a Docker image.

## 7. Step 5 — Run an Nginx Container

Run Nginx locally:

```bash
docker run -d -p 8080:80 --name my-web-server nginx
```

### Command Explanation

- `docker run` creates and starts a container.
- `-d` runs it in the background.
- `-p 8080:80` maps host port 8080 to container port 80.
- `--name` assigns a container name.
- `nginx` specifies the Docker image.

Open the application:

```text
http://localhost:8080
```

This verifies that the Nginx container is serving a web page.

## 8. Step 6 — Create a Dockerfile

A Dockerfile was created in the project root.

### Dockerfile

```dockerfile
FROM nginx:alpine

COPY app/ /usr/share/nginx/html/

EXPOSE 80
```

### Explanation

**FROM nginx:alpine**

Uses the lightweight Nginx Alpine image as the base image.

**COPY app/ /usr/share/nginx/html/**

Copies the application files into the Nginx web directory inside the container.

**EXPOSE 80**

Documents the port used by the web server inside the container.

## 9. Step 7 — Build a Custom Docker Image

Build the image:

```bash
docker build -t cloud-web-app .
```

Explanation:

- `docker build` builds an image.
- `-t cloud-web-app` assigns the image name.
- `.` specifies the current directory as the build context.

Check the image:

```bash
docker images
```

The custom image should appear in the image list.

## 10. Step 8 — Run the Custom Web Application Container

Run the custom image:

```bash
docker run -d -p 8081:80 --name cloud-web-container cloud-web-app
```

Open the application:

```text
http://localhost:8081
```

This verifies that the custom Docker image can serve the web application.

## 11. Step 9 — Inspect the Container

Check running containers:

```bash
docker ps
```

Inspect a container:

```bash
docker inspect cloud-web-container
```

Container inspection provides information about:

- Container configuration.
- Network settings.
- Port mappings.
- Environment variables.
- Mounts.
- Container state.

## 12. Step 10 — Explore Docker Networking

List Docker networks:

```bash
docker network ls
```

Docker networking enables containers to communicate with one another and with external networks.

## 13. Step 11 — Practice Environment Variables

Run a temporary container:

```bash
docker run --rm -e APP_ENV=development nginx:alpine env
```

Explanation:

- `--rm` removes the container after it exits.
- `-e` sets an environment variable.
- `APP_ENV=development` is the variable passed to the container.
- `env` displays environment variables.

This demonstrates how configuration values can be passed into containers.

## 14. Step 12 — Create a Docker Volume

Create a volume:

```bash
docker volume create cloud-web-data
```

List volumes:

```bash
docker volume ls
```

Docker volumes provide persistent storage separately from a container's writable layer.

## 15. Step 13 — Create Docker Compose Configuration

Create a file named:

```text
docker-compose.yml
```

### Current Project Configuration

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

### Explanation

- `services` defines the application services.
- `web` is the web application service.
- `build: .` builds the image from the current directory.
- `container_name` assigns the name `cloud-web-compose`.
- `ports` maps host port 80 to container port 80.
- `environment` sets the application environment variable.

## 16. Step 14 — Validate Docker Compose Configuration

Run:

```bash
docker compose config
```

This validates and displays the processed Compose configuration.

## 17. Step 15 — Start the Application Using Docker Compose

Build and start the application:

```bash
docker compose up -d --build
```

This command builds the image if required and starts the application in detached mode.

## 18. Step 16 — Verify Docker Compose Services

Check the services:

```bash
docker compose ps
```

Check running containers:

```bash
docker ps
```

The current project container is:

```text
cloud-web-compose
```

The current port mapping is:

```text
0.0.0.0:80 -> 80/tcp
```

## 19. Step 17 — Test the Web Application

Open the local application:

```text
http://localhost
```

For the deployed EC2 application, open:

```text
http://YOUR_EC2_PUBLIC_IP
```

The web application was verified to load successfully through the Docker Compose deployment.

## 20. Step 18 — Manage the Container Lifecycle

Stop and remove Compose services:

```bash
docker compose down
```

Start them again:

```bash
docker compose up -d
```

Check logs:

```bash
docker compose logs --tail=50
```

These commands help manage and troubleshoot the application lifecycle.

## 21. Step 19 — Add Docker Files to Git

Check project status:

```bash
git status
```

Add Docker-related files:

```bash
git add Dockerfile docker-compose.yml .dockerignore
```

Commit the changes:

```bash
git commit -m "Add Docker containerization"
```

Push the changes:

```bash
git push origin main
```

## 22. Docker Workflow

```text
       Web Application
              |
              v
          Dockerfile
              |
              v
          Docker Image
              |
              v
        Docker Container
              |
              v
         Port Mapping
              |
              v
       Docker Networking
              |
              v
       Environment Variables
              |
              v
        Docker Compose
              |
              v
       Running Application
```

## 23. Final Project Structure

```text
cloud-web-app-deployment/
│
├── app/
│   ├── index.html
│   ├── script.js
│   └── style.css
│
├── .github/
│   └── workflows/
│       └── ci-cd.yml
│
├── Dockerfile
├── docker-compose.yml
├── .dockerignore
└── README.md
```

## 24. Learning Outcomes

- Installed and verified Docker.
- Practiced Docker images and containers.
- Ran Nginx containers.
- Created a custom Dockerfile.
- Built custom Docker images.
- Practiced port mapping.
- Inspected containers.
- Explored Docker networking.
- Practiced environment variables.
- Created Docker volumes.
- Used Docker Compose.
- Managed container lifecycle.
- Integrated Docker files with Git and GitHub.

---

# Module 05 — DevOps, CI/CD & Monitoring

**Duration:** Day 21–Day 25

## 1. Objective

Understand DevOps principles and implement Continuous Integration and Continuous Deployment using GitHub Actions.

Automate application validation, Docker image building, and deployment to AWS EC2 through AWS Systems Manager.

## 2. Tools and Technologies

- Git and GitHub
- GitHub Actions
- Docker and Docker Compose
- AWS EC2
- AWS IAM
- AWS Systems Manager (SSM)
- GitHub OIDC authentication
- Ubuntu Linux

## 3. Step 1 — Understand DevOps

DevOps combines development and operations practices to improve collaboration, automation, software delivery, and application reliability.

### Key DevOps concepts

- Version control.
- Continuous Integration.
- Continuous Delivery and Deployment.
- Automated testing.
- Infrastructure management.
- Monitoring and logging.
- Collaboration and feedback.

## 4. Step 2 — Understand Git and GitHub Workflow

Git is a version control system used to track changes in project files.

GitHub hosts repositories and provides collaboration and automation features.

Basic Git workflow:

```bash
git status
git add .
git commit -m "Update application"
git push origin main
```

## 5. Step 3 — Create a GitHub Actions Workflow

The workflow file is located at:

```text
.github/workflows/ci-cd.yml
```

GitHub Actions automates tasks when repository events occur.

The workflow is configured to run for pushes and pull requests to the `main` branch, with manual workflow execution also supported.

## 6. Step 4 — Implement Continuous Integration

The CI job performs the following tasks:

1. Checks out the repository.
2. Configures Node.js.
3. Checks required application files.
4. Validates JavaScript syntax.
5. Checks essential HTML structure.
6. Builds the Docker image.

These checks help identify application and build issues before deployment.

## 7. Step 5 — Implement Continuous Deployment

The deployment job runs after the build-and-test job succeeds and is configured for pushes to `main`.

### Deployment process

1. GitHub Actions authenticates to AWS using OIDC.
2. AWS credentials are configured through an IAM deployment role.
3. The workflow verifies the AWS identity.
4. AWS Systems Manager sends a command to the EC2 instance.
5. EC2 pulls the latest project changes.
6. Docker Compose rebuilds and starts the application.
7. The workflow checks the deployment command status.

## 8. Step 6 — Understand GitHub OIDC Authentication

GitHub OIDC allows GitHub Actions to assume an AWS IAM role without storing long-lived AWS access keys in the repository.

The deployment requires:

- An AWS IAM OIDC identity provider.
- An IAM role with an appropriate trust policy.
- Permissions for the required deployment operations.
- A GitHub repository secret containing the role ARN.

This provides a more secure authentication approach than storing permanent AWS credentials.

## 9. Step 7 — Configure AWS Systems Manager

AWS Systems Manager is used to send remote deployment commands to the EC2 instance.

The EC2 instance requires:

- An appropriate IAM instance role.
- Systems Manager permissions.
- An active SSM Agent.
- Connectivity to the Systems Manager service.

The GitHub Actions deployment role requires permission to send the required SSM commands.

## 10. Step 8 — Docker Deployment Commands

Check running containers:

```bash
docker ps
```

Check all containers:

```bash
docker ps -a
```

Validate Compose configuration:

```bash
docker compose config
```

Build and start the application:

```bash
docker compose up -d --build
```

Check services:

```bash
docker compose ps
```

View application logs:

```bash
docker compose logs --tail=50
```

Test Nginx configuration:

```bash
docker exec cloud-web-compose nginx -t
```

Test local HTTP connectivity:

```bash
curl -I http://localhost
```

## 11. Step 9 — Trigger the CI/CD Pipeline

From the local project directory, make a change to the application or project files.

Check changes:

```bash
git status
```

Stage the changes:

```bash
git add .
```

Commit:

```bash
git commit -m "Update CI/CD project"
```

Push:

```bash
git push origin main
```

Open the GitHub repository and navigate to:

**GitHub → Repository → Actions**

Monitor the workflow and review the job logs.

## 12. Step 10 — Verify the Pipeline

The project pipeline was verified through the following checks:

- GitHub Actions workflow executed successfully.
- Application validation completed.
- Docker image build succeeded.
- AWS authentication through OIDC succeeded.
- SSM deployment completed successfully.
- Docker container was running on EC2.
- Nginx configuration was checked.
- Local HTTP request returned `200 OK`.
- Live application opened successfully in a browser.

## 13. Troubleshooting

| Issue | What to Check |
|---|---|
| GitHub Actions workflow failure | Review workflow logs and failed job steps. |
| AWS authentication failure | Check OIDC provider, IAM trust policy, and role ARN. |
| SSM deployment failure | Check SSM Agent, instance role, and command output. |
| Docker container stopped | Check `docker ps -a` and container logs. |
| Compose configuration error | Run `docker compose config`. |
| Website unavailable | Check EC2 public IP, security group, and port mapping. |

## 14. Learning Outcomes

- Understood DevOps principles.
- Practiced Git and GitHub workflows.
- Learned CI/CD concepts.
- Created an automated GitHub Actions workflow.
- Automated application validation.
- Built Docker images through CI.
- Configured AWS OIDC authentication.
- Used AWS Systems Manager for remote deployment.
- Automated application deployment to EC2.
- Practiced deployment troubleshooting.

---

# Module 06 — Cloud & DevOps Capstone Project

**Duration:** Day 26–Day 30

## 1. Objective

Build, containerize, automate, deploy, and monitor a real web application.

Integrate cloud infrastructure, Git, Docker, CI/CD, monitoring, and managed database/authentication services where implemented.

## 2. Project Overview

The capstone project is a cloud-hosted web application deployed on AWS EC2 using Docker and Nginx.

GitHub Actions automates application validation, Docker image building, and deployment through AWS Systems Manager.

Amazon CloudWatch and a scheduled Bash health-check script are used for basic monitoring.

## 3. Technologies Used

| Technology | Purpose |
|---|---|
| HTML | Web page structure |
| CSS | Application styling |
| JavaScript | Application interaction |
| Git | Version control |
| GitHub | Source code repository |
| GitHub Actions | CI/CD automation |
| AWS EC2 | Cloud compute infrastructure |
| Ubuntu 24.04 | Server operating system |
| Docker | Application containerization |
| Docker Compose | Container management |
| Nginx | Web server |
| AWS IAM | Access management |
| AWS Systems Manager | Remote deployment |
| Amazon CloudWatch | Infrastructure monitoring |
| Bash and Cron | Website health checks and scheduling |

## 4. Step 1 — Review the Application Source Code

The web application source code is maintained in the GitHub repository.

Project files:

```text
app/
├── index.html
├── style.css
└── script.js
```

The application was tested locally before containerization and deployment.

Repository:

https://github.com/Tejaskondhalkar-2003/cloud-web-app-deployment

## 5. Step 2 — Configure the Dockerfile

The application is packaged using the following Dockerfile:

```dockerfile
FROM nginx:alpine

COPY app/ /usr/share/nginx/html/

EXPOSE 80
```

This configuration uses Nginx as the base image and copies the website files into the Nginx document directory.

## 6. Step 3 — Configure Docker Compose

The project uses the following Docker Compose configuration:

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

### Configuration explanation

- Builds the application image using the Dockerfile.
- Creates a container named `cloud-web-compose`.
- Maps EC2 host port 80 to container port 80.
- Sets the application environment variable to production.

## 7. Step 4 — Deploy the Application to AWS EC2

The application is hosted on an Ubuntu EC2 instance.

### EC2 Configuration

| Setting | Configuration |
|---|---|
| Instance Name | `cloud-web-app-server` |
| Operating System | Ubuntu Server 24.04 |
| Instance Type | `t3.micro` |
| AWS Region | `us-east-1` |
| Container Name | `cloud-web-compose` |
| Web Server | Nginx |
| Port Mapping | `80:80` |

Docker and Docker Compose are installed on the EC2 instance.

The application is started using:

```bash
sudo docker compose up -d --build
```

Check the running container:

```bash
sudo docker ps
```

Check Compose services:

```bash
sudo docker compose ps
```

## 8. Step 5 — Automate Deployment Using GitHub Actions

The workflow file is:

```text
.github/workflows/ci-cd.yml
```

The deployment process follows this sequence:

1. Developer updates the application.
2. Changes are pushed to GitHub.
3. GitHub Actions starts the workflow.
4. CI validates application files.
5. Docker image is built.
6. GitHub Actions authenticates to AWS through OIDC.
7. AWS Systems Manager sends deployment commands to EC2.
8. EC2 pulls the latest project code.
9. Docker Compose rebuilds and starts the application.
10. Deployment status is checked.

## 9. Step 6 — Configure CloudWatch Monitoring

Amazon CloudWatch was used to monitor the EC2 instance.

Two CloudWatch alarms were configured.

### CPU Utilization Alarm

| Setting | Configuration |
|---|---|
| Alarm Name | `cloud-web-app-server-high-cpu` |
| Namespace | `AWS/EC2` |
| Metric | `CPUUtilization` |
| Statistic | Average |
| Period | 5 minutes |
| Threshold | Greater than 80 |
| Evaluation | 1 out of 1 datapoint |

**Purpose:** Monitors EC2 CPU usage and identifies when it exceeds the configured threshold.

### EC2 Status Check Alarm

| Setting | Configuration |
|---|---|
| Alarm Name | `cloud-web-app-server-status-check-failed` |
| Namespace | `AWS/EC2` |
| Metric | `StatusCheckFailed` |
| Statistic | Maximum |
| Period | 5 minutes |
| Threshold | Greater than or equal to 1 |
| Evaluation | 1 out of 1 datapoint |

**Purpose:** Helps identify EC2 system or instance status-check failures.

## 10. Step 7 — Create a Website Health-Check Script

A Bash script was created on the EC2 instance to verify whether the local Nginx application responds to HTTP requests.

### Script Location

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

### Script Explanation

1. Sends an HTTP request to the local website.
2. Uses a maximum request time of 10 seconds.
3. Displays a success message if the request succeeds.
4. Displays a failure message and returns a non-zero exit code if the request fails.

Make the script executable:

```bash
sudo chmod +x /usr/local/bin/website-health-check.sh
```

Run the health check:

```bash
sudo /usr/local/bin/website-health-check.sh
```

Example successful output:

```text
Website UP - HTTP check passed
```

## 11. Step 8 — Schedule Automatic Health Checks Using Cron

Cron was configured to run the health-check script every minute and append the results to a log file.

### Cron Configuration

```cron
* * * * * /usr/local/bin/website-health-check.sh >> /var/log/website-health.log 2>&1
```

### Log File

```text
/var/log/website-health.log
```

Verify the cron schedule:

```bash
sudo crontab -l
```

View recent health-check results:

```bash
sudo tail -n 10 /var/log/website-health.log
```

The log records successful checks and HTTP check failures.

**Monitoring note:** This script checks the website locally from the EC2 instance. It does not independently verify public internet accessibility or send notifications. CloudWatch alarm notifications require a notification action to be configured.

## 12. Step 9 — Verify the Live Application

The deployed application was checked using the following commands:

Check Docker containers:

```bash
sudo docker ps
```

Check Nginx configuration:

```bash
sudo docker exec cloud-web-compose nginx -t
```

Check local HTTP response:

```bash
curl -I http://localhost
```

Open the application in a browser:

```text
http://YOUR_CURRENT_EC2_PUBLIC_IP
```

### Verified Deployment Details

| Item | Configuration |
|---|---|
| EC2 Instance | `cloud-web-app-server` |
| Instance Type | `t3.micro` |
| AWS Region | `us-east-1` |
| Container | `cloud-web-compose` |
| Web Server | Nginx |
| Port Mapping | `80:80` |
| HTTP Response at last verification | `200 OK` |
| Deployment Status | Website opened successfully |

**Important:** The EC2 public IPv4 address can change after an instance stop/start unless an Elastic IP is configured. Check the current address in the AWS EC2 console before sharing the live URL. The verified deployment uses HTTP, not HTTPS.

## 13. Step 10 — Managed Database and Authentication

The Codomax capstone objectives include managed database and authentication integration.

Amazon Cognito user pool and app-client setup was explored during the project. However, a complete working application sign-in flow and managed database connection have not been verified.

Therefore, these integrations are not marked as completed deliverables in this README.

They should be added to the project only after configuration and end-to-end testing are successful.

## 14. Capstone Architecture Diagram

```text
             Developer
                 |
                 v
          GitHub Repository
                 |
                 v
           GitHub Actions
                 |
          +------+------+
          |             |
          v             v
         CI             CD
    Code Validation   AWS OIDC
    Docker Build         |
                         v
                AWS Systems Manager
                         |
                         v
                    AWS EC2
                  Ubuntu Server
                         |
                         v
                  Docker Compose
                         |
                         v
                    Nginx
                   Container
                         |
                         v
                Live Web Application
                         |
                         v
                CloudWatch Monitoring
                         |
                         v
                Website Health Check
```

## 15. Final Capstone Deliverables

| Deliverable | Project Location / Status |
|---|---|
| GitHub Repository | [cloud-web-app-deployment](https://github.com/Tejaskondhalkar-2003/cloud-web-app-deployment) |
| Cloud Deployment | AWS EC2 |
| Dockerfile | `Dockerfile` |
| Docker Compose | `docker-compose.yml` |
| CI/CD Workflow | `.github/workflows/ci-cd.yml` |
| Monitoring | CloudWatch alarms |
| Health Check | `website-health-check.sh` |
| Cron Scheduling | Configured on EC2 |
| Architecture Diagram | Included above |
| Managed Database | Not yet verified |
| Authentication | Cognito setup explored; working application flow not yet verified |

## 16. Final Capstone Result

The web application was successfully:

- Developed using HTML, CSS, and JavaScript.
- Stored and managed using Git and GitHub.
- Containerized using Docker.
- Configured using Docker Compose.
- Deployed to AWS EC2.
- Served using Nginx.
- Automated using GitHub Actions.
- Deployed remotely using AWS Systems Manager and OIDC authentication.
- Monitored using CloudWatch alarms.
- Checked using a scheduled Bash health-check script.

The project demonstrates a practical cloud deployment workflow combining Linux, AWS, Docker, GitHub Actions, CI/CD, and basic monitoring.

---

# Final Project Structure

```text
cloud-web-app-deployment/
│
├── .github/
│   └── workflows/
│       └── ci-cd.yml
│
├── app/
│   ├── index.html
│   ├── style.css
│   └── script.js
│
├── Dockerfile
├── docker-compose.yml
├── .dockerignore
├── screenshots/
└── README.md
```

# Technologies and Skills Practiced

- Cloud Computing
- Amazon Web Services (AWS)
- Amazon EC2
- AWS IAM
- AWS Systems Manager
- Amazon CloudWatch
- Linux Administration
- Networking Fundamentals
- SSH Connectivity
- Git and GitHub
- HTML, CSS, and JavaScript
- Docker
- Docker Compose
- Nginx
- GitHub Actions
- CI/CD Automation
- AWS OIDC Authentication
- Bash Scripting
- Cron Scheduling
- Application and Infrastructure Monitoring

---

# Project Links

**GitHub Repository:**  
https://github.com/Tejaskondhalkar-2003/cloud-web-app-deployment

**Live Application:**  
Check the current EC2 public IPv4 address in the AWS console before sharing the deployment URL.

---

**Author:** Tejas Kondhalkar  
**Qualification:** B.E. Electronics & Telecommunication Engineering  
**Internship:** Cloud Computing & DevOps — Codomax Digital Solutions, 2026

**Security Reminder:** Never upload private SSH keys, passwords, access tokens, or AWS credentials to GitHub. Keep sensitive configuration secure and allow only the network access required by the application.


