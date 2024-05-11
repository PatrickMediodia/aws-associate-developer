![[Pasted image 20240511130250.png]]
- use CloudWatch Agent to take logs from EC2 intances and metrics and have them onto CloudWatch
- push log files using CloudWatch agent
- can also be setup on on-premise servers

**Two Types of Agents**
![[Pasted image 20240511130916.png]]
- Logs Agent (Older One)
	- can only send logs to cloudwatch logs
- Unified Agent (Newer)
	- collect additional system level metrics
		- RAM
		- processes
	- it can do both metrics and logs
	- integration with SSM parameter store for a centralized configuration for all your agents

![[Pasted image 20240511131118.png]]
- allows for a lot more metrics and a lot more of granular details rather than the logs agent or normal monitoring for EC2 instances
	- out of the box metrics are only a high level
	- use unified agent if you want more of a deeper level