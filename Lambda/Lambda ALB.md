![[Pasted image 20240507182129.png]]
- register lambda fuction as a target group

**ALB to Lambda: HTTP to JSON**
![[Pasted image 20240507182221.png]]
- translation from HTTP to JSON
- headers, methods, parameters, and body are converted

**Lambda to ALB: JSON to HTTP**
![[Pasted image 20240507182322.png]]

![[Pasted image 20240507182654.png]]
- multi header values
- if same parameter and headers are sent using the same key, then it will be parsed as an array

![[Pasted image 20240507182913.png]]
- when creating an ALB, choose your lambda function as the target group

**Sending Events**
![[Pasted image 20240507183134.png]]

![[Pasted image 20240507183147.png]]

Returning HTML from Lambda
![[Pasted image 20240507183350.png]]
- this response makes it so that the lambda functions returns HTML which can be parsed by the browser
- this works because we set the `content-type` in the headers to `text/html` and the body returns HTML

Lambda Logs
![[Pasted image 20240507183551.png]]

Allows my the ALB to invoke lambda functions
![[Pasted image 20240507183825.png]]
![[Pasted image 20240507183808.png]]
