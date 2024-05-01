- a way to provide inputs to your CloudFormation template
- useful if some inputs cannot be determined ahead of time

![[Pasted image 20240429181313.png]]

**When should you use a parameter?**
![[Pasted image 20240429181412.png]]
- when its resource configuration it likely to change in the future
	- when you update that value, you won't have to reupload the template to change its content
- if it cannot be determined ahead of time

**Sample Parameter Settings**
![[Pasted image 20240429181557.png]]
- parameters are not just strings
- these are for validation and constraints to make sure that they are safe to use

![[Pasted image 20240429182123.png]]
- NoEcho means it will be removed in the logs and not displayed anywhere

![[Pasted image 20240429182306.png]]
- parameters can be referenced anywhere in the template
- in YAML, `Fn::Ref` can be used to reference parameters
- `!Ref {parameter name}` is a shorthand in order to access parameters
- can also reference other elements within the template

![[Pasted image 20240501093143.png]]
- NOTE: `!Ref`s are not only used for parameters, they can be used for other resourcers
	- ex. reference a security group on an EC2 instance
- in this example the `SSHSecurityGroup` is the reference to a resource

![[Pasted image 20240501093330.png]]
- in this example, the ec2 instance resource called `MyInstance` is being referenced in the`MyEIP` which is an Elastic IP Resource

![[Pasted image 20240501093510.png]]
**PseudoParameters**
- can be used at any time and are enabled by default
- this means that the CloudFormation template knows its AccountId and Region and you just have to reference it
- most used are AccountId and Region so the user does not have to tell the CloudFormation templates that

