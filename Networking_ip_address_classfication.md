## 📐 IP Address Class Ranges Using Powers of 2

### IPv4 Address Space
- IPv4 = 32 bits  
- Total Addresses: `2³² = 4,294,967,296`

---

### 🅰️ Class A
- **Starts with:** `0` (binary prefix)  
- **Range:** `1.0.0.0` to `126.255.255.255`  
- **First Octet Range:** `1 to 126`  
- **# of Networks:**  
  - `2⁷ = 128` total  
  - Minus reserved `0.x.x.x` (network) and `127.x.x.x` (loopback)  
  - ✅ **126 usable networks**  
- **# of Hosts per Network:**  
  - `2²⁴ - 2 = 16,777,214` (excluding network & broadcast)

---

### 🅱️ Class B
- **Starts with:** `10` (binary prefix)  
- **Range:** `128.0.0.0` to `191.255.255.255`  
- **First Octet Range:** `128 to 191`  
- **# of Networks:** `2¹⁴ = 16,384`  
- **# of Hosts per Network:** `2¹⁶ - 2 = 65,534`

---

### 🅲 Class C
- **Starts with:** `110` (binary prefix)  
- **Range:** `192.0.0.0` to `223.255.255.255`  
- **First Octet Range:** `192 to 223`  
- **# of Networks:** `2²¹ = 2,097,152`  
- **# of Hosts per Network:** `2⁸ - 2 = 254`

---

### 🅳 Class D (Multicast)
- **Starts with:** `1110`  
- **Range:** `224.0.0.0` to `239.255.255.255`  
- **Use:** Multicasting only  
- **# of Addresses:** `2²⁸ = 268,435,456`

---

### 🅴 Class E (Experimental)
- **Starts with:** `1111`  
- **Range:** `240.0.0.0` to `255.255.255.255`  
- **Use:** Reserved for research  
- **# of Addresses:** `2²⁸ = 268,435,456`

---

## 🧠 Summary Table (with Powers of 2)

| Class | Network Bits | Host Bits | Networks (2ⁿ)           | Hosts per Network (2ʰ - 2)     |
|-------|---------------|------------|--------------------------|-------------------------------|
| A     | 7             | 24         | 2⁷ = 128 (126 usable)    | 2²⁴ - 2 = 16,777,214          |
| B     | 14            | 16         | 2¹⁴ = 16,384             | 2¹⁶ - 2 = 65,534              |
| C     | 21            | 8          | 2²¹ = 2,097,152          | 2⁸ - 2 = 254                  |
| D     | N/A           | N/A        | Multicast                | N/A                           |
| E     | N/A           | N/A        | Experimental             | N/A                           |

---

Would you like a visual diagram of IPv4 address classes or subnet masks in the same format?
