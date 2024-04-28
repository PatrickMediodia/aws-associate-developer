- can be provisioned with beanstalk, great for dev/test
- if prod, this is not great as the database lifecycle is tied to beanstalk lifecycle
- best way to do in prod is to create an RDS separately and provide our EB application with the connection string

![[Pasted image 20240428160650.png]]

**Decouple RDS if already in Beanstalk Stack**
1. snapshot of RDS db (as a safeguard)
2. set the RDS with protect RDS database from deletion
3. create a new environment with the same config but without the RDS
4. perform a CNAME swap (blue/green) or route 53 update
	- confirm that it is working
5. Terminate old env (RDS won't be deleted)
6. Delete cloud formation stack (in _DELETE_FAILED state)
![[Pasted image 20240428160804.png]]
![[Pasted image 20240428160811.png]]
![[Pasted image 20240428161009.png]]![[Pasted image 20240428161157.png]]
- everything will also be deleted by CloudFormation