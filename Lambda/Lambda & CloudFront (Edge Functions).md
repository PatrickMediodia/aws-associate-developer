**Edge Functions**
![[Pasted image 20240512144616.png]]
- run these functions close to your users to minimize latency

**Things/Customizations you can do with CloudFront functions**
![[Pasted image 20240512144759.png]]

**CloudFront Functions**
![[Pasted image 20240512144947.png]]
- written in JavaScript (and still high performance? wow)
- high performance
- high-scale
- used to change viewer request and response
	- change the request of the viewer before it makes an origin request or after it has made an origin response

![[Pasted image 20240512145153.png]]
- written in JavaScript and Python
- functions are authored in the `us-east-1` region

Difference between CloudFront Functions and Lambda@Edge
![[Pasted image 20240512145437.png]]
![[Pasted image 20240512145853.png]]
- CloudFront
	- can scale super big (millions of requests per second)
	- CloudFront functions only support short execution times
	- quick tasks such as header manipulation or URL rewrites or redirects
- Lambda@Edge
	- can not scale as big but can perform more complex computations
	- can support longer function execution times
	- access to the body itself
	- can reference libraries such as AWS SDK for more function features