
# 🚨 Investigating a Network Compromise

In this lab, you’ll take on the role of an Incident Responder tasked with investigating a suspected network compromise. You’ll analyze memory dumps and volatile data to identify suspicious behavior, malware, and signs of lateral movement.

---

## 🎯 Objectives
- Use Volatility to investigate a compromised Windows system
- Identify processes, services, network activity, and injected code
- Correlate findings to detect lateral movement or persistence
- Practice real-world IR methodology

---

## 🛠️ Tools & Concepts
| Tool / Concept | Description |
|----------------|-------------|
| **Volatility** | Memory forensics framework |
| **Memory Dump** | Captured RAM of a live compromised system |
| **pslist / psscan / netscan** | Process and network visibility |
| **malfind** | Detect malicious code injection |
| **cmdscan / consoles** | See executed commands |
| **svcscan** | Inspect Windows services for abuse |

---

## 🧪 Lab Steps

### 🧬 1. Load and Identify Memory Profile
```bash
python vol.py -f memdump.mem imageinfo
```
- Determine correct profile (e.g., `Win7SP1x64`)

**📸 Example Output**
![Imageinfo profile result](images/imageinfo_output.png)

---

### 🔍 2. Enumerate Processes
```bash
python vol.py -f memdump.mem --profile=Win7SP1x64 pslist
python vol.py -f memdump.mem --profile=Win7SP1x64 psscan
```
- Look for suspicious names, parent-child anomalies, or hidden processes

**📸 Example Output**
![Suspicious processes found](images/pslist_suspicious.png)

---

### 🌐 3. Analyze Network and Commands
```bash
python vol.py -f memdump.mem --profile=Win7SP1x64 netscan
python vol.py -f memdump.mem --profile=Win7SP1x64 consoles
python vol.py -f memdump.mem --profile=Win7SP1x64 cmdscan
```
**📸 Example Output**
![Network connections to unknown IPs](images/netscan_output.png)

---

### 💉 4. Detect Malware
```bash
python vol.py -f memdump.mem --profile=Win7SP1x64 malfind
```
**📸 Example Output**
![Malfind detected injected DLL](images/malfind_alert.png)

---

### 🧩 5. Review Services
```bash
python vol.py -f memdump.mem --profile=Win7SP1x64 svcscan
```
**📸 Example Output**
![Suspicious service detected](images/svcscan_persistence.png)

---

## 🚩 Indicators of Compromise (IOCs)
- Unusual running processes (e.g., `svchost.exe` in wrong location)
- Network connections to uncommon ports or foreign IPs
- Evidence of privilege escalation or command-line abuse
- Injected DLLs or in-memory payloads

---

## ✅ Key Takeaways
- Memory analysis is critical for detecting in-memory malware
- Volatility allows responders to reconstruct attacker behavior
- Combining multiple plugins gives a complete threat picture
- This simulates real-world response to advanced persistent threats (APTs)

---

## 📁 Image Folder Setup

Place your screenshots in:
```
network_compromise_investigation/images/
```
Upload each file to GitHub with matching names (e.g., `imageinfo_output.png`, `netscan_output.png`).

---

## 📄 References
- [Volatility Framework](https://www.volatilityfoundation.org/)
- [Windows Incident Response](https://windowsir.blogspot.com/)
- [MITRE ATT&CK – Defense Evasion](https://attack.mitre.org/tactics/TA0005/)

---

## 📄 References
- [Volatility Framework](https://www.volatilityfoundation.org/)
- [Windows Incident Response](https://windowsir.blogspot.com/)
- [MITRE ATT&CK – Defense Evasion](https://attack.mitre.org/tactics/TA0005/)
