# 🔄 Docker Container Restart Policy

## 🤔 What is a Restart Policy?

A restart policy tells Docker:
> "What should I do if the container stops?"

Docker can:
- 🔁 Restart the container automatically
- ⛔ Not restart it
- 🚀 Restart after system reboot

This is useful for:
- 🌐 Web servers
- 🗄️ Databases
- ⚙️ Backend services

---

# 🧾 Basic Syntax

```bash
docker run --restart <policy> <image>
```

Example:

```bash
docker run --restart always nginx
```

---

# 🚀 Available Restart Policies

| Policy | Meaning |
|---|---|
| `no` | ⛔ Never restart container |
| `always` | 🔁 Always restart container |
| `unless-stopped` | 🔄 Restart unless manually stopped |
| `on-failure` | 🚨 Restart only if container exits with error |

---

# ⛔ 1. `no` (Default)

```bash
docker run --restart no nginx
```

Behavior:
- Container stops ❌
- Docker does NOT restart it

This is the default policy.

---

# 🔁 2. `always`

```bash
docker run --restart always nginx
```

Behavior:
- If container crashes 💥 → restart
- If Docker restarts 🔄 → restart
- If system reboots 🖥️ → restart

Useful for:
- 🌐 Production servers
- ⚙️ Critical applications

---

# 🔄 3. `unless-stopped`

```bash
docker run --restart unless-stopped nginx
```

Behavior:
- Restart automatically ✅
- BUT if you manually stop it:
  
```bash
docker stop my-nginx
```

Docker will NOT restart it automatically.

Useful when:
- You want auto-restart
- But manual stop should be respected

---

# 🚨 4. `on-failure`

```bash
docker run --restart on-failure nginx
```

Behavior:
- Restart only if container exits with error ❌
- Normal stop does NOT restart

Useful for:
- 🧪 Batch jobs
- 🔄 Retry-based workloads

---

# 🔢 Restart with Retry Limit

```bash
docker run --restart on-failure:5 nginx
```

Meaning:
- Retry maximum 5 times

Prevents infinite restart loops 🔁

---

# 📋 Check Restart Policy

```bash
docker inspect <container-name>
```

Example:

```bash
docker inspect my-nginx
```

Look for:

```json
"RestartPolicy"
```

---

# 🛠️ Update Restart Policy

You can change restart policy for existing container:

```bash
docker update --restart always my-nginx
```

---

# ⚙️ What Happens Internally?

When container stops:
1. Docker daemon detects exit
2. Checks restart policy
3. Decides whether to restart container
4. Starts container again if policy allows

---

# 🌍 Real-World Example

## Run Nginx with Auto Restart

```bash
docker run -d \
  --name my-nginx \
  --restart unless-stopped \
  -p 8080:80 \
  nginx
```

This container:
- 💤 Runs in background
- 🔄 Restarts automatically
- 🌐 Exposes port 8080

---

# 🚨 Common Beginner Mistakes

## ❌ 1. Thinking Restart Policy Saves Data

Restart policy only restarts container.

It does NOT:
- 💾 Save data
- 📦 Backup files

Use volumes for persistent storage.

---

## ❌ 2. Infinite Crash Loop

Bad application config can cause:

```text
Crash → Restart → Crash → Restart
```

Use:

```bash
on-failure:5
```

to limit retries.

---

## ❌ 3. Confusing `always` and `unless-stopped`

| Policy | Manual Stop Behavior |
|---|---|
| `always` | 🔁 Restarts again |
| `unless-stopped` | ⛔ Stays stopped |

---

# 📝 Quick Summary

| Policy | Behavior |
|---|---|
| `no` | ⛔ Never restart |
| `always` | 🔁 Always restart |
| `unless-stopped` | 🔄 Restart unless manually stopped |
| `on-failure` | 🚨 Restart only on error |

---

# ⚡ Most Common Example

```bash
docker run -d --restart unless-stopped nginx
```

Very commonly used for:
- 🌐 Web servers
- 🗄️ Databases
- ⚙️ APIs
- 🚀 Backend services