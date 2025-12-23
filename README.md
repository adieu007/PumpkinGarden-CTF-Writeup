# 🎃 PumpkinGarden CTF: Full Path to Root
**Target IP:** 192.168.56.106 | **Status:** System Fully Compromised 🏁

---

## 🔍 Phase 1: Scanning & Reconnaissance
* **Network Discovery**: Nmap identified the host at 192.168.56.106.
![Host Discovery](images/fig%201.png)

* **Service Mapping**: Scans revealed FTP, HTTP, and SSH services.
![Service Scan](images/fig%202.png)

---

## 📂 Phase 2: Enumeration
* **Anonymous FTP**: Found a clue in note.txt via anonymous login.
![FTP Access](images/fig%204.png)

* **Web Secrets**: Found a hidden directory containing clue.txt.
![Hidden Secret](images/fig%207.png)

---

## 🔑 Phase 3: Initial Access & Pivoting
* **SSH Entry**: Established a connection as user scarecrow.
![Initial Access](images/fig%2011.png)

* **User Pivot**: Successfully logged in as user goblin.
![Pivoting to Goblin](images/fig%2012.png)

---

## ⚡ Phase 4: Privilege Escalation
* **The Exploit**: Recreated the Tod Miller Sudo local root exploit.
![Exploit Script](images/fig%2013.png)

* **Root Success**: Successfully gained a root shell.
![Gaining Root Shell](images/fig%2015.png)

---

## 🚩 Final Flag
* **Success**: Retrieved the final key from the /root directory.
![Capture the Flag](images/fig%2016.png)
