![[Pasted image 20240427140554.png]]
- different behaviors for different endpoints which can point to diff origins

![[Pasted image 20240427140708.png]]
- in this case login will be redirected to the ec2 instance while any other request will be using the default cache behavior
- here we can set the /* route to redirect to the login page if there are no signed cookies

![[Pasted image 20240427141314.png]]