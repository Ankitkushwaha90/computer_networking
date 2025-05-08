# Link Layer & MAC Layer (For Cybersecurity)

## 1. Framing

### � What is Framing?
Framing is the process of dividing the data stream into manageable chunks called frames for transmission over the network.

### 🛠 Functions:
- Frame delimiter detection
- Addressing at MAC level
- Error detection via checksum
- Frame synchronization

### 🧑‍💻 Common Techniques:
| Technique | Description |
|-----------|-------------|
| Character Count | Frame = byte count |
| Flag Bytes with Byte Stuffing | Special flags added; escaped if in data |
| Bit Stuffing | Insert 0 after 5 consecutive 1s |
| Physical Layer Coding Violations | |

### 🔒 Security Notes:
- Frame-level manipulation can be exploited (e.g., injecting crafted Ethernet frames)
- Protocols like 802.1X ensure secure frame authentication

## 2. Error Detection and Correction

### 🔍 Error Detection:
Used to detect corruption in data during transmission.

**Techniques:**
- **Parity Bit**: Adds 1-bit to make even/odd parity
- **Checksum**: Sum of all bytes (used in TCP/IP)
- **CRC (Cyclic Redundancy Check)**: Powerful polynomial division (used in Ethernet)

### 🛠 Error Correction:
Allows correction without retransmission.

**Techniques:**
- Hamming Code
- Reed-Solomon (used in CDs, Wi-Fi)

### 🔒 Cybersecurity Relevance:
- Attacks may tamper with checksums or bypass CRC mechanisms
- Data integrity checks critical in forensics and malware detection

## 3. Flow Control

### ⚙ Purpose:
Ensure that sender doesn't overwhelm the receiver.

### a) Elementary Data Link Protocols

| Protocol | Description |
|----------|-------------|
| Stop-and-Wait | Sender waits for ACK before next frame |
| Noisy/Noiseless Channels | Models with/without errors in transmission |
| ACK/NACK | Acknowledgement or Negative Acknowledgement |

### b) Sliding Window Protocols
Allows multiple frames to be sent before needing ACKs. Used in TCP.

**Key Concepts:**
- Sender Window: Frames sent but not yet acknowledged
- Receiver Window: Frames expected
- Window Size: Number of outstanding frames allowed

**Types:**
- Go-Back-N: Resend from error frame onward
- Selective Repeat: Resend only erroneous frames

### 🔒 Security Insight:
Understanding these helps in detecting TCP attacks like ACK storm, sequence number prediction, and DoS via flood of frames

## Medium Access Control (MAC) & LANs

## 4. Channel Allocation

**Techniques:**
- Static Allocation: Fixed slot/channel per station (e.g., FDM, TDM)
- Dynamic Allocation: On-demand access (used in LANs)

## 5. Multiple Access Protocols

| Protocol | Description | Notes |
|----------|-------------|-------|
| ALOHA | Send at any time; retry on collision | High collision rate |
| Slotted ALOHA | Send in slots | Improved throughput |
| CSMA | Sense channel before sending | |
| CSMA/CD | With collision detection (used in Ethernet) | |
| CSMA/CA | Collision avoidance (used in Wi-Fi) | |
| Token Passing | Token circulates; only holder transmits | |
| Polling | Central controller polls nodes | |

### 🔒 Cybersecurity Implications:
- Jamming and collision-based DoS can exploit these protocols
- MAC spoofing or replay attacks possible in weakly authenticated systems

## 6. LAN Standards

| Standard | Description |
|----------|-------------|
| IEEE 802.3 | Ethernet (wired LAN) |
| IEEE 802.11 | Wi-Fi (wireless LAN) |
| IEEE 802.1Q | VLAN tagging |
| IEEE 802.1X | Port-based authentication (used in secure enterprise LANs) |

### 🔒 Tip:
Secure LANs use 802.1X + RADIUS servers to authenticate devices before granting access.

## 7. Link Layer Switches & Bridges

### a) Switch:
- Works at Data Link Layer (Layer 2)
- Uses MAC address table to forward frames
- Breaks up collision domains

### b) Bridge:
- Connects two LAN segments
- Learns MAC addresses to filter traffic

## 8. Learning Bridge Algorithm

### 🔄 Steps:
1. Monitor incoming frames
2. Learn MAC addresses and the port they arrive from
3. Forward frames to the correct port
4. If unknown, broadcast

### 🔒 Attack Vector:
MAC flooding can overflow bridge/switch table → forces to broadcast → enables sniffing

## 9. Spanning Tree Protocol (STP)

### 🌳 Purpose:
Prevent loops in a network with redundant links by blocking some paths

### 🔁 How it Works:
1. Elects Root Bridge
2. Calculates shortest paths
3. Disables links causing loops

### 🔒 Vulnerabilities:
STP manipulation (e.g., root bridge attack) → attacker forces traffic through their device

## 🚨 Summary for Cybersecurity

| Concept | Related Threats | Tools |
|---------|-----------------|-------|
| Framing | Malformed frames, injection | Scapy, Wireshark |
| Error Detection | CRC spoofing | Custom packet crafting |
| Flow Control | ACK storms, TCP attacks | hping3, nmap |
| MAC Protocols | DoS, jamming | aireplay-ng |
| Switches/Bridges | MAC flooding, sniffing | ettercap, macof |
| STP | Root bridge hijack | yersinia |
