- Elastic **Kubernetes** Service
- launch managed kubernetes clusters on AWS
- same goal as ECS where it will run your docker containers but it has a different api
- ECS is NOT open source while Kubernetes is
- If your company is already using Kubernetes, this makes it easier to migrate
- Cloud Agnostic, meaning it can be ran on the different cloud providers

![[Pasted image 20240428111620.png]]

![[Pasted image 20240428111803.png]]
- EKS Nodes --> ECS Containers
- EKS Pods --> ECS Tasks
- Nodes can be managed by an ASG like containers

![[Pasted image 20240428112025.png]]
- Managed Node Groups --> Kinda Like a Fargate Launch Type, but not as serverless
- Self-Managed Nodes --> EC2 Launch Type, you will need to provision them yourself and add it to the EKS cluster
- AWS Fargate --> No nodes managed

![[Pasted image 20240428112259.png]]
- THE ONLY STORAGE CLASS THAT WORKS WITH FARGATE IS EFS

**EFS volume can be shared between different EC2 instances and different ECS Tasks. It can be used as a persistent multi-AZ shared storage for your containers.**

![[Pasted image 20240428112433.png]]