# 🚀 Supanel Installation Guide

Choose the installation method that works best for you.

## Prerequisites

- Docker installed on your system
- Internet connection (for Method 1)

## Docker Installation

If you don't have Docker installed, follow these steps:

### For Ubuntu/Debian:
```bash
# Update package index
sudo apt update

# Install required packages
sudo apt install apt-transport-https ca-certificates curl gnupg lsb-release

# Add Docker's official GPG key
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

# Add Docker repository
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

# Update package index again
sudo apt update

# Install Docker
sudo apt install docker-ce docker-ce-cli containerd.io

# Start and enable Docker service
sudo systemctl start docker
sudo systemctl enable docker

# Add your user to docker group (optional, to run docker without sudo)
sudo usermod -aG docker $USER
```

### For CentOS/RHEL:
```bash
# Install required packages
sudo yum install -y yum-utils

# Add Docker repository
sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo

# Install Docker
sudo yum install docker-ce docker-ce-cli containerd.io

# Start and enable Docker service
sudo systemctl start docker
sudo systemctl enable docker

# Add your user to docker group (optional, to run docker without sudo)
sudo usermod -aG docker $USER
```

### For macOS:
1. Download Docker Desktop from: https://www.docker.com/products/docker-desktop
2. Install the downloaded .dmg file
3. Launch Docker Desktop from Applications

### For Windows:
1. Download Docker Desktop from: https://www.docker.com/products/docker-desktop
2. Install the downloaded .exe file
3. Restart your computer if prompted
4. Launch Docker Desktop

### Verify Docker Installation:
```bash
docker --version
docker run hello-world
```

## Installation Methods

### Method 1: Direct Internet Download (Recommended)
**Best for:** Users with good internet connection

#### Step 1: Download Image
```bash
docker pull ghcr.io/skilledu/supanel:latest
```

#### Step 2: Run Container
**For Linux/macOS:**
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


**One-line command (All OS):**
```bash
docker run --privileged -d -p 20:20 -p 21:21 -p 22:22 -p 25:25 -p 53:53 -p 53:53/udp -p 80:80 -p 443:443 -p 3306:3306 -p 5432:5432 -p 6379:6379 -p 27017:27017 -p 9200:9200 -p 9300:9300 -p 15672:15672 -p 5672:5672 -p 888:888 -p 2025:2025 -p 7800:7800 -p 8080:8080 -p 8443:8443 -p 9001:9001 -p 8888:8888 -p 3000:3000 -p 8000:8000 -p 39000-39009:39000-39009 --name=supanel_server ghcr.io/skilledu/supanel:latest
```


### Method 2: Download Tar File (Offline Installation)
**Best for:** Users with slow internet or offline installation needs

#### Step 1: Download Tar File
```bash
# Using wget
wget https://github.com/skilledu/supanel/releases/download/supanel/supanel.tar

# Or using curl
curl -L -o supanel.tar https://github.com/skilledu/supanel/releases/download/supanel/supanel.tar
```


#### Step 2: Load Image
```bash
# Load the tar file as Docker image
docker load -i supanel.tar

# Verify the image is loaded
docker images | grep supanel
```


#### Step 3: Run Container
**For Linux/macOS:**
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


**One-line command (All OS):**
```bash
docker run --privileged -d -p 20:20 -p 21:21 -p 22:22 -p 25:25 -p 53:53 -p 53:53/udp -p 80:80 -p 443:443 -p 3306:3306 -p 5432:5432 -p 6379:6379 -p 27017:27017 -p 9200:9200 -p 9300:9300 -p 15672:15672 -p 5672:5672 -p 888:888 -p 2025:2025 -p 7800:7800 -p 8080:8080 -p 8443:8443 -p 9001:9001 -p 8888:8888 -p 3000:3000 -p 8000:8000 -p 39000-39009:39000-39009 --name=supanel_server supanel:latest
```


## Verification

After running the command, you can verify that the container is running:

```bash
docker ps
```

You should see the `supanel_server` container in the running state.

## Accessing the Server

The Supanel server will be accessible on various ports as configured in the Docker run command.

### Web Interface Access
- **Admin Panel**: https://localhost:2025/supanel

### Default Credentials
- **Username**: `skilledu`
- **Password**: `skilledu`

## Start aaPanel Service

After the container is running, you need to start the aaPanel service inside the container:

```bash
# Access the container
docker exec -it supanel_server bash

# Start aaPanel service
sudo bt 3
```


**Note**: This container includes [aaPanel](https://www.aapanel.com/) - a free and open-source hosting control panel that has been installed on more than 3,000,000+ servers since 2017.

## Container Management

### Stopping the Server
To stop the server:
```bash
docker stop supanel_server
```

### Starting the Server Again
To start the server again:
```bash
docker start supanel_server
```

### Removing the Server
To completely remove the server:
```bash
docker stop supanel_server
docker rm supanel_server
```

## Notes

- The `--privileged` flag is required for the server to function properly
- The server exposes multiple ports for different services and protocols
- The container is named `supanel_server` for easy management
