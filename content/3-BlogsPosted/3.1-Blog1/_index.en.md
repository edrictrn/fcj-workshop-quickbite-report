---
title: "Blog 1 - Learning AWS Secrets Manager"
date: 2026-07-30
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---
# Learning AWS Secrets Manager: Securing Sensitive Configuration on the Cloud

**Content status:** Complete

While learning and building web applications on the cloud, my early habit — probably shared by many beginners — was to store sensitive values such as `DATABASE_URL`, `JWT_SECRET_KEY`, or API keys directly in a `.env` file.

Once an application moves to an EC2 server or is shared across a team, storing secrets as plain text carries real leakage risk, especially the risk of accidentally committing a file containing secrets to a GitHub repository.

Looking deeper into AWS security options, I came across **AWS Secrets Manager**. It stores and manages sensitive information securely and can rotate it automatically, without hard-coding secrets into source code or static configuration files.

## How does AWS Secrets Manager work?

The idea behind Secrets Manager is simple and secure.

Instead of the application reading environment variables from a `.env` file on local disk, it makes a secure API call to AWS Secrets Manager (usually through an SDK such as `boto3` in Python or `aws-sdk` in Node.js) to load the values into memory as soon as it starts.

Everything stored in Secrets Manager is encrypted through **AWS KMS (Key Management Service)**. On top of that, access can be scoped precisely through IAM roles, so only the intended server or application is allowed to decrypt and read a given secret.

For example, instead of hard-coding a database connection string in code:

```text
postgresql://admin:MyHardcodedPassword123@db-instance:5432/appdb
```

the application requests it from Secrets Manager, receives a decrypted JSON payload containing `username` and `password`, and only then opens the database connection.

## Trying it out: configuring and using Secrets Manager

To understand the flow better, I tried creating a secret and retrieving it, following these steps:

### Step 1: Create a secret in the AWS Console

1. Open the AWS Management Console and find AWS Secrets Manager.
2. Choose **Store a new secret**.
3. Pick the secret type (for example, *Credentials for Amazon RDS database*, or *Other type of secret* for an API key/token).
4. Enter the sensitive key/value pairs, for example:
   - `DB_HOST`: `my-db-instance.c123456789.us-east-1.rds.amazonaws.com`
   - `DB_PASSWORD`: `SecurePassword2026!`
   - `API_KEY`: `secret-api-key-xyz`
5. Name the secret (for example, `prod/backend/config`) and create it.

### Step 2: Grant IAM permissions

Grant `secretsmanager:GetSecretValue` to the IAM role attached to the EC2 instance or service that runs the application. Because the role is attached to the instance, the application never needs to store any AWS access key or secret key on the server.

### Step 3: Read the secret from the application

Instead of reading a static environment variable, the application uses the AWS SDK to fetch the value, following this flow:

```text
App starts → calls Secrets Manager API → decrypts through KMS → loads config into memory
```

{{< report-image src="images/blog/aws-secrets-manager.png" alt="Draft post about learning AWS Secrets Manager shared in the AWS Study Group VN community" caption="The post pending approval in the AWS Study Group VN Facebook group." >}}

## A few things I found useful

After researching and trying it hands-on, I found several genuinely valuable benefits:

- **Keeps source code safe:** completely removes the risk of accidentally pushing a password, connection string, or API key to GitHub.
- **Automatic secret rotation:** can be paired with AWS Lambda so Secrets Manager rotates a database password on a schedule (for example, every 30 or 90 days) fully automatically.
- **Tight IAM integration:** access can be scoped precisely to the principle of least privilege.
- **Centralized management:** changing a database password or secret key only requires one update in the AWS Console, with no need to SSH into every server to edit a configuration file.

## A few things to keep in mind

Alongside these benefits, there are a few trade-offs worth noting:

- **Cost:** AWS Secrets Manager charges per stored secret (roughly $0.40/secret/month) plus API call volume. A practical habit is to group related configuration values into a single JSON secret instead of creating one secret per variable.
- **API latency:** calling Secrets Manager on every request can add latency. The better approach is to load the secret once at application startup and cache it in memory, rather than calling the API on every request.

## When is it worth using?

From my perspective, AWS Secrets Manager is a strong fit when:

- building production applications that need a high security standard;
- managing credentials for important databases (RDS, DocumentDB, and similar);
- automatic, scheduled password rotation is required to meet security policy;
- a system has multiple microservices that share the same configuration secrets.

This is exactly why QuickBite's Terraform data module stores `DATABASE_URL` and the JWT secret in Secrets Manager: every EC2 instance in the Auto Scaling Group reads the same secret through its own IAM role, instead of each instance keeping its own copy of a `.env` file.

## Conclusion

AWS Secrets Manager is a genuinely practical service for anyone learning or deploying applications on AWS. Moving away from the traditional `.env` file toward centralized secret management on the cloud makes the codebase cleaner and more professional, while protecting the system against some of the most common leakage risks.

## References

- [AWS Documentation – AWS Secrets Manager Concepts](https://docs.aws.amazon.com/secretsmanager/latest/userguide/developerguide-concepts.html)
- [AWS Code Examples – Retrieve Secret Value using Python (boto3)](https://docs.aws.amazon.com/secretsmanager/latest/userguide/snippets.html)
