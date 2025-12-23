# 🎃 PumpkinGarden CTF: The Complete Path to Root

**Target IP:** `192.168.56.106`  
**Difficulty:** Intermediate  
**Status:** System Compromised 🏁

## 🔍 Phase 1: Scanning & Discovery
[cite_start]The goal was to identify the target and map its attack surface[cite: 3, 41].

* [cite_start]**Network Discovery**: Nmap identified the target at IP `192.168.56.106`[cite: 4, 42].
![Host Discovery](fig1.png)

* [cite_start]**Service Mapping**: A detailed scan revealed three primary entry points: **FTP (21)**, **HTTP (1515)**, and **SSH (3535)** [cite: 8, 60, 80-82].
![Service Scan Results](fig2.png)

---

## 📂 Phase 2: Enumeration
[cite_start]Enumeration focused on gathering deeper information from the identified services[cite: 11, 91].

* [cite_start]**System Information**: Detailed version scanning confirmed a Linux environment[cite: 11, 118].
![Version Scanning](fig3.png)

* [cite_start]**Anonymous FTP**: The FTP service allowed anonymous login [cite: 13-14, 121-122].
![FTP Access](fig4.png)

* [cite_start]**Initial Clue**: A `note.txt` file was retrieved from FTP, mentioning a user named "jack"[cite: 14, 122, 151].
![Reading Note](fig5.png)

* [cite_start]**Web Directory Search**: Web enumeration revealed an `/img/` directory[cite: 17, 148].
![Web Directory Index](fig6.png)

* [cite_start]**Hidden Secrets**: Deep within the `/img/` folder, a hidden directory containing `clue.txt` was found[cite: 17, 148].
![Hidden Secret Path](fig7.png)

---

## 🔑 Phase 3: Exploitation & Pivoting
[cite_start]Using the decoded credentials, I established a secure connection to the machine[cite: 23, 172].

* **Credential Discovery**: The `clue.txt` file held Base64-encoded credentials.
![Finding Clue File](fig8.png)
![Decoding Credentials](fig9.png)
![Analyzing User Context](fig10.png)

* [cite_start]**Initial Access**: Logged in via SSH as user `scarecrow` [cite: 32-33, 188].
![Scarecrow SSH Login](fig11.png)

* [cite_start]**User Pivot**: Further inspection led to user `goblin` on port `3535` [cite: 33-34, 212].
![Goblin SSH Login](fig12.png)

---

## ⚡ Phase 4: Privilege Escalation
[cite_start]The final challenge was escalating from a low-privileged user to the **Root user**, LordPumpkin [cite: 25-26, 180-181].

* [cite_start]**Identifying Vulnerability**: Found a documented **Sudo local root exploit** (Tod Miller)[cite: 28, 183].
![Sudo Exploit Code](fig13.png)

* [cite_start]**Exploit Preparation**: Recreated the exploit script locally[cite: 29, 184].
![Preparing Exploit](fig14.png)

* [cite_start]**Execution & Synchronization**: Carefully timed the exploit to gain root privileges[cite: 31, 186].
![Gaining Root Shell](fig15.png)

---

## 🚩 Final Flag
[cite_start]With root privileges, I accessed the protected `/root` directory to retrieve the final key [cite: 31-32, 187, 262].

* [cite_start]**Access Level**: `uid=0(root)` [cite: 38, 260-261].
* [cite_start]**The Flag Key**: Retrieved the final key from the system [cite: 38, 264-266].
![Capture the Flag](fig16.png)
