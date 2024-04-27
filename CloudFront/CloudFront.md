- CDN
- is a global service
- cache content at the edge locations
- improve read performance and user experience
- 216 points of presence
- DDos protection because it is worldwide and distributed
	- integration w/ shield
	- AWS Web Application Firewall

![[Pasted image 20240427131121.png]]
- ex. if user is in the US and requests data, it will connect to an edge location and the edge location will then get the data from the bucket and store in as cache. So if another user accesses the same data, it will be served from the edge location rather than from the S3 bucket

![[Pasted image 20240427131422.png]]

![[Pasted image 20240427131514.png]]

![[Pasted image 20240427131708.png]]
- protect the S3 bucket to only be accessible by the S3 bucket through OAC (Origin Access Control)
- private communication between the location and the S3 bucket
- this makes it so that the S3 bucket content is distributed all around the world

![[Pasted image 20240427131834.png]]
- CloudFront is a CDN, to distribute the content as needed in different regions
- S3 Cross Region Replication is to replicate a whole bucket to another region
	- makes files accessible without making themselves public
	- you need to protect it using OAC (Origin Access Control) and change the bucket policies so that only CloudFront is able to access this bucket
	![[Pasted image 20240427132710.png]]

Caching