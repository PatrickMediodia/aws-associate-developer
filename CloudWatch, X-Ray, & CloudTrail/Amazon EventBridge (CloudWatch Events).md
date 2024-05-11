![[Pasted image 20240511145106.png]]
- formerly known as CloudWatch Events
- can react to event based on
  1. schedule cron jobs (scheduled scripts)
  2. event pattern
	- event rules to react to a service doing something
- can trigger lambda functions

![[Pasted image 20240511145446.png]]

![[Pasted image 20240511145811.png]]
- types of event bridge buses
	- default (used by AWS services)
	- partner (used by 3rd Party AWS partners, usually SaaS)
	- custom (used by custom application)
- you can use the reply archived events feature to fix bugs
	- ex. your lambda functions errors out. after you fixed it you are able to replay the event to check if your bug has been fixed
	- useful for debugging and fixing bugs

**Schema Register**
![[Pasted image 20240511150133.png]]
- json format
- for the eventbridge to know how data is going to be structured
- it can be changed and versioned overtime

**Resource Based Policies**
![[Pasted image 20240511150436.png]]
- you can manage each specific event bus
- allow/deny events from another AWS account or AWS region
- ex. aggregate all events from your AWS organization (multiple accounts) in a single AWS account or region

**Hands-On**
- EventBridge is the enchanced version of CloudWatch Events

![[Pasted image 20240511150546.png]]
- default event bus

![[Pasted image 20240511150619.png]]
- create your own event bus

![[Pasted image 20240511150816.png]]
- have cross account access in your event bus through the resource-based policy
- NOTE: If you don't set the resource-based policy, only the event buss owner can send events to the event bus

EventBridge Event Sources - Partners
![[Pasted image 20240511150922.png]]
![[Pasted image 20240511151026.png]]
- you need to setup Auth0 which will be the one to catch the events and will be captured into EventBridge

**Create Rules**
![[Pasted image 20240511151106.png]]
- create rules for your bus
- AGAIN CAN BE EITHER: SCHEDULED (CRON) OR RULE WITH AN EVENT PATTERN

![[Pasted image 20240511151255.png]]
- choose eiter if the event source is from AWS, Other (3rd Party/Custom), or All

**Choose an event**
![[Pasted image 20240511151452.png]]
![[Pasted image 20240511151459.png]]
- sample events are given to know what the response looks like

![[Pasted image 20240511151605.png]]![[Pasted image 20240511151703.png]]
- send a SNS message every time an EC2 instance has been terminated

Multi-account Aggregation
![[Pasted image 20240511152234.png]]
- define an event pattern in one of your accounts and create an event rule for it
- in the event buss of the central account, make sure that the resource policy allows other accounts to write events to the event bus