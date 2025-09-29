# 📘 py-sandbox-debian

A Debian-based Docker image with:
- OpenSSH server
- Python3

Enables SSH access as the root user.

## 🔧 Build and Push to Docker Hub

```bash
docker buildx build --platform linux/amd64,linux/arm64 -t vheikkiniemi/py-sandbox-debian:v1.0 --push .
```

## ▶️ Run with docker-compose

```bash
docker-compose up -d
```

## 🔐 Connect via SSH

```bash
ssh root@localhost -p 2222
```

> Default password: `DockerPassword123` (change this to something secure!)

## 💻 Connect with Visual Studio Code

1. Install the **Remote - SSH** extension
2. Add the following to your `~/.ssh/config`:

```ssh
Host py-sandbox-debian
    HostName localhost
    User root
    Port 2222
```

3. Open Command Palette (Ctrl+Shift+P) → `Remote-SSH: Connect to Host...` → select `docker-debian`


---

## ✅ How to Check if a Container is Running

### Show only running containers:

```bash
docker ps
```

This will list all currently running containers. If your container (e.g. `py-sandbox-debian`) appears here, it is running.

### Show all containers (including stopped ones):

```bash
docker ps -a
```

This shows both running and stopped containers. Look at the `STATUS` column:
- `Up` = running
- `Exited` = stopped

---

## 🗑️ How to Remove a Container

### 1. Stop the container (if it's running):

```bash
docker stop py-sandbox-debian
```

### 2. Remove the container:

```bash
docker rm py-sandbox-debian
```