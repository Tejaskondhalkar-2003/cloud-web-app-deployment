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

