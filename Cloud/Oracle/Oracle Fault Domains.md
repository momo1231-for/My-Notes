# Overview
When it comes to the cloud, fault tolerance is key. You want your apps and services to stay online, even if hardware fails behind the scenes; if not, what's the point? That’s where Fault Domains (FDs) come in.Fault Domains help improve availability and reduce the risk of failure by logically isolating resources within an [**Availability Domain**](https://github.com/momo1231-for/My-Notes/blob/main/Cloud/Oracle/Oracle%20Availability%20Domains.md)(AD). They give you another layer of protection without needing to change your architecture drastically.

What Is a Fault Domain?
A Fault Domain (FD) is a logical group of hardware within a single Availability Domain. Each AD typically contains three Fault Domains, each on a separate physical infrastructure, meaning different power sources, servers, and network equipment.

You can think of Fault Domains as separate “zones” inside a data center. By placing resources in different FDs, you’re spreading your workloads out in a way that helps limit the blast radius if something goes wrong.

How It’s Structured
Each Availability Domain includes three Fault Domains by default.

Resources in different FDs are physically isolated, reducing single points of failure.

You can manually specify which FD to use when creating certain resources (like compute instances or DB systems).

OCI also allows automatic distribution across FDs when you launch multiple instances.
Why Use Fault Domains?
Here’s what you get by using Fault Domains the right way:

Hardware Isolation
A failure in one server, rack, or power circuit won’t take down everything.

Higher Uptime
Distribute workloads across FDs to minimize service impact from localized issues.

Load Balancing
Avoid overloading a single rack or power source—FDs help balance resources physically, not just logically.
Common Use Cases
Web/App Tiers:
Spread app servers across all FDs in an AD to ensure one FD going down doesn't take your service offline.

Database Redundancy:
Run Oracle RAC nodes or Data Guard standby/observer across different FDs for better high availability.

Backend Pools:
In Load Balancer configs, place backend compute instances in separate FDs to improve fault tolerance.

Maintenance Awareness:
OCI schedules some maintenance activities by FD, which means spreading across FDs reduces chances of downtime during planned maintenance.

Best Practices
Pair Fault Domains with Availability Domains for a more robust design.

Spread critical workloads evenly across all three FDs in an AD.

Use Data Guard or RAC across FDs to ensure failover capabilities if one FD fails.

Automate deployments using tools like Terraform or OCI CLI—make FD placement part of your scripts.

Test failure scenarios regularly to validate your fault tolerance strategy.

 Important Note
While Fault Domains offer physical isolation within an Availability Domain, they don’t protect you from an AD-level outage. If something major (like a natural disaster) affects the entire AD, all the FDs in that AD are affected too.
Use FDs to protect against local hardware failures, but for true disaster recovery, always replicate across multiple Availability Domains (or even regions, depending on your needs).
