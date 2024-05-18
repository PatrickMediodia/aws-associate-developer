**Inline CloudFormation**
![[Pasted image 20240513193802.png]]
- cannot include dependencies in inline functions
- `Code.ZipFile` property
- cannot include function dependencies

**S3 CloudFormation**
![[Pasted image 20240513193855.png]]
- CloudFormation wont update your function even if you update your code in S3 if you don't update
	- S3 Bucket
	- S3 Key
	- S3 Object Version
- this is why it is recommended to enable versioning so that you can just update the S3 Object Version on code updates

**Multiple Accounts**
![[Pasted image 20240513194246.png]]
- in order for a CloudFormation template from another account to access an S3 bucket in another you must set the bucket policy
	- set the allow principle to the other account
	- set execution role