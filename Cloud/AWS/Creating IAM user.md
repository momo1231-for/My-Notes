### What is AWS Budgets?

AWS Budgets is a cloud cost management and governance service that enables you to set custom spending and usage limits for your account. It continuously monitors your actual and forecasted costs against thresholds you define, sending automated alerts via email or Amazon SNS when those boundaries are breached. Within a cloud security architecture, AWS Budgets doubles as an early warning tripwire, quickly flagging the abnormal resource spikes often caused by compromised credentials, misconfigured automations, or unauthorized infrastructure deployments.

### Foundational Guardrails: Cost as a Security Metric

In cloud environments, billing alerts are not just financial tools. They are critical security tripwires. Unexpected spikes in resource consumption are often the earliest indicator of compromised credentials, unauthorized resource deployments, or cryptojacking.

Establishing baseline cost guardrails ensures that anomalous infrastructure activity immediately triggers an alert before significant damage or financial loss is incurred.

#### Example Implementation: The Baseline Tripwire

As a practical application of this principle, this project utilizes an AWS Zero Spend Budget. This acts as our foundational guardrail, automatically notifying administrators the moment actual usage deviates from expected Free Tier limits (triggering at \$0.01).

**1. Centralized Visibility**

Effective guardrails require continuous monitoring. AWS Budgets provides a dashboard to track actual and forecasted compute spend against our defined security thresholds.

![Centralized Visibility](images/1.png)

**2. Standardized Deployment**

Using predefined templates ensures rapid and accurate deployment of baseline alerts across new or isolated cloud accounts.

![Standardized Deployment](images/2.png)

**3. Automated Incident Notification**

The guardrail is configured to immediately push notifications to the security or operations team, minimizing the time to detect an anomaly.

![Automated Incident Notification](images/3.png)

**4. Continuous Verification**

Once deployed, the guardrail actively monitors the environment, ensuring continuous compliance with the established baseline.

![Continuous Verification](images/4.png)

### Identity and Access Management: Moving Away from Root

Using the root account for daily work is dangerous. The root user has unrestricted, irrevocable access to all resources and billing, meaning a compromised root password could lead to total account takeover and catastrophic costs.

By creating a dedicated user with functional permissions, we build a secure working environment. This aligns with the cybersecurity principle of least privilege, ensuring the user only has the exact permissions necessary to perform their required tasks.

#### Step-by-Step Implementation

**1. Verifying a Clean Slate**
We start by navigating to the AWS Identity and Access Management (IAM) dashboard, confirming that no users currently exist in the environment.

![Verifying a Clean Slate](images/1_2.png)

**2. Defining the User Identity**
We initialize a new IAM user and configure their console login parameters, assigning a secure custom password while mandating a password reset upon their first login.

![Defining the User Identity](images/2_2.png)

**3. Enforcing Least Privilege**
Instead of granting broad administrative rights, we attach specific, restricted policies directly to the user to match their exact functional requirements.

![Enforcing Least Privilege](images/3_2.png)

**4. Reviewing Configurations**
Before provisioning the identity, we review the user details and the specific permissions summary to ensure no excess privileges have been accidentally assigned.

![Reviewing Configurations](images/4_2.png)

**5. Securing the Credentials**
Upon successful creation, AWS generates the unique Console sign-in URL and provides the initial login credentials. These must be captured and stored securely.

![Securing the Credentials](images/5.png)

**6. Confirming the New Identity**
Finally, we verify that the new dedicated user is actively listed in the IAM dashboard, completely separate from the root account.

![Confirming the New Identity](images/6.png)