# Elastic File System

EFS is a file storage service for Amaazon Elastic Compute Cloud (EC2) instances. It is easy to use, and provides a simple interface that allows a user to create and configure file systems quickly and easily.   

With Amazon EFS, storage capacity is elastic, growing and shrinking automatically as you add and remove files, allowing applications to draw on extra storage capacity when they need it.

*IN a nutshell*: it allows us to on-the-fly add storage volumes; allows you to mount an EBS volume to multiple EC2 instances at once

EFS Features
- Supports the Network File System v4 (NFSv4) protocol
- You pay only for the storage you use (no pre-provisioning required)
- Can scale up to petabytes
- Can support thousands of concurrent NFS connections
- Data is stored across multiple AZs within a region

(not going to be as durable as S3's eleven 9s)

*EFS is block-based*, as opposed to object-based storage, so we can put files in there and share with other instances

## Configure on the Console
EFS is under "storage", though it is not available in all regions

So within a single VPC:
- The availability zones that are sleected each have their own subnet
- The IP address is automatic
- Security group is fine to use the VPC default   

File system
- While the file system is being configured, set up the EC2 instances
- Set them up in the AZs that are most relevant
- Use the security groups that are already set up

Also prudent to provision a load balancer that has multiple EC2s in it

## To start using
- *Important point* to start using the VPC, it is important that the EC2 instances that are provisioned for use are in the *same security group as the VPC*

Allows you to have your code in one centralized repository, and have EC2 instances that autoscale and then mount that EFS mount point as the root directory for apache
- saves time over bash scripts that would pull down data from S3

## Important to remember
- USE CASE: is as a file server
- you're storing your files there, making it a central repository
- multiple EC2 connecting to the same EFS volume and all accessing the same files
- you can apply to EFS user-level and directory-level permissions, which would be universal across all EC2 instances
  - e.g., payroll folder that only certain users could access
- contrast: EBS allows you to only mount one instance to a file section
