**IF DIRECT TO EC2**
- EC2 instances must be public as there is no private VPC connectivity in CloudFront
- Allow public IP of Edge Locations

**IF THROUGH ALB**
- the ALB must be public and allow the IPs of the edge locations
- in this case, the EC2 instances can be private as there is a private connection between the ALB and the EC2 instances

![[Pasted image 20240427142411.png]]