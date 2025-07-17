## Overview 
A Virtual Cloud Network (VCN) in OCI acts like a customizable, private data center in the cloud. It’s where compute instances, databases, and services get connected. Which, in a sense, is the backbone for building secure and scalable network architectures in Oracle Cloud.<p style="margin-bottom: 15px;">A VCN spans an entire region (with the [**ADs**](https://github.com/momo1231-for/My-Notes/blob/main/Cloud/Oracle/Oracle%20Availability%20Domains.md) within) and can include multiple subnets, either public (exposed to the internet) or private (internal-only). Setting up a good VCN is usually one of the first steps in any cloud deployment.</p>
## Key Components
**Internet Gateway**<p style="margin-bottom: 15px;">Allows resources in a public subnet to connect directly to the internet. Typically used for web servers or jump boxes.</p><p style="margin-bottom: 15px;">**NAT Gateway**</p><p style="margin-bottom: 15px;">This enables private subnet resources to access the internet outbound (e.g., software updates) without being exposed to incoming internet traffic. A safer way to give internet access without making instances publicly available to traffic.</p><p style="margin-bottom: 15px;">**Service Gateway**</p><p style="margin-bottom: 15px;">Used for private access to Oracle services (like Object Storage or Autonomous DB) without routing through the internet. Keeps traffic on Oracle’s private backbone, a more secure and faster way to route with OCI services but does have it's drawbacks which was addressed by DRGv2.</p><p style="margin-bottom: 15px;">**Dynamic Routing Gateway (DRG)**</p><p style="margin-bottom: 15px;">Acts as the network hub for on-premises to cloud connections. Connects a VCN to:</p><p style="margin-bottom: 15px;">FastConnect (dedicated, high-speed physical private link)</p><p style="margin-bottom: 15px;">Site-to-Site VPN (IPSec tunnel over the internet)</p><p style="margin-bottom: 15px;"><p style="margin-bottom: 15px;">**DRGv2 (Dynamic Routing Gateway Version 2)**</p><p style="margin-bottom: 15px;">With DRGv2, the connectivity model gets more flexible and modular. Supporting attachments (VCNs, remote peering, FastConnect, VPN, etc.) and route tables per attachment, allowing tighter control over traffic paths. DRGv2 makes it easier to route traffic between multiple VCNs (with a limit of 300 VCNs to one router) or across regions without complex workarounds. It's like building a full-blown software-defined network inside OCI.</p>
## Route Tables 
Route Tables determine where network traffic should go. Each subnet is associated with a route table that defines how outbound traffic is handled. Routes can direct traffic to: Internet Gateway, NAT Gateway, Service Gateway, and DRG (including DRGv2 attachments).<br/>Without a proper route, traffic just never reaches a destination.
## Security Lists
Security Lists work like stateless firewalls at the subnet level. They define what inbound and outbound traffic is allowed. Every subnet can be tied to a security list, and rules are applied to all resources in that subnet.<p style="margin-bottom: 15px;">Rules are simple: IP protocol, source/destination CIDR, port range. But they apply to everything in the subnet equally.</p>
## Network Security Groups (NSGs)
For more granular control, Network Security Groups allow resource-level security. Similar to security lists but targeted—great for grouping related instances (e.g., web tier, app tier) and controlling traffic between groups, not just in/out of a subnet.<p style="margin-bottom: 15px;">NSGs make it easier to apply rules that follow application logic instead of broad subnet-level rules.</p>
## Important Takeaways
- VCN is the foundation of networking in OCI.

- Use Internet Gateway for public access, NAT Gateway for safe outbound traffic from private subnets.

- Service Gateway keeps Oracle service access private.

- DRG connects on-prem to OCI.

- DRGv2 adds advanced routing with per-attachment control and multi-VCN support.

- Route Tables handle traffic directions.

- Security Lists are basic subnet firewall rules.

- NSGs are flexible, instance-level traffic control.
