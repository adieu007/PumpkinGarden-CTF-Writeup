# 🎃 PumpkinGarden CTF: The Complete Path to Root

**Target IP:** 192.168.56.106  
**Difficulty:** Intermediate  
**Status:** System Fully Compromised 🏁

---

## 📄 Project Overview
This repository contains a detailed penetration testing walkthrough for the PumpkinGarden CTF machine. The objective was to identify vulnerabilities, gain a low-privileged shell, and eventually escalate privileges to the root user (LordPumpkin) to retrieve the final key.

---

## 🔍 Phase 1: Scanning & Reconnaissance
The first phase involved identifying live hosts and mapping the attack surface of the target.

* **Network Discovery**: Nmap identified the target at IP 192.168.56.106.
![Host Discovery](fig%201.png)

* **Service Mapping**: A detailed scan revealed three primary entry points: **FTP (Port 21)**, **HTTP (Port 1515)**, and **SSH (Port 3535)**.
![Service Scan](fig%202.png)

* **Version Scanning**: Detailed scanning provided version info for running services.
![Version Info](fig%203.png)

---

## 📂 Phase 2: Enumeration
Enumeration focused on gathering deeper information from the identified services, including misconfigurations and credentials.

* **Anonymous FTP**: The FTP service allowed anonymous login, providing an initial entry point.
![FTP Access](fig%204.png)

* **Finding Clues**: A `note.txt` file was retrieved containing hints about the user "jack".
![Note Discovery](fig%205.png)

* **Web Directory Search**: Web enumeration revealed an `/img/` directory.
![Web Directory](fig%206.png)

* **Hidden Secrets**: Further search revealed a hidden directory containing `clue.txt`.
![Hidden Path](fig%207.png)

---

## 🔑 Phase 3: Initial Access & Pivoting
The `clue.txt` file contained Base64-encoded credentials which were decoded for further access.

* **Locating the Clue**:
![Clue Location](fig%208.png)

* **Decoding Credentials**:
![Base64 Decoding](fig%209.png)

* **Analyzing User Context**:
![User Context](fig%2010.png)

* **SSH Entry**: Established a connection as the user `scarecrow`.
![Initial Login](fig%2011.png)

* **User Pivot**: Logged in as user `goblin` to move deeper into the system.
![Pivoting to Goblin](fig%2012.png)

---

## ⚡ Phase 4: Privilege Escalation
The final challenge was escalating from a low-privileged user to the **Root user**, LordPumpkin.

* **Vulnerability**: Identified a publicly documented Sudo local root exploit (Tod Miller).
![Exploit Code](fig%2013.png)

* **Execution attempts**: Recreated and tested the exploit locally.
![Testing Exploit](fig%2014.png)

* **Success**: Gained a root shell confirming full system compromise.
![Gaining Root Shell](fig%2015.png)

---

## 🚩 Final Flag
With root privileges, I accessed the protected `/root` directory to retrieve the final key.

* **Flag Retrieval**:
![Capture the Flag](fig%2016.png)

---

## 🛠️ Technical Glossary
* **Nmap**: A tool used to "knock on the doors" of a computer to see which services are open.
* **FTP**: File Transfer Protocol; allowed "Anonymous" access in this machine.
* **Base64**: An encoding format used to hide the credentials in clue.txt.
* **SSH**: Secure Shell; used to log into the command line remotely.
* **Root**: The administrative user with total control over the machine.
* **Privilege Escalation**: The process of moving from a normal user to an admin.
