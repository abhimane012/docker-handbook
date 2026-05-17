# 🚀 How to Create and Run a Docker Container

## 🤔 What is a Container?

A container is a running instance of a Docker image.

Think of it like this:
- 📦 Image → Blueprint/template
- 🚀 Container → Running application

Example:
- 📦 Image = Cake recipe
- 🎂 Container = Actual baked cake

---

# 🧾 Basic Command

```bash
docker run <image-name>
```

---

# ✅ Example

```bash
docker run nginx
```

This command:
1. 📥 Pulls the image (if not already downloaded)
2. 🚀 Creates a container
3. ▶️ Starts the container

---

# ⚙️ What Happens Internally?

When you run:

```bash
docker run nginx
```

Docker:
1. 🔍 Checks if the image exists locally
2. 📥 Downloads it if missing
3. 📦 Creates a new container
4. 🚀 Starts the container

---

# 📋 Check Running Containers

```bash
docker ps
```

Example output:

```bash
CONTAINER ID   IMAGE   COMMAND   STATUS
abc123         nginx   ...       Up 10 seconds
```

---

# 📋 Check All Containers

```bash
docker ps -a
```

This shows:
- ▶️ Running containers
- ⏹️ Stopped containers

---

# 🏷️ Run Container with a Name

```bash
docker run --name my-nginx nginx
```

Here:
- 🏷️ `my-nginx` → Custom container name

Without a name, Docker automatically generates one.

---

# 🌐 Run Container in Background

```bash
docker run -d nginx
```

`-d` means:
- 💤 Detached mode
- Runs container in background

---

# 🔌 Run Container with Port Mapping

```bash
docker run -p 8080:80 nginx
```

Here:
- 🌍 `8080` → Port on your machine
- 📦 `80` → Port inside container

Now you can open:

```text
http://localhost:8080
```

in your browser 🌐

---

# 🛠️ Commonly Used Options

| Option | Meaning |
|---|---|
| `-d` | 💤 Run in background |
| `--name` | 🏷️ Give custom name |
| `-p` | 🔌 Port mapping |
| `-it` | 💻 Interactive terminal |
| `--rm` | 🗑️ Remove container after stop |

---

# 💻 Run Interactive Container

```bash
docker run -it ubuntu bash
```

This gives you a terminal inside the container.

Here:
- `-i` → Keep input open
- `-t` → Open terminal
- `bash` → Start bash shell

---

# ❌ Stop a Running Container

```bash
docker stop <container-id>
```

Example:

```bash
docker stop abc123
```

---

# 🗑️ Remove a Container

```bash
docker rm <container-id>
```

Example:

```bash
docker rm abc123
```

---

# 🚨 Common Beginner Mistakes

## ❌ 1. Forgetting Port Mapping

```bash
docker run nginx
```

Nginx runs, but you cannot access it from browser without `-p`.

Correct:

```bash
docker run -p 8080:80 nginx
```

---

## ❌ 2. Using Same Port Twice

```bash
docker run -p 8080:80 nginx
docker run -p 8080:80 nginx
```

This fails because port `8080` is already in use.

---

## ❌ 3. Confusing Image and Container

- 📦 Image = Template
- 🚀 Container = Running instance

One image can create multiple containers.

---

# 📝 Quick Summary

| Command | Purpose |
|---|---|
| `docker run nginx` | 🚀 Create and start container |
| `docker run -d nginx` | 💤 Run in background |
| `docker run --name myapp nginx` | 🏷️ Give container name |
| `docker run -p 8080:80 nginx` | 🔌 Map ports |
| `docker ps` | 📋 Show running containers |
| `docker ps -a` | 📋 Show all containers |
| `docker stop <id>` | ⏹️ Stop container |
| `docker rm <id>` | 🗑️ Remove container |