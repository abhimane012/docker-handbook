# 🐳 Docker Installation on Linux, macOS, and Windows

Docker can be installed on:
- 🐧 Linux
- 🍎 macOS
- 🪟 Windows

The installation process is different for each operating system.

---

# 🐧 Install Docker on Linux

Docker officially supports many Linux distributions like:
- Ubuntu
- Debian
- CentOS
- Fedora

---

# 📌 Install Docker on Ubuntu

## 1️⃣ Update System Packages

```bash
sudo apt update
```

---

## 2️⃣ Install Required Packages

```bash
sudo apt install apt-transport-https ca-certificates curl software-properties-common -y
```

---

## 3️⃣ Add Docker GPG Key

```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```

---

## 4️⃣ Add Docker Repository

```bash
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

---

## 5️⃣ Install Docker

```bash
sudo apt update
sudo apt install docker-ce docker-ce-cli containerd.io -y
```

---

## 6️⃣ Verify Docker Installation

```bash
docker --version
```

---

# ▶️ Start Docker Service

```bash
sudo systemctl start docker
```

---

# 🔄 Enable Docker at Boot

```bash
sudo systemctl enable docker
```

---

# 🧪 Test Docker

```bash
sudo docker run hello-world
```

If Docker is installed correctly, you will see a success message.

---

# 👤 Run Docker Without `sudo`

## Add Current User to Docker Group

```bash
sudo usermod -aG docker $USER
```

Then restart your terminal or logout/login.

---

# 🍎 Install Docker on macOS

Docker on macOS is usually installed using **Docker Desktop**.

---

# 💻 Method 1: Install Docker Desktop

## 1️⃣ Download Docker Desktop

Visit:

```text
https://www.docker.com/products/docker-desktop/
```

---

## 2️⃣ Install Application

- Open the downloaded `.dmg` file
- Drag Docker into the Applications folder

---

## 3️⃣ Start Docker Desktop

Open Docker Desktop from Applications.

Wait until Docker starts successfully.

---

## 4️⃣ Verify Installation

```bash
docker --version
```

---

# 🍺 Method 2: Install Docker Using Homebrew

Homebrew is a popular package manager for macOS.

---

# 📌 Install Homebrew (If Not Installed)

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

---

# 📌 Install Docker Desktop Using Homebrew

```bash
brew install --cask docker
```

---

# ▶️ Start Docker Desktop

```bash
open /Applications/Docker.app
```

---

# 🧪 Verify Docker Installation

```bash
docker --version
```

---

# 🪟 Install Docker on Windows

Docker on Windows is installed using Docker Desktop.

---

# 📌 Requirements

- Windows 10 or Windows 11
- WSL2 enabled
- Virtualization enabled in BIOS

---

# 💻 Installation Steps

## 1️⃣ Download Docker Desktop

Visit:

```text
https://www.docker.com/products/docker-desktop/
```

---

## 2️⃣ Run Installer

Open the downloaded `.exe` installer and follow the setup instructions.

---

## 3️⃣ Enable WSL2

Docker Desktop may ask to install or enable WSL2.

---

## 4️⃣ Restart System

Restart your computer after installation.

---

## 5️⃣ Start Docker Desktop

Open Docker Desktop from the Start Menu.

---

## 6️⃣ Verify Installation

Open PowerShell or CMD:

```bash
docker --version
```

---

# 🧪 Test Docker

```bash
docker run hello-world
```

---

# ⚖️ Docker Installation Comparison

| Operating System | Recommended Method |
|---|---|
| 🐧 Linux | Docker Engine |
| 🍎 macOS | Docker Desktop |
| 🪟 Windows | Docker Desktop |

---

# 📝 Key Points to Remember

- 🐳 Docker can run on Linux, macOS, and Windows
- 🐧 Linux usually uses Docker Engine
- 🍎 macOS mainly uses Docker Desktop
- 🍺 Homebrew can install Docker on macOS
- 🪟 Windows uses Docker Desktop with WSL2
- 🧪 `docker run hello-world` tests the installation