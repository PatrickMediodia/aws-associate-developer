![[Pasted image 20240503180806.png]]
- once you poll a message, it is invisible to other consumers for a period of time
	- this period of time is called the `message visiblity timeout` period
	- the default is 30 seconds
	- this means that the user has 30 seconds to process this message

![[Pasted image 20240503181312.png]]
- If message within the visibility timeout, then it could be processed twice
	- either processed by another consumer
	- or processed by the same consumer
- if a consumer knows it needs more time to process the message, there is an API called the `ChangeMessageVisibility` to get more time
	- this is so that the consumer has more time to process the message
	- so that the message would not be processed twice
- if you set this too high and the consumer crashes, it could take time to re-process the same message
- if too low, we could get many duplicates
- the `visibility timeout` should be set to something reasonable for your application

