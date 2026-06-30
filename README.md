# Cyber Security CTF Documentation

A comprehensive repository of technical notes, methodologies, and findings from various Capture The Flag (CTF) challenges, including Metasploitable, OverTheWire Bandits, PicoCTF, and TryHackMe.

---

## 🛡️ Overview

This project serves as a structured technical knowledge base for cybersecurity research and CTF participation. It documents the reconnaissance, exploitation, and post-exploitation workflows developed while navigating intentionally vulnerable environments and competitive CTF platforms. The repository is designed to facilitate the rapid recall of security methodologies and shell manipulation techniques.

---

## 🎯 Scope

This repository covers the following environments:

| Platform | Focus Area |
| --- | --- |
| **Metasploitable** | Vulnerability scanning, service exploitation, and privilege escalation. |
| **OverTheWire (Bandits)** | Linux command-line proficiency, SSH, and file manipulation. |
| **PicoCTF** | Cryptography, reverse engineering, and general security puzzles. |
| **TryHackMe** | Guided offensive security learning paths and specific CTF machines. |

---

## 🛠️ Methodology & Tech Stack

The documentation focuses on standard industry tools and manual exploitation techniques.

### Tools & Utilities

* **Reconnaissance:** `nmap`, `gobuster`
* **Exploitation:** `metasploit` (msfconsole), `hydra` (brute forcing)
* **Post-Exploitation:** Python (PTY spawning), netcat (reverse shells)
* **Analysis:** Wireshark, `exiftool`
* **Encoding/Decoding:** `base64`, `rot13`, `xxd`, `md5sum`

---

## 📂 Project Structure

```text
├── CTF/
│   ├── Metasploitable/    # Notes on service-specific exploits
│   ├── OverTheWire/       # Progressive Bandit levels solutions
│   ├── PicoCTF/           # Cryptography & binary challenge notes
│   ├── Screenshots/       # Evidence and command execution logs
│   ├── TryHackMe/         # Lab-specific methodology (LazyAdmin, RootMe)
│   └── WireShark/         # Network traffic analysis captures

```

---

## ⚙️ Key Techniques

### Shell Stabilization

To upgrade non-interactive shells to fully functional interactive shells, the following sequence is utilized:

```bash
python -c "import pty; pty.spawn('/bin/bash');"
# Ctrl+Z
stty raw -echo ; fg
reset
export TERM=xterm
export SHELL=bash

```

### Password Cracking

Example using Hydra for HTTP POST forms:

```bash
sudo hydra -l admin -P /usr/share/wordlists/rockyou.txt $IP http-post-form "/path/to/login.php:username=^USER^&password=^PASS^&Login=Login:Login failed"

```

---

## 🔒 Security Findings

* **Command Injection:** Exploitation via `;` delimiter in vulnerable web fields.
* **SQL Injection:** Bypassing authentication using `' or 1=1#`.
* **Reverse Shells:** Deployment of web-based payloads (e.g., `pentestmonkey.php`) to establish listener connections.
* **SUID Exploitation:** Identification of binaries with SUID bits set, allowing for privilege escalation via `gtfobins` methodologies.

---

## 📝 Usage

This repository acts as a personal reference manual. To replicate findings:

1. Ensure you are within the designated lab/CTF environment.
2. Consult the directory corresponding to the specific challenge platform.
3. Utilize the provided commands and methodology notes to understand the vulnerability chain.

---

## 🚀 Future Improvements

* Implement automation scripts for common reconnaissance tasks (e.g., auto-parsing `nmap` output).
* Standardize the screenshot and log documentation format across all platforms.
* Expand documentation on lateral movement techniques within restricted networks.

---

## 💡 Acknowledgements

This project leverages professional tools and community resources:

* **[TryHackMe](https://tryhackme.com/)** and **[OverTheWire](https://overthewire.org/)** for platform labs.
* **[GTFOBins](https://gtfobins.github.io/)** for binary exploitation guidance.
* **[Kali Linux](https://www.kali.org/)** for the core toolset.

---

## 👤 Author

**Arnav Maheshwari**
