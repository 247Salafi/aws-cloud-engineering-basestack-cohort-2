# BrightPath Tutors Capstone - Final Report

**Student:* Abdulhakeem Nuhu Adaji*  
**Training account / team:* zazozo *  
**AWS Region:*Europe Stockholm *  
**Date:*04-11-2026 *  

## 1. What I built
Describe the website and name the AWS resources used.

My answer; **I built BrightPath Tutors, an allegedly "static website" (Not actually static by industry definition) that displays the information of the website: for students wants to get better at science subjects, with an email attached for contact purposes. The AWS resources used: VPC, EC2, EBS snapshot, S3 Bucket, Cloudtrail for event history** 

## 2. Architecture
Paste or link your architecture diagram. Explain the browser-to-website traffic path in 3-5 sentences.

__My answer__; **The browser visits the website through the internet gateway with the help of the route table targeting 0.0.0.0/0. The traffic hits the VPC with IP 10.20.0.0/16 that has only one subnet(Which is Public) with IP 10.20.1.0/24, under the allowance of the security group that allows only HTTP on port 80 only and negates all other rules. The VPC has EC2 server and the Apache (bootstrap loader) which has a backup with the EBS snapshot**

## 3. Security decisions
- How is HTTP traffic allowed? ANSWER: its allowed through the security group that allows inbound rule of HTTP on port 80 source: 0.0.0.0/0

- Why did you not open SSH to the internet?: 

My Answer: __For automated installations and configurations the moment the cloud instance boots, and also position it for scale instantly without without waiting for administrative SSH, and finally eliminate the risk for human error__

- How is the S3 backup bucket protected?

My Answer: __S3 bucket was protected by enabling "Block all public Access" which makes it protected from any unauthorised access__

- What does CloudTrail help you review? 

My Answer: __CloudTrail helped me check the details of the created date of  snapshot, and details of other services and whether they were successfully created or not__

## 4. Storage and backup
- What did you put in S3?;

My Answer:__The index.hmtl file and the old-brochure file that was in the archive folder.__ 

- What did versioning show?

My Answer: __Versioning showed two index files, with the same names but with different info details, different ID, different date modified, different size__
- What is an EBS snapshot for? 

My Answer: __An EBS snapshot is used for backup of an EBS volume, it used to backup the exact state of an EC2 instance's operating system and configuration, should in-case of a crash or a system failure.__

- What lifecycle rule did you create?

My Answer: __The life-cycle rule that was created was made to transiotn storage class from Standard to Standard IA after 30 days. 
## 5. Database and scaling choices
Summarise your answers from `DATABASE_AND_SCALING_DECISIONS.md`.

My Answer: __RDS/Aurora is the best database interns o relationship between records of students, payments e.t.c , also utilizing Dynamo DB specifically o handle many reads from users, therefore since something has frequent views or visits, it's necessary to consider making I available in Elasticache while having the reserve copy of the file.

During traffic spike ASG/Load balancer handles spinning fresh EC2 instances and also terminating them when traffic drops.

Not Enabling NAT gateway in this project since no private subnet.

Configuring EBS for single server and EFS for multiple servers to read an write a file or folder simultaneously__

## 6. Problem and fix
Describe one issue encountered, what you checked in the console, and how you fixed it.

My Answer: __The challenge I encountered was in the VPC, I mistakenly made my subnet's IP address the same with that of my VPC Leading to an overlap.

I used AMAZON Q to figure out the error, to suggest various fixing options and explain the consequences for not fixing

I resolved the issue by deleting the subnet, creating new subnet and editing the route table and association to the new subnet__

## 7. Cost and cleanup
Record the Region, instance type, pricing source, running duration, and resources deleted.

My Answer: 

**AWS Region: Europe Stockholm
**Instance Type: Amazon Linux 2023 Kernel-6.18
**Pricing Source:
#EC2 Instance	brightpath-web-01 (t3.micro)	$0.0108/hr	$0.52
#EBS Volumes	2 × 8 GB gp3 (16 GB total)	$0.0836/GB-mo	$0.09
#EBS Snapshot	brightpath-root-backup (8 GB)	$0.0475/GB-mo	$0.03
#Public IPv4	In-use public IP on EC2	$0.005/hr	$0.24
#S3 Bucket	brightpath-backup-cohort-2	$0.023/GB-mo	$0.00 *
#VPCs 		brightpath-vpc-hakeem, test-VPC, default	Free	$0.00
#Total	~$0.87
**Running Duration: 50 hours
**Resources Deleted: EC2, EBS Volume, EBS snapsot, S3 Bucket, VPC


## 8. Evidence
List the screenshots submitted.

My Answer: List of the Submitted screenshot

* 01-VPC_CIDR
* 02a-Public_subnet
* 02b-route_table_assosiation
* 03-route_table_showing
* 04a-security_group
* 04b-security_group
* 05a-EC2_with_0.0.0.0
* 05b-EC2_AIM_PublicIP
* 05c-EBS_volume
* 06-BrightPath_public_IPv4
* 07a-S3_bucket
* 07b-S3_block_publick_access
* 08-S3_versioning
* 09-life_cycle_rule
* 10-EBS_snapshot
* 11-cloudTrail
* 12a-completed_data_base_scaling
* 12b-completed_week_concepts.
* 13a-CleanUp_EC2_Terminated
* 13b-CleanUP_EBS_Snapshot
* 13b-CleanUp_EBS_Volume
* 13c-CleanUp_Bucket1
* 13c-CleanUp_Bucket2
* 13c-CleanUp_Bucket3
* 13c-CleanUp_Bucket4
* 13c-CleanUp_Bucket5
* 13c-CleanUp_Bucket6
* 13c-CleanUp_Bucket7
* 13c-CleanUp_Bucket8
* 13d-CleanUp_VPC1
* 13d-CleanUp_VPC2
* 13d-CleanUp_VPC3
* 13d-CleanUp_VPC4
* 13d-CleanUp_VPC5
* 13d-CleanUp_VPC6
* 13d-CleanUp_VPC7
* 13d-CleanUp_VPC8
* 13d-CleanUp_VPC9
* 13d-CleanUp_VPC10
* 13d-CleanUp_VPC12
* 13d-CleanUp_VPC13
* 13e-cleanUp_Final

## 9. What I learned
Write three things you can now explain without reading notes.

My Answer: __The parts I can explain without looking at my notes;

VPC structure 

S3 bucket's versioning and life-cycle rule 

ASG/ Load balancer__
