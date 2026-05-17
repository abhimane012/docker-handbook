# 🌉 Change Default Bridge Network to a Custom Network

## 🤔 Why Create a Custom Bridge Network?

Docker already provides a default bridge network:

```text
bridge
```

But custom bridge networks are usually preferred because they provide:

- 🏷️ Automatic container name resolution
- 🔒 Better isolation
- ⚙️ Easier management
- 🚀 Better multi-container communication

Instead of using:

```text
Default bridge
```

you can create your own custom network.

---

# 📋 Step 1: Create Custom Bridge Network

```bash
docker network create my-network
```

Docker creates:

```text
my-network
```

---

# 🔍 Verify Network

```bash
docker network ls
```

Example:

```bash
NETWORK ID      NAME
xxxxxx          bridge
yyyyyy          my-network
```

---

# 🚀 Step 2: Run Container in Custom Network

```bash
docker run -dit --name app1 \
--network my-network nginx
```

---

# 🚀 Run Another Container

```bash
docker run -dit --name app2 \
--network my-network nginx
```

Both containers now belong to:

```text
my-network
```

---

# 📡 Test Communication

Enter container:

```bash
docker exec -it app1 bash
```

Ping another container:

```bash
ping app2
```

Works using container name ✅

No IP address needed.

---

# 🧭 High-Level View

```text
Container app1 📦
        ↓
Custom Bridge Network 🌉
        ↓
Container app2 📦
```

---

# ⚙️ Optional: Create Custom Subnet

```bash
docker network create \
--subnet=192.168.200.0/24 \
my-network
```

Now Docker uses:

```text
192.168.200.x
```

range.

---

# 🔍 Inspect Network

```bash
docker network inspect my-network
```

Shows:

- 🌐 Subnet
- 📦 Connected containers
- ⚙️ Driver information

---

# 🚨 Important Clarification

You cannot replace Docker's built-in:

```text
bridge
```

network directly ❌

Instead:

- Create custom network ✅
- Run containers using that network ✅

---

# 🚨 Common Beginner Mistakes

## ❌ 1. Assuming Existing Containers Move Automatically

Old containers remain in:

```text
bridge
```

You must reconnect or recreate them.

---

## ❌ 2. Forgetting `--network`

Wrong:

```bash
docker run nginx
```

Container goes to default bridge.

Correct:

```bash
docker run --network my-network nginx
```

---

## ❌ 3. Using IP Addresses

Custom networks support:

```text
Container names
```

Prefer:

```bash
ping app2
```

instead of IPs.

---

# 📝 Quick Summary

| Command | Purpose |
|---|---|
| `docker network create my-network` | 🌉 Create custom network |
| `docker network ls` | 📋 List networks |
| `docker run --network my-network` | 🚀 Run container in network |
| `docker network inspect my-network` | 🔍 Show details |

---

# 🎯 Final Understanding

```text
Default Bridge 🌉
        ↓
Create Custom Network ⚙️
        ↓
Attach Containers 📦
        ↓
Better Communication 🚀
```

Custom bridge networks are preferred over the default bridge for real-world applications.