# Softy Pinko Docker Project

## Overview

This project demonstrates how to build and containerize a full web application using Docker. It includes:

- A **Flask API back-end**
- A **static front-end served with Nginx**
- A **reverse proxy using Nginx**
- A **load-balanced scalable architecture using Docker Compose**

The project is split into multiple stages (task1 → task6), each adding more complexity and functionality.

---

## 📦 Project Structure

```
task0/
├── Dockerfile
task1/
├── api.py
├── Dockerfile
task2 & task3/
├── back-end/
│   ├── api.py
│   ├── Dockerfile
├── front-end/
│   ├── softy-pinko-front-end/ (static site files)
│   ├── Dockerfile
│   ├── softy-pinko-front-end.conf
task4/
├── back-end/
│   ├── api.py
│   ├── Dockerfile
├── front-end/
│   ├── softy-pinko-front-end/ (static site files)
│   ├── Dockerfile
│   ├── softy-pinko-front-end.conf
├── docker-compose.yml
task5/
├── back-end/
│   ├── api.py
│   ├── Dockerfile
├── front-end/
│   ├── softy-pinko-front-end/ (static site files)
│   ├── Dockerfile
│   ├── softy-pinko-front-end.conf
├── proxy/
│   ├── Dockerfile
│   ├── proxy.conf
├── docker-compose.yml
task6/
├── back-end/
│   ├── api.py
│   ├── Dockerfile
├── front-end/
│   ├── softy-pinko-front-end/ (static site files)
│   ├── Dockerfile
│   ├── softy-pinko-front-end.conf
├── proxy/
│   ├── Dockerfile
│   ├── proxy.conf
├── docker-compose.yml
├── 2-api-servers.txt
```

---

## 📌 Task Breakdown

### 📁 Task 0 - First Docker Image
**Goal**
Create a basic Docker image that runs a simple command.

**Key Concepts**
- Dockerfile basics
- Ubuntu base image
- Image building

**Output**
`Hello, World!`

### 📁 Task 1 – Basic API
- Built a simple Flask API server.
- Endpoint:
  - `/api/hello` → returns `"Hello, World!"`

---

### 📁 Task 2 – Static Front-end with Nginx
- Created a front-end using a static HTML template.
- Served using Nginx inside a Docker container.
- Configured custom Nginx server on port **9000**.

---

### 📁 Task 3 – Connecting Front-end and Back-end
- Connected front-end to Flask API using AJAX.
- Enabled **CORS** using `flask-cors`.
- Front-end dynamically displays data from API.

API call:
```
http://localhost:5252/api/hello
```

---

### 📁 Task 4 – Docker Compose Setup
- Introduced `docker-compose.yml`.
- Managed both front-end and back-end services together.
- Simplified build and run process:

```
docker-compose build
docker-compose up
```

---

### 📁 Task 5 – Reverse Proxy with Nginx
- Added a **proxy server** using Nginx.
- All traffic goes through a single entry point:

```
http://localhost:80
```

### Routing rules:
- `/` → Front-end service (Nginx on port 9000)
- `/api` → Back-end service (Flask on port 5252)

### Key benefit:
Clients only interact with the proxy, not internal services.

---

### 📁 Task 6 – Scaling with Load Balancing
- Added multiple back-end API instances.
- Nginx proxy performs **round-robin load balancing**.

Example:
- back-end-1
- back-end-2
- back-end-N

Requests to `/api/hello` are distributed automatically.

---

## 🚀 Technologies Used

- Docker
- Docker Compose
- Nginx
- Flask
- Python 3
- JavaScript (jQuery AJAX)
- HTML/CSS

---

## ⚙️ How to Run the Project

### Build and run everything:

```bash
docker-compose build
docker-compose up
```

Then open:

```
http://localhost
```
