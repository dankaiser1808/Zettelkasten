ECR is a  AWS fully managed container registry where we will be able to store docker images, that are being pulled by different AWS services like Fargate. Authentication is needed to pull from the ECR.

We can choose what type of repository we want to use for the ECR, either public or private.
ECS does charge for public ECR as follows:
- storage size 
- not for data transfer out of the ECR (*pull*).

private:
- storage size
- pull and push out of ECR


Building Images in CI/CD Pipeline and store them in ECR

- It is a fully managed AWS service that integrates well with other services. 
- Provides a private registry
- Image Lifecycle management like automatic cleanups or retention policies.

