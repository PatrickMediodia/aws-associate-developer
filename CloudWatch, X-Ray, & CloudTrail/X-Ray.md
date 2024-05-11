![[Pasted image 20240511154305.png]]
- one of the most revolutionary services AWS has to offer and currently under utilized
- one of the most important

![[Pasted image 20240511154332.png]]
- we can see
	- how many requests fail/don't fail
	- what the application does
- trace visually what happens when you talk to your EC2 instance
	- ex. orange in DynamoDB

**Advantages**
![[Pasted image 20240511154546.png]]

**Compatability**
![[Pasted image 20240511154622.png]]

**How does X-Ray work?**
![[Pasted image 20240511154748.png]]
- uses tracing
- each component dealing with the request adds its own trace, this is so that in the end, you can know the data or how the data has travelled in between each service

**How to enable X-Ray?**
![[Pasted image 20240511155157.png]]
1. Must be Java, Python, Go, .NET, Node.js) and must import the AWS SDK
	- very little code modification
	- SDK will do the work for you
2. Install the X-Ray daemon or enable X-Ray AWs Integration
	- if on-premise or EC2 instance, we need to install the daemon
		- works on low level UDP packet interceptor
		- linux/windows/mac
	- Lambda and other AWS services already has an integration with X-Ray and run the daemon for you
	- each application must also have the right IAM right to write data to X-Ray
	- the daemon sends batch data to AWS X-Ray every second

![[Pasted image 20240511155242.png]]

![[Pasted image 20240511155425.png]]
- EC2 instance/On-Premise
	- make sure that the EC2 instance has the correct permission and that the X-Ray daemon is running
- AWS Lambda
	- enable IAM execution role (lambda will be the one to write to X-Ray)
	- ensure that X-Ray is imported in the code
	- enable Lambda X-Ray Active Tracing

**Hands-On**
![[Pasted image 20240511155721.png]]
- X-Ray is now in the CloudWatch console

![[Pasted image 20240511160233.png]]
- errors will be highlighted

![[Pasted image 20240511160253.png]]
- you can see the latency, number of requests, number of faults
- response time distribution

![[Pasted image 20240511160341.png]]
- since SNS is 100% error, we can analyze the traces

![[Pasted image 20240511160529.png]]
- you can filter by nodes

![[Pasted image 20240511160622.png]]
- you can review the traces, in this case we might want to know why one of our traces has a high response time (500ms)

![[Pasted image 20240511160631.png]]
- you have details or breakdown of the trace requests based on the different events that happened

