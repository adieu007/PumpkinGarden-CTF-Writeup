# 🎃 PumpkinGarden CTF: Full Path to Root
**Target IP:** `192.168.56.106`  
**Difficulty:** Intermediate  
**Status:** System Fully Compromised 🏁

## 📑 Project Overview
This repository contains a detailed penetration testing walkthrough for the **PumpkinGarden** CTF machine. [cite_start]The objective was to identify vulnerabilities, gain a low-privileged shell, and eventually escalate privileges to the `root` user (LordPumpkin) to retrieve the final key [cite: 3, 31-32].

---

## 🔍 Phase 1: Scanning & Reconnaissance
[cite_start]The first phase involved identifying live hosts and mapping the attack surface of the target[cite: 3].

* [cite_start]**Network Discovery**: Nmap identified the target at IP `192.168.56.106`[cite: 4, 42].
* [cite_start]**Service Mapping**: A detailed scan revealed three primary entry points: **FTP** (Port 21), **HTTP** (Port 1515), and **SSH** (Port 3535) [cite: 8, 60, 80-82].

![Host Discovery](fig1.png)
![Service Scan](fig2.png)

---

## 📂 Phase 2: Enumeration
[cite_start]Enumeration focused on gathering deeper information from the identified services, including misconfigurations and credentials[cite: 11, 91].

* [cite_start]**Anonymous FTP**: The FTP service allowed anonymous login, providing an initial entry point [cite: 13-14, 121-122].
* [cite_start]**Web Secrets**: Web directory enumeration revealed a hidden path at `/img/hidden_secret/` containing a `clue.txt` file [cite: 16-17, 147-148].
* [cite_start]**Credential Discovery**: The `clue.txt` file contained Base64-encoded credentials which were decoded for further access[cite: 20, 154].

![FTP Login](fig4.png)
![Hidden Web Directory](fig7.png)

---

## 🔑 Phase 3: Initial Access & Pivoting
[cite_start]Using the decoded secrets, I established a secure connection to the machine[cite: 23, 172].

* [cite_start]**SSH Entry**: Established a connection as the user `scarecrow` [cite: 32-33].
* [cite_start]**User Pivot**: After inspecting accessible files, I found hints leading to the user `goblin` [cite: 26, 33-34, 181].
* [cite_start]**Access Level**: Successfully logged in as `goblin` on port `3535`[cite: 34, 196, 212].

![Pivoting to Goblin](fig12.png)

---

## ⚡ Phase 4: Privilege Escalation
[cite_start]The final challenge was escalating from a low-privileged user to the **Root user**, LordPumpkin [cite: 25-26, 180-181].

* [cite_start]**Vulnerability**: Identified a publicly documented **Sudo local root exploit** (Tod Miller)[cite: 28, 183].
* [cite_start]**Exploit Strategy**: I recreated the exploit script and synchronized its execution with system cleanup intervals to bypass environmental constraints [cite: 29-31, 184-186].
* [cite_start]**Success**: The exploit successfully returned a root shell, confirming full system compromise [cite: 31-32, 187].

![The Sudo Exploit Script](fig13.png)
![Gaining Root Shell](fig15.png)

---

## 🚩 Final Flag
[cite_start]With root privileges, I accessed the protected `/root` directory to retrieve the final key[cite: 38, 262].

* [cite_start]**Access Level**: `uid=0(root)` [cite: 38, 260-261].
* [cite_start]**Flag Key**: `Q29uZ3JhdHVsYXRpb25zIQ==`[cite: 38, 266].

![Capture the Flag](fig16.png)

---

## 🛠️ Tools & Technical Skills
| Phase | Objective | Tools & Techniques |
| :--- | :--- | :--- |
| **Reconnaissance** | Identify the target and live services. | [cite_start]Nmap (Ping Sweep, Service Scan) [cite: 6-7, 58-59] |
| **Enumeration** | Find hidden entry points and clues. | [cite_start]Directory Busting, Anonymous FTP Login [cite: 16, 121] |
| **Initial Access** | Establish a shell connection. | [cite_start]SSH, Base64 Decoding [cite: 20, 23, 154, 171] |
| **Privilege Escalation** | Gain root administrative control. | [cite_start]Bash Scripting, Sudo Vulnerability Exploitation [cite: 28-29, 183-184] |

---

### 🛡️ Security Recommendations
1. [cite_start]**Disable Anonymous FTP**: Prevent unauthorized file access to sensitive documents[cite: 14, 122].
2. [cite_start]**Patch Sudo**: Update the system to a version not vulnerable to local root exploits[cite: 28, 183].
3. [cite_start]**Secure Web Directories**: Do not store credentials (even encoded ones) in publicly accessible web folders[cite: 17, 148].
