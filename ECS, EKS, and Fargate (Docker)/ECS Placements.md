**Task Definitions**
![[Pasted image 20240427174405.png]]

![[Pasted image 20240427174841.png]]
- dynamic host port mapping makes it so that even though the ports of the ECS tasks change, the application load balancer would still be able to reference it
- To enable random host port, set host port = 0 (or empty), **which allows multiple containers of the same type to launch on the same EC2 container instance.**

![[Pasted image 20240427175015.png]]
- each task will have an ENI (Elastic Network Interface) which gives it a private IP and the same container port

![[Pasted image 20240427175324.png]]
- **ONE TO ONE MAPPING OF IAM ROLE TO TASK DEFINITION**
- role is defined at the task definition level, not at the service level
- all tasks that will be created with the task definition will assume the ECS task role

![[Pasted image 20240427175535.png]]

![[Pasted image 20240427175840.png]] 

**Task Placements**
![[Pasted image 20240427183025.png]]
- of course only for EC2 launch types as fargate is serverless and AWS will handle all of that for you

![[Pasted image 20240427183354.png]]

![[Pasted image 20240427183826.png]]
- will fill up the instance all the way up to save on cost, in this case memory is the criteria
- placing containers on one EC2 instance before moving on to the next
- binpack because it packs all of the containers together
- MOST COST SAVINGS BECAUSE IT MINIMIZES THE NUMBER OF EC2 INSTANCES IN USE
- MAXIMIZE THE UTILIZATION OF EC2 INSTANCES ONE AT A TIME

![[Pasted image 20240427184000.png]]
- literally random, no other way to put it

![[Pasted image 20240427184102.png]]
- spread the task evenly

![[Pasted image 20240427184123.png]]

![[Pasted image 20240427184234.png]]

**To enable random host port, set host port = 0 (or empty), which allows multiple containers of the same type to launch on the same EC2 container instance.**
![[Pasted image 20240428113103.png]]