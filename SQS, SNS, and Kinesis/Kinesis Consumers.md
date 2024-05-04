![[Pasted image 20240504130505.png]]
- get data records from data streams and process them
- can be
	-  AWS lambda
	- Kinesis Data Analytics
	- Kinesis Data Firehose
	- Custom Consumer (AWS SDK)
		- Classic
		- Enhanced Fan-Out
	- Kinesis Client Library (KCL)
		- simplify reading from data stream

**Custom Consumer**
![[Pasted image 20240504131043.png]]
**Shared (Classic) Fan-out Consumer**
- uses the old API `GetRecords()`
- the consumers of a shard will share the consumer throughput of 2MB/sec
- this means that if there are 3 consumers on shard 1, they will each have a max of 0.67 MB/sec throughput
 - **PULL MODEL**
**Enhanced Fan-out Consumer**
- uses the new API call `SubscribeToShard()`
	- make the data send or push the data to the consumers
- now 2MB/sec per shard per consumer, no need to shared the same bandwidth on the same shard with many different consumers
- **PUSH MODEL**

![[Pasted image 20240504131622.png]]
**Shared (Classic) Fan-out Consumer - PULL**
- low number of consuming applications
- read throughput of 2MB/sec per shard across all consumers
- max 5 `GetRecords` API calls/sec
- latency `~200ms`
- minimize cost ($)
- consumers poll data from Kinesis using `GetRecords` API call
- returns up to 10mb (then throttle for 5 seconds) or up to 10000 records

**Enhanced Fan-out Consumer - PUSH**
- multiple consuming applications for the same stream
- 2 MB/sec per consumer per shard
- latency `~70ms`
	- lower than shared because of the higher throughput
	- shard itself will push data into our consumer
- higher cost ($)
- Kinesis pushes data to consumers over HTTP/2 through the `SubscribeToShard` API
- Soft limit of 5 consumer applications (KCL) per data stream
	- this is the default but it can be increased, but putting in a ticket on AWS

![[Pasted image 20240504131934.png]]
 **AWS Lambda**
 - consume data without using servers
 - uses the API call `GetBatch()` onto the data stream
	 - and the data will be sent to the lambda functions by partition key to be processed
	 - since the data is batched, the partition key and sequence id will be used
- supports classic and enhanced
- read records in batches
- configure batch size and batch window
- if error occurs, lambda retires until succeeds or data expired
- process up to 10 batches per shard simultaneously

Hands-On
![[Pasted image 20240504135740.png]]
- sample price for Kinesis Data Streams
