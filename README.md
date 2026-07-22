# BReBon3S

**Browser Recon & eBased Online Network Security Scanner**

```
██████╗ ██████╗ ███████╗██████╗  ██████╗ ███╗   ██╗██████╗ ███████╗
██╔══██╗██╔══██╗██╔════╝██╔══██╗██╔═══██╗████╗  ██║╚════██╗██╔════╝
██████╔╝██████╔╝█████╗  ██████╔╝██║   ██║██╔██╗ ██║ █████╔╝███████╗
██╔══██╗██╔══██╗██╔══╝  ██╔══██╗██║   ██║██║╚██╗██║ ╚═══██╗╚════██║
██████╔╝██║  ██║███████╗██████╔╝╚██████╔╝██║ ╚████║██████╔╝███████║
╚═════╝ ╚═╝  ╚═╝╚══════╝╚═════╝  ╚═════╝ ╚═╝  ╚═══╝╚═════╝ ╚══════╝
```

> Version 1.0.0 • Passive analysis only • No root required • No exploitation

---

## What is BReBon3S?

BReBon3S is a **free, open-source, passive security analysis tool** for individuals who want to check whether a website or Android APK file looks safe before interacting with it. Built for terminal use — including Termux on Android.

**It is NOT:**
- A vulnerability scanner or penetration testing tool
- An antivirus product
- An authoritative malware detector
- A tool that submits reports or takes any automated action on your behalf

**It IS:**
- A cyberpunk-styled terminal interface for passive security checks
- A personal reputation database for sites and APKs you've personally assessed
- A directory of official abuse-reporting resources
- Fully usable offline (except API lookups)

---

## ⚡ Quick Start — Termux (Android)

> **Recommended method.** Copy and paste this block into Termux:

```bash
pkg update -y && pkg install -y python git clang libxml2 libxslt openssl libffi && \
git clone https://github.com/Ren23447/BReBon3S.git && \
cd BReBon3S && \
chmod +x termux-install.sh && \
./termux-install.sh
```

Then run:
```bash
python3 main.py
```

---

## 📱 Termux — Full Installation Guide

### What is Termux?

