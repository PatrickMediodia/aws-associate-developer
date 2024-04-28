**EC2 Launch Type**
- launch ECS tasks on ECS cluster
- a ECS cluster with EC2 instances
- you must provision and maintain the infrastructure yourself
- must run the ECS agent which registers the EC2 instance to the ECS cluster
- docker containers are placed on EC2 instances
	- AWS takes care of starting/stopping the containers
- **NOTE: THESE EC2 INSTACES ARE PROVISIONED IN ADVANCE**
![[Pasted image 20240427153720.png]]

**Fargate Launch Type**
- you do not provision the infrastructure, no EC2 instances to manage
- all serverless, because we don't manage servers
- its just ran without us knowing how it is ran, without EC2 instances to be created in the backend in our account
- way easier to manage that the EC2 launch type
![[Pasted image 20240427154106.png]]

**IAM Roles for ECS**
![[Pasted image 20240427154323.png]]

![[Pasted image 20240427154646.png]]
 
![[Pasted image 20240427154916.png]]
![[Pasted image 20240427161314.png]]
- the photo above shows that you have 3 options to run your containers on
	- fargate (serverless)
		- AWS is the one going to manage your infrastructure for you
	- EC2 instances
		- you can add instances to an ASG as needed
	- External Instances using ECS Anywhere
		- you can use your own servers to run ECS tasks but AWS will be the one to manage the tasks it is getting

![[Pasted image 20240427161537.png]]
- fargate and fargate spot are the fargate managed instances
- while infra ECS cluster is the ASG that we can configure to add EC2 instances on

**Task Definition**
![[Pasted image 20240427162414.png]]
- we can define if we have fargate or EC2 instances or both
- we can set the task size for fargate

![[Pasted image 20240427162500.png]]
- pull image from docker hub on path `nginxdemos/hello`
- map port 80 to the container

![[Pasted image 20240427162602.png]]
- comes w/ ephemeral storage
	- **a temporary form of data storage that is used for short-lived and transient workloads in data processing and analytics**

**Launch Tasks into Clusters**
![[Pasted image 20240427162718.png]]
- Fargate or EC2 instances are launch type

![[Pasted image 20240427162759.png]]
- application type
	- service -- long running (web apps)
	- task -- short only (batch jobs)

![[Pasted image 20240427162955.png]]
- you can also add applications load balancers which point to the target group which containers the different ECS containers

![[Pasted image 20240427163127.png]]

An ALB is distributing the tasks to the different containers managed by fargate
![[Pasted image 20240427163445.png]]

**ECS Service Auto Scaling**
![[Pasted image 20240427163937.png]]

**Scaling EC2 Instances on EC2 Launch Type**
![[Pasted image 20240427164815.png]]
- ECS Cluster Capacity Provider is the one that is preferred
![[Pasted image 20240427165134.png]]

**ECS Rolling Updates**
 ![[Pasted image 20240427165339.png]]
 - minimum healthy percent
	 - will dictate how many tasks are terminated based on the running capacity, if 60% and there are 10 tasks, it will terminate 4 and keep 6
- maximum percent
	- maximum percent minus the minimum healthy percent will dictate how many tasks is it allowed to create for the rolling update

![[Pasted image 20240427165641.png]]
![[Pasted image 20240427165722.png]]

**Solutions Architectures**
![[Pasted image 20240427165910.png]]
- created a serverless architecture to process images/objects uploaded to an S3 bucket using a docker container using:
	- Amazon EventBridge
	- ECS Task Role
	- ECS Fargate

![[Pasted image 20240427170250.png]]
- makes it so that every hour a ECS task in invoked and can for example do batch processing on an S3 bucket

![[Pasted image 20240427170443.png]]
- use ECS service poll and process SQS queue messages which can scale as the number of messages

![[Pasted image 20240427170623.png]]
- you can do certain actions based on ECS task lifecycle changes using eventbridge
	- for example send an email on ECS tasks events

![[Pasted image 20240428112629.png]]
`ECS_ENABLE_TASK_IAM_ROLE` --> enable IAM roles for your ECS tasks to make API requests to AWS services