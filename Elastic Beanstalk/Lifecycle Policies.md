![[Pasted image 20240428150800.png]]
- can store at most 1000 application versions
- if you don't remove them, you won't be able to deploy anymore
- you can phase out old application versions
	- based on time (remove after X amount of days)
	- based on space (remove if there are already X versions)
- versions that are currently used won't be deleted
- option to not delete the source bundle in S3 to prevent data loss

**Application Versions are stored in S3**
![[Pasted image 20240428150928.png]]
- registered in beanstalk

![[Pasted image 20240428150959.png]]
- Lifecycle Rule
	- version age
	- version number limit
- Retention
	- delete in S3
	- retain in S3