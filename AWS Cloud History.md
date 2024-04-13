![[Pasted image 20240413125412.png]]
- First was SQS
- Then SQS, S3, then EC2A
![[Pasted image 20240413125453.png]]
![[Pasted image 20240413125534.png]]

**Regions**
- AWS has regions all around the world
- A cluster of data centers
- Most AWS services are scoped

**How to choose AWS Regions**
- Compliance
	- data governance and legal requirements
- Proximity
	- latency
- Available Services
	- not all services are available in every region
- Prices

**Availability Zones**
- each region has many availability zones
- each region has a minimum of 3 and a max of 6
- one or more discrete data centers
	- redundant power
	- networking
	- connectivity

![[Pasted image 20240413130028.png]]

**AWS Points of Presence (Edge Locations)**
![[Pasted image 20240413130126.png]]

AWS Global Services
- IAM (Identity and Access Management)
- Route 53 (DNS Service)
- CloudFront (CDN - Content Delivery Network)
- WAF (Web Application Firewall)
![[Pasted image 20240413130242.png]]
- to know if a service is available in your region check out the region table

![[Pasted image 20240413130613.png]]
AWS Regional Service
- to check if services are available for certain regions