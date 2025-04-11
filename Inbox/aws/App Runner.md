#consume 

App Runner is a service that should work like fire and forget. We push our code to a git repo and App Runner will deploy the changes based on the code provided in git. It takes complete control over the infrastructure where the app will be deployed to. It also handles TLS and makes the app available over https. We only of to worry about upload your code and done!

We can also provide  an image instead of the git repo. We can push the image to the ECR and deploy it into AWS APP Runner.

Additionally, App Runner can set up a CI/CD Pipeline, where the code will be commited to, compiled and tested and then create an image as the output and store this image in ECR.

We can set up a connector to make it possible to connect the App Runner to a private instance in a vpc.


Main Features:
- Automatic Deployment
- Source Integration like git
- Scalability
- Cost-Effective
- Integrates Well with other AWS Services

