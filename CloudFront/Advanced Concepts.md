**Pricing**
- CloudFront Edge locations are all around the world
- therefore the data out per edge location varies
- the more data that is transferred out, less the cost
![[Pasted image 20240427145144.png]]

![[Pasted image 20240427145344.png]]

![[Pasted image 20240427145407.png]]

**Multiple Origin**
![[Pasted image 20240427145508.png]]

**Origin Groups**
- provides fail over and high availability to cloudfront origins
- so there is a primary and secondary origins

- this can apply to both backend (EC2 instances, or ALB backed EC2 instances) and S3 origins
- if S3 as origin, you can setup S3 CRR/SRR replication so that the failover or secondary bucket has the same data as the primary bucket

![[Pasted image 20240427145957.png]]

**Field Level Encryption**
- encrypt specific fields in POST requests that you want to secure, ex. credit cards
- edge locations will use the public key to encrypt your data, and then you can use the private keys to decrypt your data in your web servers
![[Pasted image 20240427150322.png]]

**Real Time Logs**
![[Pasted image 20240427150450.png]]
