# 📁 Change Default Docker Root Directory

## 🤔 What is Docker Root Directory?

Docker stores its data in a default location.

On Linux 🐧:

```text
/var/lib/docker
```

This directory stores:

- 📦 Images
- 🚀 Containers
- 💾 Volumes
- 🌐 Networks
- 📚 Image layers
- 📝 Logs

Sometimes you may want to move it because:

- 💾 Disk is full
- ⚡ Faster storage available
- 🗄️ Separate partition for Docker data

---

# 📋 Step 1: Stop Docker Service

```bash
sudo systemctl stop docker
```

Verify:

```bash
sudo systemctl status docker
```

---

# 📁 Step 2: Create New Directory

Example:

```bash
sudo mkdir -p /data/docker
```

New Docker root path:

```text
/data/docker
```

---

# 📂 Step 3: Copy Existing Docker Data

```bash
sudo rsync -avxP /var/lib/docker/ /data/docker
```

This copies:

- 📦 Images
- 🚀 Containers
- 💾 Volumes
- 📚 Metadata

---

# ⚙️ Step 4: Edit Docker Configuration

Create or edit:

```text
/etc/docker/daemon.json
```

Add:

```json
{
  "data-root": "/data/docker"
}
```

---

# 📋 Step 5: Reload Systemd

```bash
sudo systemctl daemon-reload
```

---

# 🚀 Step 6: Start Docker

```bash
sudo systemctl start docker
```

Enable startup:

```bash
sudo systemctl enable docker
```

---

# 🔍 Step 7: Verify New Docker Root Directory

Run:

```bash
docker info | grep "Docker Root Dir"
```

Output:

```text
Docker Root Dir: /data/docker
```

Success ✅

---

# 🧭 High-Level Workflow

```text
Stop Docker ⛔
      ↓
Create New Directory 📁
      ↓
Copy Existing Data 📂
      ↓
Update daemon.json ⚙️
      ↓
Restart Docker 🚀
      ↓
Verify Changes ✅
```

---

# 🚨 Common Beginner Mistakes

## ❌ 1. Forgetting to Stop Docker

Copying data while Docker runs can cause corruption.

---

## ❌ 2. Moving Without Copying Existing Data

Images and containers may disappear.

---

## ❌ 3. Invalid JSON

Wrong:

```json
{
data-root:/data/docker
}
```

Correct:

```json
{
  "data-root": "/data/docker"
}
```

---

## ❌ 4. Deleting Old Data Too Early

Keep:

```text
/var/lib/docker
```

until Docker starts correctly.

---

# 📝 Quick Summary

| Command | Purpose |
|---|---|
| `systemctl stop docker` | ⛔ Stop Docker |
| `rsync -avxP ...` | 📂 Copy data |
| Edit `daemon.json` | ⚙️ Change root path |
| `systemctl start docker` | 🚀 Start Docker |
| `docker info` | 🔍 Verify location |

---

# 🎯 Final Understanding

```text
Old Location
/var/lib/docker
        ↓
Move Data 📂
        ↓
Update Docker Config ⚙️
        ↓
New Location
/data/docker
```

Docker can store all its data in a custom directory instead of the default path.