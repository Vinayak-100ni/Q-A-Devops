### How does your company work?
company that mainly focuses on providing software development and IT solutions. The company works on various client-based and in-house projects, where different teams handle development, testing, deployment, and maintenance.
As a DevOps intern, I got to see how the company follows a structured workflow — starting from planning and development, to CI/CD integration, containerization, and deployment using cloud platforms. The development team works closely with DevOps and QA teams to ensure smooth delivery and automation.
The company follows agile methodology, where tasks are divided into sprints, and we track progress through tools like Jira, Overall, it focuses on collaboration, automation, and delivering efficient, scalable, and secure solutions to clients.

### What issues did you face during your internship and how did you resolve them?
One common issue was build failure in the CI/CD pipeline due to missing dependencies or incorrect environment variables. I resolved it by checking the build logs in Jenkins, identifying the exact error, and updating the pipeline configuration and environment settings.

Another issue I faced was container communication failure when deploying microservices using Docker and Kubernetes. The pods were running, but the services were not reachable. I troubleshooted it by checking pod logs, validating the service and network configurations, and updating the YAML files to fix port mappings and labels.

### How did you create the CI/CD pipeline during your project?
During my DevOps internship, I built a complete CI/CD pipeline and automated AWS infrastructure.
I used Terraform to provision AWS resources like EC2, S3, and IAM roles.
Then, I integrated Jenkins with GitHub so that every code push triggered the pipeline.
In the build stage, Jenkins used Maven to compile the code, and SonarQube to check code quality.
If the code passed, Jenkins built a Docker image, pushed it to Docker Hub, and deployed it to a Kubernetes cluster.
Finally, I used Datadog for monitoring performance and alerts.
This setup automated the entire workflow — from infrastructure creation to deployment and monitoring — improving speed, reliability, and code quality.

### Can you explain your CI/CD pipeline stages step by step?
my CI/CD pipeline had six main stages:

Code Checkout:
Jenkins automatically pulled the latest code from GitHub whenever developers pushed new commits.

Build Stage:
I used Maven to compile the code and package the application — this ensured the build was clean and error-free.

Code Quality Analysis:
I integrated SonarQube to analyze the code for bugs, vulnerabilities, and code smells.
The pipeline continued only if the code passed the SonarQube quality gate.

Docker Build & Push:
Jenkins built a Docker image of the application and pushed it to Docker Hub for versioned storage.

Deployment Stage:
Using Kubernetes, the pipeline deployed the new Docker image to the cluster running on AWS.
The infrastructure (EC2, VPC, etc.) was created and managed using Terraform, so everything was automated and consistent.

Monitoring & Alerts:
After deployment, I used Datadog to monitor system metrics, logs, and application performance.
It helped us quickly detect any post-deployment issues.


So overall, the pipeline handled everything automatically — from code commit to deployment and monitoring — which saved time, reduced manual errors, and improved delivery speed.
