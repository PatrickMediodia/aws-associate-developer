- used to control the creation of resources or outputs based on a condition
- common use cases are 
	- environment `dev/test/prod`
	- AWS Region
	- Any parameter value
- each condition can reference another condition, parameter value, or mapping
![[Pasted image 20240501100311.png]]

![[Pasted image 20240501104031.png]]
![[Pasted image 20240501104229.png]]
- if the condition is true, the MountPoint will be created