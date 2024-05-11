**THIS IS FOR EVENT SOURCE MAPPING**
- where in the lambda role will be invoking other AWS services
![[Pasted image 20240509195920.png]]
- grants the lambda function permission to AWS services/resources
- when you use an event source mapping
	- needs to use the execution role in order to read event data
![[Pasted image 20240509200436.png]]
- almost every execution role made by AWS for the lambda execution role has the `AWSLambdaBasicExecutionRole`
- this makes it so that the lambda function can write to CloudWatch logs
![[Pasted image 20240509200443.png]]
- **best practice i to create one lambda execution role per function**

**THIS IS FOR WHEN LAMBDA IS INVOKED BY OTHER SERVICES**
Lambda Resource Based Policies
![[Pasted image 20240509200120.png]]
- when our lambda functions is invoked by synchronous types of events

![[Pasted image 20240509200740.png]]![[Pasted image 20240509200814.png]]
- in this example, lambda is being invoked to by the ALB
![[Pasted image 20240509200833.png]]
- allows the S3 bucket notifications to invoke the lambda functions

**NOTE: IN ASYNCHRONOUS INVOCATIONS, IT IS THE SERVICES THAT INVOKE LAMBDA FUNCTIONS**

IF SQS, there is no resource based policies since lambda will be the one to invoke the SQS queue, effectively polling from it, and then processing them
![[Pasted image 20240509201035.png]]
![[Pasted image 20240509201102.png]]