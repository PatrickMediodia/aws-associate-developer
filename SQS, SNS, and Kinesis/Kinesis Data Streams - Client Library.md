![[Pasted image 20240504203029.png]]
- Java library that helps read record from a Kinesis data stream with distributed applications sharing the read workload
- each shard is to be read by only one (1) KCL instance
	- 4 shards = 4 KCL instance
- progress is checkpointed in DynamoDB
	- therefore you need IAM access for this

![[Pasted image 20240504204131.png]]
- due to dynamodb, the apps will know how to share the work because they know what each other/worker is doing
- if an app goes down, since we have the dynamodb checkpoint progress, once the app is back online, it could resume where it last read the data

![[Pasted image 20240504204207.png]]
- cannot have more KCL apps that shard because that extra KCL instance would not be doing anything

![[Pasted image 20240504204318.png]]
![[Pasted image 20240504204344.png]]
- to scale kinesis, you need to add more shards,
