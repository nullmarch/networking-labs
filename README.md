# Networking Labs — Cisco Packet Tracer

A collection of hands-on networking labs built in Cisco Packet 
Tracer covering VLANs, trunking, dynamic routing, and remote access.

---

## Lab 1 — VLAN and Trunking

<img width="1896" height="712" alt="vlan-trunking-toplogy" src="https://github.com/user-attachments/assets/4be1273e-5fd6-408d-bffd-8eab684b0a18" />

### Topology
- 1x Cisco 1941 Router
- 1x Cisco 3560-24PS Multilayer Switch (inter-VLAN routing)
- 4x Cisco 2960-24TT Access Switches
- 17 end devices distributed across access switches

### Concepts Demonstrated
- VLAN segmentation — grouping devices into isolated networks
- 802.1Q trunking — carrying multiple VLANs across switch links
- Inter-VLAN routing via multilayer switch
- Hierarchical star topology — core, distribution, and access layers
- Trunk links between switches (dashed lines in topology)

### What I Learned
- VLANs isolate traffic at Layer 2 without physical separation
- Trunk links must be configured on ports connecting switches 
  to carry multiple VLANs simultaneously
- A multilayer switch can route between VLANs without a 
  dedicated router
- Hierarchical design improves scalability and fault isolation

---

