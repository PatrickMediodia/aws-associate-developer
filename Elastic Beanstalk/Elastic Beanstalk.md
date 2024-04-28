- deploying applications in AWS safely and predictably
- managed service
	- handles the provisioning, load balancing, scaling, application health monitoring, instance configuration, and many more
- free, but you pay for the underlying instances that it creates
	- it uses CloudFormation under the hood to create and provision the resources needed
- based on the sample code, it was able to create the infrastructure to make it run
- centered around code and environments for your code
	- CloudFormation is more on deploying stacks arbitrarily with any kind of infrastructure
- once you delete your Beanstalk application, CloudFormation will also be the one to delete it

![[Pasted image 20240428121348.png]]
- so far this is what we've learned
- usually ALB, ASG, and RDS/ElastiCache
- if this is the usual infrastructure, it would be a hassle to recreate this every time

![[Pasted image 20240428121524.png]]
- problems on AWS
	- managing infrastructure
	- deploying code
- beanstalk makes it so that you can focus on development
- this makes it so that your deployment is consistent

![[Pasted image 20240428123444.png]]
- from a singular interface, you are able to create EC2, ASG, ELB, RDS, etc.
- these are all created using CloudFormation under the hood
- still have full control over the configuration but makes it easier since there would be a singular interface

![[Pasted image 20240428123736.png]]
- multiple environment (dev, test, prod)
- web server env tier and worker env tier
	- web server --> uses ALB and ASG
	- worker --> uses SQS queues and pulls from the queue

![[Pasted image 20240428123803.png]]
- the idea on beanstalk is that you can pretty much deploy anything

**Web Server Tier vs Worker Tier**
![[Pasted image 20240428123900.png]]
**Web Server Tier**
- traditional ELB and ASG
**Worker**
- no client directly accessing your EC2 instance, their jobs will be pushed to the queue
- ec2 instances (workers) will pull from the SQS queue to process them
- scale based on the number of SQS messages
- you can push messages to SQS queues from another web server tier (basically putting them together)

**Deployment Modes**
![[Pasted image 20240428124151.png]]
**Single Instance**
- one instance and an elastic IP can be put on it
- great for dev
**High Availability with Load Balancer**
- great for prod since it is high available due to running on different azs

**Configuring the Environment**
![[Pasted image 20240428131812.png]]
- if you want to run a website use the web server environment

![[Pasted image 20240428131936.png]]
- domain name can be automatically set for your application

Choose if Managed or Not and while platform will it use (node, python, go, etc.)
![[Pasted image 20240428132006.png]]

**This is where single instance and high availability selection comes in**
![[Pasted image 20240428132102.png]]

Of course we need to give Elastic Beanstalk the proper IAM roles to be able to create and provision resources on our behalf
- you can create a new role or use an existing one
![[Pasted image 20240428132133.png]]

You will need the following permission on your IAM roles
- `AWSElasticBeanstalkWebTier`
- `AWSElasticBeanstalkWorkerTier`
- `AWSElasticBeanstalkMulticontainerDocker`
![[Pasted image 20240428132340.png]]

- CloudFormation will be the one to create the resource needed defined in a `stack`
- create resources behind the scenes
- events --> describe how the cloud formation template is being created
- all the resources that beanstalk needs to created is being created by cloudformation
	- security groups
	- elastic ips
	- ec2 instances
	- asg
	- elb
	- etc
![[Pasted image 20240428132541.png]]

Now you will be able to access it using the domain name after everything has been created
![[Pasted image 20240428132830.png]]
- based on the sample code, it was able to create the infrastructure to make it run

You can also upload a new version in which it will deploy for you
![[Pasted image 20240428133002.png]]

You can create new environments so separate dev and prod
![[Pasted image 20240428133126.png]]

If you are using a load balancer, there is no need to set your ec2 instances to public
![[Pasted image 20240428135056.png]]
- if you create a database in the beanstalk configuration, its lifecycle will also be that of your beanstalk project. Meaning if you delete your project, it will delete all the resources including your database
- a workaround to this is to make a snapshot and restore it

Since we are now using an ASG, you can set its min and max number of instances
![[Pasted image 20240428135243.png]]
