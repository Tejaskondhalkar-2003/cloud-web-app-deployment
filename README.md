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

I created a key pair for SSH access.

Key pair name:

```text
cloud-web-app-server-key
```

Key format:

```text
.pem
```

The private key was downloaded to my Windows computer.

Example:

```text
cloud-web-app-server-key.pem
```

### Security Note

The `.pem` private key should never be uploaded to GitHub or shared with anyone.

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
ssh -i "cloud-web-app-server-key.pem" ubuntu@<YOUR_EC2_PUBLIC_IP>
```

For example:

```cmd
ssh -i "cloud-web-app-server-key.pem" ubuntu@<YOUR_EC2_PUBLIC_IP>
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
ubuntu@ip-172-31-xx-xx:~$
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
http://<YOUR_EC2_PUBLIC_IP>
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
http://<YOUR_EC2_PUBLIC_IP>
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
ssh -i "cloud-web-app-server-key.pem" ubuntu@<YOUR_EC2_PUBLIC_IP>
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
