<!-- 
  Title: Supanel Installation Guide: How to Install on Windows, Ubuntu, CentOS & macOS
  Description: Complete step-by-step Supanel installation guide. Learn how to install Docker and deploy the Supanel hosting control panel on Linux (Ubuntu/CentOS), macOS, and Windows.
  Keywords: Supanel installation guide, install Supanel on Ubuntu, CentOS Docker setup, Windows Docker Desktop, aaPanel Docker installation, free web hosting panel setup, Supanel tutorial, Docker container management
-->

<div align="center">
  <h1>🚀 Supanel Installation Guide</h1>
  <p><strong>Complete Setup Instructions for Windows, macOS, and Linux</strong></p>
  <p>Welcome to the official <strong>Supanel installation guide</strong>. Whether you are setting up a local development environment or deploying a production VPS, this guide covers everything you need to install and configure the Supanel server management platform.</p>
</div>

---

## 📋 Prerequisites for Installation

Before installing the **Supanel hosting control panel**, ensure you meet the following requirements:
- **Docker** must be installed and running on your host system.
- An active internet connection (required for Method 1).
- Root or Administrator privileges on your machine.

---

## 🐳 Step 1: Install Docker (If Not Already Installed)

Since Supanel is a highly secure, **Docker-based deployment**, you must have Docker running. Choose your operating system below for detailed Docker installation steps:

### 🐧 For Ubuntu / Debian
```bash
# Update local package index
sudo apt update

# Install prerequisite packages securely
sudo apt install apt-transport-https ca-certificates curl gnupg lsb-release

# Add Docker's official secure GPG key
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

# Add the official Docker repository
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

# Update package index and install Docker Engine
sudo apt update
sudo apt install docker-ce docker-ce-cli containerd.io

# Start and permanently enable the Docker service
sudo systemctl start docker
sudo systemctl enable docker

# (Optional) Add your user to the docker group to run without sudo
sudo usermod -aG docker $USER
```

### 🔴 For CentOS / RHEL / AlmaLinux
```bash
# Install the necessary yum utilities
sudo yum install -y yum-utils

# Add the official Docker repository
sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo

# Install the latest Docker Engine
sudo yum install docker-ce docker-ce-cli containerd.io

# Start and permanently enable the Docker service
sudo systemctl start docker
sudo systemctl enable docker

# (Optional) Add your user to the docker group
sudo usermod -aG docker $USER
```

