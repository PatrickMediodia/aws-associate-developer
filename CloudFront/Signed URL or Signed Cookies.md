- private cloudfront distribution but you only want to share it with people that paid

![[Pasted image 20240427142916.png]]
- this makes it so that your private content can be accesible by users for a period of time that you can set
- you can restrict the access using this URL through the following
	- URL expiration
	- IP ranges to access the data from
	- which AWS accounts can create signed URLs

![[Pasted image 20240427143202.png]]
- the user authenticates through our application and our application generates a signed URL which can then be used by the client to get data from the CloudFront edge location

![[Pasted image 20240427143530.png]]
- CloudFront Signed URL
	- works not only S3 as the origin, but also HTTP, backend of whatever you want
	- you can use caching features of CloudFront
	- if there is a CloudFront distribution Infront of your S3, you have to use signed URL because the bucket policy restricts it to the OAC 
- S3 Pre-Signed URL
	- issues a request as the person who pre-signed the URL, meaning they have the same permissions as the one who signed it
	- access the S3 bucket directly, so if no bucket policy restricting, then it can also be good

![[Pasted image 20240427144342.png]]
- makes so that your EC2 instance can create signed URLS
	- keep the public keys on your EC2 instances
	- and keep the public keys on your CloudFront distribution key groups
	- uses RSA 2048 bit
- **USING TRUSTED KEY GROUP IS RECOMMENDED**