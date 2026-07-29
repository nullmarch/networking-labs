# Networking Labs — Cisco Packet Tracer

A collection of hands-on networking labs built in Cisco Packet 
Tracer covering VLANs, trunking, dynamic routing, remote access, 
and WAN addressing.

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

## Lab 2 — OSPF Dynamic Routing

<img width="1893" height="710" alt="ospf-topology" src="https://github.com/user-attachments/assets/d3666924-61c8-4ffe-a369-99e962626184" />

### Topology
- 3x Cisco 1941 Routers
- 2x Cisco 2960-24TT Access Switches
- 4x End devices (PC0-PC3)

### Network Addressing
- `172.20.1.0/24` — Left LAN
- `10.12.0.0/24` — WAN link Router0 to Router1 (serial)
- `10.23.0.0/24` — Link Router1 to Router2
- `172.20.3.0/24` — Right LAN

### Concepts Demonstrated
- OSPF dynamic routing protocol — routers automatically 
  share routing information
- Serial WAN links between routers
- Multiple network segments routed through OSPF
- End-to-end connectivity across three routers

### What I Learned
- OSPF automatically discovers routes — no manual static 
  route configuration needed
- Each router advertises its directly connected networks 
  to OSPF neighbors
- Serial links simulate WAN connections between sites
- Routers in the same OSPF area share a complete topology map

## Lab 3 — Remote Access (SSH and Telnet)

<img width="1900" height="717" alt="ssh-telnet-topology" src="https://github.com/user-attachments/assets/2d20cb3f-c194-4c7e-b1e3-847562d3c4c9" />

### Topology
- 3x Cisco 3560-24PS Multilayer Switches
- 6x End devices (PC0-PC5)
- Trunk links between central and edge switches

### Concepts Demonstrated
- Telnet configuration for remote device management
- SSH configuration for secure remote access
- Difference between Telnet (plain text) and SSH (encrypted)
- Remote CLI access to network devices from end hosts

### What I Learned
- Telnet transmits credentials in plain text — 
  vulnerable to interception
- SSH encrypts the entire session — industry standard 
  for secure remote management
- Both require VTY line configuration on the device
- SSH requires a hostname, domain name, and RSA key 
  to be generated before it works

  ## Lab 4 — Manual IP Addressing vs DHCP

<img width="1902" height="713" alt="dhcp-wan-topology" src="https://github.com/user-attachments/assets/965213cd-3f1a-4c06-9252-85cdfa39934c" />


### Topology
Three geographically named sites connected via WAN serial links 
through a hub router (OR):

- **Réseau 1 (172.16.0.0/24)** — Site SB, PC A
- **Réseau 2 (172.16.1.0/24)** — Site TL, PC C  
- **Réseau 3 (172.16.2.0/24)** — Site AL, PC B
- **Internet** — simulated via dedicated router

**WAN serial links using /30 subnets:**
- `10.10.10.0/30` — SBA to OR
- `10.10.10.4/30` — TL to OR
- `10.10.10.8/30` — OR to AL
- `10.10.10.12/30` — AL to Internet

### Two Versions of This Lab

**Version 1 — Manual Addressing:**
Static IP addresses configured manually on every device — 
each PC, router interface, and switch assigned fixed addresses.

**Version 2 — DHCP:**
Router configured as DHCP server, automatically assigning 
IP addresses to end devices on each LAN.

### Why /30 on Serial Links
Serial links connect exactly two router interfaces — 
no other hosts will ever exist on that segment. /30 
provides exactly 2 usable host addresses, wasting 
the minimum number of addresses.

### Concepts Demonstrated
- Static IP addressing vs dynamic DHCP assignment
- WAN topology with hub-and-spoke design
- Serial link subnetting with /30 masks
- DHCP server configuration on a router
- Multi-site routing across WAN links

### What I Learned
- Manual addressing gives full control but doesn't scale — 
  every device needs individual configuration
- DHCP eliminates manual configuration — devices request 
  and receive addresses automatically
- /30 subnets are specifically chosen for point-to-point 
  links to minimize address waste
- Router DHCP pools must exclude the router's own interface 
  address to avoid conflicts
