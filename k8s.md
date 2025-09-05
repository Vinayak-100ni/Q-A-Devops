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

##     What is a Kubernetes Namespace, and why would you use multiple namespaces in a cluster?
A Kubernetes Namespace is a way to logically divide a cluster into virtual sub-clusters. It helps organize and isolate resources like pods, services, and deployments.

I would use multiple namespaces to:

Separate environments like dev, test, and prod in the same cluster.

Isolate teams or projects so their resources don’t conflict.

Apply different resource quotas and limits to control how much CPU and memory each group can use.

Control access with RBAC so teams only see and manage their own resources.

For example, I might run a frontend app in a dev namespace with limited resources, while the production version runs in a prod namespace with stricter quotas and monitoring

## Explain the concept of Kubernetes Services and how they enable network connectivity for Pods.
In Kubernetes, Pods are short-lived — they can die and restart with different IP addresses. A Service solves this by providing a stable IP and DNS name that load-balances traffic across all healthy pods behind it.

There are different types of Services:

ClusterIP – the default, exposes the app inside the cluster.

NodePort – exposes the app on a static port of each node for external access.

LoadBalancer – integrates with cloud provider load balancers for external traffic.

ExternalName – maps the service to an external DNS name.

So essentially, Services act as a consistent entry point and handle discovery, routing, and load balancing, ensuring clients don’t need to track changing pod IP

##     What is the role of a Kubernetes Ingress controller, and how does it work?
A Kubernetes Ingress controller manages external access to services, usually HTTP and HTTPS. Instead of creating a separate LoadBalancer for each service, I can define Ingress rules that map different paths or hostnames to different services. The Ingress controller, like NGINX or Traefik, reads those rules and routes traffic accordingly. It also handles things like SSL termination, path-based routing, and host-based routing. In simple terms, it’s like a smart router at the edge of the cluster that directs incoming traffic to the right service.

##    What is Kubernetes' role in auto-scaling, and how can you set up Horizontal Pod Autoscaling (HPA)?
Kubernetes’ role in auto-scaling:
Kubernetes helps applications scale automatically by monitoring workloads and adjusting resources as needed. It provides three main types of auto-scaling:

Horizontal Pod Autoscaler (HPA): Scales the number of pod replicas up or down based on CPU, memory, or custom metrics.

Vertical Pod Autoscaler (VPA): Adjusts the resource requests and limits for pods.

Cluster Autoscaler: Scales the number of worker nodes in the cluster.

So, Kubernetes ensures applications stay highly available and cost-efficient by only using the resources required at a given time.

How to set up HPA (Horizontal Pod Autoscaler):
To set up HPA, I would:

Deploy an application with a Deployment or ReplicaSet, specifying resource requests/limits for CPU or memory.

Enable metrics-server in the cluster because HPA relies on it to gather resource usage metrics.

Create an HPA object using kubectl autoscale. For example:
### kubectl autoscale deployment myapp --cpu-percent=50 --min=2 --max=10
Here, if average CPU usage across pods exceeds 50%, Kubernetes will scale pods up.

If it goes below, it will scale down but not below 2 pods.

Monitor scaling with:

### kubectl get hpa
##    Describe Kubernetes rolling updates and canary deployments. When and why would you use each approach?
Rolling Update = gradual, safe upgrade with no downtime.

Canary Deployment = test new version on limited users first before full rollout.

##    Explain Kubernetes' role in self-healing and how it handles container failures.
One of the biggest advantages of Kubernetes is its self-healing capability. Kubernetes constantly monitors the desired state versus the actual state of workloads, and if something goes wrong, it takes corrective actions automatically to bring the system back to the desired state.

How Kubernetes handles container failures:

Pod restarts:
If a container inside a pod crashes, the kubelet on that node automatically restarts the container based on its restart policy.

Pod replacement:
If an entire pod becomes unhealthy or the node it’s running on fails, Kubernetes schedules a new pod on a healthy node to maintain availability.

Health checks:
Kubernetes uses liveness probes and readiness probes.

If a liveness probe fails, Kubernetes restarts the container.

If a readiness probe fails, Kubernetes removes that pod from the Service endpoints until it becomes healthy again, preventing traffic from going to a bad pod.

ReplicaSets & Deployments:
Kubernetes ensures that the number of replicas defined in a Deployment always matches. If a pod is deleted or goes down, the ReplicaSet automatically creates a replacement.

##    What are Kubernetes ConfigMaps and Secrets, and how do they differ in terms of storing configuration data?
ConfigMaps are used to store non-sensitive configuration data like environment variables, database URLs, or feature flags, while Secrets are specifically designed to store sensitive data like passwords, API keys, or TLS certificates.

The main difference is that ConfigMaps store plain text configuration, whereas Secrets add an extra layer of protection by encoding the values in base64 and supporting integrations with tools like KMS or Vault for encryption.
###    How would you upgrade a Kubernetes cluster to a new version while minimizing downtime?
To upgrade a Kubernetes cluster with minimal downtime, I follow a controlled step-by-step approach. First, I check the Kubernetes release notes and make sure my add-ons and workloads are compatible. Then I upgrade the control plane components one by one, starting with the API server, followed by controller-manager, scheduler, and etcd. After the control plane is stable, I upgrade the worker nodes gradually — usually by draining one node at a time, upgrading its kubelet and kube-proxy, and then bringing it back into the cluster before moving to the next node.

Because workloads are managed by Deployments and ReplicaSets, Kubernetes reschedules pods on healthy nodes while one node is being upgraded, which minimizes downtime. I also make use of rolling updates and health probes to ensure services remain available during the process. Finally, I validate the cluster state and application health after the upgrade before proceeding further.
##    What is a Helm chart, and how does it simplify application deployment on Kubernetes?
A Helm chart is a package of pre-configured Kubernetes resources. It bundles together YAML manifests like Deployments, Services, ConfigMaps, and Ingress into a single reusable unit.

It simplifies application deployment because instead of writing and managing multiple YAML files manually, I can install an entire application with a single helm install command. Helm also supports versioning, templating, and easy upgrades or rollbacks, which makes managing complex applications much faster and less error-prone.
##    How do you monitor a Kubernetes cluster and its workloads? Mention some popular monitoring and logging solutions for Kubernetes.
I monitor a Kubernetes cluster and its workloads by collecting metrics, logs, and events at both the cluster and application level. For metrics, I typically use Prometheus along with Grafana for visualization. Prometheus scrapes metrics from Kubernetes components and workloads, and Grafana gives me real-time dashboards. For cluster health, I also use metrics-server to power features like Horizontal Pod Autoscaling.
