- take data from producers and write the data for you
- no need to write code since kinesis fire hose knows how to write data

![[Pasted image 20240504210947.png]]
Producers
- 3rd Party
	- Apps
	- Client
	- SDK
	- Kinesis Agent
- AWS
	- Kinesis Data Streams
	- Amazon CloudWatch (Logs and Events)
	- AWS IoT

Destinations
- AWS
	- S3
	- Amazon Redshift (Copy through S3)
		- first writes to S3, then Firehose will issue a copy command to Redshift
	- Amazon OpenSearch
- 3rd party
	- Data Dog
	- Splunk
	- New Relic
	- MongoDB
- Custom Destinations
	- HTTP endpoint

- fully managed service
- no administration
- serverless
- automatic scaling
- 