
# Docker Basics and Key Concepts

## What is Docker and Why Use It?

Docker is a platform for developing, shipping, and running applications in **lightweight, portable containers**. It solves the "works on my machine" problem by isolating app dependencies and enabling consistent, fast deployments.

---

## Containers vs Virtual Machines (VMs)

| Virtual Machines                     | Containers                             |
|--------------------------------------|-----------------------------------------|
| Include full Guest OS               | Share Host OS kernel                    |
| Slower to boot, heavier resources   | Fast startup, lightweight               |
| Requires Hypervisor                 | Requires Docker Engine                  |

**Diagram:**

**Virtual Machine:**
```
Hardware
 └── Host OS
     └── Hypervisor
         ├── VM 1 (Guest OS + App)
         └── VM 2 (Guest OS + App)
```

**Container:**
```
Hardware
 └── Host OS (with Docker)
     ├── Container 1 (App + Libs)
     └── Container 2 (App + Libs)
```

---

## Basic Docker Commands

### Spin up Ubuntu container:
```bash
docker run -it ubuntu
```

### Pull image and run container:
```bash
docker pull nginx
docker run -d --name mynginx -p 8080:80 nginx
```

### Listing:
```bash
docker images       # Lists images
docker ps           # Lists running containers
```

---

## Images vs Containers

- **Image**: Read-only blueprint created from a Dockerfile.
- **Container**: Running instance of an image with a writable layer.

---

## Dockerfile → Image → Container

Example `Dockerfile`:
```Dockerfile
FROM node:18
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
CMD ["npm", "start"]
```

Build and run:
```bash
docker build -t my-node-app .
docker run -p 3000:3000 my-node-app
```

---

## Port Mapping

Link a port on your **host** to a port in the **container**:
```bash
docker run -d -p 8080:80 nginx
```
Syntax:
```
-p [HOST_PORT]:[CONTAINER_PORT]
```

---

## Docker Compose

### Directory Layout:
```
my-app/
├── docker-compose.yml
├── web/
│   └── Dockerfile
└── db/
```

### Sample `docker-compose.yml`:
```yaml
version: "3.8"
services:
  web:
    build: ./web
    ports:
      - "3000:3000"
    depends_on:
      - db
    environment:
      - DB_HOST=db
      - DB_USER=postgres
      - DB_PASS=mysecret

  db:
    image: postgres:14
    volumes:
      - db_data:/var/lib/postgresql/data
    environment:
      POSTGRES_PASSWORD: mysecret

volumes:
  db_data:
```

### Commands:
```bash
docker-compose up          # Start services
docker-compose up -d       # Run in background
docker-compose down        # Stop and clean up
docker-compose ps          # List services
docker-compose logs        # Logs from services
docker-compose exec web sh # Shell inside service
```

---

## Volumes

- Used for **data persistence** and **file sharing**.
- Exists outside the container’s lifecycle.

### Create and Use:
```bash
docker volume create mydata
docker run -v mydata:/data myimage
```

### Bind Mount vs Volume:
```bash
# Bind Mount (host path)
docker run -v $(pwd)/html:/usr/share/nginx/html nginx

# Docker-managed volume
docker volume create site_data
docker run -v site_data:/usr/share/nginx/html nginx
```

### Sharing Volume Between Containers:
```bash
docker run -v shared-data:/data --name writer busybox sh -c "echo hello > /data/hello.txt"
docker run -v shared-data:/data --name reader busybox cat /data/hello.txt
```

### With Docker Compose:
```yaml
services:
  db:
    image: postgres
    volumes:
      - db_data:/var/lib/postgresql/data

volumes:
  db_data:
```

### Volume Management:
```bash
docker volume ls              # List all volumes
docker volume inspect mydata # Inspect volume
docker volume rm mydata      # Remove specific volume
docker volume prune          # Remove unused volumes
```

---

## Layer Caching in Docker

Each Dockerfile command creates a **layer**:
```Dockerfile
FROM node:18               # Layer 1
WORKDIR /app               # Layer 2
COPY package*.json .       # Layer 3
RUN npm install            # Layer 4
COPY . .                   # Layer 5
CMD ["npm", "start"]       # Layer 6
```