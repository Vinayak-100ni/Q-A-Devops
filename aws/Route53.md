## What are top-level domains (TLDs) and second-level domains, and how do they relate to Route 53?
A Top-Level Domain (TLD) is the last part of a domain like .com or .in, while the Second-Level Domain (SLD) is the name just before it, like example in example.com. In Route 53, when I register a domain, I choose both the TLD and SLD (e.g., mybusiness.com). Route 53 then lets me manage DNS records for that domain through hosted zones, mapping names like www.mybusiness.com to AWS resources

## Explain the primary services provided by Amazon Route 53
it handles domain registration, DNS resolution, health checks, traffic routing, and integrates

Amazon Route 53 is AWS’s DNS and domain management service. It mainly provides five key functions — first, domain registration, where we can buy and manage domain names directly through AWS. Second, DNS resolution, which translates domain names into IP addresses. Third, health checking and failover, which automatically redirects traffic to healthy endpoints if one fails. Fourth, traffic management using different routing policies like weighted, latency-based, or geolocation routing. And fifth, integration with other AWS services like CloudFront, ELB, and S3 to provide high availability and low latency globally.

##   What are the differences between domain registration and DNS hosting, and how does Route 53 handle both?
Domain registration is the process of buying and owning a domain name, like infobharatinterns.com, through a domain registrar. The registrar is responsible for recording your domain ownership in the global domain registry.

DNS hosting, on the other hand, is about managing how your domain name connects to your resources — for example, mapping www.infobharatinterns.com to an IP address using DNS records like A or CNAME.

Amazon Route 53 handles both.
It acts as a domain registrar when you register your domain directly through AWS, and it also provides authoritative DNS hosting through hosted zones, where you can manage all your DNS records.

##  How can you migrate a domain from another registrar to Route 53?
To migrate a domain to Route 53, I first unlock the domain at the current registrar and get the authorization or EPP code. Then, in the Route 53 console, I choose ‘Transfer Domain’, enter the domain name and authorization code, and provide the contact details. After paying the transfer fee, I approve the confirmation email from AWS. Once the transfer is complete, the domain appears in Route 53’s Registered Domains, and I can set up a hosted zone and update the name servers to Route 53 for DNS hosting

##  Explain the various routing policies supported by Route 53, including Simple, Weighted, Latency-Based, Geolocation, and Failover policies.
Amazon Route 53 supports several routing policies to control how user traffic is directed to resources.

Simple Routing Policy – It’s the default policy. It gives one record with one value, like one IP address or one load balancer. Used when there’s only a single resource for a domain.

Weighted Routing Policy – This lets you split traffic between multiple resources based on assigned weights. For example, 70% of traffic to one server and 30% to another. It’s useful for A/B testing or gradual rollouts.

Latency-Based Routing Policy – It routes users to the AWS region with the lowest latency for the best performance. For example, users in India go to the Mumbai region, and users in the US go to Virginia.

Geolocation Routing Policy – It routes traffic based on the geographic location of the user. For example, Indian users see Indian content, and US users see US content.

Failover Routing Policy – It’s used for high availability. You define a primary and a secondary endpoint. If the primary fails (based on Route 53 health checks), traffic automatically switches to the secondary.

So in short — Simple for one resource, Weighted for traffic splitting, Latency for best performance, Geolocation for location-based routing, and Failover for high availability.

##  What is the purpose of a weighted routing policy, and when would you use it?
A weighted routing policy in Route 53 is used to distribute traffic across multiple resources based on assigned weights.

For example, if I have two servers, I can send 70% of the traffic to one and 30% to another by setting corresponding weights.

It’s mainly used for A/B testing, gradual traffic migration, or testing new versions of an application without sending all users to it at once.

So, the purpose is to control the proportion of traffic going to different endpoints for testing, load balancing, or smooth rollouts.

##  How does the latency-based routing policy work, and when is it beneficial for optimizing user experience?
Latency-based routing in Route 53 directs user traffic to the AWS region that provides the lowest network latency, meaning the fastest response time.

