Database service, multiple DB's are supported, gives us features like scalability, reliability, backups and blue green deployments. Multiple Storage types based on need. 

Aurora is Amazon's DB Solution

- Multi AZ deployments
- Multi Storage nodes for ha and reliability

Follows a common approach to spread replicas over AZ's and use a Cluster Volume where one leader has read write access and the other ones have only read permissions.

Two Aurora Types: 

- Provisioned
	- Compute Requirements planned ahead of time fixed capacity
- Serverless
	- Capacity offers on-demand scaling
	- useful for variable and unpredictable loads

Aurora Global Database

multiple Database clusters work together in multiple regions. One region is the master and up to 5 db clusters in different regions.

Use Cases:

- Modernize Enterprise Applications
- Build SAAS Applications
- Serverless option
- Globally distributed Applications





