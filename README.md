# Supanel Server Installation

**Developed by [Skilled.u](https://skilledu.in/) - Master Essential Technical Skills**

Supanel is a powerful server management solution developed by Skilled.u. Choose your preferred installation method below.

## 📚 Quick Navigation

- **[🚀 Quick Installation](installation.md)** - Get started in minutes
- **[💻 VS Code Integration](vscode-integration.md)** - Development setup
- **[🎯 About Skilled.u](about-skilledu.md)** - Learn about our courses
- **[❓ Troubleshooting](troubleshooting.md)** - Common issues and solutions

## 🚀 Quick Start

### Method 1: Direct Internet Download (Recommended)
```bash
# Download and run in one command
docker run --privileged -d -p 20:20 -p 21:21 -p 22:22 -p 25:25 -p 53:53 -p 53:53/udp -p 80:80 -p 443:443 -p 3306:3306 -p 5432:5432 -p 6379:6379 -p 27017:27017 -p 9200:9200 -p 9300:9300 -p 15672:15672 -p 5672:5672 -p 888:888 -p 2025:2025 -p 7800:7800 -p 8080:8080 -p 8443:8443 -p 9001:9001 -p 8888:8888 -p 3000:3000 -p 8000:8000 -p 39000-39009:39000-39009 --name=supanel_server ghcr.io/skilledu/supanel:latest
```

### Method 2: Download Tar File (Offline)
```bash
# Download tar file
wget https://github.com/skilledu/supanel/releases/download/supanel/supanel.tar

# Load and run
docker load -i supanel.tar
docker run --privileged -d -p 20:20 -p 21:21 -p 22:22 -p 25:25 -p 53:53 -p 53:53/udp -p 80:80 -p 443:443 -p 3306:3306 -p 5432:5432 -p 6379:6379 -p 27017:27017 -p 9200:9200 -p 9300:9300 -p 15672:15672 -p 5672:5672 -p 888:888 -p 2025:2025 -p 7800:7800 -p 8080:8080 -p 8443:8443 -p 9001:9001 -p 8888:8888 -p 3000:3000 -p 8000:8000 -p 39000-39009:39000-39009 --name=supanel_server supanel:latest
```

## 🌐 Access Your Server

Once running, access your Supanel admin panel at:
- **Admin Panel**: https://localhost:2025/supanel

### Default Credentials
- **Username**: `skilledu`
- **Password**: `skilledu`

## 🚀 Start aaPanel Service

After the container is running, you need to start the aaPanel service inside the container:

```bash
# Access the container
docker exec -it supanel_server bash

# Start aaPanel service
sudo bt 3
```


**Note**: This container includes [aaPanel](https://www.aapanel.com/) - a free and open-source hosting control panel that has been installed on more than 3,000,000+ servers since 2017.

## 📞 Need Help?

- **📧 Email**: info@skilledu.in
- **📞 Phone**: +91 89890 99962
- **🌐 Website**: [https://skilledu.in/](https://skilledu.in/)

---

*For detailed installation instructions, VS Code setup, and troubleshooting, please refer to the individual README files linked above.*
