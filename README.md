### Why did you choose DevOps as a career path?
✅ Answer:
“I chose DevOps because I enjoy solving problems related to deployment, automation, and scalability. DevOps allows me to work across the full software lifecycle, from code integration and testing to containerization, deployment, and monitoring. It also has huge industry demand and growth, which motivates me to build a long-term career in this field.”

### What was your role and responsibilities during your internship?
✅ Answer:

Infrastructure as Code: Wrote Terraform scripts/modules for AWS infrastructure.

CI/CD: Set up Jenkins pipelines, GitHub webhooks, and automated deployments.

Containerization: Created Dockerfiles, built images, and managed containers.

Kubernetes: Worked with Deployments, Services, Ingress, and Helm charts.

Security & Access: Managed IAM roles, SSH keys, and disaster recovery planning.

### How do you keep yourself updated with DevOps tools?
✅ Answer:
“I follow official documentation, read blogs, watch YouTube tutorials, and practice on platforms like KillerCoda and Katacoda. I also contribute to GitHub projects and learn from DevOps communities on LinkedIn and Reddit.”

### What is DevOps, and why is it important?
✅ Answer:
“DevOps is a cultural and technical approach that brings development and operations together to deliver software faster and more reliably. It is important because it reduces release time, improves collaboration, increases reliability, and enables automation using CI/CD, IaC, containerization, and monitoring.”

### Explain CI vs CD (Delivery vs Deployment).
✅ Answer:

Continuous Integration (CI): Developers merge code frequently, and automated builds/tests run.

Continuous Delivery: Code is automatically tested and packaged, ready for production. Deployment is manual.

Continuous Deployment: Every tested change is automatically deployed to production.

### What is the difference between Git Merge and Git Rebase?
✅ Answer:

Merge: Combines two branches and creates a merge commit. Keeps history.

Rebase: Moves commits from one branch on top of another. Creates a linear history.
👉 Merge = safe, Rebase = clean history.

### What is Docker, and how is it different from a VM?
✅ Answer:
“Docker is a containerization tool that packages applications with dependencies into lightweight containers.

VMs: Heavy, each has its own OS.

Docker: Lightweight, shares the host OS kernel, faster to start, and more efficient.”

### What is a Dockerfile and Docker Compose?
✅ Answer:

Dockerfile: A script with instructions to build a Docker image (e.g., install dependencies, copy code).

Docker Compose: A YAML file to define and run multi-container applications (e.g., web + db).

### Explain Deployments, Services, and Ingress in Kubernetes.
✅ Answer:

Deployment: Defines how pods should run (replicas, updates).

Service: Exposes pods to other services (ClusterIP, NodePort, LoadBalancer).

Ingress: Manages external access (like a router with domain + SSL).

### What are ConfigMaps and Secrets in Kubernetes?
✅ Answer:

ConfigMap: Stores non-sensitive config like app settings.

Secret: Stores sensitive data like passwords or API keys (encoded in base64).


### Which cloud platform do you prefer?
✅ Answer:
“I have worked with AWS. I like it because of its wide adoption, rich DevOps services (EC2, S3, VPC, IAM, CloudWatch), and strong integration with automation tools like Terraform and Jenkins.”

### Explain Auto Scaling in AWS.
✅ Answer:
“Auto Scaling automatically adjusts the number of EC2 instances based on demand. It uses scaling policies and CloudWatch alarms to add instances when traffic increases and remove them when demand decreases.”

### Difference between Security Groups and NACL in AWS.
✅ Answer:

Security Group: Instance-level firewall, stateful (return traffic allowed automatically).

NACL: Subnet-level firewall, stateless (rules must be defined for inbound and outbound separately).

### How do you monitor applications and infrastructure?
✅ Answer:

Cloud-based: AWS CloudWatch (logs, metrics, alarms).

Open-source: Prometheus (metrics) + Grafana (dashboards).
Monitoring helps in proactive alerting and troubleshooting.


### A pod keeps crashing in Kubernetes. How will you troubleshoot?
✅ Answer:

Run kubectl describe pod <pod-name> → check events.

Run kubectl logs <pod-name> → check container logs.

Verify image, env variables, secrets, configs.

Check resource limits (CPU/Memory).

Restart pod or redeploy with fixes.

### Your CI/CD pipeline failed after code push. How will you debug?
✅ Answer:

Check Jenkins/GitHub Actions logs.

Identify which stage failed (build, test, deploy).

Fix syntax errors in YAML/Jenkinsfile.

Check credentials/tokens if deployment stage failed.

Re-run pipeline after fix.

### A developer says their feature isn’t visible after deployment. What will you do?
✅ Answer:

Verify pipeline logs (was deployment successful?).

Check container logs (was code built with latest changes?).

Run kubectl get pods → ensure new pods running.

Check load balancer/service mapping.

If rollback happened, redeploy.

### Your Docker container is running but app is not accessible. Steps?
✅ Answer:

Run docker ps → check port mapping.

Check Dockerfile EXPOSE port.

Check if app inside container is running (docker logs).

Verify firewall/security group.

Try curl localhost:<port> inside container.

### How will you deploy a three-tier app (frontend, backend, DB) on Kubernetes?
✅ Answer:

Create Docker images for each service.

Write Deployments for frontend, backend, DB.

Use Services to connect (frontend → backend → DB).

Use Persistent Volume for DB.

Configure Ingress for external access.

Optionally use Helm chart to manage deployment.

### what is git and github
Git is a version control system that helps developers track changes in code, collaborate, and manage different versions of a project.

GitHub is a cloud-based platform built on top of Git that allows developers to store, share, and collaborate on Git repositories online.
