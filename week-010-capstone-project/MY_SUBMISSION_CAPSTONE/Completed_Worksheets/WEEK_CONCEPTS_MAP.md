# Six-Week Course Concepts Checklist

Use this sheet to show where the project uses each week's ideas. Short answers are enough.

## Week 1 - Cloud Foundations
- [ ] Record the AWS Region selected by the instructor: __Europe(Stockholm)__
- [ ] In one sentence, explain why choosing a Region matters: ______It matters for reducing latency, the closer a region is to a customer the faster the application loads______________
- [ ] Name one task that AWS is responsible for and one task the customer is responsible for: __AWS is responsible for Hardware securitry and customer is responsible for software patches and patches__
- [ ] Explain the difference between a Region and an Availability Zone: __A region is the whole large part for geographical place that houses multiple smaller units called Availability zones, these are where the servers been hosted__

## Week 2 - IAM & Security
- [ ] Confirm you are signed in with the identity/role assigned by the instructor.
- [ ] Confirm MFA is enabled where you control the account. In a managed lab, do not change the instructor's identity settings.
- [ ] Explain why a broad administrator policy should not be attached to an ordinary application role: __To apply least privilege and reduce blast radius, just like a new member/ a guest into an organisation would NOT be given full access to the vault immediately the same principle applies, so granting permissions gradually when need arises___
- [ ] Open CloudTrail Event history and find a project event, such as `RunInstances` or `CreateBucket`. Save a screenshot.
- [ ] Explain in one sentence what AWS Organizations can help an organisation control: ___It can helps gives an account strict boundaries and sets what's actually possible in that account i.e by using SCP__

## Week 3 - Networking (VPC)
- [ ] Create a VPC, one public subnet, an Internet Gateway, a route table, and a security group.
- [ ] Show the route `0.0.0.0/0` pointing to the Internet Gateway.
- [ ] Confirm the web security group allows HTTP (port 80) but has no inbound SSH (port 22) rule.
- [ ] Inspect the Network ACL without changing it.
- [ ] Explain why this one-public-server project does not need a NAT Gateway: __NAT Gateway are used to help connect private subnets to the internet in a secure way, and since no private subnets as explicitly described as a "one-public-server" and in the Architectural diagram, there would be no need for it.__

## Week 4 - Compute (EC2)
- [ ] Choose an Amazon Linux AMI and the smallest suitable instance type available in the training Region.
- [ ] Record why you selected the instance type and the price you checked: ___The reason for the instance type is because the project is a simple static website, so getting larger instance would be wasteful__
- [ ] Confirm the website starts from EC2 User data; do not use a terminal.
- [ ] Explain when an Application Load Balancer and Auto Scaling Group would become useful: __The Application Load Balancer an the Auto Scaling Group would be very necessary the moment the EC2 experiences high traffic and cannot handle it__

## Week 5 - Storage (S3 & EBS)
- [ ] Create a private S3 backup bucket with Block Public Access left enabled.
- [ ] Confirm default encryption and enable versioning.
- [ ] Upload `index.html` through the S3 console and upload a second version after changing a sentence.
- [ ] Add a lifecycle rule for `archive/` objects to transition to S3 Standard-IA after 30 days. It will not transition during this short lab.
- [ ] Create a snapshot of the EC2 root EBS volume.
- [ ] Explain one case for EFS instead of EBS:__When multiple servers wants to read and write a file or folder simultaneously, especially during auto-scaling, its best to use EFS instead of EBS. eg; reviewing and uploading of profile picture during traffic spike, placing the folder in EFS which many servers can access it, making it possible to scale safely.__

## Week 6 - Databases
- [ ] Complete `DATABASE_AND_SCALING_DECISIONS.md`.
- [ ] Explain why a basic informational website does not need a database yet: __It does not a database because it's meant for user to only view the information on the page, so the website does not need to know the information of who saw the site, finally the users are not querying anything__
