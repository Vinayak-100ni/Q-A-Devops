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

# Step 1: Base image
FROM node:18

# Step 2: Set working directory
WORKDIR /app

# Step 3: Copy files into image
COPY package*.json ./
RUN npm install
COPY . .

# Step 4: Expose port
EXPOSE 3000

# Step 5: Start application
CMD ["npm", "start"]


After writing the Dockerfile, we build the image with:

docker build -t myapp:1.0 .


This command creates an image called myapp with the tag 1.0.

Significance of Dockerfile:

Consistency: Ensures the application runs the same way everywhere (dev, test, prod).

Automation: Eliminates manual setup, as the build process is scripted.

Portability: You can easily share the Dockerfile and build the image anywhere.

Versioning: Since it’s code, Dockerfiles can be version-controlled (Git).
