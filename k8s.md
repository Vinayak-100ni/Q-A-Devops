## What is Kubernetes, and why is it important in the world of container orchestration?
Kubernetes is an open-source container orchestration platform that automates how containers are deployed, scaled, and managed. It’s important because it takes away the manual effort—like restarting failed containers, load balancing traffic, or scaling applications up and down based on demand. It ensures high availability, efficient resource utilization, and makes applications portable across cloud or on-prem environments. In simple terms, Kubernetes is what allows companies to run containerized applications reliably and at scale.

##    Explain the key components of Kubernetes and their roles in container management.

<img width="1076" height="741" alt="Screenshot 2025-09-04 092339" src="https://github.com/user-attachments/assets/c5c03116-4220-41dd-a5be-0ee5f841a9b7" />

##     How do you deploy a containerized application on a Kubernetes cluster? Walk me through the process.
To deploy a containerized application on Kubernetes, I first build a Docker image of the app and push it to a container registry like Docker Hub or ECR. Then I create Kubernetes YAML manifests — usually a Deployment to define how many replicas I want and which image to run, and a Service to expose it. After that, I apply those files using kubectl apply -f, which tells Kubernetes to create the pods and service. Finally, I verify the deployment with kubectl get pods and kubectl get svc to make sure the application is up and reachable. In a production setup, I’d also configure Ingress for domain routing and enable Horizontal Pod Autoscaler for scaling based on load.

##    Describe Kubernetes Deployments and StatefulSets. What are the differences, and when would you use one over the other?
A Deployment in Kubernetes is used for stateless applications. It manages replicas of pods, ensures they are running, and supports rolling updates and rollbacks. Deployments are ideal when pods don’t need to maintain identity or state, like web servers, APIs, or front-end services.

A StatefulSet is for stateful applications. It gives each pod a unique identity, stable network name, and persistent storage. This is important for workloads like databases or Kafka, where pod order, identity, and storage consistency matter.

The main differences are:

Pod Identity: Deployments create interchangeable pods, while StatefulSets assign stable IDs.

Storage: Deployments use shared/ephemeral storage, StatefulSets use persistent volume claims per pod.

Scaling: Deployments scale freely, but StatefulSets scale pods one by one in order.

Use cases: I use Deployments for stateless services and StatefulSets for databases, message queues, or anything needing stable storage and identity.

##    How does Kubernetes handle load balancing for containerized applications?
Kubernetes handles load balancing mainly through Services. When I expose an application with a Service, Kubernetes gives it a stable IP and DNS name, and then distributes traffic across all healthy pods behind it. By default, it uses kube-proxy with iptables or IPVS to balance traffic at the network level.

For external traffic, I can use a NodePort or a LoadBalancer Service — the LoadBalancer integrates with the cloud provider’s load balancer to spread traffic across nodes. In production, we usually set up an Ingress controller on top of this, which gives more advanced HTTP load balancing, SSL termination, and path-based routing.
