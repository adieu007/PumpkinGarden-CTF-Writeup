# 🎃 PumpkinGarden CTF Writeup

This repository contains a complete walkthrough and proof-of-concept for the PumpkinGarden CTF. This project demonstrates network scanning, web enumeration, and Linux privilege escalation using a documented Sudo exploit to gain root access and retrieve the final key.

---

## 🔍 Phase 1: Scanning & Enumeration
[cite_start]First, I identified the target machine at IP `192.168.56.106`[cite: 4].
* [cite_start]**Nmap Scan**: Revealed services on Port 21 (FTP), Port 1515 (HTTP), and Port 3535 (SSH)[cite: 8, 11].
* [cite_start]**Web Discovery**: Found a hidden directory at `/img/hidden_secret/` containing a `clue.txt` file[cite: 17].

## 🔓 Phase 2: Gaining Access
* [cite_start]**Decoding**: The `clue.txt` file held Base64-encoded credentials[cite: 20]. 
* [cite_start]**Initial Shell**: I used these to log in via SSH as user `scarecrow`, then pivoted to user `goblin`[cite: 23, 34].

## ⚡ Phase 3: Privilege Escalation
Once logged in as `goblin`, I discovered a path to become the root user:
* [cite_start]**Exploit**: Used a documented Sudo local root exploit (Tod Miller)[cite: 28, 35].
* [cite_start]**Result**: Successfully gained a root shell and retrieved the **PumpkinGarden_Key**[cite: 32, 38].

---

## 📚 Technical Glossary
* **Nmap**: A tool used to "knock on the doors" of a computer to see which services (like FTP or SSH) are open.
* [cite_start]**FTP (File Transfer Protocol)**: A way to move files between computers; in this case, it allowed "Anonymous" access, which was a major security hole[cite: 13, 14].
* **Base64**: A way of encoding data into text. It isn't encryption (secret), it's just a different format that I had to decode to find the password.
* **SSH (Secure Shell)**: A secure way to log into another computer’s command line.
* **Root (LordPumpkin)**: The "God Mode" of a Linux system. [cite_start]Having root access means you have total control over the machine[cite: 26, 38].
* [cite_start]**Privilege Escalation**: The process of starting as a normal user (like `goblin`) and finding a "glitch" to become the admin (root)[cite: 25, 31].
