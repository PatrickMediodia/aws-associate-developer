![[Pasted image 20240511183935.png]]

![[Pasted image 20240511184203.png]]

![[Pasted image 20240511183953.png]]
- only management events are recorded by default
	- operations performed on resources in your AWS account
	- can be separated by read and write events
- data events are not logged by default because these are high volume operations

![[Pasted image 20240511184337.png]]
- CloudTrail insights is a paid service
- analyzes write type of events (which is the disruptive kind) to detect unusual patterns

![[Pasted image 20240511184437.png]]
- events are stored for 90 days
- if needed for long term storage, store them in S3 and use athena to query them

**Hands On**
- intercept user API calls or activity
![[Pasted image 20240511184708.png]]
- API calls for the last 90 days for this account

![[Pasted image 20240511184757.png]]
- sample CloudTrail event history log

![[Pasted image 20240511184825.png]]
- the whole event record is available