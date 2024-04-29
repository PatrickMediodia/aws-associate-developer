- declarative way of outlining your AWS Infrastructure for any resources (most of them are supported)
- just say what you want and automatically CloudFormation will automatically create these for you
- removes the need for manual configuration and manual work
	- provisioned through CloudFormation
![[Pasted image 20240429172635.png]]

![[Pasted image 20240429172745.png]]
- CloudFormation Designer

**Infrastructure as Code**
![[Pasted image 20240429173006.png]]
![[Pasted image 20240429173130.png]]
- leverages the power of the cloud where in we just create and delete things on the fly

**How CloudFormation Works**
![[Pasted image 20240429173238.png]]
- if a stack gets deleted, all the resources provisioned by that stack will be deleted
![[Pasted image 20240429173327.png]]

![[Pasted image 20240429173442.png]]

You can only update the template stack by uploading a new one or editing the template in designer
![[Pasted image 20240429174233.png]]

When you create changes, CloudFormation will be the one to tell you if it has to be replaced altogether
- if you do not want this to happen, you might want to update your CloudFormation config
![[Pasted image 20240429174840.png]]

On creation, CloudFormation automatically adds stack inforamtion on the resources it provisions
![[Pasted image 20240429174759.png]]

Parameters can help you write data such as tags on runtime
![[Pasted image 20240429175059.png]]

If you want to delete stack resources, it is better to delete the stack itself which will terminate the provisioned resources for you
- it can determine the order in which to delete things, e.g. you cannot delete a security group if an instance still uses it
![[Pasted image 20240429175259.png]]

