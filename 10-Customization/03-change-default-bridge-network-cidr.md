# 🌉 Change Default Docker Bridge Network CIDR

## 🤔 Why Change Default Bridge CIDR?

Docker creates a default bridge network called:

```text
docker0
```

By default, Docker usually assigns a subnet like:

```text
172.17.0.0/16
```

Sometimes this can conflict with:

- 🏢 Company VPN networks
- ☁️ Cloud networks
- 🖥️ Existing local networks
- 🌐 Internal infrastructure IP ranges

To avoid conflicts, you can change the bridge network CIDR.

---

# 📋 Step 1: Stop Docker Service

```bash
sudo systemctl stop docker
```

---

# ⚙️ Step 2: Edit Docker Configuration

Open:

```text
/etc/docker/daemon.json
```

Add:

```json
{
  "bip": "192.168.100.1/24"
}
```

Here:

- `bip` → Bridge IP
- `192.168.100.1/24` → New bridge CIDR

Docker will create:

```text
192.168.100.0/24
```

network range.

---

# 📝 Example with Existing Config

```json
{
  "data-root": "/data/docker",
  "bip": "192.168.100.1/24"
}
```

---

# 🚀 Step 3: Restart Docker

Reload systemd:

```bash
sudo systemctl daemon-reload
```

Start Docker:

```bash
sudo systemctl start docker
```

---

# 🔍 Step 4: Verify Changes

Check bridge details:

```bash
ip addr show docker0
```

Example:

```text
docker0: 192.168.100.1
```

---

# 🔍 Alternative Verification

```bash
docker network inspect bridge
```

Look for:

```json
"Subnet": "192.168.100.0/24"
```

---

# 🧭 High-Level Workflow

```text
Stop Docker ⛔
      ↓
Edit daemon.json ⚙️
      ↓
Set new CIDR 🌐
      ↓
Restart Docker 🚀
      ↓
Verify docker0 ✅
```

---

# 🚨 Common Beginner Mistakes

## ❌ 1. Invalid CIDR

Wrong:

```json
{
"bip":"192.168.100"
}
```

Correct:

```json
{
"bip":"192.168.100.1/24"
}
```

---

## ❌ 2. Choosing Existing Network Range

Bad:

```text
192.168.1.0/24
```

if already used by WiFi/VPN.

Can create routing conflicts ⚠️

---

## ❌ 3. Forgetting Docker Restart

Changes apply only after restart.

---

## ❌ 4. Editing While Docker Is Running

Stop Docker before major network changes.

---

# 📝 Quick Summary

| File / Command | Purpose |
|---|---|
| `/etc/docker/daemon.json` | ⚙️ Docker configuration |
| `"bip"` | 🌐 Set bridge IP/CIDR |
| `systemctl restart docker` | 🚀 Apply changes |
| `ip addr show docker0` | 🔍 Verify IP |
| `docker network inspect bridge` | 📋 Check subnet |

---

# 🎯 Final Understanding

```text
Default:
docker0 → 172.17.0.0/16

Change Config ⚙️
        ↓
Restart Docker 🚀
        ↓
docker0 → 192.168.100.0/24
```

Changing the bridge CIDR helps avoid network conflicts with other environments.