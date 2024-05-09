![[Pasted image 20240507192312.png]]

Create an EventBridge Rule
![[Pasted image 20240508182436.png]]
- rule with an event pattern is used to react to AWS service events
	- CodeCommit commit to codebase
	- S3 events
	- EC2 Instance Terminated/Spawned etc.

Run every minute
![[Pasted image 20240508183618.png]]
- schedule to run regularly

![[Pasted image 20240508183845.png]]

![[Pasted image 20240508183859.png]]

Only our EventBridge rule can run this lambda function
![[Pasted image 20240508183950.png]]

You can access the event from the lambda function itself
![[Pasted image 20240508184149.png]]