# Storing Secrets in Amazon Parameter Store to use in ECS

One way to pass secrets and variables securely to containers in AWS is to use Parameter Store. Navigate to the AWS Systems Manager service to get started.

## Parameter Store

### Create Parameter

1. Enter a name or path for the parameter.
2. Optionally add a description.
3. Select the tier to use.
4. Select the type. (we will choose SecureString.)
5. Select the KMS key source which is what will encrypt the SecureString.
6. Enter the value for the parameter.

## Creating a Role and policy for ECS in IAM

In order for the containers in our Task Definition to get parameters, we need to enable KMS decrypt and SSM get parameter permissions. Navigate to IAM to get started.

### Create Policy

Create a policy with permissions for KMS and SSM:

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "VisualEditor0",
            "Effect": "Allow",
            "Action": [
                "kms:Decrypt",
                "ssm:GetParameters"
            ],
            "Resource": [
                "arn:aws:kms:<aws-region>:<account-id>:key/<key-id>",
                "arn:aws:ssm:<aws-region>:<account-id>:parameter/<parameter>"
            ]
        }
    ]
}
```

### Create Role

1. Choose the service `Elastic Container Service` 
2. Select the use case as `Elastic Container Service Task`
3. Attach the policy created to read secrets from Parameter Store.
4. Enter a role name.
5. Enter a role description.
