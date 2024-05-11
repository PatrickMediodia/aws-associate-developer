![[Pasted image 20240511121429.png]]
- perfect place to store application logs in AWS
- define a log group first
- log group
	- arbitrary name, usually representation an application
- log streams
	- a log group can have many log streams
	- this is where your logs are coming from
- can define log expiration policies
	- never expire
	- 1 day
	- up to 10 years
- can send data to
	- Amazon S3 (exports)
	- Kinesis Data Streams
	- Kinesis Data Firehose
	- AWS Lambda
	- OpenSearch

CloudWatch Logs Sources
![[Pasted image 20240511121620.png]]
- CloudWatch Logs Agent is kind of deprecated since CloudWatch Unified Agent is being used

**CloudWatch Logs Insights**
![[Pasted image 20240511121842.png]]
- used to query CloudWatch logs
- specify a timestamp
- see a graph/visualization of the logs
- also able to see the specific log lines
- can be exported as a result or added as a dashboard

![[Pasted image 20240511122126.png]]
- NOTE: CloudWatch logs insights will on query historical data when you run the query

![[Pasted image 20240511122428.png]]
**CloudWatch Logs Exports**
- batch export to S3
	- could take up to 12 hours
	- `CreateExportTask`
	- not real time since it is batched
- subscriptions
	- real-time
	- can be sent to data streams, firehose, and lambda
	- can have filter

![[Pasted image 20240511122533.png]]
- can aggregate data from different CloudWatch logs filters from different accounts and different regions to one data stream
- log aggregation
- pipe into data streams which can have data firehose as a consumer which can put the logs into an S3 bucket

![[Pasted image 20240511122657.png]]
- subscription filter and destination is a abstracted connection between the sender and recipient from two different accounts
- there should be a destination access policy that will allow the subscription filter as well as an IAM role it can assume to be able to write to Kinesis Data Streams

**Hands-On**
![[Pasted image 20240511122948.png]]
- some services can create their own CloudWatch log groups automatically

![[Pasted image 20240511123007.png]]
- this group has 6 different log streams from different EC2 instances
- but uses the same runCommand

![[Pasted image 20240511123049.png]]
- you can view and filter the logs

**CloudWatch Filters**
![[Pasted image 20240511123157.png]]
- way to find a filter pattern

![[Pasted image 20240511123218.png]]

You could create an alarm based on your filter so that when the filter gets triggered, you are notified
- for example you could the set the filter to "ERROR" and every time an error occurs and it gets logged, you are alarmed
![[Pasted image 20240511123524.png]]

**Subscription Filters**
![[Pasted image 20240511123540.png]]
- add subscribers to your filters to when it gets triggered

**Log Retention**
![[Pasted image 20240511123628.png]]

**Export Data (Logs)**
![[Pasted image 20240511123644.png]]

**Log Group Creations**
- set the name, retention setting, and if you will use a KMS key
![[Pasted image 20240511123721.png]]

**Sample CloudWatch Logs Queries**
![[Pasted image 20240511124012.png]]

**Live Tail**
- you can tail your log groups or watch then real time
![[Pasted image 20240511124204.png]]
- you are able to put the filters to which log group, log streams, and filter patterns to tail

![[Pasted image 20240511124300.png]]
- this is an example of tailing the logs as events are posted

Sample
![[Pasted image 20240511124340.png]]
- create a log event
![[Pasted image 20240511124353.png]]
- live tail example

![[Pasted image 20240511124408.png]]
- you get 1 hour a day of free usage of live tail