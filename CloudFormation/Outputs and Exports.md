- optional
- output values that we can import into other stacks
	- you need to export them first

![[Pasted image 20240501094849.png]]

![[Pasted image 20240501095003.png]]
- Export `name` must be unique from all your exports in one region
- Basically here we are exporting the value of the referenced resource named `!Ref MyCompanyWideSSHSecurityGroup` and export it as named `SSHSecurityGroup`

![[Pasted image 20240501095209.png]]
- to import it, we can use the `Fn::ImportValue` function to get the value from the export of another template
- **NOTE: You cannot delete the template in which the values are exported from until all the templates that Import that values does not exist anymore**
