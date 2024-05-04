**Queue Methods**
- `CreateQueue(MessageRetentionPeriod)`
	- creates the queue and takes in the MessageRetentionPeriod as parameters on how long you want the messages to live in your queue
- `DeleteQueue`
	- deletes the queue and all the messages within it
- `PurgeQueue`
	- deletes all the messages in the queue

**Message Methods**
- `SendMessage(DelaySeconds)`
	- send a message to the SQS queue can specify the delay before the message can be polled
	- the default is 0 seconds
- `ReceiveMessage`
	- polling of messages
	- by default `MaxNumberOfMessages` default is `1` and has a max of `10`
		- for `ReceiveMessage` API
	- `MaxNumberOfMessages` sets the number of messages you can receive at a time
		- if greater than 1 meaning you will receive it as a batch
	- `ReceiveMessageWaitTimeSeconds` is for long polling
		- this sets the number of seconds the consumer will wait before getting a response from the queue
		- if set to 0 then it means it is set to `short polling`
		- wait up to `X` amount of seconds to wait for a message if the queue is empty
	- `ChangeMessageVisilibity`
		- change the message timeout in case you need more time to process it
- `DeleteMessage`
	- delete message from the queue after a consumer has processed it
	- this makes it so that the message will not go back to the queue

**NOTE: Batch APIs for `SendMessage`, `DeleteMessage`, `ChangeMessageVisibility` helps decrease your costs as there will be less API calls**