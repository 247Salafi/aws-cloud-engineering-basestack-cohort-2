# Cost and Cleanup Worksheet

Complete this before launching the EC2 instance. Use the AWS Pricing Calculator or the pricing shown for your chosen Region. Do not assume that another student's estimate or free-tier eligibility applies to your account.

| Item | Your answer |
|---|---|
| AWS Region | _______Europe (Stockholm)_______________________ |
| EC2 instance type selected | _______________Amazon Linux 2023 Kernel-6.18_______________ |
| Pricing source checked | ____________On-Demand Linux Based pricing $0.0108/hour__________________ |
| Estimated cost for the planned lab period | __________$0.87(50 Hours)__________________ |
| EBS root volume size | ________8GB*2 = 16GB______________________ |
| Are you deploying a NAT Gateway? Why/why not? | __NO__ __I don't need NAT Gateway because I don't have private Subnets, and NAT Gateway are used to interact with private subnet either through ssh or the internet used to__|
| Are you deploying a load balancer or Auto Scaling Group? Why/why not?|___No, Because the website is simple setup and the architecture does not give room for that__|
| Date and time you plan to clean up resources | __________Thursday 29-10-2026____________________ |

## End-of-lab cleanup

- [ ] Terminate the EC2 instance.
- [ ] Delete the EBS snapshot after assessment.
- [ ] Empty the S3 bucket, including object versions, and delete the bucket.
- [ ] Delete the project security group, route table, Internet Gateway, subnet, and VPC in dependency order.
- [ ] Recheck the EC2, EBS, S3, and VPC consoles for remaining project resources.

**Cost reminder:** Terminating EC2 does not necessarily delete snapshots or S3 objects. Resources may still incur charges until they are deleted.
