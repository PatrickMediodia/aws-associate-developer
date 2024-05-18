![[Pasted image 20240512142549.png]]
- by default lambda logs are stored in CloudWatch logs
	- make sure that your AWS Lambda function has an execution role with an IAM policy that authorizes writes to CloudWatch logs
- CloudWatch metrics
	- lambda metrics are display in AWS CloudWatch Metrics
	- Iterator age is how far behind you are in reading a stream

![[Pasted image 20240512142751.png]]
- just enable X-Ray in the console and AWS runs the AWS daemon fro you
- use X-Ray SDK in code
- make sure execution role has `AWSXRayDaemonWriteAccess`
- Environment variables
	- `_X_AMZN_TRACE_ID` contains the tracing header
	- `AWS_XRAY_CONTENT_MISSING` by default, LOG_ERROR
	- `AWS_XRAY_DAEMON_ADDRESS` the X-Ray daemon IP address and port number

**Hands On**
![[Pasted image 20240512143041.png]]
- monitor tab on the lambda function

![[Pasted image 20240512143102.png]]
- metrics show you information around the lambda function
	- invocation (number of times it was ran)
	- duration (how long it ran)
	- error count and success rate (the percentage of times it was a success vs failure)
	- throttles (if your function has gone over your limits)
	- async delivery failures (number of times your function was executed asynchonously and failed)
	- iterator age (how far it is reading in a stream)
	- concurrent executions (how many invocations of your lambda function are running at a time)

![[Pasted image 20240512143524.png]]
![[Pasted image 20240512143540.png]]
- log stream of our lambda functions

**Activate AWS X-Ray**
![[Pasted image 20240512143643.png]]
![[Pasted image 20240512143718.png]]
- the management console will attempt to add this permission

![[Pasted image 20240512143948.png]]
- this lambda function now has the permission to `PutTraceSegments` and `PutTelemetryRecords`

![[Pasted image 20240512144311.png]]