- one of the most popular of AWS offering
- Elastic Compute Cloud (EC2)
- Infrastructure as a Service
- Mainly Consists of
	- Virtual Machines (EC2)
	- Virtual Drives (EBS)
	- Distributing Load (ELB)
	- Scaling the services automatically (ASG)
- Fundamental to know how the cloud works
![[Pasted image 20240413152037.png]]

**EC2 Sizing and Configuration Options**
1. OS
	a. Linux
	b. Windows
	c. Mac
2. CPU - Compute power or cores
3. RAM
4. Storage
	a. Network Attached (EBS & EFS)
	b. Hardware (EC2 Instance Store)
5. Network
	a. Speed of the card
	b. Public IP address
6. Firewall Rules - Security Groups
7. Bootstrap Script
	a. Configure at first launch
	b. EC2 User Data

**EC2 User Data (Bootstrapping)**
- bootstrapping is launching commands when the machine start
- only run once when it first starts
- automate the boot tasks
	- install updates
	- install software
	- download common files from the internet
	- anything you can think of
- the more that you add to the script the more your instance has to do and therefore will impact the instance setup time
- EC2 user data script is run with the **ROOT** user
	- so it has all the permissions it needs
	- and all of the commands will have the sudo rights

**EC2 Configuration**
![[Pasted image 20240413153700.png]]
![[Pasted image 20240413153725.png]]
![[Pasted image 20240413153648.png]]
- select Allow HTTP traffic from the internet because we will use this EC2 instance as a web server

![[Pasted image 20240413153903.png]]
- EBS `Delete on termination` is enabled by default

```
#EXAMPLE USER DATA

#!/bin/bash
# Use this for your user data (script from top to bottom)
# install httpd (Linux 2 version)
yum update -y
yum install -y httpd
systemctl start httpd
systemctl enable httpd
echo "<h1>Hello World from $(hostname -f)</h1>" > /var/www/html/index.html
```

**Security Groups**
![[Pasted image 20240413154614.png]]

**Instance States**
**Stop**
- Stop the instance and you will not be billed for it
- It will not terminate the instance, only stop it. You can start it back up again
- if you stop an instance and start it back up again
	- its public IP address will change
	- but its private IP will remain the same
**Start**
- takes time before it is able to run again because it came from a stopped state

**EC2 Instance Types Examples** 
![[Pasted image 20240413152935.png]]
- pick the right size for your workload/application
- t2.micro will be used in the hands on

![[Pasted image 20240413155711.png]]
- m --> instance class, in this case a general purpose instance
- 5 --> generation, 5th generation and AWS will iterate once a new generation is created
- 2xlarge --> size within a instance class
	- smal
	- large
	- 2xlarge
	- 4xlarge
	- 8xlarge
	- ....
	- metal

**General Purpose**
- diversity of workloads
	- web servers
	- code repositories
- Balance between
	- Compute
	- Memory
	- Networking
- `t2.micro` is general purpose
![[Pasted image 20240413155923.png]]

**Compute Optimized**
- compute intensive tasks
	- batch processing
	- media transcoding
	- high performance web servers
	- high performance computing
	- modeling and machine learning
	- dedicated gaming servers
- compute optimized are of the `C` names
![[Pasted image 20240413160021.png]]

**Memory Optimized**
- workloads that process large data sets in memory
	- high performance for relational/non-relational databases
	- distributed web scale cache stores
	- in memory databases for BI
	- applications performing real-time processing of big unstructured data
- compute optimized `R` series, meaning `RAM`
![[Pasted image 20240413160217.png]]

**Storage Optimized**
- storage intensive tasks that require high, sequential read and write access to large data sets on local storage
	- high frequency OLTP (Online Transaction Processing) Systems
	- Relational and NoSQL Databases
	- Cache for in memory databases (redis)
	- Data warehousing applications
	- Distributed File Systems
- `i`, `d`, `h1`
![[Pasted image 20240413160501.png]]
**Accelerated Computing**
**HPC Optimized**

**Security Groups**
- firewalls for `EC2` instances
- network security
- control traffic that is allows in or out of EC2 instances
- can only contain **`allow`** rules
- Security group rules can reference by IP or by security group
- an instance can have many security groups
![[Pasted image 20240413162217.png]]

- regulates access to ports
- Authorized IP ranges (IPv4 and IPv6)
- Control of inbound network (from outside to the instance)
- Control of outbound network (from the instance to the outside)
![[Pasted image 20240413162336.png]]

- If authorized port and IP, it will allow it
- If not authorized IP, it will not get through it and it will be a timeout
- default allow any outbound
![[Pasted image 20240413162610.png]]

- Security groups can be attached to multiple instances, and an instance can have multiple security groups
- Locked down to region/vpc combination
	- if you switch to a region, you have to recreate the security group
	- or if you switch vpc, you have to also recreate the security group
- lives outside the EC2 (the ec2 lives inside and is encapsulated by the security group)
	- if traffic is blocked, the EC2 instance won't see it
	- firewall outside your EC2 instance
- GOOD TO MAINTAIN ONE SEPARATE SECURITY GROUP FOR SSH ACCESS
	- you want to make sure SSH access is done correctly
