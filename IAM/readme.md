## AWS Global, Regional and AZ Services

- **VPC** - Regional (Created within a region)
- **Subnet** - AZ (Can span in only one availability zone)
- **Security Groups** - Regional (SG is tied to a region and can be applied to the instance in a same region)
- **VPC Endpoints** - Regional(VPC Gateway & Interface Endpoints cannot be created between a VPC and an AWS service in a different region)
- **VPC Peering** - Cross Regional
- **Elastic IP Address** - Regional (Elastic IP addresses created within the region can be assigned to instances within the region only)
- **Elastic Network Interface** - AZ(When you create an ENI, it exists within a particular subnet, and that subnet is associated with a specific AZ. As a result, an ENI can only be attached to instances that are within the same AZ as the ENI itself)
- **Route 53 -** Global(Route 53 is a DNS (Domain Name System) service that operates across all AWS regions globally. When you create a hosted zone or manage DNS records with Route 53, it applies globally, meaning it can direct traffic to resources in any AWS region or even outside AWS. It operates at edge locations)
- **CloudFront** - Global
- **Elastic Load Balancers** - Regional ( Elastic Load Balancer distributes traffic across instances in multiple Availability Zones in the same region. Use Route 53 to route traffic to load balancers across regions)
- **Transit Gateway -** Regional
- **AWS Global Accelerator -** Global
- **EC2**
  - **Resource Identifiers** - Regional
  - **Instances** - AZ
  - **EBS** - AZ (Can only be attached to instances in same AZ)
  - **AMIs** - Regional (AMI provides templates to launch EC2 instances. AMI is tied to the Region where its files are located with Amazon S3. For using AMI in different regions, the AMI can be copied to other regions)
  - **Auto Scaling -** Regional
  - **ECS and ECR -** Regional
- **S3 -** Global but data is regional
- **DynamoDB -** Regional

## **IAM**

### IAM Role

- AWS identity with permission policies
- Can be assumable by anyone who needs it instead of being tied to a specific person
- Provides temporary credentials when assumed
- You can use roles to delegate access to users, applications, or services that don't normally have access to your AWS resources. For example, you might want to grant users in your AWS account access to resources they don't usually have, or grant users in one AWS account access to resources in another account.
- Roles can be assumed by following:
  - An IAM user in the same AWS account or another AWS account.
  - IAM roles in the same account
  - Services that allow you to run code on compute services, like Amazon EC2 or AWS Lambda
  - Features that perform actions to your resources on your behalf, like Amazon S3 object replication
  - Services that deliver temporary security credentials to your applications that run outside of AWS, such as IAM Roles Anywhere or Amazon ECS Anywhere
- **Service Role:** A service role is an IAM role that a service assumes to perform actions on your behalf. An IAM administrator can create, modify, and delete a service role from within IAM.
- **Service Linked Role:** A service-linked role is a type of service role that is linked to an AWS service. The service can assume the role to perform an action on your behalf. Service-linked roles appear in your AWS account and are owned by the service. An IAM administrator can view, but not edit the permissions for service-linked roles. For deleting service linked roles, the related resources must be deleted first.
- **Delegation:** The granting of permissions to someone to allow access to resources that you control. Delegation involves setting up a trust between two accounts. The first is the account that owns the resource (the trusting account). The second is the account that contains the users that need to access the resource (the trusted account). The trusted and trusting accounts can be any of the following:
  - The same account.
  - Separate accounts that are both under your organization's control.
  - Two accounts owned by different organizations.
    To delegate permission to access a resource, you create an IAM role in the trusting account that has two policies attached. The permissions policy grants the user of the role the needed permissions to carry out the intended tasks on the resource. The trust policy specifies which trusted account members are allowed to assume the role.

### IAM Security Tools

- **IAM Credentials Report(Account Level) : O**ffers comprehensive information about user access and permissions within an IAM system. They provide data on users, groups, roles, and their associated permissions. Count-level reports break down permissions and access counts by user, group, or role, enabling organizations to pinpoint specific areas of concern.
- **IAM Access Advisor(User Level) :** Provides detailed insights into user permissions, offering recommendations for optimizing access rights based on historical usage patterns. Access Advisor is focused on the individual user level.
- **IAM Access Analyzer:**
  - IAM Access Analyzer external access analyzers help identify resources in your organization and accounts that are shared with an external entity.
  - IAM Access Analyzer unused access analyzers help identify unused access in your organization and accounts.
  - IAM Access Analyzer validates IAM policies against policy grammar and AWS best practices.
  - IAM Access Analyzer custom policy checks help validate IAM policies against your specified security standards.
  - IAM Access Analyzer generates IAM policies based on access activity in your AWS CloudTrail logs.
