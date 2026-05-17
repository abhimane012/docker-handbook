# 🌉 Docker Bridge Network

## 🤔 What is a Bridge Network?

A bridge network is the **default Docker network type**.

It allows containers on the same host to communicate with each other using an internal private network.

Think of it like:
> 🏠 A private LAN (local network) for containers on the same machine

---

# 🧾 Default Behavior

When you run a container without specifying a network:

```bash
docker run nginx
```

Docker automatically attaches it to the:

```text
bridge network
```

---

# 🧭 High-Level View

```text
Container A 📦   ←→   Bridge Network 🌉   ←→   Container B 📦
```

Containers can communicate using:
- 🌐 IP address
- 🏷️ Container name (if custom network is used)

---

# ⚙️ How It Works Internally

When a container starts in bridge network:

1. 🔌 Docker creates a virtual network interface
2. 🌐 Assigns a private IP address (like 172.x.x.x)
3. 🌉 Connects container to bridge (docker0)
4. 📡 Enables NAT for internet access

---

# 📋 Check Bridge Network

```bash
docker network ls
```

You will see:

```text
NETWORK ID     NAME      DRIVER
xxxxxxx        bridge    bridge
```

---

# 🔍 Inspect Bridge Network

```bash
docker network inspect bridge
```

Shows:
- 📦 Connected containers
- 🌐 IP addresses
- 🔧 Network settings

---

# 🚀 Example: Running Containers in Bridge Network

```bash
docker run -dit --name c1 nginx
docker run -dit --name c2 nginx
```

Both containers are now in the bridge network.

---

# 📡 Container Communication

Inside bridge network:

```text
c1 → c2 (via IP address)
c2 → c1 (via IP address)
```

But:
- ❌ Name-based communication is limited in default bridge network
- ⚠️ IP addresses can change when container restarts

---

# 🌍 Internet Access

Bridge network also allows containers to access the internet:

```text
Container → Bridge → Host NAT → Internet
```

Example:

```bash
apt update
curl google.com
```

Works inside container ✅

---

# 🧱 Custom Bridge Network (Recommended)

Instead of default bridge, you can create your own:

```bash
docker network create my-bridge
```

Run containers:

```bash
docker run -dit --name app1 --network my-bridge nginx
docker run -dit --name app2 --network my-bridge nginx
```

Now containers can:
- 🏷️ Talk using names
- 🔄 Resolve DNS automatically

---

# ⚠️ Default Bridge vs Custom Bridge

| Feature | Default Bridge 🌉 | Custom Bridge 🌉 |
|---|---|---|
| Container communication | IP only | Name + IP |
| DNS support | ❌ Limited | ✅ Yes |
| Recommended | ❌ No | ✅ Yes |
| Isolation | Basic | Better |

---

# 🚨 Common Beginner Mistakes

## ❌ 1. Using Default Bridge for Multi-Container Apps

Hard to manage due to IP-based communication.

---

## ❌ 2. Not Using Custom Networks

Best practice:

```bash
docker network create app-net
```

---

## ❌ 3. Assuming Containers Can Talk Without Network

Containers must be on same network to communicate.

---

# 📝 Quick Summary

- 🌉 Bridge network is Docker’s default network
- 📦 It connects containers on the same host
- 🌐 Provides internet access via NAT
- ⚠️ Default bridge uses IP-based communication
- ✅ Custom bridge is preferred for real applications

---

# 🎯 Final Understanding

```text
Container 📦
      ↓
Bridge Network 🌉
      ↓
Other Containers 📦 + Internet 🌍
```

Bridge network acts like a private LAN for containers on a single machine.