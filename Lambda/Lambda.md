![[Pasted image 20240506202029.png]]
- up to 15 minutes only
- run on-demand,only billed on when you run your functions


- easy pricing
	- pay per request and compute time
- up to 10gb ram pero function
- increasing amount of RAM will also improve CPU and network
	- so it is tightly coupled

- Language Support
	- Node.js
	- Python
	- Java
	- C#
	- Golang
	- C#
	- Ruby
	- Custom Runtime API (community supported, example Rust)

- Lambda Container Image
	- the container image must implement the Lambda Runtime API
	- unless it does that, you should use ECS or fargate

AWS Services Integration
- APi Gateway - expose our functions as API endpoints
- Kinesis - data transformation
- DynamoDB - trigger lambda functions on DB events
- S3 - trigger on bucket events
- CloudFront - Lambda at edge
- CloudWatch Events
	- react on changes on AWS infrastructure
	- ex. code pipeline changes
	- Logs
- SNS
- SQS
- Cognito - react to user login database

- there is an initial "build step" during the first invocation of your function
- 128MB RAM to 10420MB (100GB) RAM

Serveless CRON Job
- rather than having an EC2 run a CRON job every hour lets say
	- it will not do anything after it has run your function
- a better solution is using CloudWatch events to have an Lambda trigger every hour for a serverless solution and so that no resourcers are wasted

![[Pasted image 20240506203338.png]]
- Data of lambda can be from various sources
- it will scale to the number of requests your receive
- this is why it is serverless because you don't have to manage any of these
- pay per request

- you need to deploy changes after you have edited your function

![[Pasted image 20240506204704.png]]
- go into CloudWatch logs to find the root cause of the problems of your lambda functions