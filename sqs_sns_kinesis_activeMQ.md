![image](https://github.com/user-attachments/assets/6a42a199-e095-4364-a98d-495dab224e9e)# sqs_sns_kinesis_activeMQ

## Introduction to Messaging
We have 2 types of communications in messaging
1. Synchronous communications
2. Asynchronous/Event based communication
![image](https://github.com/user-attachments/assets/8e1c03d6-2a1a-4d04-aff8-9b1d8a6fd152)
3. Synchronous between applications can be problematic if there are sudden spikes of traffic 
4. What if you need to suddenly encode 1000 videos but usually it's 10? 
5. In that case, it's better to decouple your applications, 
  * using SQS: queue model
  * using SNS: pub/sub model
  * using Kinesis: real-time streaming model 
6. These services can scale independently from our application!

## SQS
1. There will producers who produce message and send to the queue to store them
2. There will be consumer, who takes the message and works on it and then consumer will delet the message from queue <br/> ![image](https://github.com/user-attachments/assets/50dc0119-f1cc-4ac5-8529-211558272d26)
3. consumer can be EC2 instances, lambda functions or servers, consumers can take upto 10 messages at a time
4. we can do the horizontal scalling to improve the throughput of processing
5. To not duplicate the message processing, we have message visibility timeout for 30sec so other consumers cant see or process the message till 30sex
6. we can also use the SQS as a buffer in high amount of requests(at the time of sales) as the SQS is auto scalling it is infinitely scalable
8. ![image](https://github.com/user-attachments/assets/ea0b6fbb-dfa3-4496-a9cb-423137f920a3)
9. ![image](https://github.com/user-attachments/assets/a8a6aaf7-4d10-4fdc-b3c2-95250ba4f271)
10. ![image](https://github.com/user-attachments/assets/c34c6401-a27c-46c8-978d-66600aeb22ce)

## ordering data into SQS
![image](https://github.com/user-attachments/assets/46fd8928-b342-4b45-8d7e-09f2025bde41)


## SNS
1. Here we have SNS topics
2. For suppose and producer needs to send the notifications to multiple receives for the same order, then SNS topic will be used as a single receiver
3. ![image](https://github.com/user-attachments/assets/81531199-e412-46a5-8185-cd35bc949d2e)
![image](https://github.com/user-attachments/assets/92e11a2b-3894-4b37-b6f7-18602b69f2a3)

## SNS + SQS: Fan Out pattern
1. push once in SNS, receive in all SQS queues that are subscribers
2. Make sure your SQS queue access ploicy allows for SNS to write
3. JSON policy used to send the queries by filtering to specific topic 
![image](https://github.com/user-attachments/assets/b84b7dfc-1816-4426-8db4-fe119207a09d)
![image](https://github.com/user-attachments/assets/68ee3ff2-8678-4248-9ad1-2416ef7b4398)

## Kinesis
1. Kinesis makes it easy to collect, process and analyze streaming data in real-time
2. Kinesis Data Streams: capture, process, and store data streams
3. Kinesis Data Firehose: load data streams into AWS data stores <br/> ![image](https://github.com/user-attachments/assets/cf0e7676-4fad-43c3-91a3-1c9928553263)
4. Kinesis Data Analytics: analyze data streams with SQL or Apache Flink
5. Kinesis Video Streams: capture, process, and store video streams 
![image](https://github.com/user-attachments/assets/a51af072-1c57-43b3-85a0-fad8a54fb7f2)

## SQS vs SNS vs Kinesis
![image](https://github.com/user-attachments/assets/e881a9a3-b7e0-4181-a0ab-53de62efbe7b)



