![[Pasted image 20240511132726.png]]
- alarms used to trigger notification for any metric
- alarm states
	- OK
	- INSUFFICIENT_DATA
	- ALARM

![[Pasted image 20240511132753.png]]
- Alarm Targets
	- EC2 Instances
	- ASG (Out or In)
	- SNS (can trigger lambda functions from it)

**Composite Alarms**
![[Pasted image 20240511133045.png]]
- combining alarm together
- AND or OR conditions
- useful to reduce alarm noise
	- only notify me if CPU is high and network is low
	- because if CPU is high and network is high, that is just a normal event

**EC2 Instance Recovery**
![[Pasted image 20240511133205.png]]
- Types of instance checks
	- Instance Status = CHECK THE EC2 VM
	- System Status = check the underlying hardware
- if instances are unhealthy, you can trigger a recovery

**Good to Know**
- you can use cloudwatch log filters to trigger cloudwatch alarms
- you can test these by using the `set-alam-state` api call
![[Pasted image 20240511133323.png]]

**Hands-On**
- terminate alarm if CPU goes to 100%
![[Pasted image 20240511133455.png]]

![[Pasted image 20240511133519.png]]

![[Pasted image 20240511133542.png]]
- choose a way to compute a metric

![[Pasted image 20240511143443.png]]
- if CPU utilization is greater than 95%

![[Pasted image 20240511143504.png]]
- this means in 15 minutes because one data point is 5 minutes since this is only standard EC2 metrics

![[Pasted image 20240511143607.png]]
- this could be useful to handle if you know your application fails and pegs the server at > 95%, this means that the machine can be terminated

![[Pasted image 20240511143710.png]]
- not yet triggering since we need 3 data points
- we could use the `set-alam-state` to test what would happen if the alarm is triggered

![[Pasted image 20240511143758.png]]
![[Pasted image 20240511143858.png]]

![[Pasted image 20240511143925.png]]