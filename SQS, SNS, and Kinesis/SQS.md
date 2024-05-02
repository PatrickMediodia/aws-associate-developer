- oldest AWS service
- orchestrate between different services with SQS being the middleware

![[Pasted image 20240502184120.png]]
- Synchronous vs Asynchronous
	- Synchronous --> Application to Application
	- Asynchronous --> Application to Queue to Application
		- not directly connected
		- buying service will push to the queue
		- shipping service will poll the queue if there are events or items to be processed

![[Pasted image 20240502184624.png]]
 - SQS: Queue Model
 - SNS: Pub/Sub Model
 - Kinesis: Real Time Streaming Model

**SQS Queue**
![[Pasted image 20240502184818.png]]
- acts as a buffer and decouples your producers and consumers

![[Pasted image 20240502185312.png]]
- oldest offering (over 10 years old)
- fully managed service used to decouple application
- unlimited throughput and unlimited number of messages in the queue
- has limited retention
	- default retention: 4 days
	- max retention: 14 days
	- must be read and deleted before the retention period is over
	- otherwise it would be lost
- low latency (less than 10 ms)
- less than 256kb
- can have duplicate messages (at least once delivery)
	- this should be handled by your application
- can have out of order messages (best effort ordering)
	- there is another verison called the FIFO queue which solves this problem

**Producers**
![[Pasted image 20240502185629.png]]
- producers sends messages using the SDK
- a processed message is deleted

**Consumers**
![[Pasted image 20240502185831.png]]
- can be ec2, on-premise servers, or AWS Lambda
- you have to delete the message after it has been processed to make sure that no other consumer will receive that message. This means that it has been completed

![[Pasted image 20240502190024.png]]
- each consumer will get a receive set of messages by polling the queue
- we can scale consumers horizontally to improve the throughput of processing

![[Pasted image 20240502190215.png]]
- a CloudWatch metric available that can be used for ASG is the SQS queue length
- we could set a CloudWatch alarm to check if it has passed a certain number of messages and scale based on that

![[Pasted image 20240502190333.png]]
- with this you can scale the front end and the backend accordingly as they are not tightly coupled together
- robust and scalable

**Security**
![[Pasted image 20240502190531.png]]
- in flight encryption through the HTTPS API
- at rest encryption using KMS keys
- client side encryption but client has to perform the encryption and decryption themselves