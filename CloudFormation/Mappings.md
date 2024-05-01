- fixed variables within your CloudFormation template
![[Pasted image 20240501093831.png]]
- key value pairs
- the region map makes sense because AMIs are region and architecture specific

![[Pasted image 20240501094200.png]]
- Use `Fn::FindInMap` to return a named value from a specific key
- here we also used a pseudo parameter using the `!Ref:AWS::Region` which will automatically get the region our CloudFormation template is in

- Parameters vs Mapping
	- Mapping
		- great when you know in advance all the values that can be taken
		- if they can be deduced from variables such as: Region, Availability Zone, AWS Account, Environment
		- safer control over the template
	- Parameters
			- when the values are really user specific