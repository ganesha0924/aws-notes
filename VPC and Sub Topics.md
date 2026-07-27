1. VPC (Virtual Private Cloud)

What is it?
A VPC is your own private network inside AWS.
You control:
IP addresses
Subnets
Routing
Security

2. Private subnet -
	BY Default if we don't specify anything. everything is private subnet
	Private Subnet
	No direct internet access.
	More secure.
	Used for sensitive resources.

   Public subnet - 
	Has internet access.
	Used for resources users need to reach.
	To connect to internet need IGW

   Internet Gateway (IGW)
	
	Allows the VPC to connect to the internet.

	Without IGW:
	No internet
	No website access

3.Public Route Table
	What is it?
	Tells traffic where to go.
	Remember

	Route Table = Google Maps for network traffic.
4.Security Group
	What is it?

	Firewall for EC2.

	Controls:

	Incoming traffic (Inbound)
	Outgoing traffic (Outbound)

5.Bastion Host
	What is it?
	A public EC2 used to access private EC2 servers.

6.
	Private Route Table: Controls traffic for resources in a private subnet.
	It does not have a direct route to the Internet Gateway (IGW), so the subnet isn't directly reachable from the internet.
	If internet access is needed (for updates or downloads), it sends traffic to a NAT Gateway instead.
														

=============================================================================

SG - works on Instance level
NACL (Network Access Control List)- Works on Subnet level

Real-world use
	Security Group: Allow HTTP (80) and HTTPS (443) to your web server.
	NACL: Block traffic from a suspicious IP range for the entire subnet.


| Security Group     | NACL                    |
| ------------------ | ----------------------- |
| Works on EC2       | Works on Subnet         |
| Stateful           | Stateless               |
| Allows only        | Allows & Denies         |
| More commonly used | Extra layer of security |


1.VPC Endpoints

	What is it?
	Allows private resources to access AWS services without using the internet.
	Examples:
	S3
	DynamoDB

	Real-world use:
	A private EC2 uploads files to an S3 bucket without using an Internet Gateway or NAT Gateway.


2.Managed Prefix Lists

	What is it?
	A reusable list of IP addresses or CIDR blocks.
	Instead of adding the same IPs in many Security Groups or Route Tables, create one Prefix List and reuse it.
	Remember
	Managed Prefix List = One IP list, use everywhere.

3.VPC Peering
	What is it?
	Connects two VPCs so they can communicate privately.
	Requirements:
	Add routes in both VPCs.
	Communication is private over the AWS network.
	Remember
	VPC Peering = Private bridge between two VPCs.

	Note: even if two vpcs are different in aws account VPC PEERING WORKS

4.5. Transit Gateway (TGW)
	What is it?

	A central hub that connects many VPCs and even on-premises networks.

	Without TGW:

	Every VPC needs separate peering connections. AND DIFFICULT TO MANAGE

	With TGW:

	All VPCs connect to one central gateway.

