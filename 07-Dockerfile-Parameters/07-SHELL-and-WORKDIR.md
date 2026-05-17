# 💻 `SHELL` Instruction in Dockerfile

## 🤔 What is `SHELL`?

`SHELL` changes the default shell used for `RUN` commands.

Docker normally uses:

```text
/bin/sh -c
```

on Linux.

---

# 🧾 Syntax

```dockerfile
SHELL ["shell", "option"]
```

---

# ✅ Example

```dockerfile
SHELL ["/bin/bash", "-c"]
```

Now Docker uses `bash` instead of `sh`.

---

# 🪟 Windows Example

```dockerfile
SHELL ["powershell", "-Command"]
```

---

# ⚙️ Example Usage

```dockerfile
SHELL ["/bin/bash", "-c"]

RUN echo "Hello from bash"
```

---

# ⚠️ Important Notes

- 💻 Affects future `RUN` commands
- 🐧 Mostly used when specific shell features are needed
- 📄 Optional instruction

---

# 📝 Common Examples

```dockerfile
SHELL ["/bin/bash", "-c"]
SHELL ["powershell", "-Command"]
```

---

# 📁 `WORKDIR` Instruction in Dockerfile

## 🤔 What is `WORKDIR`?

`WORKDIR` sets the working directory inside the container.

All future commands run from this directory.

---

# 🧾 Syntax

```dockerfile
WORKDIR <directory>
```

---

# ✅ Example

```dockerfile
WORKDIR /app
```

Now Docker works inside `/app`.

---

# ⚙️ Example Usage

```dockerfile
WORKDIR /app

COPY . .

RUN npm install
```

Here:
- Files are copied into `/app`
- `npm install` runs inside `/app`

---

# 📂 Multiple WORKDIR Example

```dockerfile
WORKDIR /app
WORKDIR src
```

Final directory becomes:

```text
/app/src
```

---

# ⚠️ Important Notes

- 📁 Automatically creates directory if missing
- 🧹 Better than using repeated `cd` commands
- 📄 Affects `RUN`, `CMD`, `COPY`, and `ENTRYPOINT`

---

# 📝 Common Examples

```dockerfile
WORKDIR /app
WORKDIR /usr/src/app
WORKDIR /backend
```