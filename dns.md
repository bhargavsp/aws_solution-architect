# DNS (Domain Name system)

## what is DNS?
1. Domain Name System which translates the human friendly hostnames into the machine IP addresses
2. www.google.com => 172.217.18.36
3. DNS is the backbone of the Internet
4. DNS uses hierarchical naming structure

## DNS Terminologies
* Domain Registrar: Amazon Route 53, GoDaddy, ...
* DNS Records: A,AAAA, CNAME, NS, ....
* zone file: which contains all the DNS records, this is were we match host names to the IP addresses
* Name server: resolves the DNS queries
* Top Level Domain (TLD): .com, .us, .in, .gov, .org
* Second Level Domain (SLD): amazon.com, goodle.com
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/112b204c-2e3b-460e-831b-142bf72ef969)

## How DNS works
1. DNS is a Domain Name System works as a transalator between the browser (which we type the browser addres in the english) and the internet (which only understands the IP address)
2.  There ar 4 types of the DNS servers:
3.  DNS recrusive resolver/DNS resolver
4.  Root name server
5.  TLD (Top Level Domain)servers: it stores the addresses of the Authoritative name servers so that they can be communicated to the particular authoritative name server once they are ser 
6.  Authoritative name server: they are maintained by the domain registrars (ex. godaddy), the authoritative name server is assigned while we are buying the domain from the godaddy, and also this information is shared with the TLD servers, so they TLD serveers contact the particular authoritative name server while the request is made from the client. Refer to for brief explanation https://www.youtube.com/watch?v=JkEYOt08-rU&t=1s and
7.  https://www.cloudflare.com/learning/dns/what-is-dns/
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/c9cb5b04-2fd4-445f-bc80-15e5a3214b25)

## amazon Route 53
1. Route 53 has a bunch of the records
2. Each record has a lot of information, such as
* Domain/subdomain Name — e.g., example.com
* Record Type — e.g., A or AAAA
* Value - e.g., 12.34.56.78
* Routing Policy — how Route 53 responds to queries
* TTL — amount of time the record cached at DNS Resolvers
3. Types of record types that are supported in the Route 53
* (must know): A / AAAA / CNAME / NS
* (advanced): CAA / DS / MX / NAPTR / PTR / SOA /TXT / SPF / SRV

## route 53 record types
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/7768fd0f-ae54-4079-9604-11fefc1144e2)

## Route 53 Hosted zones and public vs private hosted zones
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/363032f6-aa33-4a86-8120-b2c601ffef6f)
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/c6e7a15a-0aad-4bac-9966-ecfa5133eaab)




