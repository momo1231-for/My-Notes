## Overview
Authorization (AuthZ) in Oracle Cloud Infrastructure (OCI) determines what actions are allowed on cloud resources and who is allowed to perform them. Unlike [*authentication (AuthN) in OCI*](https://github.com/momo1231-for/My-Notes/blob/main/Cloud/Oracle/Oracle%20Cloud%20Infrastructure%20(OCI)%20-%20Authentication%20(AuthN).md), which verifies identity, authorization is about permissions and access control. OCI handles AuthZ using a powerful and flexible IAM policy framework that works across compartments, identity domains, and tenancy-wide configurations.
## How OCI Authorization Works
Access control in OCI is policy-driven. Every API call made to a resource is evaluated against the active IAM policies to determine whether the request is allowed or denied. Policies are written in a human-readable format and define what groups can do what actions on which resources, in which compartments.
####  Policy Syntax Simple Example: 
Allow **group DevOps** to **manage instances** in compartment **Project-X**.<p style="margin-bottom: 15px;">Which means anyone in the DevOps group of users can manage (create, update, delete, or read) compute instances in the Project-X compartment.
## Key Concepts of Policies
1. **Access Rules:** These are text-based rules that define who can access what and at what permission level. They can be written at the **tenancy**, **compartment**, or **domain level**. They use certain verbs as conditions like:.<p style="margin-bottom: 15px;">**Inspect** - Which allows a user to only view *metadata*<br/>**Read** - Which enables a user to do everything that can be done with "inspect" and *get the data* but does not allow for interaction.<br/>**Use** - Which enables a user to do everything that can be done with "read" and allows interaction, which means connecting the resource to other resources but can't modify the resource itself.<br/>**Manage** - Which gives full access to a resource.
2. **Compartments:** Policies are compartment-aware, meaning access can be scoped down to a specific project, environment, or team. Multiple policies can be written to reflect an organization's access structure. So an organization needs to put workloads into well-defined compartments, or it would be harder to implement proper access control.
3. **Groups:** Users are added to groups. Policies should only grant access to groups, and never directly to a user; that is why it's important for an organization to properly map out its access control strategy.
## Benefits of OCI Authorization
1. **Granular Access Control:** Define permissions at the level of actions, resources, and compartments.
2.  **Human-Readable Policies:** Easy to understand and audit.
3.  **Scalable:** Works across complex multi-tier environments.
4.  **Modular and Reusable:** Combine with compartments and groups for flexible access models.
## Best Practices
1. Assign permissions to groups, not individuals.
2. Use least privilege: Only grant the minimum permissions required for a person to perform their work activities.
3. Scope policies to specific compartments instead of tenancy-wide, wherever possible.
4. Break down large policies into smaller, role-specific ones for better manageability.
5. Combine with Identity Domains and Compartments to create secure, isolated access boundaries.
