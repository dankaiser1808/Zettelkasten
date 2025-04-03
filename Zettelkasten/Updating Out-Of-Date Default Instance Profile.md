#aws 

While going through the KodeKloud hands-on Elastic Beanstalk deployment task I faced an issue where the default EC2 instance profile was lacking permissions and therefore the web application could not be deployed. After some research I found the permissions that are needed for the instance profile and created the role myself with the following permissions:

- AWSElasticBeanstalkWebTier
- AWSElasticBeanstalkWorkerTier
- AWSElasticBeanstalkMulticontainerDocker

Selecting the newly created role for the EC2 instance profile fixed the issue.

[Managing Elastic Beanstalk Instance Profiles](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/iam-instanceprofile.html)

