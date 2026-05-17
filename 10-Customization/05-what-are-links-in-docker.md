# 🔗 What are Links in Docker?

## 🤔 What is Docker Link?

Docker links were an old feature used to connect containers and allow them to communicate with each other.

Links helped containers:

- 📦 Discover other containers
- 🌐 Share networking information
- 🔗 Access linked containers by name
- 🌱 Pass environment variables

Think of it like:

> "Connect one container to another using a shortcut"

---

# 🧾 Basic Syntax

```bash
docker run --link <source-container>:<alias> <image>
```

---

# ✅ Example

Start database container:

```bash
docker run -d --name db mysql
```

Start app container:

```bash
docker run -it --link db:mysql-app ubuntu
```

Here:

- `db` → Existing container
- `mysql-app` → Alias name

Inside container:

```bash
ping mysql-app
```

Container can reach database ✅

---

# 🧭 High-Level View

```text
Database Container 📦
        ↓
Docker Link 🔗
        ↓
Application Container 📦
```

---

# ⚙️ What Happened Internally?

Docker automatically:

- 🌐 Added networking information
- 📝 Updated `/etc/hosts`
- 🌱 Added environment variables

Example:

```text
MYSQL_APP_PORT
MYSQL_APP_NAME
```

---

# 📋 Check Hosts File

Inside container:

```bash
cat /etc/hosts
```

You may see:

```text
172.17.0.2 mysql-app
```

Docker inserted the mapping automatically.

---

# 🚨 Important: Links Are Legacy

Docker links are considered:

```text
Legacy / Deprecated ⚠️
```

Modern Docker networking replaced links.

Today we use:

```bash
docker network create my-network
```

Containers on same custom network can communicate directly using names.

---

# ✅ Modern Alternative

Create network:

```bash
docker network create app-net
```

Run containers:

```bash
docker run -d --name db \
--network app-net mysql

docker run -d --name app \
--network app-net ubuntu
```

Now:

```bash
ping db
```

works automatically ✅

No `--link` needed.

---

# 🔄 Links vs Custom Networks

| Feature | Links 🔗 | Custom Network 🌉 |
|---|---:|---:|
| Container name resolution | Limited | ✅ |
| Scalable | ❌ | ✅ |
| Modern approach | ❌ | ✅ |
| Deprecated | ✅ | ❌ |

---

# 🚨 Common Beginner Mistakes

## ❌ 1. Learning Links for New Projects

Use:

```bash
docker network
```

instead.

---

## ❌ 2. Thinking Links Work Across Hosts

Links only worked on same Docker host.

---

## ❌ 3. Assuming Links Are Recommended

Docker networking replaced them long ago.

---

# 📝 Quick Summary

- 🔗 Links connected containers
- 🌐 Added hostname and environment variables
- ⚠️ Considered deprecated
- 🌉 Custom networks replaced links
- ✅ Use user-defined bridge networks today

---

# 🎯 Final Understanding

```text
Old Way:
Container A 📦
      ↓
Link 🔗
      ↓
Container B 📦


Modern Way:
Container A 📦
      ↓
Custom Network 🌉
      ↓
Container B 📦
```

Docker links were an early way of connecting containers, but custom networks are now the preferred solution.