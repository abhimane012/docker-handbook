# 🧩 Docker Compose File Parameters (with Example)

## 🤔 What is a Docker Compose File?

A `docker-compose.yml` file defines how multiple containers (services) should run together.

It describes:
- 📦 Containers
- 🌐 Networks
- 💾 Volumes
- ⚙️ Configurations

---

# 📁 Basic Structure

```yaml
version: "3.8"

services:
  ...
  
volumes:
  ...

networks:
  ...
```

---

# 🧱 1. `version`

Defines Compose file format version.

```yaml
version: "3.8"
```

---

# ⚙️ 2. `services`

Defines all containers.

```yaml
services:
  web:
    image: nginx
```

Each service = one container 📦

---

# 🏷️ 3. `image`

Defines container image.

```yaml
image: nginx
```

---

# 🏗️ 4. `build`

Build image from Dockerfile.

```yaml
build: .
```

---

# 🔌 5. `ports`

Maps host to container ports.

```yaml
ports:
  - "8080:80"
```

---

# 🌐 6. `networks`

Attach service to network.

```yaml
networks:
  - my-network
```

---

# 💾 7. `volumes`

Mount storage.

```yaml
volumes:
  - my-data:/data
```

---

# ⚙️ 8. `environment`

Set environment variables.

```yaml
environment:
  MYSQL_ROOT_PASSWORD: root
  ENV: production
```

---

# 📂 9. `env_file`

Load variables from file.

```yaml
env_file:
  - .env
```

---

# 🔁 10. `depends_on`

Service startup order.

```yaml
depends_on:
  - db
```

---

# 🚀 11. `command`

Override default command.

```yaml
command: npm start
```

---

# 🧑 12. `container_name`

Set custom container name.

```yaml
container_name: my-web-app
```

---

# 🔄 13. `restart`

Restart policy.

```yaml
restart: always
```

Options:
- `no`
- `always`
- `on-failure`
- `unless-stopped`

---

# 📡 14. `expose`

Expose ports internally only.

```yaml
expose:
  - "80"
```

---

# 🧠 15. `deploy` (Swarm only)

Used for scaling and limits.

```yaml
deploy:
  replicas: 3
```

---

# 📄 Full Example

```yaml
version: "3.8"

services:
  web:
    image: nginx
    ports:
      - "8080:80"
    networks:
      - app-net
    restart: always

  db:
    image: mysql
    environment:
      MYSQL_ROOT_PASSWORD: root
    volumes:
      - db-data:/var/lib/mysql
    networks:
      - app-net
    restart: always
    depends_on:
      - web

volumes:
  db-data:

networks:
  app-net:
```

---

# 🧭 High-Level View

```text
docker-compose.yml 📄
        ↓
Defines services ⚙️
        ↓
Docker Compose 🚀
        ↓
Containers + Network + Volumes 📦🌐💾
```

---

# 📝 Quick Summary

| Parameter | Purpose |
|---|---|
| `services` | 📦 Define containers |
| `image` | 🏷️ Use image |
| `build` | 🏗️ Build image |
| `ports` | 🔌 Port mapping |
| `volumes` | 💾 Storage |
| `environment` | ⚙️ Variables |
| `depends_on` | 🔁 Startup order |
| `networks` | 🌐 Networking |
| `restart` | 🔄 Restart policy |

---

# 🎯 Final Understanding

```text
Compose File 📄
      ↓
Defines Everything ⚙️
      ↓
Docker Compose 🚀
      ↓
Full Application Running 📦📦📦
```

Docker Compose parameters help define complete multi-container applications in a single file.