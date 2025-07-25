
# 🧠 Introduction to Autopsy Forensic Browser Lab

This lab explores the use of the **Autopsy Forensic Browser**, an open-source digital forensics tool, to investigate disk images, extract artifacts, and generate forensic reports — aligning with GIAC Certified Forensic Examiner (GCFE) objectives.

---

## 🎯 Objectives
- Install and run Autopsy
- Create and manage forensic cases
- Analyze disk images (E01 format)
- Tag and report on digital evidence
- Extract forensic flags for challenge verification

---

## 🛠️ Tools & Concepts
| Tool / Concept | Description |
|----------------|-------------|
| **Autopsy** | GUI forensic tool powered by The Sleuth Kit (TSK) |
| **E01 file** | Proprietary forensic image format |
| **Chain of Custody** | Documentation trail of handling digital evidence |
| **NTFS File System** | Common file system examined during investigation |
| **Report Generation** | Exported in HTML, Excel, or Body File format |

---

## 🧪 Lab Workflow

### 🔧 1. Install Autopsy (on Windows)
- Navigate to NTFS (H:) drive
- Install `autopsy-3.0.8-32bit.msi`
- Launch Autopsy from the desktop

### 📁 2. Create a Case
- Name: `NTFS Capture`
- Location: `H:\Case`
- Case Number: `Lab07`
- Examiner: `Student`
- Add data source: `ntfs_pract.E01`
- Leave default timezone and analysis options

### 🔍 3. Examine Evidence
- Navigate the NTFS image like Windows Explorer
- View file details, volumes, and file system metadata
- Analyze files such as `NTUSER.DAT`, documents, images, and videos
- Use Hex View and Text View to inspect contents

### 🏷️ 4. Tag Items
- Tag images and documents using `Tag and Comment`
- These bookmarks are included in the final report

### 📄 5. Generate a Forensic Report
- Format: HTML
- Include: Tagged Results > Bookmark
- View report in browser

---

## 🚩 Flag Challenge
Autopsy contains hidden forensic flags embedded in image files. The lab includes steps to extract files such as `flag1.png` to `flag6.png` and uncover hidden numbers as part of a simulated Capture-The-Flag (CTF) challenge.

---

## ✅ Key Takeaways
- Autopsy offers a free, powerful GUI for forensic analysis
- Supports E01 image formats, metadata parsing, and report generation
- Useful in educational and professional digital forensic workflows

---

## 📷 Screenshots *(Optional)*
You can include screenshots of:
- Autopsy interface
- Tagged items
- Final report
- Hex/Text views

---

## 🧾 Source
Lab developed with support from TAACCCT Grant No. TC-22525-11-60-A-48 and Infosec Learning, Inc. ©2022
