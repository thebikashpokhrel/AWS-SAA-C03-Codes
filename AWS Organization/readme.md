# AWS Organizations

- Policy based management for multiple AWS accounts.
- Group AWS accounts under Organization Units (OUs).
- SCPs apply at the organization or OU level, while IAM policies are applied at the user, group, or role level within an individual AWS account.
- SCPs offer central control over the maximum available permissions for the IAM users and IAM roles in your organization.
- SCPs do not grant permissions to the IAM users and IAM roles in your organization.
- SCPs set limits on the actions that the IAM users and IAM roles in your organization can perform.

### Scenarios:

- If you have an S3 bucket and want to make sure only users from accounts in your AWS organization can access it, you would add the `aws:PrincipalOrgID` condition to the bucket policy and set it to your organization's ID. This way, even if new accounts are added to your organization later, they will automatically inherit the permissions without you needing to update the policy.

- **`aws:PrincipalOrgPaths`:** It’s a condition key that allows you to filter IAM principals (users or roles) based on their position in the AWS organization hierarchy. You can use it to control access to resources based on the organizational unit (OU) or account path.

  Imagine you have an organization with different OUs: “Development,” “Production,” and “Testing.” You want to restrict access to an Amazon S3 bucket (e.g., sensitive financial data) only to users in the “Production” OU. In your S3 bucket policy, add a condition:

```json
"Condition": {
    "StringEquals": {
        "aws:PrincipalOrgPaths": "type:Root/OU=Production,OU=MyOrg"
    }
}
```

- The **`aws:Principal tag`** is a powerful feature that allows you to control access to AWS resources based on the principal (user or role) making the request. It’s like a special label that specifies who is allowed to perform certain actions on a resource.

## Use Cases

## 1. Automating Account Creation and Categorization

**Scenario**:  
Your company needs to launch new workloads rapidly across multiple projects. You want to automate the process of creating AWS accounts and ensure that they are properly categorized and secured.

**Solution**:

- Use AWS Organizations to automatically create accounts.
- Categorize accounts into groups (e.g., Development, Production).
- Apply Service Control Policies (SCPs) for security.
- Use CloudFormation StackSets for touchless infrastructure provisioning.

---

## 2. Enforcing Compliance Policies

**Scenario**:  
You need to ensure that all resources in your AWS environment meet security and regulatory compliance requirements.

**Solution**:

- Apply SCPs to enforce security actions.
- Use AWS CloudTrail for centralized logging.
- Use AWS Config to check for standard configurations.
- Use AWS Backup for regular backups.
- Apply AWS Control Tower for pre-packaged governance rules.

---

## 3. Security Team Monitoring

**Scenario**:  
The Security team needs access to monitor and mitigate potential threats across all accounts.

**Solution**:

- Create a Security group with read-only access to resources.
- Use Amazon GuardDuty for active threat detection.
- Leverage IAM Access Analyzer for identifying unintended access to resources.

---

## 4. Sharing Resources Across Accounts

**Scenario**:  
You want to share centralized resources like AWS Directory Services and VPC subnets across multiple AWS accounts.

**Solution**:

- Use AWS Resource Access Manager (RAM) to share resources.
- Share AWS Directory Service for Microsoft AD as a central identity store.
- Use AWS Service Catalog to provide access to approved IT services.

---

## 5. Centralized Governance and Security Control

**Scenario**:  
You want to ensure that every account adheres to a standard set of security and governance controls.

**Solution**:

- Use AWS Control Tower to apply governance guardrails.
- Define SCPs to enforce key actions.
- Centralize logging using AWS CloudTrail and store logs in an immutable log archive.
