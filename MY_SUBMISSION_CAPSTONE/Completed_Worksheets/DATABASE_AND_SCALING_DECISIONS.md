# Simple Database and Scaling Decisions

You do **not** need to create any of these extra services. Pick the service that best fits each situation and explain your choice in one or two sentences.

1. BrightPath later needs to store learners, lesson bookings, payment status and relationships between records. Which database type fits best: RDS/Aurora or DynamoDB? Why?

   My choice and reason: _______RDS/AURORA --This Database is best for relational data where data are connected and linked____

2. BrightPath adds a simple public timetable lookup with many reads and a key-based access pattern. Would DynamoDB be worth considering? Why?

   My answer: ____Yes, Dynamo DB would be worth Considering, firstly since Dynamo is focused on key i.e unique identifiers  and secondly this timetable would be taking many reads and Dynamo is also built for scalability and high usage________

3. The website repeatedly reads the same timetable and should keep a short-lived copy to reduce repeated database reads. What role could ElastiCache play, and why should it not be the only copy of the data?

   My answer: _________The ElastiCache plays a vary crucial role by reducing latency and computational cost by the timetable fully available since it's been read many times, and the timetable cannot be stored only on ElastiCache because the data is just temporarily stored for a short lived period stored in the RAM and if there's downtime at any point the data is lost and if the data was stored only on ElastiCache it's permanently lost__

4. If the relational database becomes important to business continuity, what does RDS Multi-AZ help with?

   My answer: __It helps with making sure those data are safe, it serves as a stand by promising durability. Meaning the data are been duplicated across different availability zones so that if one fails the other one takes over__

5. Website visits grow and one EC2 instance is no longer enough. What roles would an Application Load Balancer and an Auto Scaling Group play?

   My answer: ____This is the main role of the ALB because it redirects traffic to other instances and ASG regenerates new EC2 with the same configuration to handle the traffic spike when some conditions(Target tracking policy) are met relieving that first instance off the traffic overload__

6. A private application server must download updates but must not accept inbound internet connections. What networking design might use a NAT Gateway, and why is that unnecessary for this project's public web server?

   My answer: __Public/Private Subnet Architecture must use a NAT gateway. NAT Gateway is unnecessary or even wasteful because firstly NAT Gateway is a oneway connection used by the private subnet to connect to the internet and here no NAT Gateway. Furthermore this project uses a simple static web hosting format and has only one subnet(which is public) that is facing the internet, also the IP address for this server is already set to be public, which defeats the goal of NAT Gateway__

7. A website has one server that needs its own boot disk, while several Linux servers need to share the same files. Which storage option fits each case: EBS or EFS?

   My answer: ___First Case: Since that website needs it's own boot disk then EBS is preferred at this juncture, Because EBS acts as a physical hard drive inside the EC2 instance. Second Case: The Several servers that needs to share files, then EFS is perfect for this scenario because EFS acts as shared network drive that many server can connect to it and read and write all at once__

## Reminder
There can be more than one reasonable design. Marks are for a clear, sensible reason, not memorising a single sentence.public web 
