- stream big data in your systems
- made up of multiple shards
	- are numbered
	- have to provision ahead of time
	- can scale the # of shared
	- data is split in all of the shards
- shards define your stream capacity in terms of ingestion (data going in) and consumption rate (data going out)

![[Pasted image 20240504122602.png]]
- `Producers`
	- **send data to your Kinesis Data Streams**
	- can be
		- applications
		- client
		- AWS SDK, KPL (Kinesis Producer Library)
		- Kinesis Agent (stream applications logs into kinesis data stream)
	- rely on the SDK on a low level
		- produce records into the Kinesis data stream
	
- `Records`
	- are sent by the producers
	- made up of
		- **partition key**
			- define and determine which shard the record will go to
		- **data blob (up to 1 MB)**
			- the data/value itself
	- records are sent at a rate of 1MB/sec or 1000 msg/sec per shared
		- if 6 shards == 6MB/sec or 6000 msg/sec

- `Consumers`
	- **once data is in the kinesis data streams it can be consumed by many consumers**
	- can be
		- apps (KCL - Kinesis Client Library, SDK)
		- lambda functions
		- Kinesis Data Firehose
		- Kinesis Data Analytics
	- consumers receive the message with
		- partition key --> which shard it came from
		- sequence no --> represents where the record was in the shard
		- data blob --> the data itself
	- consumer modes
		- shared
			- 2 MB/sec per shard all consumers
		- enhanced
			- 2 MB/sec per shared per consumer

![[Pasted image 20240504122821.png]]
- data retention between 1 day to 365 days
- ability to reprocess (replay) data
- once data is inserted in Kinesis, it can't be deleted (immutability)
- data that shared the same partition goes to the same shard (key based ordering)
- producers
	- AWS SDK, Kinesis Producer Library (KPL), Kinesis Agent
- consumers
	- write your own: Kinesis Client Library (KCL), AWS SDK
	- managed consumer: Lambda, Kinesis Data Firehose, Kinesis Data Analytics

**Capacity Modes**
![[Pasted image 20240504123515.png]]
- Provisioned Mode
	- historic capacity mode
	- choose number of shared provisioned
	- scale them manually or using API
	- each shard gets 1MB/s IN (or 1000 records per second)
	- each shared gets 2MB/s OUT (classic or enhanced fan-out consumer)
	- **pay per shard provisioned per hour**
	- if can plan capacity advanced, go for provisioned
- On Demand Mode
	- newer mode
	- no need to provision or manage the capacity
	- capacity is adjusted over time on-demand
	- default capacity provisioned (4MB/s IN or 4000 records per second)
	- scales automatically based on observed throughput peak during the last 30 days
	- **pay per stream per hour & data in/out per GB**
	- good if you don't know your capacity in advance

**Security**
![[Pasted image 20240504123825.png]]
- deployed within a region
- control access/authorization using IAM policies
	- produce and read from the shard
- encryption in flight for HTTPS endpoints
- encryption at rest using KMS
- you can implement your own encryption/decryption of data on the client side (harder)
- VPC endpoints are available so that EC2 instances within a VPC can access Kinesis data streams
- Monitor API calls using CloudTrail