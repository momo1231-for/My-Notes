# Overview
Oracle Cloud Infrastructure (OCI) provides **Availability Domains (ADs)** to ensure **high availability**, **fault isolation**, and **resilient architecture** for cloud workloads. Understanding Availability Domains is crucial for designing fault-tolerant systems in OCI.
## What is an Availability Domain?
An **Availability Domain** is a **physically isolated data center** within a region. Each AD is designed to be highly reliable, independent of failures in other ADs, and interconnected through **low-latency, high-bandwidth networks**
## Architecture Layout
- All ADs within a region share the same **identity**, **networking**, and **object storage**.
- **Cross-AD latency is very low**, so you can run distributed applications efficiently.
## Benefits of Using Availability Domains
- **Fault Isolation:** Hardware failure in one AD doesn’t affect others.
- **High Availability:** Deploy across multiple ADs for redundancy.
- **Scalability:** Distribute workloads across ADs for better resource management.
- **Disaster Recovery:** Design DR architectures within the same region using different ADs.
## Use Cases
- **Highly Available Applications**: Deploy multiple instances across ADs behind a load balancer.
- **Database Replication**: Use Autonomous Database or Oracle Data Guard across ADs for resilience.
- **Scalable Storage**: Use block volumes and distribute across ADs for performance and reliability.
- **In-region Disaster Recovery**: Planned failover to another AD in case of outages.
## Best Practices
- Use [**Fault Domains**](https://github.com/momo1231-for/My-Notes/blob/main/Cloud/Oracle/Oracle%20Fault%20Domains.md) within an AD to further isolate failure risks at the hardware rack level.
- Combine **AD-aware deployment** with **region-based** redundancy for stronger DR plans.
- [**Leverage Oracle Data Guard**](https://github.com/momo1231-for/My-Notes/blob/main/Cloud/Oracle/Oracle%20Data%20Guard.md) to replicate databases across Availability Domains (or even across regions) for automated failover and zero-data-loss recovery.
- Always verify the **number of ADs available** in a region, as some have only one (especially newer or smaller regions).
