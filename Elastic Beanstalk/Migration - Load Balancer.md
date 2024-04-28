- after creating an elastic beanstalk environment, you cannot change the elastic load balancer type
	- only change the configuration, but still the same load balancer type
- cannot go from ALB to NLB or to CLB
- To migrate
	1. Create a new environment with the same configuration except the load balancer
		- cant use the clone feature since it will copy the exact same infrastructure, and in this case we want to change the LB
	2. deploy your application onto the new environment
	3. shift the traffic to your old environment to your new one
		- cname swap or Route 53 update
	![[Pasted image 20240428160436.png]]

**RDS with Beanstalk**