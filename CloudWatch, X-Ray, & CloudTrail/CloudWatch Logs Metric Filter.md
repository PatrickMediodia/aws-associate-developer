![[Pasted image 20240511131526.png]]
1. stream ec2 instance logs into cloud watch logs
2. have a metric filter to check these logs
3. could have a cloud watch alarm to check if a metric filter has been hit x amount of times
	- ex. if there has been 5 errors in the last minute which could be a cause for concern
4. alarm could publish to a topic to notify the subscribers

- does not back-fill and only gets events that have been created when it is running

**Hands On**
![[Pasted image 20240511131730.png]]
- create a metric filter for HTTP 400 response codes

![[Pasted image 20240511132043.png]]
![[Pasted image 20240511132053.png]]![[Pasted image 20240511132143.png]]

Metric Filter Alarms
![[Pasted image 20240511132359.png]]
- alarm when a filter has been triggered

![[Pasted image 20240511132429.png]]
- conditions to when the alarm will be triggered
- in this case it is triggered if there are more than 50 instances of 400 status code which our filter is triggered on

![[Pasted image 20240511132439.png]]
- you could select how to trigger an alarm, in this case we are sending the alarm to an SNS topic