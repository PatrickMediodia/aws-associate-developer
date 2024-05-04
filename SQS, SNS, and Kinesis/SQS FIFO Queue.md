![[Pasted image 20240504100459.png]]
- First In First Out (ordering of messages in the queue)
- messages will be ordered in the queue
	- the first messages that arrive in the queue will be the first one to be processed/leave the queue
- the consumer will receive the messages in the exact same order that they arrived in the queue
- due to the ordering constraint and guarantee of a FIFO queue
	- limited throughput
	- `300 msg/s`
		- without batching
	- `3000 msg/s` with batching (there could be up to 10 messages per poll)
- exactly-once send capability (by removing duplicates)
- messages are processed in order by the consumer
- scenario it can be used:
	- decoupling of applications
	- order or messages is important
	- able to work with the throughput limitations

![[Pasted image 20240504100626.png]]
- **REMEMBER: YOU HAVE TO END THE QUEUE NAME WITH `.fifo`**

![[Pasted image 20240504100646.png]]
- almost has the same settings as a standard queue
- but has an option for `Content-based deduplication`
	- deduplicates the messages and makes sure that it is processed only once
	- deduplicates it if the same message is sent twice in a small window or amount of time (5 minutes?)
- checks the `dededuplication id` if there is the same id for the messages

**Deduplication**
![[Pasted image 20240504101629.png]]
- De-duplication interval is 5 minutes
	- if you send the same message in 5 minutes, then the second or same message will be refused
	- I don't think you can change the time interval
- **Two de-duplication methods**
	- **Content-based**
		- SHA-256 hash of the message body
		- if the same hash which is based of the message body is seen twice, then it will be refused
	- **Explicitly provide a Message Deduplication ID**
		- if the same deduplication ID is encountered twice, then it will be refused

**Message Grouping**
![[Pasted image 20240504101812.png]]
- `MessageGroupID` groups messages with the same ID together
	- this is a required field when sending messages to a FIFO queue
	- if you only have one consumer, set this to only one value so that all the messages are in order
- this allows for ordering of a subset of messages, the subset being the messages with the same `MessageGroupID`
	- Messages that have the same ID will be ordered within the group
	- each group ID can have a different consumer (parallel processing)
- **NOTE: ORDERING ACROSS GROUPS IS NOT GURANTEED**

![[Pasted image 20240504102323.png]]
- a scenario could be the message group ID could be for a specific user
- so the subset of messages for a consumer of a specific user would receive ordered messages