##  When would you choose an Application Load Balancer (ALB) over a Network Load Balancer (NLB), and vice versa?
ALB is best when I need smart routing for HTTP/HTTPS at Layer 7,For example, if I want to route traffic based on URLs, hostnames,t’s best for web applications, APIs, and microservices.

NLB when I need ultra-high performance and very low latency at the transport layer (Layer 4). For example, handling millions of requests per second, TCP/UDP traffic, or workloads like gaming
