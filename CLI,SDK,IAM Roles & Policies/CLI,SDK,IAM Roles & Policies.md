- CLI with MFA
	- uses STS get-session-token and gave
		- acces_key_id
		- secret_access_key_id
		- session_token
	- you also put your code in the CLI, alongside with the token
	- gives out temporary credentials in the CLI

- AWS SDK
	- Java
	- .NET
	- Python (AWS CLI uses this)
	- know when to use the SDK
	- SDK by default will use the **us-east-1** region if you do not set anything

AWS Limits
- API Rate Limits
	- DescribeInstances: 100 calls per second
	- GetObject 5500 get calls per second per prefix
- Service Quotas
	- ex. On-Demand Standard Limit: 1152 vCPUs
	- to get a service quota increase you need to request an increase

Exponential Backoff
- used when we get a `throttling exception` when we go over these API rate and service limits
- if you use the SDK, this is already included in the AWS SDK behavior
- but if using the AWS API, you will be the one to retry and implement it
	- must only implement retries if `5xx server errors` and `throttling`
	- do not implement if `4xx server errors`, which just means that there is something wrong that has been sent by your client

- ex. if retry for 1 second
![[Pasted image 20240422165527.png]]

**Credentials Provider Chain**
![[Pasted image 20240423174225.png]]

Singing URLs using Credentials
![[Pasted image 20240423174751.png]]