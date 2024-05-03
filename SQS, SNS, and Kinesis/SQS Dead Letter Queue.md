
- `MaximumReceives` the max amount of times a message in a queue could go back
	- if it exceeds this, it will go to the dead letter queue
- it could be problematic if this message is not processed and stays in the queue as it uses up resources
	- this could happen if the message is not formatted properly
	- or if the consumer does not understand the message

![[Pasted image 20240503183553.png]]
- messages that exceed the `MaximumReceives` threshold will go to the dead letter queue which can be analyzed on why it failed on a later date
- useful for debugging
- **NOTE: A DLQ MUST BE THE SAME TYPE AS ITS MAIN QUEUE**
	- a dead letter queue of a FIFO queue must also be a FIFO queue
	- a dead letter queue of a standard queue must also be a standard queue
- it might be a good idea to set a long `retention period` or expiration date for the message of a dead letter queue so that it can be debugged why it failed

**Redrive to Source**
![[Pasted image 20240503183816.png]]
- feature to help consume messages in the DLQ to understand what is wrong with them
- basically just send them back to the source queue after it has been manually fixed
- consumer can process this message without even knowing that it went to the dead letter queue


