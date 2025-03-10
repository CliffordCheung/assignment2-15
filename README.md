# assignment2-15

Q1. What is needed to authorize your EC2 to retrieve secrets from the AWS Secret Manager?

To authorize EC2 to retrieve secrets from the AWS Secret Manager, you need the following:
1. Create and IAM Role that grants the necessary permissions to access AWS Secrets Manager.
2. Attach the IAM Role to the EC2 Instance. This allows the instance to assume the role and use the permissions granted by the role.
3. Create a policy that grants the IAM role permissions to retrieve secrets from AWS Secrets Manager. Attach this policy to the IAM role.
4. Ensure that the EC2 instance is configued to use the IAM role.
5. Use the AWS SDK to access the secrets in the application running on the EC2 instance.

Q2. Derive the IAM policy (i.e. JSON)?
    - Using the secret name prod/cart-service/credentials, derive a sensible ARN as the specific resource for access

{
  "Version": "2012-10-17",
  "Statement": [
  {
      "Effect": "Allow",
      "Action": "secretsmanager:GetSecretValue",
      "Resource": "arn:aws:secretsmanager:region:account-id:secret:secret-id"
    },
    {
      "Effect": "Allow",
      "Action": "kms:Decrypt",
      "Resource": "arn:aws:kms:region:account-id:key/key-id"
    }
  ]
}
