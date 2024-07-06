# Containers

## What is Docker 
1. Docker is a software development platform to deploy apps
2. Apps are packaged in containers that can be run on any OS
3. Apps run the same, regardless of where they're run 
* Any machine
* No compatibility issues
* Predictable behavior
* Less work
* Easier to maintain and deploy
* Works with any language, any OS, any technology
* Use cases: microservices architecture, lift-and-shift apps from on-premises to the AWS cloud
* Docker images are stored in the Docker repositoies

## Docker Hub (https://hub.docker.com) 
1. Public repository
2. Find base images for many technologies or OS (e.g., Ubuntu, MySQL)

## Amazon ECR (Amazon Elastic Container Registry)
1. Private repository
2. Public repository (Amazon ECR Public Gallery https://gallery.ecr.aws) 

## Docker vs VM's
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/43081587-7db4-4fa0-b4f9-9746167bd067)

## Starting with the Docker
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/24215afa-b3c6-4cef-96e0-07d83dac762a)

## amazon container/kubernetes services
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/580760b2-5db8-4ef4-8d10-d92e6e066648)

## Amazon ECS
1. Ec2 Launch type: <br/>![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/baf7028c-0218-4ca5-9497-ad47348db241)
2. Fargate alunch type: ![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/11c42963-8509-4e23-871e-4e1d02a339fa)

## IAM role for the ECS
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/3d145164-e782-4753-8f0a-1999704e1e6f)

## ECS - Load balancer integrations
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/cb557da7-1926-4a07-a1b0-ed7892af2910)

## ECS - Data volumes (EFS)
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/b988dabb-7eb9-420f-ba12-f48af8e89f98)

## ECS serice- Auto scaling
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/2a3500e9-bdad-4449-9efb-14ae5274951c)
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/ae3837d3-2ec7-4b30-8422-2d9ff0d6dc2e)
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/5d918937-9fee-4f68-a480-97de3e5eb5ba)

## usecase for ECS
1. ECS task invoked by the Event Bridge <br/>![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/0742e639-72a0-4b0a-a628-d01166cce0da)
2. ECS intercept stopped tasks using eventbridge ![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/96c6fd97-5b21-474b-8367-6fe5b0dfd583)

## Amazon ECR
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/4dffd0ba-b267-478e-8fa7-eefc2de5c37b)

## Amazon EKS overview
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/348ace1d-cd68-4cfc-b042-d5909b3160ef)
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/3208fde5-8bd7-4db7-a52d-842219c1ee94)

## EKS Node types
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/00134b33-4658-441c-aa06-3ef593092600)
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/90226c11-8099-43ff-846b-93b7b9c8c1a0)

## AWS App runer
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/13421353-9971-4f0f-ad2c-4520517d2c7d)
