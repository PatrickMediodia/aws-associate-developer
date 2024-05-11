![[Pasted image 20240506205140.png]]
- we are just waiting for the result synchronously

![[Pasted image 20240506205310.png]]

![[Pasted image 20240506205349.png]]
- synchronous invocation since we are waiting of the reply of the lambda function

**Lamba CLI Methods**
- `aws lambda list-functions --region {region}`
- `aws lambda invoke --function-name {function name} --cli-binary-format raw-in-base64-out --payload { payload, can be json } --region {region} response.json`
	- writes the result to response.json

**Application Load Balancer (API Gateway)**
![[Pasted image 20240506205846.png]]
- set your lambda function as the target group behind your ALB

How does ALB send requests to your lambda function
- basically there is a way to convert your HTTP requests to JSON which you can process in your lambda function
![[Pasted image 20240506210107.png]]

![[Pasted image 20240506210222.png]]
- it then returns an HTTP response of its own converting it from JSON to HTTP

Multi-header Values
![[Pasted image 20240506210436.png]]
- lambda supports multi header values by parsing the query parameters in a way that if there are multiple occurances of the same parameter, it will return it as an array

![[Pasted image 20240506211303.png]]
- this will only be accesible to the ALB due to the security group
- When creating a target group, select the lambda function that you want

 ![[Pasted image 20240506212340.png]]
 - we can get the event that was passed on to us by the load balancer