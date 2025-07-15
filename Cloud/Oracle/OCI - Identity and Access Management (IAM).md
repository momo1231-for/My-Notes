## Overview
**Identity and Access Management** is an important part of cloud security, as it directly combats one of the pillars in the **CIA** triad, which is the **Confidentiality** pillar. It is also the responsibility of every organization to properly define (**AuthZ**) and manage [(**AuthN**)](https://github.com/momo1231-for/My-Notes/blob/main/Cloud/Oracle/Oracle%20Cloud%20Infrastructure%20(OCI)%20-%20Authentication%20(AuthN).md) their access control.<p style="margin-bottom: 15px;">Understanding core identity concepts is essential for managing users, access policies, and resource organization across environments. OCI takes a structured approach using identity domains, compartments, and resource identifiers to provide enterprise-grade control.</p>
## OCI Identity Concepts
### Identity Domains
An Identity Domain is a dedicated space for managing users, groups, and authentication within OCI. Each identity domain can have its own set of users, groups, and policies.
### Compartments
Compartments are logical containers used to organize and isolate cloud resources. They help group related resources (like all compute, network, and storage for a particular application) and control access to them using IAM policies. 
#### Key Features of Compartments
Six levels of nesting are supported, meaning it allows for up to six levels of putting compartments within each other, allowing a tree-like hierarchy of compartments for scalable organization. Quotas and budgets can be applied to control usage within a compartment. Policies can be assigned at any level to define who can access what.
### Resources and OCIDs
In OCI, almost everything is a resource—compute instances, block volumes, networks, buckets, etc. Each resource is assigned a unique identifier called an Oracle Cloud Identifier (OCID). An OCID is a globally unique ID used to reference any resource in OCI. OCIDs are critical when using automation tools (CLI, SDKs, Terraform) or writing policies, as they provide precise references to specific resources across regions, compartments, and domains.
## Best Practices
1. Use Identity Domains to separate users and policies by project or environment (e.g., Dev, QA, Prod).
2. Reference OCIDs in scripts and policies for accurate targeting.
3. Structure Compartments logically—by team, project, or service—and nest them to reflect organizational hierarchy.
4. Apply quotas and budgets to control resource usage within compartments.
5. Combine compartments with IAM policies to implement least-privilege access.
