- you need to give the corresponding queue access policy to the services that would push and poll messages from the queue
- In this case:
	- The EC2 instance from another account is polling/getting from our SQS queue
	- The S3 bucket will push to the queue on event notifications
	
![[Pasted image 20240503175648.png]]

You can add other accounts to the access policy for cross account access
- those you can send and receive have separate access policies
![[Pasted image 20240503180050.png]]
