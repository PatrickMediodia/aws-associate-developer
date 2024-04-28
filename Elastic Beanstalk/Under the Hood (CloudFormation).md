![[Pasted image 20240428152536.png]]
- Beanstalk relies on CloudFormation
- CloudFormation is used to provision other AWS services
-  Even though the ElasticBeanstalk UI only allows you to configure a few things
	- with `ebextensions` and CloudFormation, you can configure anything you want
- used to extend your Beanstalk applications

![[Pasted image 20240428152604.png]]
- 1 stack for env, and 1 stack for prod

In resources, you can view the things that a certain CloudFormation stack has created for you
![[Pasted image 20240428152733.png]]

