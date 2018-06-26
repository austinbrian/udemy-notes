# Placement Groups

Key exam topic

*Clustered Placement Group*
A  grouping of instances within a single AZ. Placement groups are recommended for applications that need low network latency, high network throughput, or both. ALWAYS IN A SINGLE AZ

Only certain instances can be launched into a Clustered Placement Group
  - can't do t2 micros; need high RAM or high CPU utilization

*Spread Placement Group*
Group of instances that are each placed on distinct underlying hardward.
For applications that have a small number of critical instances that should be kept separate from one another. (The opposite of Clustered Placement)
CAN BE SPREAD ACROSS MULTIPLE AZs


Exam quick facts:
- A clustered placement group can't span multiple AZs
- A spread placement group can and .
- If you see the name "Placement Group" in the exam, assume it is a *Clustered* Placement Group, just because that is the older type; Spread were introduced in 2017
- The name you specify for a placement gropu must be unique within your AWS account.
- Only certain types of instances can be launched in a placement group (Compute Optimized, GPU, Memory Optimized, Storage Optimized)
- AWS recommend homogenous instances within placement groups
- You can't merge placement groups.
- You can't move an existing instance into a placement group
  - You _could_ create an AMI from your existing instance, and then launch a new instance from the AMI into a placement group though.
- 
