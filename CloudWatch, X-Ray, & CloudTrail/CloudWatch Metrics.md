![[Pasted image 20240511115833.png]]
- metrics for every service in AWS
- metric is a variable to monitor
- namespaces
	- a collection of metrics
	- usually based on services (EC2 namespace, S3 namespace)
- metrics
	- a variable to monitor
	- there could be custom metrics as well
- dimensions
	- attributes of a metric
	- up to 30 dimensions
- you could create a dashboard from CloudWatch metrics
- have timestamps

**EC2 Metrics**
![[Pasted image 20240511115935.png]]
- detailed (1 minute) vs standard (5 minutes)
- detailed has an additional cost
- react faster to changing metrics (ex. ASG)
- **NOTE:** EC2 Memory Usage is by default not pushed, it is a custom metric

![[Pasted image 20240511120016.png]]
- namespaces of our metrics

![[Pasted image 20240511120043.png]]
![[Pasted image 20240511120057.png]]
- example of ec2 metrics

![[Pasted image 20240511120144.png]]
- since detailed monitoring is not turned on, it is getting metrics every 5 minutes

![[Pasted image 20240511120238.png]]
- view charts as different types

![[Pasted image 20240511120252.png]]
- you can add metric to the dashboard, share it, or download it as CSV

**Custom Metrics**
![[Pasted image 20240511120644.png]]
- you can push custom metrics using the `PutMetricData` api
- define your own custom metrics
- you can put how often should the metric be updated
	- use the `StorageResolution` API parameters
	- two possible values
		- standard (1 minute)
		- high resolution (1/5/10/30 seconds)
- you can push past or future data
	- make sure that to configure your instance time correctly

![[Pasted image 20240511120706.png]]
- timestamp can be specified which can be up to 2 weeks in the past or 2 hours into the future

![[Pasted image 20240511120752.png]]
- you can reference a metric data file for your parameters

![[Pasted image 20240511120829.png]]
- or reference your parameters in the command itself 

![[Pasted image 20240511120926.png]]
- you can create a script on your EC2 instances to push metric data regularly
- unified agent also uses the `PutMetricData` API call to push data into CloudWatch

![[Pasted image 20240511121041.png]]