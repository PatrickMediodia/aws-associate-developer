![[Pasted image 20240511144420.png]]
- kind of like automated testing
- reproduce what your customers do programmatically to find issues before customers are impacted
- kinds of like selenium and cypress
- one use case is to run this every so often, and if it fails, you could trigger a cloudwatch alarm which could invoke a lambda function that will update a Route53 DNS record to point to an instance where we know the deployment is good

![[Pasted image 20240511144614.png]]