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
9. To make the instances highly available, we should configure NAT gatways in the multiple AZ, for the fault tolerance
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/81bd85f9-51a7-467e-a592-36be1737414f)

## NAT gatewat vs NAT instance
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/2ef90757-0f67-4eaf-898d-4b146c9e46d7)

## NAT gateway vs Bastion hosts
1. Bastion Host: It handles inbound traffic from the internet, typically SSH or RDP connections, and forwards them to instances in private subnets.
2. NAT Instance: It primarily handles outbound traffic initiated by instances in private subnets by translating their private IP addresses to a public IP address.

## Security Groups and NACLs
1. NACL are like a firewall which control traffic from and to subnets
2. One NACL per subnet, new subnets are assigned the Default NACL 
3. You define NACL Rules: 
4. Rules have a number ( I -32766), higher precedence with a lower number 
5. First rule match will drive the decision 
6. Example: if you define #100 ALLOW 10.0.O.lO/32 and #200 DENY 10.0.0.10/32, the IP address will be allowed because 1 00 has a higher precedence over 200 
   * The last rule is an asterisk (*) and denies a request in case of no rule match 
   * AWS recommends adding rules by increment of 100 
   * Newly created NACLs will deny everything 
   * NACL are a great way of blocking a specific IP address at the subnet level

1. Incoming Request: So let's take an example of a subnet and we know when you have an EC2 instance that we attach a security group to it. But there is an extra level of protection on the subnet that we haven't seen yet, which is your network ACL or NACL. And let's take an example to really understand the role of a NACL in an incoming request. So a request goes to your EC2 instance, now what is happening from a network perspective? Well, first the request is going to make it to the NACL before going into the subnets. And so there are going to be some inbound rules on the NACL that are going to be defined. And if the request is not allowed, then the request doesn't go in. And if it is allowed, then it will go in, right? So the NACL is stateless. So we'll see what that means in a second. So the first request goes through the NACL and then it reaches inside the subnets and it goes through the security group inbound rules, okay. So we know how this works. So again, if the request is not allowed explicitly then it is denied. Now something about security group is that they are stateful. So remember NACLs are stateless and security groups are stateful. So what does that mean? That means that if the request makes it through the inbound rules of the security group and makes it to the EC2 instance, the EC2 instance will then reply with whatever reply there is to do for the application perspective. And then the outbound is automatically going to be accepted at the security group level. This is because the security group is stateful. That means whatever is accepted in can go also out. So here, there is no rules being evaluated. And the security group outbound rules are not mattering in this example. So now that we know that the outbound at the security group level is always allowed because it's stateful, what happens still? Well the NACL is not stateful, it is stateless, and therefore, because it is stateless then the NACL outbound rules are going to be evaluated. And again, if they are not passing, then the request will not make it through. So this is for an incoming request. 
2. Outgoing Request: Now let's go through the same scenario, but for an outgoing request, and you can try doing this on your own by pausing the video, just to see if you understand the difference between stateful and stateless. Okay. Did you try? Okay, let's go. So the security group this time, so the EC2 instance is making an outbound request. So it's doing a request to the outside. And so the EC2 instance will first maybe use, for example, connect to www.google.com, and so therefore the first rules that are going to be evaluated are the security group outbound rules. So is the traffic allowed out from the EC2 instance to the web? Then if the rules are good and the request is allowed, then the request goes through the NACL outbound rules as well. So they're evaluated. Then the request reaches www.google.com, it comes back to Amazon web services, and obviously the NACL is stateless and therefore the NACL inbound rules are going to be evaluated. And finally, while the inbound within the subnet at the security level is also going to be allowed no matter what, because of the statefulness of your security group rules. So here the inbound rules of your security group do not make a difference because the admin roles was already accepted and your security group is stateful. So hopefully that is a very clear explanation between stateful and stateless.
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/627c2641-a54d-4cbf-9202-5c1d03e8434f)

## Ephemeral ports
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/cfede6ca-d36c-4419-a3db-d1be517ec33e)

## NACL with the ephemeral port
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/6351c7b3-eb7c-4612-9611-9671201210f6)

## SG's vs NACL's
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/71899554-1f2c-483e-afd3-b30302aab37c)

## VPC peering
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/6cab2868-5a13-4b66-8749-f04a5a2373ae)

## VPC Endpoint
1. Interface Endpoint only preferred, if the access is required from on-premises (Site to Site VPN or Direct Connect), a differentVPC or a different region else use the gateway enpoint as it is free
2. There are 2 types of Endpoints
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/b8994789-0b0d-4734-a45b-315f0fa0e5b2)
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/2041229f-27f2-47c0-857a-05bd56be298d)

## VPC Flow Logs
1. Capture information about IP traffc going into your interfaces: 
2. VPC Flow Logs 
3. Subnet Flow Logs 
4. Elastic Network Interface (ENI) Flow Logs 
5. Helps to monitor & troubleshoot connectivity issues 
6. Flow logs data can go to S3, CloudWatch Logs, and Kinesis Data Firehose 
7. Captures network information from AWS managed interfaces too: ELB, RDS, ElastiCache, Redshift, WorkSpaces, NATGW,Transit Gateway...
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/a0fcea6b-a96e-4438-8080-9ece5f4e5794)
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/8b1a2e4e-e988-4a4b-951c-1d463af41ddb)

## SIte-site VPN
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/af5aa839-65b0-4c1b-82e0-42fa51aa1090)

## VPN Cloud Hub
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/bb28c44d-aff1-4746-ab1b-e37e8c5ed2d8)

## Direct connect (DX)
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/5d093ee7-bf96-4980-aa7a-595d82f1d0eb)

![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/e7a0bab7-c04f-4776-8bd5-b69386b7da54)

## Transit Gateway
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/45536fa2-8e13-4d9f-ae46-71c3f17a2bb0)

## transit gateway vs vitual private gateway
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/6b248d0c-3eb6-455f-bfd7-7440994a7063)
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/ca5074fe-61ca-4f53-a33a-37d9be28bf43)
