- metrics are something that is of value to track
- namespaces - metrics are grouped into namespaces
	- usually namespaces are per service
		- EC2 namespaces
		- S3 namespaces
	- metrics can have up to 30 dimensions

- ec2 metrics are being pushed every 5 minutes
	- you can enable detailed monitoring for ec2 for an additional cost

 - you can have custom metrics
	 - for example to get the RAM usage in EC2 instances should be a metric
	 - use the `PutMetricData` API call
- metric resolution can be
	- standard (1 minute) or high resolution (1/5/10/30 seconds)
- make sure to configure your EC2 instance time correctly
![[Pasted image 20240511104525.png]]
![[Pasted image 20240511104705.png]]
- set the `storage-resolution` parameter to set if it is a standard or high resolution custom metric

![[Pasted image 20240511104822.png]]