# ❓ Troubleshooting Guide

Common issues and solutions for Supanel server installation and usage.

## Installation Issues

### Docker Not Installed
**Problem**: `docker: command not found`

**Solution**:
1. Install Docker following the instructions in [installation.md](installation.md)
2. For Ubuntu/Debian:
   ```bash
   sudo apt update
   sudo apt install docker.io
   sudo systemctl start docker
   sudo systemctl enable docker
   ```
3. For Windows/macOS: Download Docker Desktop from https://www.docker.com/products/docker-desktop

### Permission Denied
**Problem**: `permission denied while trying to connect to the Docker daemon socket`

**Solution**:
```bash
# Add your user to docker group
sudo usermod -aG docker $USER

# Log out and log back in, or run:
newgrp docker

# Or run with sudo
sudo docker run ...
```

### Port Already in Use
**Problem**: `bind: address already in use`

**Solution**:
1. Check which process is using the port:
   ```bash
   # For Linux/macOS
   sudo lsof -i :80
   
   # For Windows
   netstat -ano | findstr :80
   ```
2. Stop the conflicting service or use different ports
3. Or stop the existing container:
   ```bash
   docker stop supanel_server
   docker rm supanel_server
   ```

### Image Pull Failed
**Problem**: `Error response from daemon: pull access denied`

**Solution**:
1. Check internet connection
2. Try pulling again:
   ```bash
   docker pull ghcr.io/skilledu/supanel:latest
   ```
3. If still failing, use the tar file method from [installation.md](installation.md)

## Container Issues

### Container Won't Start
**Problem**: Container exits immediately after starting

**Solution**:
1. Check container logs:
   ```bash
   docker logs supanel_server
   ```
2. Make sure you're using the `--privileged` flag
3. Check if all required ports are available
4. Verify Docker has enough resources allocated
5. Start the aaPanel service inside the container:
   ```bash
   docker exec -it supanel_server bash
   sudo bt 3
   ```

### Container Not Accessible
**Problem**: Can't access admin panel at localhost:2025/supanel

**Solution**:
1. Verify container is running:
   ```bash
   docker ps
   ```
2. Check port mapping:
   ```bash
   docker port supanel_server
   ```
3. Access admin panel: https://localhost:2025/supanel
4. Use default credentials:
   - Username: `skilledu`
   - Password: `skilledu`

### Container Keeps Restarting
**Problem**: Container status shows "Restarting"

**Solution**:
1. Check logs for errors:
   ```bash
   docker logs supanel_server
   ```
2. Increase Docker memory allocation in Docker Desktop settings
3. Check system resources (RAM, CPU)
4. Restart Docker Desktop

## VS Code Integration Issues

### Container Not Showing in VS Code
**Problem**: Can't see container in Remote Explorer

**Solution**:
1. Make sure container is running: `docker ps`
2. Restart VS Code
3. Refresh Remote Explorer (click refresh button)
4. Check if Docker extension is installed and enabled

### Can't Connect to Container
**Problem**: VS Code fails to connect to container

**Solution**:
1. Check container status: `docker ps`
2. Verify container name is `supanel_server`
3. Try connecting via terminal first:
   ```bash
   docker exec -it supanel_server bash
   ```
4. Restart VS Code and try again

### Services Not Accessible in VS Code
**Problem**: Can't access localhost services from VS Code

**Solution**:
1. Verify port forwarding is working
2. Check if ports are properly mapped in docker run command
3. Try accessing services from host machine first
4. Check VS Code Remote Explorer settings

## Performance Issues

### Slow Container Performance
**Problem**: Container is slow or unresponsive

**Solution**:
1. Increase Docker resources in Docker Desktop settings
2. Close other applications to free up system resources
3. Check system memory and CPU usage
4. Restart Docker Desktop

### High Memory Usage
**Problem**: Container using too much memory

**Solution**:
1. Check container resource usage:
   ```bash
   docker stats supanel_server
   ```
2. Increase Docker memory limit in settings
3. Close unnecessary applications
4. Consider using a more powerful machine

## Network Issues

### Can't Access from Other Devices
**Problem**: Can't access server from other devices on network

**Solution**:
1. Use host network mode:
   ```bash
   docker run --network host --privileged -d --name=supanel_server ghcr.io/skilledu/supanel:latest
   ```
2. Or bind to all interfaces:
   ```bash
   docker run --privileged -d -p 0.0.0.0:80:80 --name=supanel_server ghcr.io/skilledu/supanel:latest
   ```

### SSL/HTTPS Issues
**Problem**: HTTPS not working or certificate errors

**Solution**:
1. Access admin panel: https://localhost:2025/supanel
2. Check if SSL certificates are properly configured
3. Check container logs for SSL-related errors
4. Use default credentials if login page appears:
   - Username: `skilledu`
   - Password: `skilledu`

## Data and Backup Issues

### Data Loss
**Problem**: Container data is lost after restart

**Solution**:
1. Use Docker volumes for persistent data:
   ```bash
   docker run --privileged -d -v supanel_data:/data --name=supanel_server ghcr.io/skilledu/supanel:latest
   ```
2. Backup important data before container updates
3. Use Docker Compose for better data management

### Can't Access Previous Data
**Problem**: Can't access data from previous container

**Solution**:
1. Check if old container still exists:
   ```bash
   docker ps -a
   ```
2. Start the old container:
   ```bash
   docker start <old_container_name>
   ```
3. Copy data from old container to new one

## Getting Help

### Still Having Issues?

1. **Check Logs**: Always check container logs first
   ```bash
   docker logs supanel_server
   ```

2. **Restart Everything**: Sometimes a simple restart helps
   ```bash
   docker stop supanel_server
   docker rm supanel_server
   # Run installation command again
   ```

3. **Contact Support**:
   - **📧 Email**: info@skilledu.in
   - **📞 Phone**: +91 89890 99962
   - **🌐 Website**: [https://skilledu.in/](https://skilledu.in/)

4. **Community Help**: Check our community forums and discussions

### Useful Commands

```bash
# Check container status
docker ps

# View container logs
docker logs supanel_server

# Access container terminal
docker exec -it supanel_server bash

# Check container resource usage
docker stats supanel_server

# Stop and remove container
docker stop supanel_server
docker rm supanel_server

# List all containers (including stopped)
docker ps -a

# Remove all stopped containers
docker container prune

# Check Docker version
docker --version

# Check Docker daemon status
docker info
```

### System Requirements

- **Minimum RAM**: 4GB (8GB recommended)
- **Minimum CPU**: 2 cores (4 cores recommended)
- **Disk Space**: 10GB free space
- **OS**: Windows 10+, macOS 10.14+, or Linux
- **Docker**: Version 20.10 or higher

Remember: Most issues can be resolved by checking logs, restarting the container, or ensuring proper resource allocation. When in doubt, contact our support team!