### 🍏 For macOS Users
1. Download **Docker Desktop for Mac** from the official site: [https://www.docker.com/products/docker-desktop](https://www.docker.com/products/docker-desktop)
2. Open the downloaded `.dmg` file and drag Docker to your Applications folder.
3. Launch Docker Desktop from Launchpad and grant the necessary permissions.

### 🪟 For Windows Users
1. Download **Docker Desktop for Windows** from: [https://www.docker.com/products/docker-desktop](https://www.docker.com/products/docker-desktop)
2. Run the `.exe` installer and follow the on-screen prompts. Ensure WSL2 is enabled if prompted.
3. Restart your computer.
4. Launch Docker Desktop and wait for the engine to start.

### ✅ Verify Your Docker Installation
Run these commands to ensure Docker is active:
```bash
docker --version
docker run hello-world
```

---

## 🚀 Step 2: Choose Your Supanel Installation Method

### Method 1: Direct Internet Download (Highly Recommended)
**Best for:** Cloud VPS, Dedicated Servers, and users with a fast internet connection.

#### 1. Pull the Official Supanel Image
```bash
docker pull ghcr.io/skilledu/supanel:latest
```

#### 2. Run the Supanel Container
Execute the command that corresponds to your operating system to deploy the **aaPanel container**:

**For Linux & macOS Terminal:**
```bash
docker run --privileged -d \
  -p 20:20 -p 21:21 -p 22:22 -p 25:25 \
  -p 53:53 -p 53:53/udp -p 80:80 -p 443:443 \
  -p 3306:3306 -p 5432:5432 -p 6379:6379 \
  -p 27017:27017 -p 9200:9200 -p 9300:9300 \
  -p 15672:15672 -p 5672:5672 -p 888:888 \
  -p 2025:2025 -p 7800:7800 -p 8080:8080 \
  -p 8443:8443 -p 9001:9001 -p 8888:8888 \
  -p 3000:3000 -p 8000:8000 \
  -p 39000-39009:39000-39009 \
  --name=supanel_server \
  ghcr.io/skilledu/supanel:latest
```

**For Windows PowerShell:**
```powershell
docker run --privileged -d `
  -p 20:20 -p 21:21 -p 22:22 -p 25:25 `
  -p 53:53 -p 53:53/udp -p 80:80 -p 443:443 `
  -p 3306:3306 -p 5432:5432 -p 6379:6379 `
  -p 27017:27017 -p 9200:9200 -p 9300:9300 `
  -p 15672:15672 -p 5672:5672 -p 888:888 `
  -p 2025:2025 -p 7800:7800 -p 8080:8080 `
  -p 8443:8443 -p 9001:9001 -p 8888:8888 `
  -p 3000:3000 -p 8000:8000 `
  -p 39000-39009:39000-39009 `
  --name=supanel_server `
  ghcr.io/skilledu/supanel:latest
```

**For Windows CMD:**
```cmd
docker run --privileged -d ^
  -p 20:20 -p 21:21 -p 22:22 -p 25:25 ^
  -p 53:53 -p 53:53/udp -p 80:80 -p 443:443 ^
  -p 3306:3306 -p 5432:5432 -p 6379:6379 ^
  -p 27017:27017 -p 9200:9200 -p 9300:9300 ^
  -p 15672:15672 -p 5672:5672 -p 888:888 ^
  -p 2025:2025 -p 7800:7800 -p 8080:8080 ^
  -p 8443:8443 -p 9001:9001 -p 8888:8888 ^
  -p 3000:3000 -p 8000:8000 ^
  -p 39000-39009:39000-39009 ^
  --name=supanel_server ^
  ghcr.io/skilledu/supanel:latest
```

**One-line command (Universal / All OS):**
```bash
docker run --privileged -d -p 20:20 -p 21:21 -p 22:22 -p 25:25 -p 53:53 -p 53:53/udp -p 80:80 -p 443:443 -p 3306:3306 -p 5432:5432 -p 6379:6379 -p 27017:27017 -p 9200:9200 -p 9300:9300 -p 15672:15672 -p 5672:5672 -p 888:888 -p 2025:2025 -p 7800:7800 -p 8080:8080 -p 8443:8443 -p 9001:9001 -p 8888:8888 -p 3000:3000 -p 8000:8000 -p 39000-39009:39000-39009 --name=supanel_server ghcr.io/skilledu/supanel:latest
```

---

### Method 2: Download Tar File (Offline Air-gapped Installation)
**Best for:** Local enterprise networks, offline setups, or extremely slow internet connections.

#### 1. Download the Supanel Tar File
```bash
# Using wget
wget https://github.com/skilledu/supanel/releases/download/supanel/supanel.tar

# Or using curl
curl -L -o supanel.tar https://github.com/skilledu/supanel/releases/download/supanel/supanel.tar
```

#### 2. Load the Docker Image
```bash
# Extract the tar archive into Docker
docker load -i supanel.tar

# Verify the image was successfully loaded
docker images | grep supanel
```

#### 3. Run the Offline Supanel Container
*Note: This command uses the local `supanel:latest` image tag rather than the cloud `ghcr.io` link.*

**For Linux & macOS Terminal:**
```bash
docker run --privileged -d \
  -p 20:20 -p 21:21 -p 22:22 -p 25:25 \
  -p 53:53 -p 53:53/udp -p 80:80 -p 443:443 \
  -p 3306:3306 -p 5432:5432 -p 6379:6379 \
  -p 27017:27017 -p 9200:9200 -p 9300:9300 \
  -p 15672:15672 -p 5672:5672 -p 888:888 \
  -p 2025:2025 -p 7800:7800 -p 8080:8080 \
  -p 8443:8443 -p 9001:9001 -p 8888:8888 \
  -p 3000:3000 -p 8000:8000 \
  -p 39000-39009:39000-39009 \
  --name=supanel_server \
  supanel:latest
```

**For Windows PowerShell:**
```powershell
docker run --privileged -d `
  -p 20:20 -p 21:21 -p 22:22 -p 25:25 `
  -p 53:53 -p 53:53/udp -p 80:80 -p 443:443 `
  -p 3306:3306 -p 5432:5432 -p 6379:6379 `
  -p 27017:27017 -p 9200:9200 -p 9300:9300 `
  -p 15672:15672 -p 5672:5672 -p 888:888 `
  -p 2025:2025 -p 7800:7800 -p 8080:8080 `
  -p 8443:8443 -p 9001:9001 -p 8888:8888 `
  -p 3000:3000 -p 8000:8000 `
  -p 39000-39009:39000-39009 `
  --name=supanel_server `
  supanel:latest
```

**One-line command (Universal / All OS):**
```bash
docker run --privileged -d -p 20:20 -p 21:21 -p 22:22 -p 25:25 -p 53:53 -p 53:53/udp -p 80:80 -p 443:443 -p 3306:3306 -p 5432:5432 -p 6379:6379 -p 27017:27017 -p 9200:9200 -p 9300:9300 -p 15672:15672 -p 5672:5672 -p 888:888 -p 2025:2025 -p 7800:7800 -p 8080:8080 -p 8443:8443 -p 9001:9001 -p 8888:8888 -p 3000:3000 -p 8000:8000 -p 39000-39009:39000-39009 --name=supanel_server supanel:latest
```

---

## ✅ Step 3: Verification & Initializing the Panel

### 1. Verify the Container is Running
After executing the run command, verify that the Docker container is active:
```bash
docker ps
```
You should see `supanel_server` listed in the output with an "Up" status.

### 2. Start the Internal aaPanel Service
Supanel requires the internal aaPanel services to be initialized before you can log in:
```bash
# Access the active container
docker exec -it supanel_server bash

# Start the aaPanel background service
sudo bt 3
```

> **Important Architecture Note**: This container comes natively integrated with **[aaPanel](https://www.aapanel.com/)**, an enterprise-grade open-source hosting control panel managing over 3,000,000 servers worldwide since 2017.

---

## 🌐 Accessing the Supanel Server UI

Once initialized, the **Supanel control panel** will be accessible through your browser. 

### Web Interface Access URL
- **Admin Panel**: [http://localhost:2025/supanel](http://localhost:2025/supanel)  
*(If installing on a remote VPS, replace `localhost` with your public server IP).*

### Default Authentication Credentials
- **Username**: `skilledu`
- **Password**: `skilledu`

---

## ⚙️ Container Management Commands

As a server administrator, you can easily manage the lifecycle of your **Supanel installation** using these standard Docker commands:

### Stop the Server Safely
```bash
docker stop supanel_server
```

### Restart / Start the Server
```bash
docker start supanel_server
```

### Completely Remove the Server Instance
```bash
docker stop supanel_server
docker rm supanel_server
```

### 📌 Critical Deployment Notes
- The `--privileged` flag is strictly required for the container to access system-level functions (like managing internal firewall settings).
- The server exposes multiple ports intentionally to support HTTP/HTTPS, MySQL, Redis, DNS, and FTP functionality natively.
- The container name is fixed to `supanel_server` for easier management.

---

*Need help? Visit [Skilled.u](https://skilledu.in/) for professional server management courses and expert tutorials.*
