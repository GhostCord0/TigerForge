# TigerForge
🐯 Windows LNK Payload Generator for Red Team &amp; Security Research

---

## ⚠️ Legal Disclaimer

> **TigerForge is developed strictly for educational purposes, authorized penetration testing, and cybersecurity research in controlled lab environments.**
>
> Using this tool against systems you do not own or have explicit written permission to test is **illegal** and **unethical**. The author assumes **no responsibility** for any misuse or damage caused by this tool. Always operate within the boundaries of applicable laws and regulations.

---

## 📖 Overview

**TigerForge** is a Windows `.lnk` (shortcut) payload generator designed for red team operators, penetration testers, and security researchers. It crafts highly customizable LNK files that execute **PowerShell commands** upon interaction — simulating real-world phishing vectors and initial access techniques used in adversary simulations.

Understanding how attackers weaponize seemingly innocent shortcut files is a critical part of modern defensive security. TigerForge brings that tradecraft into your lab.

---

## ✨ Features

- 🔧 **Custom PowerShell Command Injection** — Embed any PowerShell payload into the LNK target field
- 🎭 **Icon Spoofing** — Disguise the shortcut with legitimate-looking system icons
- 👁️ **Argument Obfuscation** — Conceal command-line arguments from casual inspection
- 📁 **Working Directory Control** — Set execution context for the spawned process
- 🪟 **Window State Control** — Run payloads silently (hidden window) or visibly
- 💾 **Batch Generation** — Generate multiple LNK files in one session
- 🖥️ **Clean GUI** — Intuitive interface, no command-line required

---

## 🔬 Use Cases

| Scenario | Description |
|----------|-------------|
| **Phishing Simulation** | Test your organization's resilience against LNK-based spearphishing |
| **Red Team Operations** | Initial access payload delivery via USB drops or email attachments |
| **Malware Analysis** | Understand how threat actors abuse `.lnk` files for defense research |
| **CTF Challenges** | Build and analyze shortcut-based challenges |
| **Security Awareness** | Demonstrate attack vectors to blue teams and SOC analysts |

---

## 🚀 Getting Started

### Requirements

- Windows 10 / 11
- .NET 6.0 or later

### Installation

```bash
git clone https://github.com/GhostCord0/TigerForge.git
cd TigerForge
```

Open the solution in **Visual Studio 2022** and build in `Release` mode.

Or download the latest pre-built binary from the [Releases](../../releases) page.

---

## 🛠️ How It Works

Windows `.lnk` files are Shell Link binary format files defined by `[MS-SHLLINK]`. They contain metadata including a **target path**, **arguments**, **working directory**, and **icon location**.

TigerForge manipulates these fields to embed PowerShell execution chains — commonly used as T1547 / T1566.002 techniques in the [MITRE ATT&CK](https://attack.mitre.org/) framework — allowing security professionals to replicate real adversary TTPs in isolated environments.

```
[LNK File]
  └─ Target     → powershell.exe
  └─ Arguments  → -WindowStyle Hidden -EncodedCommand <BASE64>
  └─ Icon       → %SystemRoot%\system32\shell32.dll
  └─ WorkingDir → %TEMP%
```