- EC2 problems
	- If your application is not accessible and is timing out, then it is most likely a security group issue
	- If connection refused, this means that it went through he security group and this it is an application error or it is not launched
- By default
	- all inbound traffic is block
	- all outbound traffic is allowed

![[Pasted image 20240413163323.png]]
- security group referencing is used so that you don't have to think about IP addresses all the time
- in the example above, the inbound rules allows security group 1 and 2, which allows the first 2 instances to connect. While the 3rd instance has security group 3 so it is not allowed to connect because it is not set in the inbound rules

**Ports to Know**
- 22 --> SSH (Secure Shell)
	- log into a linux instance
- 21 --> FTP (File Transfer Protocol)
	- upload files to a file shared
- 22 --> SFTP (Secure File Transfer Protocl)
	- upload files using SSH
- 80 --> HTTP
	- access unsecured websites
- 443 --> HTTPS
	- access secured websites
- 3389 --> RDP (Remote Desktop Protocol)
	- log into a windows instance

**SSH**
- SSH --> only Linux, Mac, and Windows 10 >
- Putty --> any windows
- EC2 Instance Connect
	- a web browser in which hosts a CLI for your instance
	- only works for amazon linux 2 right now
![[Pasted image 20240413164504.png]]

**SSH into your Instance**
![[Pasted image 20240413164837.png]]
- Amazon Linux 2 AMI already has a user configured and it is named ec2-user
- `ssh -i EC2Tutorial.pem ec2-user@{public ip addres}`

![[Pasted image 20240413165425.png]]

**NOTE: Never put your access and secret key ids into your EC2 instance using aws configure. Instead create and attach an IAM role to the instance**

**EC2 Instance Purchasing Options**
- **On-Demand**
	- short workloads
	- predictable pricing
	- pay for what you use
	- Linux or Windows
		- pay by second/billing per second, after the first minute
	- All other operating systems
		- billing per hour
	- highest cost but no upfront payment
	- no long term commitment
	- for short term and un-interruptible workloads
![[Pasted image 20240413171517.png]]

- **Reserved (1 & 3 years)**
	- Reserved Instances
		- long workloads
	- up to 72% discount
	- reserved specific instance attributes (type, region, tenancy, OS)
	- reservation period - 1 or 3 years (the longer the more discounts)
	- payment options
		- no upfront + 
		- partial upfront ++
		- all upfront +++
	- scope
		- region
		- zone (AZ)
	- used for steady-state usage applications (databases)
	- can buy and sell instances in the `Reserved Instances Marketplace`
	
	- Convertible Reserved Instances
		- long workloads with flexible instances
		- change instance type overtime
		- can change (type, family, OS, scope, and tenancy)
		- less discount rather than reserved because of flexibility (up to 66%)

- **Savings Plans (1 & 3 years)**
	- more modern
	- long workloads
	- rather than commit to a specific instance type, you commit to a usage amount in dollars
	- up to 72% savings, the same as reserved instances
	- commit to a certain type of usage
		- ex. $10/hour for 1 or 3 years
	- any usage beyond the committed savings plan is billed on-demand price
	- locked to specific instance family and region, but flexible across the said family
![[Pasted image 20240413172119.png]]

- **Spot Instances**
	- short workloads
	- cheap
	- can lose instances (less reliable)
		- will lose it if max price that you are willing to pay is less than the current spot price
	- up to 90% discount compared to on-demand
	- most cost efficient instances in AWS
	- for workloads that are resilient to failure
		- batch jobs
		- data analysis
		- image processing
		- any distributed workloads
		- workloads with a flexible start and end time
	- not suitable for critical jobs or databases
![[Pasted image 20240413172539.png]]

- **Dedicated Host**
	- book an entire physical server fully dedicated to your use case
	- control instance placement
	- addresses compliance requirements and use your existing server-bound software licenses (per-socket, per-core, per-VM software licenses)
	- purchasing options
		- On-demand
			- pay per second for active dedicated host
		- Reserved
			- 1 or 3 years (No, Partial, or Full upfront payment)
	- the most expensive option
	- BYOL (Bring your own license)
	- strong regulatory or compliance needs
![[Pasted image 20240413172728.png]]

- **Dedicated Instances**
	- no other customers will share your hardware
	- runs on hardware that's dedicated to you, different from physical server
	- may share hardware with other instances in same account
	- no control over instance placements (can move hardware after Stop/Start)

![[Pasted image 20240413172858.png]]
- Dedicated Hosts vs Instances
	- Instances
		- own instance on own hardware
	- Hosts
		- access to physical server itself and gives visibility to lower level hardware

- **Capacity Reservations**
	- reserve on-demand instances capacity in a specific AZ for any duration
	- you always have access to EC2 capacity when you need it
	- no time commitment (create/cancel anytime), no billing discounts
	- only purpose is to reserve capacity
	- combine with regional reserved instances and savings plants to benefit billing discounts
	- charged as on-demand rate whether you run your instances or not
		- reserved capacity will be billed for and makes sure that you have the capacity when you need it
![[Pasted image 20240413173246.png]]

**Which Purchasing Option is right for me?**
![[Pasted image 20240413173444.png]]

**Price Comparison**
![[Pasted image 20240413173453.png]]
