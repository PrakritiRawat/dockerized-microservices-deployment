

# 🐳 Microservices Deployment with Docker Compose & Docker Swarm

---

## 📌 Introduction
This project demonstrates how to deploy a **microservice-based application** using:

- **Docker Compose** ➔ for local development 🖥️
- **Docker Swarm** ➔ for production-like environments 🚀

It covers service building, scaling, monitoring, and troubleshooting, all using modern container orchestration techniques.

---

## 🏗️ Project Structure

```
my-microservices-app/
├── auth-service/
│   ├── Dockerfile
│   ├── app.py
│   ├── requirements.txt
├── user-service/
│   ├── Dockerfile
│   ├── app.py
│   ├── requirements.txt
├── docker-compose.yml
├── docker-stack.yml
└── .env
```

✅ *Organized and modular microservices structure.*

---

## 🚀 Step 1: Build and Run Locally Using Docker Compose

### 1️⃣ Build the Services

```bash
docker-compose build
```


---

### 2️⃣ Start the Services

```bash
docker-compose up -d
```

---

### 3️⃣ Check Running Containers

```bash
docker-compose ps
```

---

### 4️⃣ Test Service Endpoints

```bash
curl http://localhost:5000/auth
curl http://localhost:5001/user
```

---

### 5️⃣ View Service Logs

```bash
docker-compose logs -f auth-service
```

---

### 6️⃣ Stop the Services

```bash
docker-compose down
```

---

## 🌍 Step 2: Deploy in Production Using Docker Swarm

---

### 1️⃣ Initialize Swarm Mode

```bash
docker swarm init
```

---

### 2️⃣ Add Worker Nodes

```bash
docker swarm join --token <TOKEN> <MANAGER_IP>:2377
```

---

### 3️⃣ Verify Swarm Nodes

```bash
docker node ls
```

---

### 4️⃣ Build Docker Images

```bash
docker build -t auth-service ./auth-service
docker build -t user-service ./user-service
```

---

### 5️⃣ Deploy the Application Stack

```bash
docker stack deploy -c docker-stack.yml myapp
```

---

### 6️⃣ Check Running Services

```bash
docker stack services myapp
```

---

### 7️⃣ View Service Replicas

```bash
docker service ps myapp_auth-service
```

---

### 8️⃣ Check Live Logs

```bash
docker service logs -f myapp_auth-service
```

---

### 9️⃣ Scale a Service Dynamically

```bash
docker service scale myapp_auth-service=4
```

---

### 🔟 Test Services from Browser or CURL

```bash
curl http://<MANAGER_NODE_IP>:5000/auth
curl http://<MANAGER_NODE_IP>:5001/user
```

---

### 1️⃣1️⃣ Remove the Deployed Stack

```bash
docker stack rm myapp
```

---

### 1️⃣2️⃣ Leave Swarm Mode (on Worker Node)

```bash
docker swarm leave
```

---

### 1️⃣3️⃣ Force Leave Swarm (on Manager Node)

```bash
docker swarm leave --force
```

---

## 🔍 Troubleshooting Guide

✅ **View container logs:**

```bash
docker-compose logs <service_name>
```

✅ **Check problematic Swarm services:**

```bash
docker service ps <service_name>
```

✅ **Verify port bindings:**

```bash
docker ps
```

✅ **Check Docker Engine status:**

```bash
systemctl status docker
```

✅ **Inspect Docker networks:**

```bash
docker network inspect <network_name>
```

---

## 📋 Best Practices & Notes

- 📄 Use `.env` files for managing environment variables and secrets.
- ✅ Implement **health checks** in `docker-compose.yml` and `docker-stack.yml`.
- 📊 Enable centralized **logging and monitoring** (e.g., ELK Stack, Prometheus).
- 🔒 Use **Docker Secrets** for production-grade secret management.
- 🛠 Prefer **multi-stage builds** for smaller production images.

---

## 🚨 Need Help?
Feel free to raise an issue, fork the repository, or contribute to the project! 😊  
Happy Dockering and Scaling! 🚀🐳

---

# 🎯 Final Touch
✅ You have a **perfect full-cycle microservices deployment guide** with **Docker Compose** for dev and **Docker Swarm** for prod!

---
