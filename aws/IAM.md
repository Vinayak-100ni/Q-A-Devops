##  How do you control access to AWS services and resources using IAM?
I control access by designing the right combination of IAM users, groups, roles, and policies, always applying least privilege and security best practices. For example, if a developer only needs access to S3 buckets, I attach an S3-specific policy instead of giving them admin access.

##  Explain the difference between an AWS user, group, role, and policy.
Users are individual identities with credentials.

Groups let me assign common permissions to multiple users.

Roles are used when AWS services or external entities need temporary access without using permanent credentials.

Policies are JSON documents that define what actions are allowed or denied on which resources.

##  What are the best practices for creating and managing IAM users in AWS?
I always follow least privilege, avoid root usage, manage users via groups, enforce MFA, rotate or avoid long-term keys, and regularly audit permissions

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
