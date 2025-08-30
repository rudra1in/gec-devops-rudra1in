🚀 Docker 101: For Developers & DevOps Beginners

Welcome to Docker 101! This guide is designed for **developers and DevOps engineers** who are new to Docker but want to understand it from a **hands-on, practical** perspective.

---

## 📚 Table of Contents

1. [What is Docker?](#what-is-docker)
2. [Core Concepts](#core-concepts)
3. [Docker Architecture](#docker-architecture)
4. [Lab 1: Docker Installation & Sanity Check](#lab-1-docker-installation--sanity-check)
5. [Lab 2: Running Your First Container](#lab-2-running-your-first-container)
6. [Lab 3: Exploring Images & Docker Hub](#lab-3-exploring-images--docker-hub)
7. [Lab 4: Writing Your First Dockerfile](#lab-4-writing-your-first-dockerfile)
8. [Lab 5: Managing Containers and Images](#lab-5-managing-containers-and-images)
9. [🧠 Recap & Next Steps](#-recap--next-steps)

---

## 🐳 What is Docker?

Docker is a **containerization platform** that packages your application and all its dependencies into a **single container** that can run anywhere.

**Benefits:**
- Works on any machine (macOS, Linux, Windows)
- Lightweight and fast (compared to virtual machines)
- Isolated environments
- Easier CI/CD pipelines

---

## 🔧 Core Concepts

| Term         | Description |
|--------------|-------------|
| **Image**    | Read-only blueprint for containers |
| **Container**| A running instance of an image |
| **Dockerfile** | Script to build an image |
| **Docker Engine** | The daemon that runs and manages containers |
| **Docker Hub** | Public image registry (like GitHub for containers) |

---

## 🧠 Docker Architecture (Diagram)

```text
               +-------------------+
               |   Your App Code   |
               +--------+----------+
                        |
                  [ Dockerfile ]
                        |
            docker build -t myapp .
                        |
               +-------------------+
               |     Image         |
               +--------+----------+
                        |
               docker run myapp
                        |
               +-------------------+
               |   Container (app) |
               +-------------------+

Docker Desktop GUI lets you manage containers visually
````

---

## 🧪 Lab 1: Docker Installation & Sanity Check

Make sure Docker is installed and working.

### ✅ Check version:

```bash
docker version
```

### ✅ See Docker engine info:

```bash
docker info
```

### ✅ Run a test container:

```bash
docker run hello-world
```

➡️ This pulls a test image from Docker Hub and runs it. If it prints “Hello from Docker!”, you’re good to go.

---

## 🧪 Lab 2: Running Your First Container

We'll run a lightweight Linux container.

### ✅ Run an interactive Alpine shell:

```bash
docker run -it alpine sh
```

Now you're inside a minimal Linux OS.

### 🧪 Try commands inside container:

```bash
apk update
apk add curl
curl https://example.com
```

💡 When you exit the shell, the container stops.

---

## 🧪 Lab 3: Exploring Images & Docker Hub

### ✅ Pull and run a public image:

```bash
docker pull nginx
docker run -d -p 8080:80 nginx
```

* `-d` runs detached (in background)
* `-p 8080:80` maps host port 8080 → container port 80

### ✅ View running containers:

```bash
docker ps
```

➡️ Visit [http://localhost:8080](http://localhost:8080) in your browser.

### ✅ Explore with Docker Desktop:

* View logs
* Inspect ports
* See CPU/memory stats

---

## 🧪 Lab 4: Writing Your First Dockerfile

Let’s containerize a simple Node.js app.

### 📁 Files:

**app.js**

```js
const express = require('express')
const app = express()
app.get('/', (req, res) => res.send('Hello Docker!'))
app.listen(3000)
```

**package.json**

```json
{
  "name": "docker101-app",
  "dependencies": {
    "express": "^4.18.0"
  }
}
```

### 📝 Dockerfile

```Dockerfile
FROM node:18
WORKDIR /app
COPY . .
RUN npm install
EXPOSE 3000
CMD ["node", "app.js"]
```

### ✅ Build & run:

```bash
docker build -t docker101-node .
docker run -p 3000:3000 docker101-node
```

➡️ Visit [http://localhost:3000](http://localhost:3000) to see your app.

---

## 🧪 Lab 5: Managing Containers and Images

### ✅ Stop and remove containers:

```bash
docker ps -a             # see all containers
docker stop <container>  # stop by name or ID
docker rm <container>    # remove stopped container
```

### ✅ Remove images:

```bash
docker images
docker rmi <image>
```

### ✅ Clean up:

```bash
docker system prune
```

---

## 🧠 Recap & Next Steps

### ✅ What you learned:

* What containers are and why we use them
* How to run and build Docker containers
* How to inspect and manage them
* How to write a Dockerfile

### 🚀 What to try next:

* Docker Compose (multi-container apps)
* Volume mounting for hot reload
* Use Docker in your CI/CD pipeline
* Push your image to Docker Hub

---

*Thanks for learning Docker 101!*

```

---

Let me know if you want a version of this tailored for Python, Java, or Go instead of Node.js — or if you'd like me to turn this into slides or a printable handout.
```
