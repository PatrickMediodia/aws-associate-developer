![[Pasted image 20240504094049.png]]
- max message limit is 256kb
- how to send large messages
- use an S3 bucket as a repository for the large data
	- producer will send a message with a small metadata message which will point to the object/large message in S3
	- consumer will then read the message with the small meta data which points to the object in the s3 bucket and the consumer will then read that
- one use case is if you're processing video files, you don't send the video file through the SQS queue