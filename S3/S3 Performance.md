![[Pasted image 20240423181915.png]]



![[Pasted image 20240423182106.png]]
**Multipart Upload**
- recommended for files greater than 100MB
- must use for files greater than 5GB
- parallelize uploads to speed up transfers

**Transfer Acceleration**
- over 200 edge locations
- increase speed by uploading S3 object into edge location, and then this edge location will transport the file to the user through the AWS private network

![[Pasted image 20240423182336.png]]
- S3 Byte Range Fetches
	- parallelize the request for S3 objects by using byte range fetches which will use many get requests to specific ranges
	- you could also only request a specific byte range so you don't have to request the whole file