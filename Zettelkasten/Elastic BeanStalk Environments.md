#aws 

Within Elastic Beanstalk, necessary infrastructure services and their configurations are grouped in environments (production, dev, etc.). Elastic Beanstalk will walk us through the configurations of the services like which VPC to use, RDB Instances, LoadBalancing and monitoring through CloudWatch. By then end, Elastic Beanstalk will automatically create all the necessary infrastructure components that we configured for the environment. A single BeanStalk application can have multiple environments, while an environment runs a single version of an application. Environments don't share resources with one another.

---
[[Updating Elastic BeanStalk Applications]]
[[Updating Out-Of-Date Default Instance Profile]]