![[Pasted image 20240428140031.png]]

**All at Once**
![[Pasted image 20240428140309.png]]
- fastest deployment
- has downtime
- **great for quick iterations on dev environments** where you want to deploy your code fast
- **no additional cost**
- update all the instances all at once
1. stop the applications
	- blue (running) to gray (stopped)
2. install and run the new applications
	- install while stopped
	- then run the new updates (green)

**Rolling**
![[Pasted image 20240428140652.png]]
- do the updates by batches so that the application will not go down altogether
- the application will only be running in decreased capacity
- application is running both version simultaneously at some point
- no additional cost
- if you set small bucket size and you have hundreds of instances, it would be a long deployment

**Rolling w/ Additional Batches**
![[Pasted image 20240428140955.png]]
- application is always running at the minimum capacity
	- which in this case is 4
- small additional cost
- application is running both version simultaneously
- additional batch is removed at the end of the deployment
- longer deployment
- good for prod
- how?
	- deploy first the new instances with the new version
	- take down the same number of instances with the old version
	- now the batch is not updated, take down another batch with the same size
	- by the end you would have an extra batch, just terminate those

**Immutable**
![[Pasted image 20240428141241.png]]
- zero downtime
- creates a temporary ASG with the new updates
	- it will first create one instance with the new version to verify that it is working through health checks
	- if it works, it will then deploy the others
- once the updates have been installed, the instances will be moved to the current ASG and the old instances with the old version will be terminated

**Blue/Green Deployment**
![[Pasted image 20240428141705.png]]
- before, all of the previous deployment strategies deployed in the same environment
- create a new environment altogether and deploy there
- new environment can be validated independently
	- can roll back if there are issues
- you can use route 53 to redirect some of the traffic to the staging environment to test everything
	- this is to make sure that your newly deployed environment and application works as intended
	- once you are happy, you can swap URLs with the test environment
	- essentially point to the new environment and shutdown the old environment
- not a direct feature of AWS, very manual to do

**Traffic Splitting**
![[Pasted image 20240428143117.png]]
- **Canary Testing**
	- new application version is deployed to a temporary ASG with the same capacity
- new application is deployed to a temp ASG with the same capacity
- basically giving the new ASG only a few amount of traffic in order to test it
	- its health is also monitored
	- if it is deemed unhealthy, it can be rolled back very quickly (just stop sending 10% to the temp ASG)
- no application downtime
- if all is well, the new instances are migrated to the temporary ASG to the main ASG
- kind of like blue green, but blue green uses environments not ASG and is manual in nature

![[Pasted image 20240428143209.png]]

Swap Environment Domain
- involves swapping the domain entries so that the address will be pointing to the other IP
- ex. swap prod and dev, to make the dev one prod after testing
- ex. you can first create a copy of prod and then do changes, and then swap the environment domain on it

![[Pasted image 20240428144838.png]]