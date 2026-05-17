# 📄 Dockerfile Instructions / Parameters List

## 🧾 Common Dockerfile Instructions

| Instruction | Purpose |
|---|---|
| `FROM` | 📦 Set base image |
| `RUN` | ⚙️ Execute command during build |
| `CMD` | 🚀 Default command when container starts |
| `LABEL` | 🏷️ Add metadata |
| `EXPOSE` | 🔌 Document container port |
| `ENV` | 🌐 Set environment variables |
| `ADD` | 📂 Copy files with extra features |
| `COPY` | 📁 Copy files/directories |
| `ENTRYPOINT` | 🎯 Main container executable |
| `VOLUME` | 💾 Create mount point |
| `USER` | 👤 Set user |
| `WORKDIR` | 📁 Set working directory |
| `ARG` | 🛠️ Build-time variables |
| `ONBUILD` | 🔄 Trigger instruction for child image |
| `STOPSIGNAL` | ⏹️ Set stop signal |
| `HEALTHCHECK` | ❤️ Check container health |
| `SHELL` | 💻 Change default shell |

---

# 🧱 Multi-Stage Build Related

| Instruction | Purpose |
|---|---|
| `FROM ... AS` | 🏗️ Name build stage |
| `COPY --from=` | 📦 Copy from another stage |

---

# 📌 Commonly Used Instructions

These are used most often 👇

```dockerfile
FROM
RUN
COPY
WORKDIR
CMD
ENTRYPOINT
ENV
EXPOSE
ARG
```

---

# 📝 Minimal Example

```dockerfile
FROM python:3.12

WORKDIR /app

COPY . .

RUN pip install -r requirements.txt

CMD ["python", "app.py"]
```