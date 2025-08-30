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
