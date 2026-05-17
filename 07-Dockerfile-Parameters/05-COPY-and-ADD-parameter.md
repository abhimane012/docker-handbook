# 📂 `COPY` Instruction in Dockerfile

## 🤔 What is `COPY`?

`COPY` copies files and directories from the local machine into the Docker image.

---

# 🧾 Syntax

```dockerfile
COPY <source> <destination>
```

---

# ✅ Example

```dockerfile
COPY . /app
```

Copies current directory files into `/app` inside image.

---

# 📁 Copy Single File

```dockerfile
COPY app.py /app/
```

---

# 📂 Copy Multiple Files

```dockerfile
COPY file1.txt file2.txt /app/
```

---

# 🏗️ Copy from Another Build Stage

```dockerfile
COPY --from=builder /app/bin /app/bin
```

---

# ⚠️ Important Notes

- 📄 Only copies local files
- 🚫 Does NOT extract compressed files automatically
- 📚 Commonly used more than `ADD`

---

# 📝 Common Examples

```dockerfile
COPY . .
COPY package.json /app/
COPY src/ /app/src/
```

---

# 📦 `ADD` Instruction in Dockerfile

## 🤔 What is `ADD`?

`ADD` is similar to `COPY` but has extra features.

It can:
- 📂 Copy files/directories
- 📦 Extract compressed archives automatically
- 🌐 Download files from URLs

---

# 🧾 Syntax

```dockerfile
ADD <source> <destination>
```

---

# ✅ Example

```dockerfile
ADD . /app
```

---

# 📦 Auto Extract Archive

```dockerfile
ADD app.tar.gz /app/
```

Docker automatically extracts the archive 📂

---

# 🌐 Download from URL

```dockerfile
ADD https://example.com/file.txt /app/
```

---

# ⚠️ Important Notes

- ⚡ `ADD` has more functionality than `COPY`
- 📄 Prefer `COPY` unless extra features are needed
- 🌐 URL downloads can reduce build reproducibility

---

# 🔄 `COPY` vs `ADD`

| Feature | `COPY` | `ADD` |
|---|---|---|
| 📂 Copy files | ✅ | ✅ |
| 📦 Auto extract archives | ❌ | ✅ |
| 🌐 Download URLs | ❌ | ✅ |
| 📄 Simple and predictable | ✅ | ❌ |

---

# 📝 Common Examples

```dockerfile
ADD app.tar.gz /app/
ADD https://example.com/file.txt /tmp/
ADD src/ /app/src/
```