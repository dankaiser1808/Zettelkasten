#consume #aws

Provides us with the ability to run jobs in AWS. We can define multiple jobs with different amount of resources. Batch just needs to compute environment which can be EC2 Instances and based on the amount of jobs and their requirements batch will handle to schedule the jobs on the instances.

It provides a queuing system and also priority levels for optimized job scheduling.

AWS manages Jobs in a lifecycle.

1. Submitted (First stage, aknowledged by AWS but not queued yet)
2. Pending (Job is waiting in the queue ready to be scheduled, might be waiting for job dependencies or resource availability)
3. Runnable (Ready to be assigned to a compute environment)
4. Starting (assigned to compute env containers will be started)
5. Running (currently in the process executing the job)
	1. Failed or Successfully

Batch Components:
- Create a Job Definition for AWS Batch
	- Resources needed, command to run, ENV vars, ...
	- Job Submission
	- Job Queues
	- Job Scheduler (Determines where and when to run jobs)
	- Job Execution (in docker containers, isolated runtime environments)
	- Compute Environments are a Collection of compute resources to run the Jobs, either EC2 Spot, on demand or Fargate.

Main Features
- Dynamically provision resources for the Jobs
- Job Qeue and Prio
- Cost Efficient
- Integrates with AWS Services
- Customizable Compute Environment

