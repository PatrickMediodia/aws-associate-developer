![[Pasted image 20240504105330.png]]
- send one message to many receivers
- you could have a direct integration
	- but may be problematic as every time you need to have a new consumer, you have to write the direct integration for that
- SNS is a pub/sub pattern
- the `sender will publish` a message to a topic, then there would be `many subscribers to that topic`

**SNS Publish**
![[Pasted image 20240504105657.png]]
- `event producer` only sends message to one SNS topic
	- up to 100,00 topics
- as many `event receivers (subscriptions)` as we want
	- listens to the SNS topic notifications
	- subscribers to a topic will get all the messages (unless you filter the messages)
	- up to 12,500,000 million subscriptions per topic
- can send
	- general
		- emails
		- SMS
		- HTTP(s) endpoints
	- AWS services
		- SQS
		- Lambda
		- Kinesis Data Firehouse (S3 or Redshift)

**SNS Subscriptions**
![[Pasted image 20240504105910.png]]