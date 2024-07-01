# Networking

## Networking has 2 sorts of IP's 
1. IPV4 -  
2. IPV6 - Hexadecimal (used for IOT)

## Private and Public IP
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/0e9e9cdc-5dd9-4a48-8477-0a5643dd66cc)
1. machines connect to WWW using an NAT + internet gateway (a proxy)
2. only a specified number if IP's are used as Private IP's
3. private IP means the machine can only be identified on that particular private network only

## can we connect to the EC2 instance through SSH with the private IP
1. It is not possible because the private IP's only belong to the particular network.
2. example the AWS instance private IP belongs to the AWS network,
3. Only the internal AWS network private IP can connect to the other private IP inside the AWS network.  

## How the DNS works
1. DNS is a Domain Name System works as a transalator between the browser (which we type the browser addres in the english) and the internet (which only understands the IP address)
2.  There ar 4 types of the DNS servers:
3.  DNS recrusive resolver/DNS resolver
4.  Root name server
5.  TLD (Top Level Domain)servers: it stores the addresses of the Authoritative name servers so that they can be communicated to the particular authoritative name server once they are ser 
6.  Authoritative name server: they are maintained by the domain registrars (ex. godaddy), the authoritative name server is assigned while we are buying the domain from the godaddy, and also this information is shared with the TLD servers, so they TLD serveers contact the particular authoritative name server while the request is made from the client. Refer to for brief explanation https://www.youtube.com/watch?v=JkEYOt08-rU&t=1s and
7.  https://www.cloudflare.com/learning/dns/what-is-dns/
