<!-- 
  Title: Supanel Server Management Platform | Docker-Based Hosting Control Panel
  Description: Download and install Supanel by Skilled.u. The best free server management solution, aaPanel alternative, and Docker-based hosting control panel for managing VPS, MySQL, PHP, and websites on Windows, Linux, and macOS.
  Keywords: Supanel, Supanel Server Installation, Skilled.u, aaPanel alternative, free cPanel alternative, web hosting control panel, Docker server panel, Windows server management, Linux VPS management, macOS local server, Supanel tutorial, localhost, Docker hosting
-->

<div align="center">
  <h1>🚀 Supanel Server Management Platform | Docker-Based Hosting Control Panel</h1>
  <p><strong>Developed by <a href="https://skilledu.in/">Skilled.u</a> - Master Essential Technical Skills</strong></p>
  
  [![Docker Pulls](https://img.shields.io/docker/pulls/skilledu/supanel)](https://hub.docker.com/r/skilledu/supanel)
  [![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
  [![Platform](https://img.shields.io/badge/Platform-Windows%20%7C%20Linux%20%7C%20macOS-success)](#)
  [![aaPanel Powered](https://img.shields.io/badge/Powered_by-aaPanel-orange)](#)

  <p><strong>Supanel</strong> is a powerful Docker-based server management platform designed for developers, system administrators, DevOps engineers, hosting providers, and businesses. It provides a complete web hosting environment with integrated services including aaPanel, database management, FTP, web server hosting, SSL management, email hosting, and application deployment across any operating system.</p>
</div>

---

## 🌟 Why Choose Supanel?

Supanel simplifies server administration by providing a pre-configured hosting environment inside a secure Docker container. Instead of manually installing multiple services, users can deploy a complete hosting stack within minutes. Whether you are developing locally on Windows/Mac or deploying to a production Linux VPS, Supanel is the perfect **free cPanel and Plesk alternative**.

### ✨ Key Benefits
* ✅ **One-Command Installation**
* ✅ **Docker-Based Cross-Platform Deployment** (Windows, Linux, macOS)
* ✅ **Integrated aaPanel Control Panel**
* ✅ **Website & Domain Management**
* ✅ **MySQL & PostgreSQL Support**
* ✅ **Redis & MongoDB Support**
* ✅ **SSL Certificate Management**
* ✅ **Email Server Support**
* ✅ **FTP Server Support**
* ✅ **Reverse Proxy Support**
* ✅ **Developer Friendly Environment**
* ✅ **Self-Hosted Infrastructure**

---

## 🛠️ Comprehensive Features

### 🌐 Hosting Management
* Website Hosting & Deployment
* Complete Domain Management
* Automated SSL Installation (Let's Encrypt)
* Reverse Proxy Configuration
* Native Nginx & Apache Support

### 🗄️ Database Support
* MySQL
* PostgreSQL
* MongoDB
* Redis

### 💻 Development Environment
* Docker Container Integration
* API Hosting & Routing
* Node.js Applications Support
* Python Applications Support
* PHP Applications Support (PHP 7.x & 8.x)

### 🛡️ Security Features
* Advanced Firewall Support
* SSL Certificates Manager
* Strict Access Control
* Secure Authentication

### ⚙️ System Administration
* Real-time Server Monitoring
* Resource Management (CPU, RAM, Disk)
* Process Monitoring
* Background Service Management

---

## 📚 Quick Navigation

- **[🚀 Quick Installation Guide](installation.md)** - Get started with Supanel in minutes
- **[💻 VS Code Integration](vscode-integration.md)** - Development setup and environment
- **[🎯 About Skilled.u](about-skilledu.md)** - Learn about our tech courses and tutorials
- **[❓ Troubleshooting Support](troubleshooting.md)** - Common issues and Supanel server solutions

---

## 💻 System Requirements

To ensure optimal performance for your **server management**, please verify your system meets these minimum requirements:
- **OS**: Any OS with Docker installed (**Windows** via Docker Desktop/WSL2, **macOS** via Docker Desktop, or any **Linux** distribution).
- **RAM**: Minimum 1GB (2GB+ Recommended for smooth database operations).
- **Storage**: Minimum 10GB of free disk space.
- **Network**: Localhost for development, or a static public IP address for VPS/Cloud deployment.

---

## 🚀 How to Install Supanel Server (Complete Setup Guide)

Deploying the **Supanel server management panel** is incredibly easy. Choose your preferred **Supanel installation** method below:

### Method 1: Direct Internet Download (Recommended)
This is the fastest way to install Supanel on Windows, Mac, or Linux. Run the following Docker command in your terminal, Command Prompt, or PowerShell:

```bash
# Download and run Supanel hosting panel in one single command
docker run --privileged -d -p 20:20 -p 21:21 -p 22:22 -p 25:25 -p 53:53 -p 53:53/udp -p 80:80 -p 443:443 -p 3306:3306 -p 5432:5432 -p 6379:6379 -p 27017:27017 -p 9200:9200 -p 9300:9300 -p 15672:15672 -p 5672:5672 -p 888:888 -p 2025:2025 -p 7800:7800 -p 8080:8080 -p 8443:8443 -p 9001:9001 -p 8888:8888 -p 3000:3000 -p 8000:8000 -p 39000-39009:39000-39009 --name=supanel_server ghcr.io/skilledu/supanel:latest
```

### Method 2: Download Tar File (Offline Local Installation)
Perfect for offline environments or restricted enterprise networks. Load the tar file directly into your Docker daemon.

```bash
# 1. Download the Supanel server tar archive
wget https://github.com/skilledu/supanel/releases/download/supanel/supanel.tar

# 2. Load the Docker image
docker load -i supanel.tar

# 3. Run the Supanel container
docker run --privileged -d -p 20:20 -p 21:21 -p 22:22 -p 25:25 -p 53:53 -p 53:53/udp -p 80:80 -p 443:443 -p 3306:3306 -p 5432:5432 -p 6379:6379 -p 27017:27017 -p 9200:9200 -p 9300:9300 -p 15672:15672 -p 5672:5672 -p 888:888 -p 2025:2025 -p 7800:7800 -p 8080:8080 -p 8443:8443 -p 9001:9001 -p 8888:8888 -p 3000:3000 -p 8000:8000 -p 39000-39009:39000-39009 --name=supanel_server supanel:latest
```

---

## ⚙️ Start the aaPanel Service in Supanel

Once the Supanel Docker container is actively running, you must initialize the built-in **aaPanel** core service:

```bash
# Access the running Supanel server container terminal
docker exec -it supanel_server bash

# Start the aaPanel background service securely
sudo bt 3
```

---

## 🌐 Accessing Your Supanel Admin Dashboard

After starting the services, you can securely log in to your **Supanel admin hosting panel** via your web browser:
- **Admin Panel Login URL**: `http://localhost:2025/supanel` *(Replace localhost with your Server IP if installing remotely)*

### Default Supanel Login Credentials
- **Username**: `skilledu`
- **Password**: `skilledu`

---

## 💡 Frequently Asked Questions (FAQ)

**Q1: What is Supanel?**  
**A:** Supanel is a complete **Docker-based server management solution** created by Skilled.u. It provides a visual GUI to manage websites, SSLs, databases, and Docker containers without using command-line instructions.

**Q2: Can I install Supanel on Windows or Mac?**  
**A:** Yes! Because Supanel runs entirely within Docker, it is fully cross-platform. You can install it on **Windows 10/11** (via Docker Desktop), **macOS**, or any **Linux** distribution. It's perfect for both local development and live production servers.

**Q3: Is Supanel a good alternative to cPanel?**  
**A:** Yes! Supanel is widely considered an excellent, lightweight **free cPanel alternative** and **Plesk alternative** for developers and system admins managing personal or enterprise VPS hosting.

---

## 📞 Need Help with Supanel Setup?

Our expert support team at Skilled.u is here to help you maximize your server management experience:
- **📧 Email Support**: info@skilledu.in
- **📞 Direct Phone**: +91 89890 99962
- **🌐 Official Website**: [https://skilledu.in/](https://skilledu.in/)

*Tags: Supanel, Supanel Server Installation, Hosting Control Panel, DevOps platform, Node.js hosting, Python Hosting, Install aaPanel on Windows, Mac OS Server Management, Docker server panel, Free cPanel Alternative, Server Management Solution, Skilled.u Panel, Localhost Dashboard*
