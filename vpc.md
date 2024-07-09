# VPC (Virtual Private Cloud)
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

## AWS VPC
1. **VPC:** AWS has an default VPC assigned for every AWS account
2. **Subnet:** have 3 subnets, in 3 different AZ, with 3 CIDR blocks, within the same AWS default VPC range
3. **Route table:** It routes the traffic to route through our VPC
4. **Internet Gateway**: This gives the Internet access through our VPC 
