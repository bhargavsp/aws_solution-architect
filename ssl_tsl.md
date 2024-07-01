# SSL and TSL certificates

## what and How are the SSL/TSL certificates work 
1. An SSL- Certificate allows traffic between your clients and your load balancer to be encrypted in transit called (in-flight encryption)
2. SSL refers to Secure Sockets Layer; used to encrypt connections
3. TLS refers to Transport Layer Security, which is a newer version
4. Nowadays, TLS certificates are mainly used, but people still refer as SSL
5. Public SSL- certificates are issued by Certificate Authorities (CA). Ex: Comodo, Symantec, GoDaddy, GlobalSign, Digicert, Letsencrypt, etc...
6. The SSL certificate is atttached to our Elastic Load balance, so the traffic from the client to our server is encrypted
7. if we are using some website and there is Green lock it is secure and has certificated, if there is a red sign, the request is not encrypted and it is not recommended to use the credit or debit card details
8. SSL certificates have an expiration date and must be renewed
9. The load balancer uses an X.509 certificate (SSL/TLS server certificate)
10. You can manage certificates using ACM (AWS Certificate Manager)
11. You can create upload your own certificates alternatively
12. HTTPS listener: 
    * You must specify a default certificate 
    * You can add an optional list of certs to support multiple domains 
    * Clients can use SNI (Server Name Indication) to specify the hostname they reach 
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/28f281dc-a665-406f-a320-07e42242a4fb)

## SSL - server Name Indication (SNI)
1.  SNI solves the problem of solving multiple SSL certificate onto one web server to serve the multiple websites
2.  It's a newer protocol and require the client to indicate the hostname of the target server in the initial SSL handshake
3.  the server will then find the correct certificate or return the default one
4.  onyl works with the ALB and NLB not with the CLB
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/a4c48574-b122-4355-80e6-d7c8ede0ff32)
