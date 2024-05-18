![[Pasted image 20240512150748.png]]
- by default launched in an AWS owned VPC and therefore cannot access your AWS resources in your VPC

![[Pasted image 20240512151134.png]]
- your ENI will reference the lambda function which allows it to connect to other AWS services in your VPC

![[Pasted image 20240512151913.png]]
NOTE: deploying your lambda function in a public subnet does not give it a public IP that you can access it from
- your lambda function can access other AWS in the same subnet
- in order to give your lambda function in your VPC internet access
	- deploy it in a private subnet
	- you need to connect it to a NAT (Network Address Translation) Gateway
	- which is connected to the Internet Gateway which will then allow you to access the internet
- your lambda function can access other AWS in a different public subnet through
	- through NAT Gateway and Internet Gateway through the public subnet
	- or through VPC endpoints through the private subnet
		- remember that VPC endpoints connect your AWS services together privately without a NAT
- CloudWatch logs still run even if the lambda function is inside a private subnet without NAT gateway or VPC endpoints

**Hands On**
![[Pasted image 20240512152628.png]]
- creating a edge function

![[Pasted image 20240512153042.png]]
- create a security group for your lambda function

![[Pasted image 20240512152932.png]]
- selecting a VPC for your lambda function
- there is a warning that shows that a lambda function does not have internet access unless your VPC provides access
	- deploy your lambda function in a private subnet
	- and give it internet access through the NAT gateway and Internet Gateway

![[Pasted image 20240512153338.png]]
- attach the lambda security group created before

![[Pasted image 20240512153617.png]]
- when you create a lambda function in a VPC, to be able to run, it needs to have network interfaces
	- now they belong to you and your vpc
	- therefore you will be the one to give it network interfaces
	- give your lambda function enough permissions to do so

![[Pasted image 20240512153925.png]]
![[Pasted image 20240512153955.png]]
- attach the lambda EMI access policy
- has all the necessary permissions to be able to give our lambda function to exist in our VPC
