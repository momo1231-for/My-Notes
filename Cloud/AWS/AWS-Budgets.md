##What is AWS Budgets?##

AWS Budgets is a cloud cost management and governance service that enables you to set custom spending and usage limits for your account. It continuously monitors your actual and forecasted costs against thresholds you define, sending automated alerts via email or Amazon SNS when those boundaries are breached. 

Within a cloud security architecture, AWS Budgets can double as an early warning tripwire, quickly flagging the abnormal resource spikes often caused by compromised credentials, misconfigured automations, or unauthorized infrastructure deployments.

### Foundational Guardrails: Cost as a Security Metric

In cloud environments, billing alerts are not just financial tools. They are critical security tripwires. Unexpected spikes in resource consumption are often the earliest indicator of compromised credentials, unauthorized resource deployments, or cryptojacking.

Establishing baseline cost guardrails ensures that anomalous infrastructure activity immediately triggers an alert before significant damage or financial loss is incurred.

#### Example Implementation: The Baseline Tripwire

As a practical application of this principle, this project utilizes an AWS Zero Spend Budget. This acts as our foundational guardrail, automatically notifying administrators the moment actual usage deviates from expected Free Tier limits (triggering at $0.01).

**1. Centralized Visibility**  
Effective guardrails require continuous monitoring. AWS Budgets provides a dashboard to track actual and forecasted compute spend against our defined security thresholds.  

![AWS Budgets Dashboard](1.png)

**2. Standardized Deployment**  
Using predefined templates ensures rapid and accurate deployment of baseline alerts across new or isolated cloud accounts.  

![Choose Budget Template](2.png)

**3. Automated Incident Notification**  
The guardrail is configured to immediately push notifications to the security or operations team, minimizing the time to detect an anomaly.  

![Configure Notifications](3.png)

**4. Continuous Verification**  
Once deployed, the guardrail actively monitors the environment, ensuring continuous compliance with the established baseline.  

![Budget Created](4.png)
