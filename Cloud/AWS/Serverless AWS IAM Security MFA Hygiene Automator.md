# Serverless AWS IAM Security Hygiene Automator

## 📌 Executive Summary
In cloud environments, identity is the primary security perimeter. This project transitions a foundational AWS account from manual, root-dependent operations to a strict least-privilege architecture. It introduces a zero-cost, serverless automation pipeline that continuously audits the environment for IAM vulnerabilities—specifically enforcing Multi-Factor Authentication (MFA) compliance across all users.

## 🏗 Architecture & Workflow
*(Insert a visual architecture diagram here showing EventBridge triggering Lambda, Lambda querying IAM, and outputting to CloudWatch)*

**Event-Driven Pipeline:**
1. **Amazon EventBridge** triggers the audit on a scheduled CRON/Rate basis.
2. **AWS Lambda** (Python 3.14) executes the core inspection logic.
3. **Boto3 (AWS SDK)** queries the IAM API to paginate through all users and account summaries.
4. **Amazon CloudWatch** ingests the execution logs for observability and audit trails.

## 🔐 Identity & Access Management (IAM) Strategy
This architecture strictly adheres to the principle of least privilege, entirely deprecating the root user for daily operations.

*   **SecurityAuditor Profile:** A read-only IAM user configured locally via AWS CLI for safe script testing and environment validation.
*   **PlatformAdmin Profile:** A dedicated administrative user (`AdministratorAccess`) secured with MFA, utilized exclusively for infrastructure deployment.
*   **Lambda Execution Role:** A custom service role (`LambdaSecurityHygieneRole`) restricted to `SecurityAudit` and `AWSLambdaBasicExecutionRole` policies, granting the function only the exact permissions needed to query IAM and write logs.

## 💻 Core Logic Implementation
The automation is powered by a custom Python 3.14 script utilizing the `boto3` library. The logic is designed to validate the root account baseline before iterating through all IAM users.

```python
# Snippet highlighting the IAM user pagination and MFA validation
paginator = iam.get_paginator('list_users')
for page in paginator.paginate():
    for user in page['Users']:
        username = user['UserName']
        mfa_response = iam.list_mfa_devices(UserName=username)
        
        if len(mfa_response.get('MFADevices', [])) > 0:
            print(f"[PASS] User '{username}' has MFA ENABLED.")
        else:
            print(f"[FAIL] User '{username}' is VULNERABLE (No MFA).")