[Termux](https://termux.dev) is a free Android terminal emulator that gives you a Linux-like shell environment without root. BReBon3S is designed to work perfectly inside it.

**Get Termux from:** [F-Droid](https://f-droid.org/en/packages/com.termux/) *(recommended — Google Play version is outdated)*

---

### Step 0 — Prerequisites (read before installing)

Termux uses its own package manager (`pkg`) for system-level software. Several Python packages in BReBon3S have C extensions that must be compiled on your device, which requires system tools. **You must install these before running `pip install`**, or the installation will fail.

| System Package | Why It's Needed |
|---|---|
| `python` | Python 3 interpreter + pip package manager |
| `git` | Clone the BReBon3S repo from GitHub |
| `clang` | C/C++ compiler — required to build packages with native extensions (lxml, cffi, cryptography) |
| `libxml2` | XML parsing C library — required to compile `lxml` |
| `libxslt` | XSLT C library — required to compile `lxml` |
| `openssl` | TLS/SSL support — required for `requests` HTTPS connections |
| `libffi` | Foreign Function Interface — required by `cffi` and `cryptography` |
| `libc++` | C++ runtime library — required by some compiled Python extensions |

Install them all in one command:

```bash
pkg update -y
pkg install -y python git clang libxml2 libxslt openssl libffi "libc++"
```

> **Why `pkg update` first?**
> Running updates before installs avoids version conflicts and ensures you get working packages. Always run `pkg update` before installing new packages in Termux.

---

### Step 1 — Update Termux

```bash
pkg update -y
pkg upgrade -y
```

If asked to replace config files, press **`N`** (keep existing).

---

### Step 2 — Install system prerequisites

```bash
pkg install -y python git clang libxml2 libxslt openssl libffi "libc++"
```

**Verify Python installed correctly:**
```bash
python3 --version
pip3 --version
```

You should see Python 3.10 or newer and a pip version number.

---

### Step 3 — Clone BReBon3S

```bash
cd ~
git clone https://github.com/Ren23447/BReBon3S.git
cd BReBon3S
```

---

### Step 4 — Run the Termux installer

```bash
chmod +x termux-install.sh
./termux-install.sh
```

The installer will:
- Install all Python packages automatically
- Handle `lxml` gracefully (falls back to `html.parser` if compilation fails)
- Create your local database
- Verify all imports work
- Add a `brebon3s` alias to your shell

---

### Step 5 — Run BReBon3S

```bash
python3 main.py
```

Or if you reloaded your shell after install:
```bash
brebon3s
```

---

### Termux Troubleshooting

<details>
<summary><b>❌ pip install fails with "error: command 'clang' failed"</b></summary>

```bash
pkg install clang
```
Then retry the install.
</details>

<details>
<summary><b>❌ lxml fails to compile</b></summary>

This is normal on some devices. BReBon3S automatically falls back to `html.parser`. If you want lxml:
```bash
pkg install clang libxml2 libxslt
pip install lxml
```
</details>

<details>
<summary><b>❌ "ModuleNotFoundError: No module named 'modules'"</b></summary>

You must run BReBon3S from inside the BReBon3S directory:
```bash
cd ~/BReBon3S
python3 main.py
```
</details>

<details>
<summary><b>❌ SSL errors during requests</b></summary>

```bash
pkg install openssl ca-certificates
```
Then retry.
</details>

<details>
<summary><b>❌ "pkg: command not found"</b></summary>

You are not running in Termux. Use `install.sh` instead (for Linux/macOS).
</details>

<details>
<summary><b>❌ "cryptography" fails with Rust error</b></summary>

The `cryptography` package requires a Rust compiler on some ARM builds. If needed:
```bash
pkg install rust
pip install cryptography
```
Warning: Rust is a ~400 MB download.
</details>

<details>
<summary><b>⚠ Termux asks to allow storage access</b></summary>

BReBon3S only reads APK files you point it to. If you want to browse APKs in your Downloads folder, grant storage access once:
```bash
termux-setup-storage
```
</details>

---

## 💻 Linux / macOS Installation

```bash
git clone https://github.com/Ren23447/BReBon3S.git
cd BReBon3S
chmod +x install.sh
./install.sh
python3 main.py
```

## 🪟 Windows Installation

```cmd
git clone https://github.com/Ren23447/BReBon3S.git
cd BReBon3S
pip install -r requirements.txt
python main.py
```

---

## Features

### 🌐 Website Analysis (Passive)
- HTTPS verification
- TLS/SSL certificate inspection (validity, expiry, issuer, SANs)
- DNS record lookup (A, AAAA, MX, NS, TXT, CNAME, SPF, DMARC)
- Redirect chain tracing (cross-origin detection)
- Security header audit (CSP, HSTS, X-Frame-Options, X-Content-Type-Options, etc.)
- External JavaScript file detection
- Third-party tracker identification (Google Analytics, Meta Pixel, Hotjar, etc.)
- HTML form inspection (password fields, action URLs, methods)
- Phishing indicator heuristics (suspicious TLDs, IP-based URLs, keyword patterns, homograph chars)
- Suspicious download link detection (.exe, .apk, .bat, .ps1, etc.)
- Meta-refresh redirect detection
- VirusTotal URL reputation lookup *(requires free API key)*
- URLScan.io submission *(requires free API key)*
- Informational safety score with plain-English explanations

### 📱 APK Analysis (Static — no installation)
- SHA-256 / SHA-1 / MD5 file hashes
- APK structure validation
- AndroidManifest.xml parsing (permissions, package name, version)
- High-risk permission flagging with plain-English descriptions
- Embedded URL and domain extraction
- Certificate/signature file detection
- Native library listing
- DEX file inventory
- Risk summary

### 🗃 Local Reputation Database
- User-managed JSON database — **stored locally, never uploaded**
- Mark websites and APK hashes as: **Safe / Suspicious / Malicious**
- Full CRUD: add, edit, remove, search
- Export to JSON / Import from JSON
- Automatically checked when you scan a domain

### 📢 Reporting Resources
15+ official reporting links including: Google Safe Browsing, Microsoft SmartScreen, PhishTank, FBI IC3, FTC, Action Fraud UK, Europol, NCSC, NCMEC CyberTipline, IWF, VirusTotal, and more.

---

## Python Dependencies

| Package | Version | Purpose |
|---|---|---|
| `rich` | ≥13.7.0 | Terminal UI (colors, tables, panels, progress bars) |
| `colorama` | ≥0.4.6 | Cross-platform ANSI color init |
| `requests` | ≥2.31.0 | HTTP requests for website analysis |
| `dnspython` | ≥2.4.2 | DNS record lookups |
| `beautifulsoup4` | ≥4.12.3 | HTML parsing for tracker/form detection |
| `lxml` | ≥5.2.0 | Fast HTML parser *(optional — falls back to html.parser)* |

---

## Optional API Keys (Free Tiers Available)

BReBon3S works without any API keys. Keys unlock additional reputation lookups:

| Service | What it adds | Sign up |
|---|---|---|
| VirusTotal | URL/file reputation from 70+ AV engines | https://www.virustotal.com/gui/sign-in |
| URLScan.io | Visual website scanning | https://urlscan.io/user/signup |

Configure via **Option 5 → Settings** in the app.

---

## Project Structure

```
BReBon3S/
├── main.py                  ← Application entry point and UI screens
├── requirements.txt         ← Python dependencies
├── install.sh               ← Linux/macOS installer
├── termux-install.sh        ← Termux (Android) installer ← START HERE on Android
├── uninstall.sh             ← Linux/macOS uninstaller
├── README.md                ← This file
├── LICENSE                  ← MIT License
├── modules/
│   ├── __init__.py
│   ├── ui.py                ← Rich/Colorama terminal UI components
│   ├── website.py           ← Website passive analysis
│   ├── apk.py               ← APK static analysis
│   ├── database.py          ← Local reputation database
│   ├── reporting.py         ← Abuse reporting resources
│   ├── settings.py          ← Configuration management
│   └── utils.py             ← Shared utilities
└── data/
    ├── reputation_db.json   ← Local database (auto-created)
    └── config.json          ← User settings (auto-created)
```

---

## Disclaimer

BReBon3S is provided for **informational and educational purposes only**.

- **Passive analysis only** — no exploitation, no active scanning, no root required
- Results **cannot guarantee** a site or APK is safe or malicious
- The tool does **not upload your files** to any external service unless you configure an API key
- The local database reflects **your personal assessments only**
- Provided **AS IS** without warranty

Always use multiple sources and exercise your own judgement.

---

## License

MIT License — see [LICENSE](LICENSE)

## Contributing & Issues

https://github.com/Ren23447/BReBon3S/issues
