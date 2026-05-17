# 👤 `MAINTAINER` Instruction in Dockerfile

## 🤔 What is `MAINTAINER`?

`MAINTAINER` was used to specify the author/maintainer of the Dockerfile.

---

# 🧾 Syntax

```dockerfile
MAINTAINER <name>
```

---

# ✅ Example

```dockerfile
MAINTAINER Abhishek Mane
```

---

# ⚠️ Important

`MAINTAINER` is deprecated ❌

Modern Dockerfiles use:

```dockerfile
LABEL
```

instead.

---

# ✅ Modern Alternative

```dockerfile
LABEL maintainer="Abhishek Mane"
```

---

# ⚙️ `RUN` Instruction in Dockerfile

## 🤔 What is `RUN`?

`RUN` executes commands during image build time.

Used for:
- 📦 Installing packages
- ⚙️ Running setup commands
- 🛠️ Configuring environment

---

# 🧾 Syntax

```dockerfile
RUN <command>
```

---

# ✅ Example

```dockerfile
RUN apt update
```

---

# 📦 Install Packages Example

```dockerfile
RUN apt install -y nginx
```

---

# 🐍 Python Example

```dockerfile
RUN pip install flask
```

---

# 🧱 Multiple Commands

```dockerfile
RUN apt update && apt install -y curl
```

---

# ⚠️ Important Notes

- 📚 Every `RUN` creates a new image layer
- ⚡ Combining commands reduces layers
- 🧹 Clean unnecessary files to reduce image size

---

# 📝 Common Examples

```dockerfile
RUN apt update
RUN apt install -y python3
RUN pip install -r requirements.txt
RUN mkdir /app