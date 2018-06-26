# Autoscaling 101

What is an autoscaling group?
- The whole reasoning is to have a redundant platform, a redundant website, to avoid downtime if there is a problem.


How to make one:
1. Make sure elastic load balancer is running
2. Create a healthcheck file
3. Go to the Launch configurations - this goes through what you would normally do when you create an EC2 instance -- but you're not actually configuring any EC2 instance
4. Create an AutoScaling Group with that launch configuration
5. Choose all availability zones within the region (up to the number of instances you are using; so if there are 3 instances you are using, choose 3 AZs)
6. Under Advanced Details, since we have load balancers, use that; select ELB instead of EC2
7. Length of time depends on the length of time that the bootstrap script is going to take (going to go with 150 seconds in this case). 
8. Create AutoScaling Group policies - you can either scale on the group size when certain triggers are hit (e.g., if CPU utilization is >90% for 5 minutes); then add an instance.
  - or you can keep the group at its initial size
9. Set notification triggers: whenever instances launch, terminate, fail to launch, fail to terminate
10. Assign some tags and launch the auto-scaling group

*NOTE*: it may take a  minute for the group to really launch, and to kick off the EC2 instances that you've asked for

Once your Instances start going down, the group will start firing up new instances to replace them.
