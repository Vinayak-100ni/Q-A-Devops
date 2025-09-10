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
