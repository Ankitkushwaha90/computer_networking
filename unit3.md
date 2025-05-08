# Network Layer (For Cybersecurity)

## 1. Point-to-Point Networks

### 📌 Definition:
Direct connection between two network nodes (like router-router)

**Example:** PPP (Point-to-Point Protocol), serial links

### 🔒 Security Insight:
- Vulnerable to man-in-the-middle (MitM) attacks if not encrypted
- Ensure PPP over SSL/TLS in sensitive connections

## 2. Logical Addressing

### 📌 Role:
Assigns unique addresses to devices in a network  
IP addresses used to identify and route packets

### 🧩 Types:
- **IPv4:** 32-bit, e.g., 192.168.1.1
- **IPv6:** 128-bit, e.g., 2001:0db8::1

### 🔒 Cyber Tip:
- Attackers use IP spoofing to disguise source
- Use ingress filtering, deep packet inspection

## 3. Basic Internetworking Components

### a) IP (Internet Protocol)
- Connectionless, best-effort delivery
- Handles addressing and routing

**🔒 Security Concern:** IP header manipulation, spoofing

### b) CIDR (Classless Inter-Domain Routing)
- Removes old A/B/C class restrictions  
- Format: 192.168.1.0/24 (24 bits for network)

**🔒 Useful in:** subnetting detection, network reconnaissance

### c) ARP (Address Resolution Protocol)
- Resolves IP → MAC address  
- Local LAN communication  

**🔒 Vulnerability:** ARP Spoofing / Poisoning  
Attacker maps victim IP to their MAC  

**🔧 Tools:** arpspoof, ettercap, wireshark

### d) RARP (Reverse ARP)
- MAC → IP (rare now, replaced by DHCP)

### e) DHCP (Dynamic Host Configuration Protocol)
- Auto-assigns IP, subnet mask, gateway, DNS  

**🔒 Threats:**
- Rogue DHCP server: attacker assigns malicious configs  
- DHCP starvation: exhausts IP pool  

**🔧 Tools:** Yersinia, dhcpstarv

### f) ICMP (Internet Control Message Protocol)
- Used for diagnostics: ping, traceroute  

**🔒 Attacks:**
- ICMP Flood (Ping of Death)  
- ICMP Tunneling for hidden data exfiltration  

**🔧 Tools:** hping3, ncat, icmp-tunnel

## 4. Routing, Forwarding, Delivery

### 🔁 Routing:
Process of choosing best path for packet delivery

### 📤 Forwarding:
Act of sending packet to the next hop/router

### 🎯 Delivery:
Ensuring packet reaches correct destination host

**🔒 Security Tip:**  
Monitor for route hijacking, malicious BGP advertisements

## 5. Static and Dynamic Routing

### 🛠 Static Routing:
- Manually configured  
- Simple, less prone to manipulation, but not scalable  

**🔒 Used in small secure networks**

### ⚙ Dynamic Routing:
- Routers exchange info using protocols (RIP, OSPF, BGP)  

**🔒 Dynamic route updates can be intercepted or spoofed**

## 6. Routing Algorithms and Protocols

### a) Distance Vector Routing (e.g., RIP)
- Periodically advertises routes to neighbors  
- Uses hop count as metric  

**🔒 Susceptible to:**
- Route poisoning  
- Fake route injection  

### b) Link State Routing (e.g., OSPF)
- Full view of network  
- Calculates shortest path using Dijkstra  

**🔒 More secure than RIP, but still can be manipulated if unencrypted**

### c) Path Vector Protocols (e.g., BGP)
- Used in the Internet between ISPs  
- Maintains AS path info  

**🔒 BGP Hijacking:** attacker advertises wrong prefix (e.g., YouTube's 2008 outage)

## 7. Congestion Control Algorithms

### 🛣 Purpose:
Avoid overwhelming routers/networks with too much traffic

### 📦 Techniques:
| Technique | Description |
|-----------|-------------|
| Leaky Bucket | Fixed output rate |
| Token Bucket | Flexible, burst allowed if tokens available |
| RED (Random Early Detection) | Drop packets early to prevent overload |
| **TCP Congestion Control:** | |
| - Slow Start | |
| - Congestion Avoidance | |
| - Fast Retransmit | |
| - Fast Recovery | |

**🔒 Relevance in Security:**
- Flood attacks intentionally exploit congestion (e.g., SYN Flood)  
- Use rate-limiting, IDS/IPS, and anomaly detection  

## 8. IPv6 (Internet Protocol version 6)

### 🌐 Features:
- 128-bit address  
- Larger address space  
- Built-in IPSec  
- No ARP (uses NDP - Neighbor Discovery Protocol)  

**🔒 Security Points:**  
Still vulnerable to:  
- RA Spoofing (Router Advertisement)  
- NDP attacks  
- Transition mechanisms (like dual-stack) can be abused  

**🔧 Tools:** THC-IPv6, ipv6-toolkit

## Summary Table for Cybersecurity Use

| Component | Security Threat | Tool Example |
|-----------|----------------|-------------|
| ARP | ARP spoofing | arpspoof, ettercap |
| DHCP | Rogue server, starvation | Yersinia, dhcpstarv |
| ICMP | Flood, tunneling | hping3, icmp-tunnel |
| RIP/OSPF | Fake routes | Scapy, Yersinia |
| BGP | Hijacking | BGPmon, bgpstream |
| IP | Spoofing, fragmentation | Scapy, nmap |
| Congestion | DoS via flooding | LOIC, HOIC, hping |
