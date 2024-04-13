- Global Service

- **Root account**
	- create by default when we create your account
	- should not be used or shared
	- should only used to create your initial admin account
	- not best practice to use the root account since account can do everything which is a problem from a security perspective 
	
- **Users**
	- people within your organization
	- can be group
	- one user represents one person

- **Groups**
	- a group or pool of users that share the same policies or permissions
	- can only contain users
	- CANNOT contain other groups
	- a user that is in a group inherits the policies of a group
	- allows easier managing of permissions

![[Pasted image 20240413131241.png]]
- Users don't have to belong to a group (not best practice)
- A user can belong to multiple groups

**Permissions**
- Users and Groups are assigned JSON documents called Policies
- Policies define permission of the users
	- do not allow your users to be able to do everything (security risk)
	- apply the idea of "least privilege"
- If given the `AdministratorAccess` policy, an account can do anything

**Policies**
![[Pasted image 20240413132608.png]]
- group
	- all users in the group will inherit the groups permissions
- inline
	- it will only be attached on a single user
	
- Policy Structure
	- version - policy version number (2012-10-17)
	- id - an id that uniquely identifies a policy
	- statements
		- SID *(Optional)*
			- identifier for a statement
		- Effect
			- either ALLOW or DENY
		- Principal
			- which ACCOUNT/USER/ROLE will this policy apply to
		- Action
			- which actions can the user do?
			- list of actions or api calls that the user can or cannot do based on the effect
			- Read S3 bucket data
			- Describe running EC2 instances
		- Resource
			- on which resources do those effects and actions apply to
		- Condition *(Optional)*
			- when will this policy take effect
	- You can change policies using the ff:
		- JSON Editor
		- Visual Editor (Just builds out the json)

**Tags**
- optional
- allows to give your resources meta-data
- Ex. Department --> Engineering

**Account Alias**
- allows you to add an alias to make it easier to sign in to your account
- kind of like a user and need to be unique

If you only see the account id in the top right corner of your AWS account it means that you are signed in as the root user

**Password Policies**
- stronger password --> higher security
- example of password policies
	- min password length
	- uppercase letters
	- lowercase letters
	- numbers
	- non-alphanumeric characters
- allow or not allow users to change their own passwords
- password expiration
	- users are required to change their password after some time
- password re-use
	- cannot change it to one that they already had before

**MFA**
- something you know (password) + something you own (device that generate the token)
- main benefit --> account is not compromised even if they know the password since the token is also needed

- Google Authentication
	- phone only
- Authy
	- multi-device
![[Pasted image 20240413134115.png]]
![[Pasted image 20240413134137.png]]

**How can users access AWS?**
- AWS Management Console
	- password protected
	- MFA
- AWS Command Line Interface (CLI)
	- protected by access keys
	- internet with AWS services using commands in the CLI
	- direct access to the public APIs of AWS services
	- `aws s3 cp {from path} {to s3 bucket}`
 - AWS Software Developer Kit (SDK)
	 - for code
	 - protected by access keys
	 - language specific libraries
	 - embedded within your application
- Access keys are generated through the AWS console
- Access keys are secret, just like a password and thus **must not be shared**
	- Access Key ID --> username
	- Secret Access Key --> password
	
![[Pasted image 20240413140107.png]]![[Pasted image 20240413140208.png]]
![[Pasted image 20240413140259.png]]
- AWS CLI that will be used in this course is for python

`aws configure`
- allows you to enter your access key id and secret access key id credentials for CLI access

**AWS Cloud Shell**
- a online interactive shell that allows you to access the CLI through the web browser
- does not need prior setup, the keys are automatically setup in your account
- all the files that you are creating in your CloudShell environment is kept
- yo can download or upload files to your CloudShell

**IAM Roles**
- assigned to AWS to do some actions on your behalf
- kind of like users but are intended to be used with **AWS services**
- Ex. attach roles to an EC2 instance server
- Example Roles
	- EC2 Instance Roles
	- Lambda Function Roles
	- Roles for CloudFormation
![[Pasted image 20240413142710.png]]

**IAM Security Tools**
![[Pasted image 20240413143135.png]]

**IAM Credentials Report (Account Level)**
- lists all of your accounts users and the status of their various credentials
- generates a CSV of all the users in an account
- shows when the user has been created, if the password has been changed or enabled, rotated, last used, etc.
![[Pasted image 20240413143213.png]]

**IAM Access Advisor (User Level)**
- show service permissions granted to a user
- and when those services were last accessed
- useful for the concept of lease privilege as you can see what they have access to and when they were last accessed
- granular checking of access permisions
![[Pasted image 20240413143344.png]]
![[Pasted image 20240413143354.png]]

**IAM Best Practices**
- do not use the root account except for the AWS account setup
- One physical user = One AWS user
- Assign users to groups and assign permission to groups
	- this allows for easier managing of permissions since it is at the group level
- Create a strong password policy
- If possible, enforce the use of MFA (multi-factor authentication)
- Create and use **Roles** for giving permissions to AWS services
- Use Access Keys for programmatic Access (CLI/SDK)
- Use Credentials Report and Access Advisor to Audit your users and accounts
- **NEVER SHARE IAM USERS AND ACCESS KEYS**

**Shared Responsibility Model**
- AWS is responsible for the infrastructure while the User is responsible on how to use that infrastructure
![[Pasted image 20240413144237.png]]

**IAM Summary**
![[Pasted image 20240413144334.png]]