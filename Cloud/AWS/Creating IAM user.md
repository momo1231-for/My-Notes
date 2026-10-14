## What is an IAM User?

An IAM user is a specific identity you create within your AWS account to represent a person or an application.

Think of the root account as the building owner holding a master key to every single room. In contrast, an IAM user is like an employee given a blank keycard. By default, they cannot open any doors. You must attach specific permission policies to tell AWS exactly which rooms they are allowed to enter.

### Identity and Access Management: Moving Away from Root

Using the root account for daily work is dangerous. The root user has unrestricted, irrevocable access to all resources and billing, meaning a compromised root password could lead to total account takeover and catastrophic costs.

By creating a dedicated user with functional permissions, we build a secure working environment. This aligns with the cybersecurity principle of least privilege, ensuring the user only has the exact permissions necessary to perform their required tasks.

#### Step-by-Step Implementation

**1. Verifying a Clean Slate**
We start by navigating to the AWS Identity and Access Management (IAM) dashboard, confirming that no users currently exist in the environment.

![Verifying a Clean Slate](https://github.com/momo1231-for/Post-Images/blob/main/Cloud/AWS/Creating%20an%20IAM%20user/1.png)

**2. Defining the User Identity**
We initialize a new IAM user and configure their console login parameters, assigning a secure custom password while mandating a password reset upon their first login.

![Defining the User Identity](https://github.com/momo1231-for/Post-Images/blob/main/Cloud/AWS/Creating%20an%20IAM%20user/2.png)

**3. Enforcing Least Privilege**
Instead of granting broad administrative rights, we attach specific, restricted policies directly to the user to match their exact functional requirements.

![Enforcing Least Privilege](https://github.com/momo1231-for/Post-Images/blob/main/Cloud/AWS/Creating%20an%20IAM%20user/3.png)

**4. Reviewing Configurations**
Before provisioning the identity, we review the user details and the specific permissions summary to ensure no excess privileges have been accidentally assigned.

![Reviewing Configurations](https://github.com/momo1231-for/Post-Images/blob/main/Cloud/AWS/Creating%20an%20IAM%20user/4.png)

**5. Securing the Credentials**
Upon successful creation, AWS generates the unique Console sign-in URL and provides the initial login credentials. These must be captured and stored securely.

![Securing the Credentials](https://github.com/momo1231-for/Post-Images/blob/main/Cloud/AWS/Creating%20an%20IAM%20user/5.png)

**6. Confirming the New Identity**
Finally, we verify that the new dedicated user is actively listed in the IAM dashboard, completely separate from the root account.

![Confirming the New Identity](https://github.com/momo1231-for/Post-Images/blob/main/Cloud/AWS/Creating%20an%20IAM%20user/6.png)
