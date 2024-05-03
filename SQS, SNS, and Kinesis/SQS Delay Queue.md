![[Pasted image 20240503185046.png]]
- delay messages so consumers don't see it immediately
	- the message can only be polled by the consumers after this delay is finished
- up to 15 minutes
- default is 0 seconds, meaning the message is available right away
- can set a default at queue level
- can override the default on send using the `DelaySeconds` parameter

Set the `Delivery Delay` value for the whole queue
![[Pasted image 20240503185237.png]]

You can also override this setting per message
![[Pasted image 20240503190158.png]]