For example, a user in India would be routed to an application hosted in the Mumbai region, while a user in the US would go to the Virginia region.

This is beneficial for optimizing user experience, especially for global applications, because it reduces response time and improves performance by serving content from the closest or fastest region.

##  What are health checks in Amazon Route 53, and how can they be used to monitor the health of resources?
In Amazon Route 53, health checks are used to monitor the health and availability of resources like EC2 instances, load balancers, or on-premises servers.

Route 53 periodically sends HTTP, HTTPS, or TCP requests to the endpoint to check its status.

If the resource fails the health check, Route 53 can automatically redirect traffic to a healthy endpoint using failover routing.

This helps achieve high availability and reliability for applications.

So essentially, health checks let Route 53 detect failures and ensure users are always routed to healthy, responsive resources.

##  How can you configure a failover routing policy with Route 53, and what role do health checks play in this scenario?
In Route 53, failover routing allows you to create a primary and a secondary endpoint for a domain. You associate a health check with the primary endpoint so Route 53 can monitor its availability. If the primary fails, traffic is automatically routed to the secondary. Health checks are essential here because they determine the health of the primary resource and trigger the failover to ensure high availability and reliability

##  Discuss best practices for optimizing Route 53 for high availability and low latency.
To optimize Amazon Route 53 for high availability and low latency, some best practices are:

Use multiple AWS regions – Deploy your application across multiple regions and use latency-based routing so users connect to the closest or fastest region.

Implement health checks and failover – Set up health checks for your endpoints and use failover routing to redirect traffic automatically if an endpoint becomes unhealthy.

Leverage weighted routing for gradual rollouts – Split traffic between resources to test new versions without affecting all users, reducing risk of downtime.

Use geolocation routing when needed – Direct users to region-specific content for better performance and compliance.

Monitor and update DNS TTLs wisely – Use appropriate Time-To-Live (TTL) values for DNS records to balance between fast failover and DNS query efficiency.

Integrate with CloudFront and ELB – Combine Route 53 with CloudFront or Elastic Load Balancers to cache content globally and distribute traffic efficiently.

##  Give examples of scenarios where you would use Route 53 for global load balancing, failover, or disaster recovery.
Amazon Route 53 can be used in several scenarios for global load balancing, failover, and disaster recovery:

Global Load Balancing:

If a web application is deployed in multiple AWS regions, like Mumbai, Virginia, and Singapore, latency-based routing can send users to the region with the lowest response time.

Example: A user in India connects to Mumbai, while a user in the US connects to Virginia, ensuring low latency globally.

Failover:

For a critical application hosted in a primary region, a secondary region or backup EC2 instance can be configured.

Example: If the primary Mumbai server fails, Route 53 automatically routes traffic to the secondary Virginia server using failover routing with health checks.

Disaster Recovery:

For DR strategies, you can maintain a hot standby or warm standby region.

Example: In case the primary region goes down due to a natural disaster, Route 53 redirects all traffic to the standby region, ensuring business continuity.

So, Route 53 provides the flexibility to handle global traffic efficiently while maintaining high availability and disaster recovery readiness.

###   Explain different types of records in RT53(Like A, AAAA, NS, SOA, etc.)
In Amazon Route 53, DNS records are used to define how domain names are resolved to IP addresses or other resources. The main record types are:

A Record (Address Record):
It maps a domain name to an IPv4 address.
For example, example.com → 192.0.2.1.
It’s used when you want your domain to point to an EC2 instance or load balancer using IPv4.

AAAA Record:
Similar to an A record, but it maps a domain name to an IPv6 address.
Example: example.com → 2001:0db8:85a3::8a2e:0370:7334.

CNAME Record (Canonical Name):
It maps one domain name to another domain name (an alias).
For example, www.example.com → example.com.
It’s useful when you want multiple domain names to point to the same application.
