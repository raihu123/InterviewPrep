### Core AWS Services and Concepts

1. **EC2 (Elastic Compute Cloud)**:
   - **Purpose**: Provides resizable compute capacity in the cloud.
   - **Key Concepts**: Instance types, AMIs, security groups, EBS volumes, auto-scaling, and Elastic Load Balancer.
   - **Frequently Asked**: 
        - **What are different EC2 instance types?**
        General Purpose (e.g., T2, T3), Compute Optimized (C5), Memory Optimized (R5), Storage Optimized (I3), and GPU Instances (P3).
        
        - **How to manage security groups?**
        Security groups act as virtual firewalls controlling inbound and outbound traffic to EC2 instances. You can add, modify, or delete rules for IP addresses, CIDR ranges, and ports.

        - **Spot vs. On-Demand vs. Reserved Instances?**
          - **Spot**: Cost-effective but may be terminated if AWS needs capacity.
          - **On-Demand**: Pay for compute capacity by the second, no long-term commitments.
          - **Reserved**: Up to 75% discount for a 1 or 3-year commitment.


2. **S3 (Simple Storage Service)**:
   - **Purpose**: Object storage for storing and retrieving data.
   - **Key Features**: Versioning, encryption, lifecycle policies, storage classes (Standard, Intelligent-Tiering, Glacier).
   - **Frequently Asked**:
     - **Difference between S3 Standard and Glacier?**
       - **Standard**: Low-latency storage for frequently accessed data.
       - **Glacier**: Archival storage, low cost, high latency for infrequent access.

     - **How to enable static website hosting on S3?**
      Set the bucket's properties to enable static website hosting, upload HTML files, and specify the index and error document.

     - **Use cases for S3 bucket policies and cross-region replication?**
       - **Bucket Policies**: Control access at the bucket level using JSON-based permissions.
       - **Cross-Region Replication**: Automatically replicates objects across different AWS regions for disaster recovery.

3. **VPC (Virtual Private Cloud)**:
   - **Purpose**: Isolated virtual network to launch AWS resources.
   - **Key Concepts**: Subnets, route tables, internet gateway, NAT gateway, security groups, and NACLs.
   - **Frequently Asked**:
     - **Differences between security groups and NACLs?**
       - **Security Groups**: Stateful, applied at the instance level.
       - **NACLs**: Stateless, applied at the subnet level, evaluates rules in order.

   - **How to set up a VPC peering connection?**
    Create a peering connection between two VPCs, update the route tables, and adjust security groups and NACLs as necessary.

- **What is a VPC endpoint, and when would you use it?**
 Allows private access to AWS services without using the internet. Used to connect to services like S3 or DynamoDB securely within your VPC.

4. **RDS (Relational Database Service)**:
   - **Purpose**: Managed relational database service (e.g., MySQL, PostgreSQL, Oracle, SQL Server).
   - **Key Concepts**: Automated backups, multi-AZ, read replicas.
   - **Frequently Asked**:
     - **Multi-AZ vs. Read Replicas?**
       - **Multi-AZ**: Provides high availability by synchronous replication to a standby instance in a different AZ.
       - **Read Replicas**: Asynchronous replication to improve read scalability.

   - **How to encrypt RDS databases?**
    Enable encryption at rest using AWS KMS during the creation of the RDS instance. Data, backups, and snapshots are automatically encrypted.

5. **Lambda**:
   - **Purpose**: Serverless compute service that runs code in response to events.
   - **Key Concepts**: Event-driven architecture, integration with API Gateway, DynamoDB triggers, and CloudWatch.
   - **Frequently Asked**:
     - **How does AWS Lambda work with API Gateway?**
    API Gateway acts as a "front door" for Lambda functions, handling HTTP requests and invoking Lambda in response.

   - **Difference between synchronous and asynchronous invocation?**
     - **Synchronous**: Waits for a response (e.g., via API Gateway).
     - **Asynchronous**: Returns immediately (e.g., event-driven architectures).

6. **DynamoDB**:
   - **Purpose**: NoSQL database service.
   - **Key Features**: Global secondary indexes, DynamoDB streams, and provisioned vs. on-demand capacity.
   - **Frequently Asked**:
     - **Difference between strongly consistent and eventually consistent reads?**
       - **Strongly Consistent**: Returns the latest updated value.
       - **Eventually Consistent**: May return stale data but offers better performance and lower cost.

   - **How do DynamoDB global tables work?**
    Provides multi-region, fully replicated tables to ensure data consistency and high availability across regions.


