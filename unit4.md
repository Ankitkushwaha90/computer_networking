# Transport Layer (For Cybersecurity)

## 1. Process-to-Process Delivery

### 📌 Definition:
Unlike the Network layer (host-to-host), Transport layer ensures data is delivered from one process to another using port numbers.

### 🧩 Example:
- Web server process listens on port 80
- DNS service uses port 53

### 🔒 Security Note:
- Attackers scan for open ports to identify running services (nmap, masscan)
- Use firewalls and port-knocking for protection

## 2. Transport Layer Protocols

### a) UDP (User Datagram Protocol)
- Connectionless, lightweight
- No delivery guarantee, ordering, or congestion control

**🔒 Vulnerabilities:**
- Used in UDP flood attacks, DNS amplification, reflection attacks
- Lacks authentication; monitor suspicious high-rate traffic

**🔧 Tools:** `hping3`, `nmap -sU`

### b) TCP (Transmission Control Protocol)
- Connection-oriented, reliable
- Ensures packet ordering, retransmission, flow control, congestion control

**🔒 Attack Surface:**
- TCP SYN Floods, session hijacking, RST injection
- Packet crafting tools like Scapy, Ettercap

## 3. Multiplexing & Demultiplexing

### 🧠 Concept:
- **Multiplexing:** Multiple processes share one network link (assign port numbers)
- **Demultiplexing:** Receiving system maps data to correct process

**🔒 Cyber Use:**
- Used in reverse shells and covert channels
- Monitor abnormal port usage

## 4. Connection Management (TCP 3-Way Handshake)

### 🚦 Steps:
1. `SYN` → Initiate  
2. `SYN-ACK` → Acknowledge  
3. `ACK` → Confirm connection  

**🔒 Vulnerability:**
- **SYN Flood Attack:** Send multiple SYNs but never ACK → exhaust server resources

**🔧 Defense:**
- SYN cookies
- Firewalls
- Rate limiting

## 5. Flow Control & Retransmission

### 🔁 Flow Control:
- Prevents sender from overwhelming receiver
- Achieved via TCP sliding window mechanism

### 🔄 Retransmission:
- Lost packets are re-sent (based on ACK timeout or duplicate ACKs)

**🔒 Security Insight:**
- ACK spoofing can cause desynchronization
- IDS can detect anomalous retransmissions

## 6. Window Management

### 📦 TCP Sliding Window:
- Controls how much data is sent before requiring an ACK
- Allows for efficient and controlled transmission

**🔒 Implication:**
- Improper tuning may lead to buffer overflow attacks
- Can be exploited for side-channel attacks (timing-based)

## 7. TCP Congestion Control

### 📊 Mechanisms:
| Mechanism | Description |
|-----------|-------------|
| Slow Start | Begin with low rate, increase exponentially |
| Congestion Avoidance | Linear growth |
| Fast Retransmit | Retransmit after 3 duplicate ACKs |
| Fast Recovery | Adjust window without full restart |

**🔒 Use in Defense:**
- Flood detection systems check for congestion anomalies
- QoS policies can enforce thresholds

## 8. Quality of Service (QoS)

### 📌 Purpose:
- Prioritize important traffic (VoIP, real-time apps)
- Manage latency, jitter, bandwidth

**🔒 Security Benefit:**
- Helps detect anomalies (e.g., unexpected priority traffic)
- Avoid misuse of DSCP bits for covert channels

## Summary Table for Cybersecurity Analysis

| Concept | Role | Security Relevance | Tools |
|---------|------|--------------------|-------|
| UDP | Fast, no ACK | Reflection, DoS, scanning | nmap, hping3 |
| TCP | Reliable, ACK-based | SYN Flood, Hijacking | Wireshark, Scapy |
| Port numbers | Identify services | Port scanning, RCE vectors | nmap, masscan |
| Flow control | Avoid buffer overflow | Exploitable via packet manipulation | Ettercap |
| Congestion control | Manage traffic | Flood protection, anomaly detection | tcpdump |
| QoS | Prioritize traffic | Abuse for covert traffic | tc, Wireshark |

## Real-World Cybersecurity Use Cases

- 🔍 **Sniffing TCP Handshakes** to detect SYN Floods
- 🔒 **Detecting Covert Channels** via odd QoS or UDP usage
- 🛡 **Building Firewalls** using transport-layer rules (TCP/UDP ports)
- 🕵️‍♂️ **Session Hijacking** via TCP sequence number prediction
- 🧠 **Machine Learning IDS** using TCP window size, flags, and retransmissions
