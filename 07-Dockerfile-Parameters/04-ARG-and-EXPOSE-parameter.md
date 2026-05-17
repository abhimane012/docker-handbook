# 🛠️ `ARG` Instruction in Dockerfile

## 🤔 What is `ARG`?

`ARG` defines build-time variables.

These variables are available only during image build.

---

# 🧾 Syntax

```dockerfile
ARG <name>
```

---

# ✅ Example

```dockerfile
ARG VERSION=1.0
```

---

# 🏗️ Use ARG During Build

```dockerfile
FROM ubuntu

ARG APP_VERSION

RUN echo $APP_VERSION
```

---

# 🚀 Pass Value While Building

```bash
docker build --build-arg APP_VERSION=2.0 .
```

---

# ⚠️ Important Notes

- 🏗️ `ARG` works during build time only
- 🚫 Not available automatically inside running container
- 🔒 Do not store secrets in `ARG`

---

# 📝 Common Examples

```dockerfile
ARG VERSION=1.0
ARG PORT=8080
ARG NODE_ENV=production
```

---

# 🔌 `EXPOSE` Instruction in Dockerfile

## 🤔 What is `EXPOSE`?

`EXPOSE` documents which port the container uses.

It tells:
> "This application listens on this port."

---

# 🧾 Syntax

```dockerfile
EXPOSE <port>
```

---

# ✅ Example

```dockerfile
EXPOSE 80
```

---

# 🌐 Multiple Ports

```dockerfile
EXPOSE 80 443
```

---

# 🔌 TCP and UDP Example

```dockerfile
EXPOSE 53/udp
```

---

# ⚠️ Important Notes

- 📄 `EXPOSE` is documentation only
- 🚫 It does NOT automatically publish ports
- 🌍 Use `-p` during `docker run` to access from host

Example:

```bash
docker run -p 8080:80 nginx
```

---

# 📝 Common Examples

```dockerfile
EXPOSE 80
EXPOSE 3000
EXPOSE 8080
EXPOSE 443
EXPOSE 53/udp
```