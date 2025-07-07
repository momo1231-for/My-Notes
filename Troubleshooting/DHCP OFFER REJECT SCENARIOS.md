# **DHCP OFFER REJECT SCENARIOS**
A client may reject a **DHCP (Dynamic Host Configuration Protocol) offer** in some special cases. Here are the primary scenarios:

### **1. Duplicate IP Detection (DAD) Failure**
- The client might send out a quick check — like an ARP or a ping — to see if the IP address it was offered is already being used by someone else.

- If it gets a reply (meaning someone else is using that IP), it rejects the offer and lets the DHCP server know by sending a **DHCP Decline** message.

### **2. Offer Doesn’t Meet Client Requirements**

- The offer might be missing important details like the default gateway, DNS server, or other settings the client needs.
    
- Or the lease time for the IP might be too short or not what the client expects.
    If the offer packet is broken, the client sees it as invalid and just ignores it.

### **3. Client Already Has a Better Lease**

- If the client already has an IP lease from a different network and still thinks it's valid, it might ignore the new offer and stick with the old one.

### **4. Multiple DHCP Offers – Chooses Another**

- If more than one DHCP server replies, the client picks just one offer — usually the first one it gets or the one that fits best.
    
- It ignores the rest by simply not responding to them.
  

### **5. Policy or Security Filtering**

- Some devices have security settings that block offers from unknown or untrusted DHCP servers — like when rogue DHCP detection or certain network policies are turned on.

### **7. Static IP Configuration**

- If the device is set up with both DHCP and a static IP, it might choose the static one and ignore any offers from the DHCP server(mind you this is quite rare)

### **8. MAC Address Filtering or Spoofing Detection**

- In some setups, each device is expected to have a specific IP based on its MAC address. If the DHCP offer doesn’t match what’s expected, the client or network might reject it.
