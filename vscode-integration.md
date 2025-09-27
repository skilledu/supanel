# 💻 VS Code Integration Guide

Learn how to connect VS Code to your Supanel server for seamless development.

## Prerequisites for VS Code

Install these VS Code extensions:
1. **Remote Explorer** - For connecting to remote containers
2. **Dev Containers** - For development container support

## Step 1: Install VS Code Extensions

1. Open VS Code
2. Go to Extensions (Ctrl+Shift+X)
3. Search and install:
   - `Remote Explorer`
   - `Dev Containers`

## Step 2: Connect to Supanel Container

1. Open VS Code
2. Click on **Remote Explorer** icon in the sidebar
3. Select **Dev Containers** from the dropdown
4. Find `supanel_server` container in the list
5. Click the **Connect** button next to the container
6. VS Code will open a new window connected to the container

## Step 3: Access Server Services Locally

Once connected to the container via VS Code:

### Web Interface Access
- **Admin Panel**: https://localhost:2025/supanel

### Default Credentials
- **Username**: `skilledu`
- **Password**: `skilledu`

### Database Access
- **MySQL**: localhost:3306
- **PostgreSQL**: localhost:5432
- **Redis**: localhost:6379
- **MongoDB**: localhost:27017

### Other Services
- **Elasticsearch**: localhost:9200
- **RabbitMQ Management**: localhost:15672
- **RabbitMQ**: localhost:5672
- **FTP**: localhost:21
- **SSH**: localhost:22

## Step 4: Development Workflow

1. **File Management**: Edit files directly in VS Code
2. **Terminal Access**: Use integrated terminal for commands
3. **Service Management**: Start/stop services using terminal
4. **Log Monitoring**: View logs in real-time
5. **Port Forwarding**: All ports are automatically forwarded to localhost

## Step 5: Service Management in VS Code

```bash
# Access container terminal in VS Code
# Use Ctrl+` to open integrated terminal

# Start aaPanel service
sudo bt 3
```

## Benefits of VS Code Integration

- **Local Development**: Work on server files as if they're local
- **Integrated Terminal**: Run commands without leaving VS Code
- **File Explorer**: Browse and edit server files easily
- **Debugging**: Debug applications running in the container
- **Extensions**: Use VS Code extensions within the container
- **Git Integration**: Version control directly in the container

## Docker Desktop GUI Alternative

If you prefer a graphical interface:

### Step 1: Open Docker Desktop
1. Launch Docker Desktop application
2. Wait for Docker to start completely (green status indicator)

### Step 2: Pull Image via GUI
1. Go to **Images** tab in Docker Desktop
2. Click **Pull** button
3. Enter: `ghcr.io/skilledu/supanel:latest`
4. Click **Pull** to download the image

### Step 3: Create Container via GUI
1. Go to **Containers** tab
2. Click **Create** button
3. Fill in the following details:
   - **Image**: `ghcr.io/skilledu/supanel:latest`
   - **Container name**: `supanel_server`
   - **Ports**: Add all the ports mentioned in installation guide
   - **Advanced options**: Check "Privileged mode"
4. Click **Create** to start the container

### Step 4: Manage Container via GUI
- **Start**: Click the play button next to container name
- **Stop**: Click the stop button next to container name
- **Restart**: Click the restart button
- **View Logs**: Click on container name to see logs
- **Delete**: Click the delete button to remove container

## Troubleshooting

### Container Not Showing in VS Code
1. Make sure the container is running: `docker ps`
2. Restart VS Code
3. Refresh the Remote Explorer
4. Make sure you have **Dev Containers** extension installed
5. Select **Dev Containers** from the Remote Explorer dropdown

### Can't Connect to Services
1. Check if ports are properly mapped
2. Verify container is running: `docker ps`
3. Check container logs: `docker logs supanel_server`

### Permission Issues
1. Make sure you're using the `--privileged` flag
2. Check Docker Desktop settings for resource allocation
3. Restart Docker Desktop if needed
