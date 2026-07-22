# BReBon3S

## Browser Recon & eBased Online Network Security Scanner

<p align="center">
<img src="assets/Screenshot_20260722-154936_Termux.png" width="800">
</p>

```
██████╗ ██████╗ ███████╗██████╗  ██████╗ ███╗   ██╗██████╗ ███████╗
██╔══██╗██╔══██╗██╔════╝██╔══██╗██╔═══██╗████╗  ██║╚════██╗██╔════╝
██████╔╝██████╔╝█████╗  ██████╔╝██║   ██║██╔██╗ ██║ █████╔╝███████╗
██╔══██╗██╔══██╗██╔══╝  ██╔══██╗██║   ██║██║╚██╗██║ ╚═══██╗╚════██║
██████╔╝██║  ██║███████╗██████╔╝╚██████╔╝██║ ╚████║██████╔╝███████║
╚═════╝ ╚═╝  ╚═╝╚══════╝╚═════╝  ╚═════╝ ╚═╝  ╚═══╝╚═════╝ ╚══════╝
```

> Version 1.0.0  
> Passive security analysis only • No root required • No exploitation

---

# 🔍 What is BReBon3S?

**BReBon3S (Browser Recon & eBased Online Network Security Scanner)** is a free, open-source security analysis tool designed to help users perform basic safety checks on websites and Android APK files.

Built specifically for terminal environments such as **Termux on Android**.

BReBon3S focuses on passive analysis and reputation checking rather than active attacks.

---

# ⚠️ What BReBon3S Is NOT

BReBon3S is not:

- ❌ A vulnerability scanner
- ❌ A penetration testing tool
- ❌ An antivirus replacement
- ❌ A guaranteed malware detector
- ❌ A tool that automatically attacks, exploits, or reports targets

---

# ✅ Features

- 🔎 Website reputation checking
- 📱 Android APK analysis
- 🗄️ Local reputation database
- 📊 Security information storage
- 📝 Reporting resource directory
- 💻 Cyberpunk terminal interface
- 📦 Offline-friendly design
- 📱 Termux support
- 🚫 No root required

---

# ⚡ Quick Start — Termux

Install required packages:

```bash
pkg update -y && pkg upgrade -y

pkg install -y python git clang libxml2 libxslt openssl libffi unzip
```

Clone BReBon3S:

```bash
git clone https://github.com/Ren23447/BReBon3S.git
```

Enter the directory:

```bash
cd BReBon3S
```

Install:

```bash
chmod +x termux-install.sh

./termux-install.sh
```

Run:

```bash
python3 main.py
```

---

# 📱 Termux Installation Requirements

| Package | Purpose |
|---|---|
| Python | Runs BReBon3S |
| Git | Downloads and updates project |
| Clang | Compiles required packages |
| Libxml2 | XML processing support |
| Libxslt | XSLT processing support |
| OpenSSL | Secure connections |
| Libffi | Cryptography support |
| Unzip | Extracting archives |

---

# 🔄 Updating BReBon3S

Inside the BReBon3S folder:

```bash
git pull
```

Update dependencies:

```bash
pip install -r requirements.txt
```

Run:

```bash
python3 main.py
```

---

# 📂 Project Structure

```
BReBon3S/
│
├── main.py
├── website.py
├── apk.py
├── database.py
├── reporting.py
├── settings.py
├── utils.py
├── requirements.txt
├── termux-install.sh
│
└── assets/
    └── Screenshot_20260722-154936_Termux.png
```

---

# 🛡️ Safety Disclaimer

BReBon3S provides security information and analysis.

Results should be treated as indicators and not absolute proof that a website or application is safe or malicious.

Always verify important security decisions using trusted security resources.

---

# 📜 License

Open-source project licensed under the included LICENSE file.
