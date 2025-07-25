
# 🌐 Deep Dive into Packet Analysis using Wireshark & NetworkMiner

This lab focuses on performing packet-level network analysis using tools like **Wireshark** and **NetworkMiner**. You'll identify suspicious network behavior and trace communication between attackers and victims.

---

## 🎯 Objectives
- Analyze captured packet data using Wireshark
- Identify TCP, UDP, HTTP, and DNS traffic patterns
- Use NetworkMiner to extract files and metadata from packet captures
- Interpret Indicators of Compromise (IOCs) from network behavior

---

## 🛠️ Tools & Concepts
| Tool / Concept | Description |
|----------------|-------------|
| **Wireshark** | GUI-based network protocol analyzer |
| **NetworkMiner** | Passive network sniffer and forensic analysis tool |
| **PCAP Files** | Packet capture files with raw network traffic |
| **TCP Streams** | Continuous connections between two endpoints |
| **HTTP/DNS Traffic** | Common protocols used for command and control or exfiltration |

---

## 🧪 Lab Steps

### 📦 1. Open PCAP in Wireshark
- File > Open > Select `capture.pcap`
- Use filters like:
  ```wireshark
  http
  dns
  tcp.stream eq 1
  ip.addr == x.x.x.x
  ```

### 🔍 2. Analyze HTTP & DNS Activity
- Use the **Statistics > HTTP** menu
- Follow individual TCP streams:
  - Right-click a packet → **Follow → TCP stream**
  - Look for suspicious GET/POST requests or payloads

### 🧵 3. Reconstruct Sessions and Files
- File > Export Objects > HTTP
- Save and inspect any downloadable or embedded files

---

### 🧲 4. NetworkMiner Analysis
- Launch NetworkMiner and open the same `.pcap` file
- It will auto-extract:
  - Hostnames
  - File transfers
  - Credentials (if unencrypted)
  - SSL certs and user-agents

---

## 🚩 Key Indicators of Compromise (IOCs)
- Communication with known malicious IPs/domains
- Executables or scripts being downloaded via HTTP
- Unusual DNS queries or high-frequency lookups
- Base64-encoded strings in URLs or payloads

---

## ✅ Key Takeaways
- Network analysis is crucial for intrusion detection and response
- Wireshark reveals the "who/what/when/where" of network traffic
- NetworkMiner simplifies the forensics process by auto-extracting artifacts
- Real-world analysts use these tools to trace back to the source of compromise

---

## 📄 References
- [Wireshark User Guide](https://www.wireshark.org/docs/wsug_html_chunked/)
- [NetworkMiner](https://www.netresec.com/?page=NetworkMiner)
- [PCAP Analysis Techniques](https://unit42.paloaltonetworks.com/)
