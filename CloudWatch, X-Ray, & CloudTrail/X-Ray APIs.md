**Write APIs**
![[Pasted image 20240511171022.png]]
- used by the X-Ray daemon to write data to the X-Ray service
- `PutTraceSegments`
	- uploads segment documents to AWS X-Ray
	- necessary if you want to write to X-Ray
- `PutTelemetryRecords`
	- how many segments are received
	- how many segments have been rejected
	- backend connection errors
	- helps with the metrics
- `GetSamplingRules`
	- retrieve all sampling rules
	- to know what/when to send
	- remember that when we change the sampling rates that we didn't have to restart the daemon? 
	- this is because it is using this API call `GetSamplingRules` so that it knows the sampling rate it needs to follow
	- all the X-Ray daemons use this to follow what you have set
- `GetSamplingTargets` & `GetSamplingStatisticsSummaries` (Advanced)

**Read APIs**
![[Pasted image 20240511171409.png]]
- `GetServiceGraph
	- get the main graph that we saw in the console
- `BatchGetTraces`
	- retrieves a list of traces specific by ID
	- each trace is a collection of segment documents that originates from a single request
- `GetTraceSummaries`
	- retrieve IDs and annotations for traces available for a specified time frame using an optional filter
	- to get the full traces, pass the trace IDs to `BatchGetTraces`
- `GetTraceGraph`
	- retrieves a service graph for one or more specific trace IDs