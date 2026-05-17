# ⏹️ How to Stop a Docker Container

## 🤔 Why Do We Stop Containers?

Containers keep running in the background until they are stopped.

You may want to stop a container to:
- 🛠️ Save system resources
- 🔄 Restart the application
- 🐞 Fix issues
- 🗑️ Remove the container later

---

# 🧾 Basic Command

```bash
docker stop <container-id>
```

or

```bash
docker stop <container-name>
```

---

# ✅ Example Using Container ID

```bash
docker stop abc123
```

Here:
- `abc123` → Container ID

---

# ✅ Example Using Container Name

```bash
docker stop my-nginx
```

Here:
- `my-nginx` → Container name

---

# 📋 Find Running Containers

Before stopping a container, first check running containers:

```bash
docker ps
```

Example output:

```bash
CONTAINER ID   IMAGE   NAMES
abc123         nginx   my-nginx
```

You can stop using:
- 📌 Container ID
- 🏷️ Container name

---

# ⚙️ What Happens Internally?

When you run:

```bash
docker stop my-nginx
```

Docker:
1. 📩 Sends a stop signal to the container
2. ⏳ Gives it some time to shut down safely
3. ⏹️ Stops the container

---

# 📋 Check Stopped Containers

```bash
docker ps -a
```

Stopped containers appear with status like:

```text
Exited
```

---

# 🚀 Start a Stopped Container Again

```bash
docker start my-nginx
```

This starts the stopped container again.

---

# ❌ Force Stop a Container

Sometimes a container does not stop normally.

Use:

```bash
docker kill <container-id>
```

Example:

```bash
docker kill my-nginx
```

⚠️ `docker kill` immediately stops the container without waiting.

---

# 🚨 Common Beginner Mistakes

## ❌ 1. Using Image Name Instead of Container Name

Wrong:

```bash
docker stop nginx
```

This only works if the container name is actually `nginx`.

Always check with:

```bash
docker ps
```

---

## ❌ 2. Trying to Stop an Already Stopped Container

Docker shows an error if the container is already stopped.

---

## ❌ 3. Confusing `stop` and `rm`

- ⏹️ `docker stop` → Stops container
- 🗑️ `docker rm` → Removes container

Stopping does NOT remove the container.

---

# 📝 Quick Summary

| Command | Purpose |
|---|---|
| `docker ps` | 📋 Show running containers |
| `docker stop <id>` | ⏹️ Stop container |
| `docker start <id>` | 🚀 Start stopped container |
| `docker kill <id>` | ❌ Force stop container |
| `docker ps -a` | 📋 Show all containers |