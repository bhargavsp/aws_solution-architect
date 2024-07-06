# Cloud Front

## what is Cloud Front
1. Cloud Front is the Content Delivery Network (CDN). Amazon CloudFront is a web service that speeds up distribution of your static and dynamic web content, such as . html, . css, . js, and image files, to your users.
2. Basically the content will be cached at the edge location (POPs) maybe for a day
3. It has a 216 point of presence globally(same as edge location)
4. has an DDOs protection using the security, amazon firewall

## cloud Front origins(the server or the s3 bucket where our appplication data is saved is called as a origin)
1. S3 bucket 
* For distributing files and caching them at the edge
* Enhanced security with CloudFront Origin Access Control (OAC)
* OAC is replacing Origin Access Identity (OAI)
* CloudFront can be used as an ingress (to upload files to S3) 
2. Custom Origin (HTTP) 
* Application Load Balancer
* EC2 instance
* S3 website (must first enable the bucket as a static S3 website)
* Any HTTP backend you want
* To access the cloud front the EC2 or the ELB must be public (else the cloudfront cant access our server)
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/092678ff-a5b9-4009-8ae6-bc8b4961fb27)
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/aed206fe-9eb0-43eb-bb8a-1e9f0e26a401)


## S3 cross region replication
1. Must be setup for each region you want replication to happen
2. Files are updated in near real-time
3. Read only
4. Great for dynamic content that needs to be available at low-latency in few regions
   
## Cloud Front pricing classes
TO reduce the cost in the cloud front we can limit the number of edge location to access
1. Price Class All: all regions — best performance
2. Price Class 200: most regions, but excludes the most expensive regions
3. Price Class 100: only the least expensive regions
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/668d4d3b-dd68-4e25-94cc-2cbc200a2d9a)

## Cloud Front - cache invalidations
Incase we want to update the backend origin data, the cloud Front cached data will be updated only after the TTL has completed, so to avoid this we have cache invalidations in cloudfront, it refreshes the content bypassing the TTL, it can refresh the whole content or just some path of it 
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/94747cf9-7d9a-4834-b153-9c81fb43fb6a)

## AWS Global Acclerator
Before knowing about the AWS Global Acclerator, we have to know the 2 concepts
1. unicast IP: Each server has its own IP address <br/> ![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/20b84515-e1e6-4fd3-873e-e221f48e626c)
2. Anycast IP: Every server of the application has a same IP, so the client connects to nearest IP and get the data ![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/a6285d73-daa7-433d-9128-2c6c67b9970a)
3. AWS Global Acclerator uses the Anycast IP concept to work
4. Leverage the AWS internal network to route to your application, they doesnt change at any time
5. 2 Anycast IP(static IP) are created for your application
6. The Anycast IP send traffic directly to Edge Locations The Edge locations send the traffic to your application
7. if there is an failover, in less than 1 minute there will be a healthy end port
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/4e25c5f0-7e88-47b3-bb51-87f08be31156)

## Global Accelerator vs CloudFront
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/711db7e1-baa7-4333-9688-07164a36709e)



