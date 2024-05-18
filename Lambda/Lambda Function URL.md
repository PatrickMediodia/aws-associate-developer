- dedicated HTTPS endpoint for your lambda function without the need for API gateway or ALB

![[Pasted image 20240515184327.png]]

![[Pasted image 20240515184521.png]]

![[Pasted image 20240515184638.png]]
- need to set AuthType to NONE to allow public and unauthenticated access

![[Pasted image 20240515184836.png]]
- if same account, either resource based or identity based policy as allow
- if cross account, both resource and identity based policy must allow

![[Pasted image 20240515185801.png]]
NOTE: YOU CAN ONLY CREATE A FUNCTION URL FOR UNPUBLISHED VERSIONS OR AN ALIAS