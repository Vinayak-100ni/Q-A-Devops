### 1. What is AWS IAM?
AWS IAM (Identity and Access Management) is a service that helps me securely control access to AWS resources. It lets me create users, groups, and roles, and assign permissions using policies.

---

### 2. What are IAM users, groups, and roles?
- **Users**: Individual identities for people or apps.  
- **Groups**: Collections of users with shared permissions.  
- **Roles**: Temporary access identities used by AWS services or external entities.

---

### 3. What is the difference between IAM roles and IAM users?
IAM users are permanent identities for humans or apps.  
IAM roles are temporary identities with permissions that can be assumed when needed — for example, by EC2 instances or Lambda functions.

---

### 4. What is the IAM root user, and why should you avoid using it?
The root user is the account owner with full access to everything. It should be avoided because if it gets compromised, the entire AWS account is at risk. I use it only for critical setup tasks and enable MFA on it.

---

### 5. What are IAM policies?
IAM policies are JSON documents that define what actions are allowed or denied for specific AWS resources.

---

### 6. What’s the difference between AWS managed, customer managed, and inline policies?
- **AWS Managed**: Predefined by AWS.  
- **Customer Managed**: Created and managed by us.  
- **Inline**: Attached directly to a specific user, group, or role.

---

### 7. What is the difference between identity-based and resource-based policies?
- **Identity-based**: Attached to users, groups, or roles.  
- **Resource-based**: Attached directly to AWS resources like S3 buckets or Lambda functions.

---

### 8. What are IAM permission boundaries?
Permission boundaries are advanced settings that define the maximum permissions a role or user can get, even if policies grant more.

---

### 9. What are IAM Access Keys, and when should they be used?
Access keys are used for programmatic access via AWS CLI or SDKs. They should only be used when you can’t use IAM roles, like for on-prem scripts.

---

### 10. How does IAM integrate with Multi-Factor Authentication (MFA)?
MFA adds an extra layer of security by requiring a one-time code along with a password. I enable MFA for all sensitive accounts, especially root and admin users.

---

### 11. What are IAM roles with service principals?
Service principals define which AWS service can assume a role. For example, `ec2.amazonaws.com` means EC2 instances can assume that role.

---

### How do temporary security credentials work in IAM?
They’re short-term credentials created by assuming a role or using AWS STS (Security Token Service). They automatically expire after a set time.

---

###  What is the maximum number of IAM users per AWS account?
By default, we can have up to **5,000 IAM users** per AWS account.

---

###  What is IAM policy evaluation logic (explicit deny, allow, etc.)?
IAM first checks for **explicit deny**, which always overrides.  
If no deny exists and there’s an **allow**, access is granted.  
If neither, access is implicitly denied.

---

###  What’s the difference between identity federation and cross-account roles?
- **Identity Federation**: Allows external identities (like Google or corporate SSO) to access AWS without creating IAM users.  
- **Cross-Account Roles**: Allow access from one AWS account to another using IAM roles.

---

###  How do IAM roles work with AWS services like EC2 and Lambda?
We attach roles to EC2 or Lambda, and AWS automatically provides temporary credentials to those services so they can access resources securely — without hardcoding keys.

---

###  What are IAM password policies, and why are they important?
Password policies define complexity rules like minimum length, special characters, and rotation periods. They help maintain strong security hygiene.

---

###  What is the IAM Access Analyzer?
IAM Access Analyzer identifies resources shared publicly or with other accounts so I can review and fix unintended access.

---

###  How can you monitor IAM activities in AWS?
I use **AWS CloudTrail** to log all IAM actions and **AWS Config** to track configuration changes. I also review IAM Access Analyzer findings regularly.

---

###  What are some best practices for securing IAM in AWS?
- Enable MFA on root and admin users.  
- Follow the **principle of least privilege**.  
- Rotate access keys regularly.  
- Avoid using root user for daily tasks.  
- Use roles instead of long-term keys.

##  How do you enable multi-factor authentication (MFA) for AWS IAM users?
I enable MFA for an IAM user by:

Signing in to the AWS Management Console with admin privileges.

Going to the IAM service → Users → Select the user.

In the Security credentials tab, I choose Assign MFA device.

Then I pick the device type – usually a virtual MFA app like Google Authenticator or Authy, or a hardware token.

I scan the QR code from AWS into the app and enter the two consecutive OTP codes shown.

Once verified, MFA is successfully enabled for that IAM user.

##  Describe the process of setting up cross-account access in AWS IAM.
creating a role in the target account with a trust policy for the external account, attaching permissions, and then letting the external account assume that role with temporary credentials.

##  Explain the differences between IAM policies and resource-based policies in AWS.
Attachment: IAM policies attach to identities(users, groups, or roles), resource-based policies attach to resources.

Cross-account access: IAM policies can’t grant access to another AWS account directly, but resource-based policies can.

##  How do you rotate access keys for IAM users, and why is key rotation important?
I rotate IAM access keys by creating a new one, updating applications to use it, testing, and then deleting the old key. Rotation is important to reduce the risk of leaked or compromised keys . Alternatively, I use AWS Secrets Manager or AWS CLI automation scripts to manage and rotate keys securely without manual steps.

##  What is trusted entity in aws
A trusted entity in AWS is simply the user, service, or account that is allowed to assume an IAM role. For example, if I create a role for EC2 to access S3, then EC2 is the trusted entity. It’s defined in the role’s trust policy,

##  Your organization is concerned about security breaches due to compromised AWS access keys. How would you implement a secure access key rotation strategy for IAM users?
If my organization is concerned about compromised AWS access keys, I would implement a secure access key rotation strategy. The idea is to make sure no IAM user has old, unused, or long-lived keys lying around.

I’d approach it like this:

Enable IAM access analyzer / credential report to identify users with active access keys and see when they were last rotated.

Enforce rotation policy — for example, rotate keys every 90 days using an IAM password and key policy.

Use automation — set up a Lambda function or AWS Config rule to detect keys older than the allowed age and notify via SNS or even disable them automatically.

Rotation steps:

Create a new key for the user.

Update applications or scripts to use the new key.

Test to ensure it works.

Deactivate the old key, then delete it once confirmed.

Best practice — wherever possible, replace IAM user keys with IAM roles and temporary credentials (via STS or AWS SSO), so we avoid long-lived keys altogether.

##  Your organization is migrating on-premises applications to AWS. How would you ensure a seamless transition for user authentication and authorization using AWS IAM?
To ensure seamless authentication during migration, I’d integrate AWS IAM with our existing identity provider using IAM Identity Center or SAML, so users continue with the same credentials. I’d use IAM roles with least-privilege policies, enforce MFA for sensitive access, and test gradually to ensure a smooth cutover

