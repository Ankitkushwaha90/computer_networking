# Networking Basics for Cybersecurity

## 1. Goals and Applications of Networks

### 🌐 Goals:
- Resource Sharing (e.g., files, printers)
- Communication (e.g., email, VoIP, video conferencing)
- Access to Remote Information (web browsing, FTP)
- Centralized Management & Control (for admins/security)
- Reliability & Fault Tolerance

### ⚔️ Cybersecurity Focus:
- Understand attack surfaces in each service (e.g., DNS poisoning, email spoofing)
- Secure communication channels (TLS, VPNs)
- Monitor shared resources for misuse

## 2. Categories of Networks

| Category | Description                | Example               |
|----------|----------------------------|-----------------------|
| PAN      | Personal Area Network      | Bluetooth, USB tethering |
| LAN      | Local Area Network         | Home/Office network   |
| MAN      | Metropolitan Area Network  | City-wide Wi-Fi       |
| WAN      | Wide Area Network          | Internet              |
| CAN      | Campus Area Network        | University network    |
| SAN      | Storage Area Network       | Data center storage   |
| VPN      | Virtual Private Network    | Secure remote access  |

### 🔒 Security Implication:
Each network type has different threats and mitigation strategies (e.g., LAN = ARP spoofing; WAN = DDoS attacks)

## 3. Organization of the Internet

### Structure:
- End Systems (Clients/Servers)
- Routers (Forward packets)
- ISPs (Provide Internet access)
- Backbone Networks (High-capacity networks interconnecting ISPs)
- IXPs (Internet Exchange Points)

### Layers of Participation:
- Tier-1 ISPs: Direct access to internet backbone
- Tier-2 ISPs: Buy access from Tier-1
- Tier-3 ISPs: Provide last-mile access to end-users

## 4. ISP (Internet Service Provider)
- Provides connectivity to the internet
- Assigns IP addresses
- May offer DNS, email, proxy, and firewall services
- Logs traffic (important for cybersecurity investigations)

## 5. Network Structure & Architecture

### 💡 Layering Principles:
- Break network functionality into layers
- Each layer offers services to the layer above
- Each layer hides implementation details

### 📶 Services:
- Connection-oriented (e.g., TCP)
- Connectionless (e.g., UDP)

### 📜 Protocols:
Set of rules governing data communication (e.g., HTTP, FTP, DNS)

### 🏛 Standards:
Ensure interoperability (defined by IEEE, IETF, ITU)

## 6. The OSI Reference Model (7 Layers)

| Layer | Name          | Function                 | Example          |
|-------|---------------|--------------------------|------------------|
| 7     | Application   | User interface           | HTTP, SMTP       |
| 6     | Presentation  | Data format, encryption  | SSL/TLS          |
| 5     | Session       | Dialog control           | NetBIOS, RPC     |
| 4     | Transport     | Reliable delivery        | TCP, UDP         |
| 3     | Network       | Logical addressing, routing | IP             |
| 2     | Data Link     | MAC addressing           | Ethernet, ARP    |
| 1     | Physical      | Bit transmission         | Cables, radio signals |

## 7. TCP/IP Protocol Suite

| Layer        | Protocols          | Security Consideration       |
|--------------|--------------------|------------------------------|
| Application  | HTTP, DNS, SMTP    | XSS, DNS Spoofing            |
| Transport    | TCP, UDP           | Port scanning, SYN floods    |
| Internet     | IP, ICMP           | IP Spoofing                  |
| Link         | ARP, Ethernet      | MAC spoofing, ARP poisoning  |

## 8. Network Devices & Components

| Device       | Function                | Security Notes                  |
|--------------|-------------------------|---------------------------------|
| Router       | Directs traffic         | Can be exploited (default creds)|
| Switch       | Connects devices at layer 2 | Target for MAC flooding     |
| Hub          | Broadcasts data         | Not secure (no segmentation)    |
| Modem        | Modulates signals       | Entry point to ISP             |
| Firewall     | Filters traffic         | First line of defense          |
| Access Point | Wireless access         | Must be encrypted (WPA2/3)     |

## ⚙️ Physical Layer

## 9. Network Topology Design

| Topology | Description               | Use-Case              |
|----------|---------------------------|-----------------------|
| Bus      | Single backbone           | Simple, outdated     |
| Star     | Central device (switch)   | Common in LAN        |
| Ring     | Circular path             | Token Ring           |
| Mesh     | Redundant links           | High availability    |
| Hybrid   | Combo of above            | Scalable             |

## 10. Types of Connections
- **Point-to-Point**: One-to-one link (e.g., direct cable)
- **Multipoint**: Shared link (e.g., broadcast)
- **Unicast / Multicast / Broadcast** (Logical types)

## 11. Transmission Media

| Media         | Type     | Example          | Security Concerns            |
|---------------|----------|------------------|------------------------------|
| Twisted Pair  | Wired    | Ethernet         | Easy to tap physically       |
| Coaxial Cable | Wired    | Cable TV         | Interference                 |
| Optical Fiber | Wired    | Long distance    | More secure, expensive       |
| Radio Waves   | Wireless | Wi-Fi            | Sniffing                     |
| Infrared      | Wireless | Remote controls  | Short range                  |
| Microwave     | Wireless | Satellite        | High latency                 |

## 12. Signal Transmission and Encoding
- Analog vs Digital signals
- Modulation Techniques: AM, FM, PM
- Encoding Schemes: NRZ, Manchester, 4B/5B
- Bandwidth and bitrate affect data rate and noise resistance

## 13. Network Performance and Transmission Impairments

### Metrics:
- Bandwidth (Max rate of data)
- Throughput (Actual data transfer rate)
- Latency (Delay in transmission)
- Jitter (Variation in delay)
- Error Rate

### Impairments:
- Attenuation: Signal loss
- Noise: Unwanted signals
- Distortion: Signal shape change
- Interference: Overlapping signals

## 14. Switching Techniques and Multiplexing

### ➿ Switching:

| Type    | Description         | Example |
|---------|---------------------|---------|
| Circuit | Dedicated path      | PSTN    |
| Packet  | Data in packets     | Internet|
| Message | Whole message sent  | Older systems |

### 🔀 Multiplexing:

| Type | Description        | Example      |
|------|--------------------|--------------|
| FDM  | Frequency          | TV channels  |
| TDM  | Time slots         | Telephone    |
| WDM  | Light wavelength   | Optical fiber|
| CDM  | Code               | Wireless     |

## 🛡 Why It Matters for Cybersecurity
- Each layer has threats (e.g., ARP spoofing at Data Link, IP spoofing at Network, SYN flood at Transport)
- Knowing topology helps defend (Star vs Mesh resilience)
- Signal/media vulnerabilities (Sniffing, tapping, jamming)
- Understand protocols to exploit or defend (e.g., DNS, TCP handshake)
- Switching and multiplexing affect packet inspection, IDS placement
