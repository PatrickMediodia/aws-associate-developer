- cache lives at each CloudFront edge location
	- you will have as many caches as many edge locations
- each object in the cache is identified using the cache key

![[Pasted image 20240427133027.png]]
- you want to make it so that the is more cache hits rather than miss
	- this is to minimize the requests to the origin

![[Pasted image 20240427133304.png]]

**Cache Policies**
![[Pasted image 20240427133359.png]] 

**HTTP Headers**
![[Pasted image 20240427133631.png]]

**Query Strings**
![[Pasted image 20240427133733.png]]

![[Pasted image 20240427134140.png]]
- You can only include some stuff in the orgin request and leave some out

Cache Policy Vs Origin Request Policy
![[Pasted image 20240427134235.png]]
- only the stuff in the **cache policy** will be used as **cache keys**
- while if the user needs to enhance a request, they can add origin request policies so that there are additional headers, cookies, and query strings sent without being used as keys (basically white listed)