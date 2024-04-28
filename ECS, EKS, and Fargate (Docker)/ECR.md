- elastic container register
- store and manage docker images on AWS
- AWS version of dockerhub
	- public repository `https://gallery.ecr.aws`

![[Pasted image 20240427185130.png]]
- storing docker images

![[Pasted image 20240427185250.png]]

- aws ecr get-login-password
	- get your docker credentials for your docker cli
	- this will allow you to use this credentials on your local docker to be able to connect to aws ecr

![[Pasted image 20240427190209.png]]![[Pasted image 20240427190218.png]]![[Pasted image 20240427190325.png]]

Any permissions issues against ECR are most likely due to IAM permissions. Your CodeBuild service must have the required permissions to push Docker images to ECR repositories.
![[Pasted image 20240428112755.png]]