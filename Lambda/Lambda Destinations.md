- async and event mappers are hard to see if the lambda function failed or succeeded, or if it did, how to retrieve the data
- send result of an async invocation or failure of an event mapper into somewhere

![[Pasted image 20240509193042.png]]
**Asynchronous Events**
- CloudWatch events --> Amazon EventBridge Bus
- kinda looks like the DLQ for the asynchronous setting
- recommendation is to use destination rather than DLQ even though you can do both
	- this is because this is newer and allows for more targets
	- DLQ only allows sending of failures to SQS and SNS
- destinations allows both success and failures to send to
	- SQS
	- SNS
	- Lambda
	- EventBridge

**Event Source Mapping**
- for discarded event batches
- if it does not succeed and rather than blocking our whole process, we will put it into a failed destination

NOTE: IF SQS YOU, YOU CAN SET EITHER A DLQ OR DESTINATIONS

**Hands On**
- add both for success and failures
![[Pasted image 20240509193215.png]]
- create two queues for these destinations, one for success and one for failure

![[Pasted image 20240509194126.png]]

Lambda Destinations can create an IAM role to write to a SQS or SNS queue automatically
![[Pasted image 20240509194240.png]]

Below you can see that the destinations have been properly configured
![[Pasted image 20240509194350.png]]

Example of Successful Invocation
![[Pasted image 20240509194541.png]]
- can see the record
	- source
	- http type
- response payload and body
- can see both the event source and the event response and some extra information from the SQS message

Example of a failure case
- example is an s3 notification asynchronous lambda invocation
![[Pasted image 20240509195217.png]]

it will only go the the failure queue after it has exhausted all its retries as it is an asynchronous invocation
![[Pasted image 20240509195309.png]]

We can take a look at the message body so that we can know what went wrong
- check response payload and body
- as well as the message meta-data
![[Pasted image 20240509195416.png]]