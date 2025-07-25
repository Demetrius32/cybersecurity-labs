
# 🕵️‍♂️ Finding Malicious Indicators in Memory

In this lab, you’ll perform **memory analysis using Volatility**, a powerful framework for investigating memory dumps to detect malware, suspicious processes, and hidden indicators of compromise (IOCs).

---

## 🎯 Objectives
- Extract volatile data from a memory dump
- Identify suspicious processes, DLLs, and network connections
- Detect malware and correlate indicators
- Practice real-world incident response triage techniques

---

## 🛠️ Tools & Concepts
| Tool / Concept | Description |
|----------------|-------------|
| **Volatility** | Open-source memory forensics framework |
| **Memory Dump** | A snapshot of a system’s RAM for analysis |
| **pslist / psscan** | Reveal running processes and terminated ones |
| **netscan** | Identify network connections and open ports |
| **dlllist** | Review DLLs loaded by each process |
| **malfind** | Detect injected code and hidden malware |
| **hashdump** | Extract user password hashes |

---

## 🧪 Lab Steps

### 🧬 1. Load the Memory Dump
- Launch the virtual machine
- Navigate to Volatility folder:  
  ```
  cd Volatility-master
  ```

- Run this command to identify the image profile:
  ```bash
  python vol.py -f /media/sf_Shared/Labs/memdump.mem imageinfo
  ```

---

### 🔍 2. Process and Network Analysis
- List active processes:
  ```bash
  python vol.py -f memdump.mem --profile=WinXPSP2x86 pslist
  ```

- Scan for hidden or terminated processes:
  ```bash
  python vol.py -f memdump.mem --profile=WinXPSP2x86 psscan
  ```

- Check network connections:
  ```bash
  python vol.py -f memdump.mem --profile=WinXPSP2x86 netscan
  ```

---

### 🧠 3. Look for Malware
- Find code injection:
  ```bash
  python vol.py -f memdump.mem --profile=WinXPSP2x86 malfind
  ```

- List DLLs per process:
  ```bash
  python vol.py -f memdump.mem --profile=WinXPSP2x86 dlllist
  ```

- Dump suspicious processes:
  ```bash
  python vol.py -f memdump.mem --profile=WinXPSP2x86 procdump -p <PID> --dump-dir=dump
  ```

---

## 🚩 Key Indicators of Compromise (IOCs)
- Suspicious process names (e.g., `lsass.exe` not running as SYSTEM)
- Non-standard ports with active connections
- Code injections found in `malfind`
- Unusual DLLs loaded into trusted processes
- Extracted hashes that appear in breach databases

---

## ✅ Key Takeaways
- Memory forensics is essential for uncovering hidden malware
- Volatility offers powerful triage capabilities for IR teams
- Real-world skills: memory profiling, process tracking, IOC detection

---

## 📄 References
- Volatility Documentation: https://www.volatilityfoundation.org/
- MITRE ATT&CK: Discovery & Execution Tactics
