![[Pasted image 20240511172826.png]]
**One (1) per EC2 Instance**
- X-Ray container as a Daemon
- Each EC2 instance in your ECS cluster would have its own X-Ray daemon

**One (1) per Container**
- X-Ray container as a "Side Car"
- one side car per app container
- side car pattern

**Fargate Cluster**
- same as the side car pattern
- one to one relation between app container and side car

![[Pasted image 20240511173115.png]]
- sidecar pattern
1. map the container port `2000` to the instance `udp` protocol using `portMappings`
2. set the `AWS_XRAY_DAEMON_ADDRESS` environment variable to the same udp port
	- in this case port `2000`
	- so the X-Ray Daemon would know how to target your app containers
3. **`link` your port mapping to your X-Ray Daemon**