1\. VPC (Virtual Private Cloud)



What is it?

A VPC is your own private network inside AWS.

You control:

IP addresses

Subnets

Routing

Security



2\. Private subnet -

&#x09;BY Default if we don't specify anything. everything is private subnet

&#x09;Private Subnet

&#x09;No direct internet access.

&#x09;More secure.

&#x09;Used for sensitive resources.



&#x20;  Public subnet - 

&#x09;Has internet access.

&#x09;Used for resources users need to reach.

&#x09;To connect to internet need IGW



&#x20;  Internet Gateway (IGW)

&#x09;

&#x09;Allows the VPC to connect to the internet.



&#x09;Without IGW:

&#x09;No internet

&#x09;No website access



3.Public Route Table

&#x09;What is it?

&#x09;Tells traffic where to go.

&#x09;Remember



&#x09;Route Table = Google Maps for network traffic.

4.Security Group

&#x09;What is it?



&#x09;Firewall for EC2.



&#x09;Controls:



&#x09;Incoming traffic (Inbound)

&#x09;Outgoing traffic (Outbound)



5.Bastion Host

&#x09;What is it?

&#x09;A public EC2 used to access private EC2 servers.



6\.

&#x09;Private Route Table: Controls traffic for resources in a private subnet.

&#x09;**It does not have a direct route to the Internet Gateway (IGW), so the subnet isn't directly reachable from the internet.**

&#x09;If internet access is needed (for updates or downloads), it sends traffic to a NAT Gateway instead.

&#x09;													



=============================================================================



SG - works on Instance level

NACL (Network Access Control List)- Works on Subnet level



Real-world use

&#x09;Security Group: Allow HTTP (80) and HTTPS (443) to your web server.

&#x09;NACL: Block traffic from a suspicious IP range for the entire subnet.





| Security Group     | NACL                    |

| ------------------ | ----------------------- |

| Works on EC2       | Works on Subnet         |

| Stateful           | Stateless               |

| Allows only        | Allows \& Denies         |

| More commonly used | Extra layer of security |





1.VPC Endpoints



&#x09;What is it?

&#x09;Allows private resources to access AWS services without using the internet.

&#x09;Examples:

&#x09;S3

&#x09;DynamoDB



&#x09;Real-world use:

&#x09;A private EC2 uploads files to an S3 bucket without using an Internet Gateway or NAT Gateway.





2.Managed Prefix Lists



&#x09;What is it?

&#x09;A reusable list of IP addresses or CIDR blocks.

&#x09;Instead of adding the same IPs in many Security Groups or Route Tables, create one Prefix List and reuse it.

&#x09;Remember

&#x09;Managed Prefix List = One IP list, use everywhere.



3.VPC Peering

&#x09;What is it?

&#x09;Connects two VPCs so they can communicate privately.

&#x09;Requirements:

&#x09;Add routes in both VPCs.

&#x09;Communication is private over the AWS network.

&#x09;Remember

&#x09;VPC Peering = Private bridge between two VPCs.



&#x09;**Note: even if two vpcs are different in aws account VPC PEERING WORKS**



**4.5. Transit Gateway (TGW)**

&#x09;**What is it?**



&#x09;**A central hub that connects many VPCs and even on-premises networks.**



&#x09;**Without TGW:**



&#x09;**Every VPC needs separate peering connections. AND DIFFICULT TO MANAGE**



&#x09;**With TGW:**



&#x09;**All VPCs connect to one central gateway.**





