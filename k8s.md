## What is Kubernetes, and why is it important in the world of container orchestration?
Kubernetes is an open-source container orchestration platform that automates how containers are deployed, scaled, and managed. It’s important because it takes away the manual effort—like restarting failed containers, load balancing traffic, or scaling applications up and down based on demand. It ensures high availability, efficient resource utilization, and makes applications portable across cloud or on-prem environments. In simple terms, Kubernetes is what allows companies to run containerized applications reliably and at scale.

##    Explain the key components of Kubernetes and their roles in container management.
Kubernetes is made up of several key components that work together to manage containers effectively:

Pod – The smallest deployable unit in Kubernetes, which can contain one or more tightly coupled containers.

Node – A worker machine where pods actually run. Each node has the runtime, kubelet, and kube-proxy.

Cluster – A group of nodes managed by Kubernetes.

Control Plane (Master Components) – This manages the overall cluster. It includes:

API Server – The entry point for all commands and communication.

etcd – A distributed key-value store that keeps the cluster state.

Scheduler – Decides which node a pod should run on based on resource availability.

Controller Manager – Ensures the desired state matches the current state, like restarting failed pods or handling replicas.

Kubelet – An agent that runs on each node and makes sure containers inside pods are running as expected.

Kube-proxy – Manages network rules so services can talk to each other inside and outside the cluster.

Service – Provides stable networking and load balancing for a set of pods.

ConfigMap & Secret – Manage configuration and sensitive data separately from the application code.

All of these work together so Kubernetes can automatically deploy, scale, heal, and load balance containerized applications
<img width="1076" height="741" alt="Screenshot 2025-09-04 092339" src="https://github.com/user-attachments/assets/c5c03116-4220-41dd-a5be-0ee5f841a9b7" />
