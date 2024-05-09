![[Pasted image 20240509181724.png]]
- lambda can process events in AWS by synchronous, asynchronous, and event source mapping
- applies to Kinesis Data Streams, SQS (Normal and FIFO), and Dynamo DB Streams
- records need to be polled from the source (this is why it does not apply to SNS and Kinesis Data Firehose)

Two Types of Event Source Mapper
	- Streams
		- Kinesis Data Streams and DynamoDB Streams
	- Queues

**Streams**
![[Pasted image 20240509184524.png]]
- you can configure where to start your read from
- items in a shard or stream will be ordered in the shard level
- processed items aren't removed from the stream

**Error Handling**
![[Pasted image 20240509184906.png]]
- an error in a batch triggers and entire reprocessing of the function until it succeeds or items in the batch expire

**Queues**
![[Pasted image 20240509185039.png]]
- DLQ on lambda only works under lambda

![[Pasted image 20240509185333.png]]
- FIFO: lambda will scale to the number of active message groups (group id setting in SQS)
- Standard: Lambda will scale up to process a standard queue as quickly as possible

![[Pasted image 20240509185700.png]]
Event Mapper Scaling
- Kinesis Data Stream and DynamoDB Stream
	- one lambda invocation per shard
	- can use parallelization to process up to 10 batches per shard simultaneously
- SQS Standard
	- up to 60 more instances per minute to scale up and process the standard queue
- SQS FIFO
	- messages with the same groupid will be processed in order
	- the lambda function scaled to the number of active message groups (1 to 1?)

**Hands On**
- Add Trigger for an SQS Queue
![[Pasted image 20240509185956.png]]
- the max batch size used to be 10 but now it is larger

Batch window
![[Pasted image 20240509190126.png]]
- this is so that the function is more efficient in that it will either reach the batch size or the batch window

Attach a permission to the role so that the lambda function can poll from the SQS queue
![[Pasted image 20240509190259.png]]

You can see from the logs that the lambda function has successfully polled from the SQS queue
![[Pasted image 20240509190603.png]]

Disable the SQS queue if you aren't using it so that the lambda function does not continue to poll the SQS queue
![[Pasted image 20240509190702.png]]

