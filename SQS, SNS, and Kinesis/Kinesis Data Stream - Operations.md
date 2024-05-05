- scaling kinesis

**Shard Splitting** (Scale Up)
![[Pasted image 20240504204808.png]]
- split a shard into two (2)
- used to increase the stream capacity (1 MB/s IN per shard)
- used to divide a hot shard (a shard that is being accessed a lot)
- increased capacity and cost
	- since we are billed per shard
- old shard will be closed for writes and will be deleted once its data has expired
- No automatic scaling in Kinesis Data Streams
	- up to you to manually increase/decrease capacity
- can't split into more than two shards in a single operation

**Shard Merging** (Scale Down)
![[Pasted image 20240504205019.png]]
- decrease capacity and save cost
- group cold shards (low traffic)
- old shards are closed for writes and will be deleted once the data has expired
- can't split more than two shards in a single operation