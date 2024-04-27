![[Pasted image 20240423184828.png]]
- **SSE (Server-Side Encryption)**
	- SS3-S3 
		- enabled by default for new buckets and new objects
		- encrypts s3 objects using keys handled, managed, and owned by AWS
		- AES-256
		- must set header to `"x-amz-server-side-encryption":"AES256"` to enable SSE-S3
	- SSE-KMS
		- use AWS KMS to manage encryption keys
	- SSE-C
		- using own encryption keys
- **Client-Side Encryption**
	- encrypting the files before uploading it to S3

**SS3-S3**
![[Pasted image 20240423185217.png]]

**SSE-KMS**
![[Pasted image 20240423185435.png]]
- can be trailed using CloudTrail as it logs every time a key is used
- gives the user control to which keys to use
- must set header to `"x-amz-server-side-encryption":"aws:kms"` to enable SSE-S3

**SSE-KMS**
![[Pasted image 20240423185538.png]]
- if you have all your objects encrypted using KMS, it could throttle as you will use up your API calls to the KMS service

**SSE-C**
- key is fully managed by the customer outside of AWS
- AWS does not store the encryption key you provide
- HTTPs must be used
- must pass the key in the HTTP headers for every HTTP request
- to read the said file, the user must also pass the key as headers that was sent on uploading the file
![[Pasted image 20240423185843.png]]

**Client Side Encryption**
- client side libraries such as AWS S3 Client Side Encryption Library
- clients must encrypt the data themselves before sending to Amazon S3
- clients must decrypt the data themselves when retrieving from Amazon S3
	- it will also be decrypted on the client side
- all of this will be handled by the user that is why a library might be useful
- you can only do this through the CLI or SDK because you will pass the key as headers

![[Pasted image 20240423190451.png]]
Encryption in transit (SSL/TLS)
- Amazon exposes two endpoints (HTTP and HTTPS)
- for S3, it is of course recommended to use HTTPS

![[Pasted image 20240423190620.png]]
- to make sure that the bucket is being accessed securely, you could add a bucket policy to deny the request if the SecureTransport condition is set to false


You have a default KMS key for the S3 service


![[Pasted image 20240423191317.png]]
- you can force the user to upload objects to the bucket with encryption using bucket policies
- this is because bucket policies are evaluated before default encryption

**Cross-Origin Resource Sharing (CORS)**
Origin = scheme (protocol) + host (domain) + port
![[Pasted image 20240424182408.png]]
![[Pasted image 20240424182533.png]]
- **CORS Headers**
	- Access-Control-Allow-Credentials --> true/false
	- Access-Control-Allow-Methods --> GET, PUT, POST, DELETE, etc.
	- Access-Control-Allow-Origin --> the actual origin
	- Acess-Control-Max-Age --> time

**S3 Questions Related to CORS**
![[Pasted image 20240424182804.png]]
![[Pasted image 20240424183747.png]]

**S3 - MFA Delete**
![[Pasted image 20240424184000.png]]
- when enabled, the user needs to enter a MFA code for destructive actions such as
	- permanently deleting an object version
	- suspend versioning on the bucket
- currently you can only set this through the AWS CLI

**S3 Access Logs**
- for audit purposes, you may want to log all access to s3 buckets
- any request made to the S3 bucket from any account will we logged into another S3 bucket
- target logging bucket must be in the same AWS region
![[Pasted image 20240424185150.png]]![[Pasted image 20240424185217.png]]

**Pre-Signed URLs**
![[Pasted image 20240424190919.png]]
- pre-signed