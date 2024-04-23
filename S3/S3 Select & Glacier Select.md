![[Pasted image 20240423182550.png]]
- select and filter files using SQL so that there is less client side filtering that will happen
	- less queried data, less cpu cost
- will do the filtering in the server side


- Object Meta-Data
	- you can add meta-data to the S3 objects that you upload
	- user defined meta-data must have the "x-amz_meta-" tag before them
	- can be retrieved while retrieving the object
- Object Tags
	- useful for fine-grained permissions and analytics

 - **Cannot filter by meta-data and tags**
	- so why?
	- you must use an external DB as a search index such as DynamoDB