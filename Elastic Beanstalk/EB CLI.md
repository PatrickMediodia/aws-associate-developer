![[Pasted image 20240428145204.png]]

1. Describe your dependencies
	- requirements.txt for python
	- package.json for node.js
2. package code as zip and describe dependencies
3. Console: upload zip file to console (creates a new app version), and then deploy
4. CLI: create new app version using CLI (uploads zip), and then deploy
- Note: That zip when uploaded to beanstalk gets uploaded to S3 and then refers that in the Beanstalk interface
5. Beanstalk will deploy the zip on each EC2 instance and resolve the dependencies and start the application