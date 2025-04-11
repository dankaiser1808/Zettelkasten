#consume #aws 

VMware is a virtualization platform that gives us tools and environments to manage virtual machines.

vSphere -> the actual hypervisor that spins up VMs on the server
vSAN -> storage solution
NSX-T -> virtualization and security platform

It is used to provide VMs in on premise environments.


So what often happens is that companies use VMware in their own data center but use EC2 and VPC in the cloud. This is not an ideal situation since the company uses two different virtualization solutions that could cause issues when moving from one to the other. But we want to have both platform to be as identical as possible.

We can enable VMware cloud in AWS and run VMware under the hood provided by AWS.

With this, we have the same virtualization technologies running in AWS and on-prem which makes it super easy to move VM's between those two environments for DR, cost saving, or compute resource capacity reasons.

Usecases to use VMware Cloud could be:

- Extending on-prem datacenter
- Simplify disaster recovery
- Migrate and scale rapidly to the cloud
- Enables us to use AWS services for VM that were running on-premise!



