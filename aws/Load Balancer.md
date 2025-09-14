##  When would you choose an Application Load Balancer (ALB) over a Network Load Balancer (NLB), and vice versa?
ALB is best when I need smart routing for HTTP/HTTPS at Layer 7,For example, if I want to route traffic based on URLs, hostnames,t’s best for web applications, APIs, and microservices.

NLB when I need ultra-high performance and very low latency at the transport layer (Layer 4). For example, handling millions of requests per second, TCP/UDP traffic, or workloads like gaming

##  What is a target group in the context of ALB, and how is it used for routing traffic to instances?
target groups act as the bridge between the load balancer and the actual backend services, and they allow to route traffic to different services based on rules like path or hostname.

##  Explain the concept of listeners and rules in load balancer configuration.
In a load balancer, a listener is like the entry point. It checks for incoming connection requests on a specific port and protocol, for example, HTTP on port 80 or HTTPS on port 443.

Rules are the conditions attached to that listener which decide where to send the traffic. For example, I can create rules based on hostnames (api.example.com) or paths (/images) and forward that traffic to the right target group.

##  What are the health checks performed by AWS load balancers, and how do they impact instance health?
AWS load balancers use health checks to make sure traffic only goes to healthy instances. A health check is basically a test request the load balancer sends to each target, like hitting a specific path on HTTP (/health) or checking a TCP port.

If an instance responds correctly within the configured threshold, it’s marked healthy and will continue receiving traffic. If it fails multiple checks in a row, it’s marked unhealthy, and the load balancer automatically stops sending traffic to it until it recovers.

##  How does AWS ensure high availability for load balancers, and what are the best practices for achieving redundancy?
AWS ensures high availability by deploying load balancers across multiple AZs, and best practice is to enable multi-AZ, configure health checks, and use Route 53 for multi-region redundancy.

## Explain the use of cross-zone load balancing in AWS, and when would you enable or disable it?
Cross-zone load balancing means the load balancer can distribute traffic evenly across all registered targets in all Availability Zones, not just within the AZ where the request came in.

I would enable it when I want even distribution of traffic and don’t want targets in one AZ to be overloaded while others sit idle. This is especially useful if the number of instances is not the same across AZs.

I might disable it if I want strict isolation per AZ for compliance, latency, or cost reasons — for example, with a Network Load Balancer, cross-zone balancing can increase inter-AZ data transfer costs.
