- S3, SNS, Cloud Watch events
- for services that trigger your lambda functions behind the scenes

- internal event queue, which is read by a lambda function
	- lambda attempts to retry

- lambda functions much be idempotent, in which incase of retries, its result should be the same
- why use async functions
	- some services require it
	- speed up processing because you don't need to wait for the result as they are ran asynchronously

![[Pasted image 20240507184514.png]]
Sample of AWS Asynchronous Invocations
- S3 event notifications
- SNS notifications
- CloudWatch Events / EventBridge
	- have our lambda functions react to AWS infrastructure
- CodeCommit (new branch, new push, new tag)
- CodePipeline (lambda invocation during the pipeline)

![[Pasted image 20240507184927.png]]
- Invoke a lambda function but not needing to know its result because it may still be currently running
- response status code 202 confirms this

![[Pasted image 20240507190021.png]]
- since we won't know its result, we wont know if it errors out
- this is just the nature of it since we don't want to know its result which is the nature of it being aynschronous
- we just start the lambda function and we are done with it
- if this is the case, we could setup a dead letter queue to catch our errors

![[Pasted image 20240507190211.png]]
- you can enable that

![[Pasted image 20240507190510.png]]
- you can set how many times to retry
- 1st retry is after 1 minute, and the second retry is after 2 minutes

![[Pasted image 20240507190610.png]]
- make sure than your lambda function has the appropriate permissions to write to SQS
- you can give it 