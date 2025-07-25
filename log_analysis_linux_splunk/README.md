
# 🔍 Log Analysis in Linux and Splunk

In this lab, you’ll work with both **Linux command-line tools** and **Splunk**, a powerful SIEM platform, to analyze log files and detect potential security events. You'll explore how logs are generated, collected, and used to find suspicious activity.

---

## 🎯 Objectives
- Understand the structure and location of Linux logs
- Use `grep`, `cat`, and `less` to parse logs via CLI
- Upload log files into Splunk and perform searches
- Identify suspicious login attempts and failed authentications

---

## 🛠️ Tools & Concepts
| Tool / Concept | Description |
|----------------|-------------|
| **/var/log/** | Default directory for Linux log files |
| **auth.log / secure** | Logs for authentication events |
| **grep / cat / less** | Linux tools for searching and viewing log content |
| **Splunk** | Security Information and Event Management (SIEM) platform |
| **Search Queries** | Search Processing Language (SPL) to analyze events |

---

## 🧪 Lab Steps

### 🐧 1. Explore Linux Logs
- View authentication logs:
  ```bash
  cat /var/log/auth.log
  ```
- Search for failed SSH logins:
  ```bash
  grep "Failed password" /var/log/auth.log
  ```

- Identify successful root access:
  ```bash
  grep "Accepted" /var/log/auth.log | grep "root"
  ```

---

### 🧠 2. Load Data into Splunk
- Login to Splunk
- Add Data → Upload → Choose your `.log` file
- Assign sourcetype: `linux_secure` or `linux_auth`
- Continue and start indexing

---

### 🔍 3. Run Basic Splunk Searches
- View failed logins:
  ```
  index=main sourcetype=linux_auth "Failed password"
  ```

- View successful logins:
  ```
  index=main sourcetype=linux_auth "Accepted password"
  ```

- View by username:
  ```
  index=main sourcetype=linux_auth user=root
  ```

---

## 🚩 What to Look For
- High number of failed login attempts
- Brute force attempts from same IP
- Login from unknown locations or times
- Use of rarely seen user accounts

---

## ✅ Key Takeaways
- Log analysis is a critical step in incident detection
- Linux provides raw log access via `/var/log`
- Splunk helps visualize and automate log investigation
- Combining CLI + SIEM skills makes for a strong defender

---

## 📄 References
- [Splunk Docs](https://docs.splunk.com/)
- [Linux Log Files Explained](https://www.thegeekdiary.com/understanding-var-log-secure-file/)
- [MITRE ATT&CK: Credential Access](https://attack.mitre.org/)
