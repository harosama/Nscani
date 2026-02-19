# 🔍 Nscani Stealth Port Scanner with Decoy Support

A fast, stealthy TCP port scanner with real decoy scanning using spoofed IP packets. Built in Python, works like a system tool.

---

## 📦 Installation

```bash
# Clone the repo
git clone https://github.com/harosama/Nscani.git
cd nscani

# Make it executable
chmod +x nscani

# Install as a system tool (run from anywhere)
sudo mv nscani /usr/local/bin/nscani
```

Now just type `nscani` from anywhere in your terminal.

---

## ⚡ Quick Start 

```bash
# Basic scan
nscani 192.168.1.1

# Full stealth scan with decoys
sudo nscani 192.168.1.1 --start-port 1 --end-port 1024 --use-decoys --num-decoys 5
```

---

## 🚀 Usage

```
nscani <target> [options]
```

| Argument | Description | Default |
|---|---|---|
| `target` | IP address or hostname | required |
| `--start-port` | First port to scan | 1 |
| `--end-port` | Last port to scan | 100 |
| `--evasion-level` | `slow` `stealth` `normal` `fast` | stealth |
| `--use-decoys` | Enable decoy scanning (requires sudo) | off |
| `--num-decoys` | Number of fake IPs to use | 5 |
| `--randomize-order` | Randomize port scan order | off |
| `--verbose` | Show progress every 50 ports | off |

---

## 💡 Examples

```bash
# Scan common ports
nscani 192.168.1.1 --start-port 1 --end-port 1024

# Stealth scan with decoys
sudo nscani 192.168.1.1 --start-port 1 --end-port 1024 --use-decoys --num-decoys 5

# Maximum stealth
sudo nscani 192.168.1.1 --start-port 1 --end-port 1024 \
  --evasion-level slow \
  --use-decoys \
  --num-decoys 15 \
  --randomize-order \
  --verbose

# Fast scan
nscani 192.168.1.1 --start-port 1 --end-port 65535 --evasion-level fast
```

---

## 🎭 How Decoy Scanning Works

```
Without Decoys:  [Your IP] ──────────────────────→ Target

With Decoys:     [Decoy1]  ──┐
                 [Decoy2]  ──┤
                 [Your IP] ──┼──────────────────→ Target
                 [Decoy3]  ──┤
                 [Decoy4]  ──┘
                 (which one is real? 🤷)
```

Decoy scanning sends spoofed SYN packets from fake IPs mixed with your real scan, making it very hard for IDS/IPS to identify you.

> **Requires root** — uses raw sockets to craft spoofed packets.

---

## 🕵️ Evasion Levels

| Level | Speed | Stealth |
|---|---|---|
| `slow` | Very slow | Maximum |
| `stealth` | Moderate | High (default) |
| `normal` | Fast | Medium |
| `fast` | Very fast | Low |

---

## 📋 Example Output

```
======================================================================
  RESULTS — 3 open, 0 filtered on 192.168.1.1
======================================================================
  PORT         STATE        SERVICE              VERSION
  ------------------------------------------------------------
  21/tcp       open         ftp                  220 TP-LINK FTP version 1.0
  23/tcp       open         telnet
  80/tcp       open         http                 WebServer/1.0 UPnP/1.0
======================================================================
```

---

## ✅ Requirements

- Python 3.x
- Root/sudo for decoy scanning
- Linux or macOS (Windows supported but limited)

No external libraries needed — pure Python standard library.

---

## ⚠️ Legal Disclaimer

For **authorized penetration testing and educational purposes only**. Only scan systems you own or have explicit permission to test. Unauthorized scanning may be illegal.

---

## 👤 Author

Made by Ibtissem Benmessaoud  

## Made with love 💜!
