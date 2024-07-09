![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/0a27657a-6cda-42ed-b539-6790b9c6d246)# VPC (Virtual Private Cloud)
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/55d97410-81a8-427a-b06f-2db00dc96bf1)

## Understanding the CIDR, Private and Public IP
1. CIDR (Classless Inter-Domain Routing) — a method for allocating IP addresses
2. Used in Security Groups rules and AWS networking in general
3. They help to define an IP address range: 
* We've seen WW.XX.YY.ZZ/32 => one IP 
* We've seen 0.0.0.0/0 => all IPS 
* But we can define: 192.168.0.0/26 => Here 26 gives the set of IP addresses 192.168.0.0 - 192.168.0.63 (64 IP addresses)
4. A CIDR consists of two components 
* **Base IP:** 
  * Represents an IP contained in the range (XX.XX.XX.XX) 
  * Example: 100.0.0, 192.168.00, 
* **Subnet Mask:** 
  * Defines how many bits can change in the IP 
  * Example: /O, /24, /32 
  * Can take two forms: 
    * /8 => 255.0.0.0 
    * /16 => 255.255.0.0 
    * /24 => 255.255.255.0 
    * /32 => 255.255.255.255

## Understanding Subnet Mask
The subnet mask is used to define the allowed IP range for that subnet
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/1adfef3d-32e2-4329-b93a-a31c55f749d4)

## Public vs Private IP (in IPV4)
1. The Internet Assigned Numbers Authority (IANA) established certain blocks of IPv4 addresses for the use of private (LAN) and public (Internet) Addresses
2.  10.0.0.0 - 10.255.255.255 (10.0.0.0/8) in big networks
3.  172.16.0.0 - 172.31.255.255 (172.16.0.0/12) AWS defaultVPC in that range
4.  192.1680.0 - 192.168.255.255 (192.168.00/16) e.g., home networks
5.  Rest all the IP addesses on teh Internet are the Public

## AWS VPC (Virtual Private Cloud)
1. **VPC:** AWS has an default VPC assigned for every AWS account
2. **Subnet:** have 3 subnets, in 3 different AZ, with 3 CIDR blocks, within the same AWS default VPC range
3. **Route table:** It routes the traffic to route through our VPC
4. **Internet Gateway**: This gives the Internet access through our VPC 
5. We can create multiple VPC's in a region (max.5 per region- soft limit)
6. we can have max 5 CIDR per VPC
   * Min. size in /28 (16 IP)
   * Max. size is /16 (65536 IP)
7. Your VPC CIDR should NOT overlap with your other networks (e.g.. corporate)

## VPC - subnet (IPv4)
1. AWS reserves 5 IP addresses in each subnet, that is the reason we will be reduced by the 5 in total IP address every time
2. ![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/a4867833-6983-442b-ae26-20f312799632)

## Internet Gateway (IGW)
1. Allows resources (e.g., EC2 instances) in aVPC connect to the Internet
2. It scales horizontally and is highly available and redundant
3. Must be created separately from a VPC
4. One VPC can only be attached to one IGW and vice versa
5. Internet Gateways on their own do not allow Internet access...
6. Route tables must also be edited!

## Bastion Hosts
It is to access the EC2 instances that are on the private subnet,
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/b39ea108-d086-406f-8671-11d13bc5401c)

## NAT Instance (outdated)
1. presently we are using the `NAT Gateway` instead of the NAT Instance
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/d6382291-6e31-4fa8-8269-8273abb58c87)
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/3563019e-9f80-415d-9fa0-debd1585e1cc)

## NAT Gateway
1. AWS-managed NAT, higher bandwidth, high availability, no administration 
2. Pay per hour for usage and bandwidth 
3. NAT GW is created in a specific Availability Zone, uses an Elastic IP 
4. Can't be used by EC2 instance in the same subnet (only from other subnets) 
5. Requires an IGW (Private Subnet => NATGW => IGW) 
6. 5 Gbps of bandwidth with automatic scaling up to 100 Gbps 
7. No Security Groups to manage / required 
8. Blackhole in the route table means the ec2 instance connected  to that is stopped or terminated 
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/81bd85f9-51a7-467e-a592-36be1737414f)

## NAT gatewat vs NAT instance
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/2ef90757-0f67-4eaf-898d-4b146c9e46d7)

## NAT gateway vs Bastion hosts
1. Bastion Host: It handles inbound traffic from the internet, typically SSH or RDP connections, and forwards them to instances in private subnets.
2. NAT Instance: It primarily handles outbound traffic initiated by instances in private subnets by translating their private IP addresses to a public IP address.
