![[Pasted image 20240501104438.png]]

`Fn::Ref`
![[Pasted image 20240501104532.png]]
- parameters return the value of the parameter
- resources return the physical ID of the underlying resource

`Fn:GetAtt`
	- get more information about the resource than ref, since ref only returns the id
	- an example can be shown down below for the GetAtt for EC2 instances
	- you can only get what CloudFormation supports for that attribute
![[Pasted image 20240501104746.png]]

![[Pasted image 20240501105010.png]]
- since we need to have an EBS volume in the same availability zone of our instance we can use the `!GetAtt {name of ec2 resource}.AvailabilityZone` get the availability zone of an instance

`Fn::ImportValue`
![[Pasted image 20240501105413.png]]
- import values exported in other stacks

`Fn::Base64`
![[Pasted image 20240501105533.png]]
- convert string to its Base64 representation
- pass encoded data to EC2 Instances

`Condition Functions`
![[Pasted image 20240501105711.png]]