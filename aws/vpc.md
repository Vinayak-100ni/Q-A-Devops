##  What is Amazon Virtual Private Cloud (Amazon VPC), and why is it important in AWS networking?
Amazon VPC is a private, isolated virtual network inside AWS where I can launch and manage my resources like EC2, RDS, or load balancers. It’s important because it gives me full control over networking — things like IP ranges, subnets, route tables, internet gateways, NAT, security groups, and NACLs.

##  What is the primary difference between a public subnet and a private subnet in a VPC?
The primary difference is about internet access. A public subnet has a route to the Internet Gateway, so resources like EC2 instances in it can communicate directly with the internet.

A private subnet doesn’t have a direct route to the Internet Gateway. Instances there stay isolated from the internet, and if they need outbound access, they usually go through a NAT Gateway or NAT instance.

##  How do you connect a VPC to an on-premises data center, and what are the options available for this connection?
You can connect a VPC to an on-premises data center using a Site-to-Site VPN over the internet, AWS Direct Connect for private dedicated links, or a hybrid of both for reliability.

##  Explain the purpose of Amazon VPC peering and its use cases.
Amazon VPC peering lets me connect two VPCs privately so resources in them can talk to each other using private IPs, without going over the public internet.

Use cases include connecting VPCs from different teams or business units, sharing services like authentication or logging across VPCs, or even connecting VPCs across different AWS accounts or regions.

##  What is the significance of route tables in a VPC, and how do you control traffic routing between subnets?
In a VPC, route tables define how traffic flows. Each subnet is associated with a route table, and the routes inside it decide where packets go,By customizing route tables, I can control whether a subnet is public or private and how subnets communicate with each other.