7. **CloudFront**:
   - **Purpose**: Content delivery network (CDN) to deliver static and dynamic content.
   - **Key Concepts**: Edge locations, distributions, caching, and origin access identity (OAI).
   - **Frequently Asked**:
     - **What is OAI in CloudFront?**
    **Origin Access Identity (OAI)**: Ensures that only CloudFront can access your S3 bucket, enhancing security.

   - **How does CloudFront integrate with S3?**
   CloudFront can serve as a CDN for S3-hosted static websites, providing edge caching and reduced latency.

8. **IAM (Identity and Access Management)**:
   - **Purpose**: Manage permissions and access for users and services.
   - **Key Concepts**: Users, groups, roles, policies.
   - **Frequently Asked**:
     - **Difference between IAM roles and IAM users?**
       - **IAM Users**: Represent a single person with long-term credentials.
       - **IAM Roles**: Assume temporary permissions, ideal for cross-account access and service-to-service communication.

   - **What are IAM policy evaluation logic and permission boundaries?**
     - **Policy Evaluation**: Determines whether a request is allowed or denied based on the policies attached to users, groups, and roles.
     - **Permission Boundaries**: Set the maximum permissions a user or role can have.

9. **CloudFormation**:
   - **Purpose**: Infrastructure as Code (IaC) for deploying AWS resources.
   - **Key Concepts**: Templates, stacks, drift detection, and change sets.
   - **Frequently Asked**:
     - **How does CloudFormation handle rollbacks?**
    Automatically rolls back to the previous known state if there is an error during stack creation or update.

   - **Nested stacks and how to use them?**
   Nested stacks enable reusing CloudFormation templates by referencing other templates. Useful for modular and hierarchical deployments.

10. **ECS (Elastic Container Service) & EKS (Elastic Kubernetes Service)**:
    - **Purpose**: Container orchestration services.
    - **Key Concepts**: Task definitions, services, Fargate vs. EC2 launch types, cluster autoscaling.
    - **Frequently Asked**:
      - **Difference between ECS and EKS?**
        - **ECS**: AWS’s native container management service using Fargate or EC2.
        - **EKS**: Managed Kubernetes service for running Kubernetes applications.

    - **How does ECS integrate with ALB?**
    ECS integrates with Application Load Balancers by registering tasks as targets, enabling containerized applications to scale and load balance dynamically.

### High-Level Architecture Concepts
1. **High Availability & Fault Tolerance**:
   - Use multi-AZ deployments, auto-scaling, and load balancing.
   - Frequently Asked: How to design a highly available system on AWS?
     - Use multi-AZ and multi-region deployments, auto-scaling, and load balancing. Leverage services like RDS Multi-AZ, Route 53, and CloudFront.

2. **Cost Optimization**:
   - Use the AWS Cost Explorer, Reserved Instances, Spot Instances, and Trusted Advisor.
   - Frequently Asked: What are some best practices for optimizing AWS costs?
     - Use Reserved Instances, Spot Instances, and Savings Plans. Enable auto-scaling, monitor usage with Cost Explorer, and set up AWS Budgets.

3. **Security Best Practices**:
   - Use IAM roles instead of IAM users, enable CloudTrail, use GuardDuty.
   - Frequently Asked: How do you secure an S3 bucket? What is the Shared Responsibility Model?
     - Use bucket policies, enable server-side encryption, block public access, and enforce IAM policies. Consider using CloudFront with OAI for access control

4. **Serverless Architectures**:
   - Combine Lambda, API Gateway, and DynamoDB for serverless apps.
   - Frequently Asked: What are the benefits of serverless architectures?
     1. **No Server Management**: AWS manages the infrastructure, scaling, and patching.
     2. **Automatic Scaling**: Scales automatically based on the workload.
     3. **Cost Efficiency**: Pay only for actual usage, with no idle resource costs.
     4. **Reduced Operational Complexity**: Simplifies deployment and operations.
     5. **Improved Time-to-Market**: Focus on writing code rather than managing servers.

5. **Monitoring and Logging**:
   - Use CloudWatch for logs and metrics, CloudTrail for audit logs.
   - Frequently Asked: How do you set up monitoring for EC2 or Lambda?
     - Use CloudWatch metrics for EC2 and Lambda. Set up CloudWatch Alarms for critical thresholds, and use CloudTrail for audit logging.
