![[Pasted image 20240428151947.png]]
- a zip file containing our code must be deployed to elastic beanstalk
- all the parameters set in the UI can be configured with code using files
- requirements
	- must be stored in the `.ebextensions/` in your root folder
	- YAML/JSON format
	- .config extensions (example: logging.config)
	- able to modify some default settings using: option_settings
	- ability to add resources such as RDS, ElastiCache, DynamoDB, etc.

- resources managed by the `.ebextensions` gets deleted if the environment goes away
	- if you create ElastiCache as part of your beanstalk envrionment
	- if you delete your beanstalk environment, your elasticache will go away as well

![[Pasted image 20240428152032.png]]
- has the `.config` extension
- and placed in the `.ebextensions\` folder
- option_settings
	- here we just added environment variables such as the `DB_URL` and the `DB_USER`

![[Pasted image 20240428152311.png]]