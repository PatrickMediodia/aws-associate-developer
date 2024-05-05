- how to get data into Kinesis
- put data records into data streams
- data records consists of
	- sequence number
		- unique per partition-key within shard
	- partition key
		- must specify while putting records into the stream
	- data blob
		- the actual data
		- up to 1MB

`Producers`
![[Pasted image 20240504124641.png]]
- AWS SDK
	- simple producer
- Kinesis Producer Library (KPL)
	- Available in C++ and Java
	- Built on top of the SDK but has advanced capabilities available as APIs such as Batch, Compression, Retries
- Kinesis Agent
	- Monitor Log Files and stream those to your Kinesis Data Stream
	- Built on top of the KPL
- Write throughput
	- 1 MB/sec or 1000 records/sec per shard
- `PutRecord` API
	- put data into the Kinesis Data Stream
- Use batching with `PutRecords` API to reduce costs and increase throughput
	- Kinesis Producer Library already does this for us

![[Pasted image 20240504125452.png]]
- hash function
	- takes in the partition key and figure out to which shard to send the data
- same partition key = same shared
	- this is because the same partition key will yield the same hash function result
- in this scenario if a device is sending a lot of data, it could overwhelm the shard
	- make sure that your partition key is well distributed to avoid the concept of a hot partition
	- hot partition --> one shared with more throughput than the others which will bring and imbalance
- a well distributed key might be 6 shards and 10,000 users and using the user ID as the partition key
- a badly distributed key might be 6 shards with 3 users namely Chrome, Firefox, and Safari as the chrome partition key will be used more and therefore the shard for that key will be overwhelmed
- **NOTE: MAKE SURE TO USE A WELL DISTRIBUTED PARTITION KEY**


`ProvisionedThroughputExceeded`
![[Pasted image 20240504125738.png]]
- over producing a shard

**Solution**
- Use a highly distributed partition key
	- so that the producers writing to a shard will be distributed throughout
- Retries with exponential backoff
	- this makes it so that producers will try again at a later time once the throughput can now accommodate the data they will send
	- exponential retries is needed so that not all of the producers will retry and overwhelm the shard at the same time
- Increase shards (scaling)
	- shard splitting into two to augment the throughput

