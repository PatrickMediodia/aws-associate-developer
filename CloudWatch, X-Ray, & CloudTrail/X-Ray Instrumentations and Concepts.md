![[Pasted image 20240511161148.png]]
- instrumentation
	- measure of products performance
	- diagnose errors
	- write trace information

![[Pasted image 20240511161544.png]]
- trace --> end to end trace
- segments --> a application/service in your trace map
- sub-segments --> more details in your segment
- sampling - decrease the amount of requests sent to X-Ray to reduce cost, because maybe we don't need everything that X-Ray is sending
- annotations
	- key value pairs used to index traces and used to search with filters
- meta-data
	- key value pairs but not index and not used for searching

**Sampling Rules**
![[Pasted image 20240511161716.png]]
- control the amount of data you send to X-Ray and record
- more data send = the more you will pay

![[Pasted image 20240511161936.png]]
- reservoir - number of trace that X-Ray will for sure record
- rate - in percent that X-Ray will record beyond the reservoir size
	- a setting of one will mean that all traces will be recorded
	- this may be good for debugging, but probably not for production
- if you change your sampling rules, you don't have to restart your application or have to do anything with your X-Ray in SDk
	- the X-Ray daemon would know how to get these sampling rules and send the right amount of data

**Hands-On**
![[Pasted image 20240511162647.png]]
- setting the sampling rules

![[Pasted image 20240511162719.png]]
- 1 trace per second
- 5% fix rate
- matching criteria - all traces

![[Pasted image 20240511162823.png]]
- the lower the priority number, the more it is going to be prioritized

![[Pasted image 20240511162925.png]]
- set the reservoir size and fixed rate

![[Pasted image 20240511163001.png]]
- set your matching criteria as needed

