## What is Docker, and how does it differ from traditional virtualization?
Docker is a containerization platform that packages applications along with all their dependencies into lightweight, portable containers. Unlike traditional virtualization, where each virtual machine includes a full guest operating system on top of a hypervisor, Docker containers share the host operating system’s kernel and only package what’s necessary for the application.
The key differences are:

Lightweight: Containers start in seconds and use fewer resources compared to VMs.

Portability: A Docker container runs the same way on any environment — developer laptop, test server, or cloud.

Isolation: Containers isolate applications, but without the overhead of running multiple operating systems.

Density: More containers can run on the same hardware compared to VMs, making it efficient and cost-effective.

So, Docker enables faster development, consistent environments, and more efficient use of resources compared to traditional virtualization

##     Explain the key components of Docker's architecture.
Docker’s architecture is mainly built around three key components:
Docker Engine – This is the core runtime. It has:

Docker Daemon (dockerd): Runs on the host, manages images, containers, networks, and volumes.

Docker CLI (docker): Command-line tool that developers use to interact with Docker.

Both communicate through a REST API.
Docker Images – These are read-only templates that define what goes inside a container, including the application and its dependencies. Images are versioned and stored in registries.

Docker Containers – These are the running instances of images. Containers are lightweight, isolated, and portable.

Docker Registry (like Docker Hub or private registry) – A centralized place to store and distribute images.

Additionally, Docker uses networking (bridge, host, overlay) and volumes for persistent storage.
Together, these components allow developers to build, ship, and run applications consistently across environments.

##     What are Docker containers, and how do they work?
Docker containers are lightweight, standalone, and executable units that package an application with everything it needs — code, libraries, dependencies, and runtime. They run on top of the Docker Engine and share the host operating system’s kernel, which makes them much more efficient than virtual machines.

When you run a container, Docker takes a read-only image, adds a thin writable layer on top, and executes it as an isolated process on the host. Containers use Linux features like namespaces for isolation and cgroups for resource control.

This means each container runs independently but shares the same OS kernel, which is why containers start in seconds, use fewer resources, and can be easily moved between environments without compatibility issues

##    How do you create a Docker image? Can you explain the Dockerfile and its significance?
To create a Docker image, we usually write a Dockerfile and then build the image using the docker build command.

A Dockerfile is essentially a text file containing step-by-step instructions that Docker uses to assemble an image. It defines everything the image needs — such as the base operating system, application code, dependencies, environment variables, and commands to run when the container starts.

For example:

### Step 1: Base image
FROM node:18

### Step 2: Set working directory
WORKDIR /app

### Step 3: Copy files into image
COPY package*.json ./
RUN npm install
COPY . .

### Step 4: Expose port
EXPOSE 3000

### Step 5: Start application
CMD ["npm", "start"]

After writing the Dockerfile, we build the image with:

docker build -t myapp:1.0 .

This command creates an image called myapp with the tag 1.0.

Significance of Dockerfile:

Consistency: Ensures the application runs the same way everywhere (dev, test, prod).

Automation: Eliminates manual setup, as the build process is scripted.

Portability: You can easily share the Dockerfile and build the image anywhere.

Versioning: Since it’s code, Dockerfiles can be version-controlled (Git).

##     What is the difference between an image and a container in Docker?
     Docker Image	                                                   Docker Container
Blueprint/template for the application------------------------Running instance of an image
Static, read-only---------------------------------------------Dynamic, can be started/stopped/removed
Created once and reused many times----------------------------Created from an image
Stored in Docker Hub/Registry---------------------------------Runs in the Docker Engine
##     What is Docker Compose, and how does it simplify multi-container application orchestration?
Docker Compose is a tool used to define and manage multi-container applications using a single YAML configuration file (docker-compose.yml). Instead of starting each container manually with long docker run commands, you can define services, networks, and volumes in one place and bring the whole application up with a single command:
#### docker-compose up

it simplifies orchestration:

Single configuration file, 

Easier management – Start, stop, and scale multiple containers with simple commands

Service linking – Automatically creates a private network so containers can talk to each other by service name (e.g., db, backend, frontend).

Reproducibility – Same setup can be shared with teammates and run in any environment.

Scalability – You can scale services (e.g., docker-compose up --scale backend=3) without extra complexity.

##     Describe the Docker networking modes and how containers communicate with each other.
Docker provides different networking modes to control how containers communicate with each other and the outside world.

1. Bridge (default)

Containers get a private IP on a virtual bridge network.

Containers on the same bridge can talk to each other using their container name as DNS.

To expose a service externally, we use port mapping (-p 8080:80).
✅ Most commonly used for standalone applications.

2. Host

The container shares the host machine’s network stack.

No port mapping is required — container services are directly accessible on host IP/ports.
✅ Useful for performance-critical apps or when you need direct host networking.

3. None

The container is isolated from all networks.

Only loopback (localhost) works inside the container.
✅ Used for security or when you want full custom networking.

4. Overlay (in Swarm/Kubernetes setups)

Creates a network that spans across multiple Docker hosts.

Allows containers running on different nodes to communicate securely.
✅ Used in distributed applications and microservices.

5. Macvlan

Assigns a unique MAC address to the container, making it appear as a physical device on the local network.

Containers can get IPs from the same subnet as the host.
✅ Useful when containers need to look like physical devices in a network.

How containers communicate with each other:

Within same bridge network: They communicate directly via container name (thanks to Docker’s DNS).

Across different networks: You need to connect the container to the same user-defined network.

External communication: Expose ports using -p or --publish flag.
