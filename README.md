# Chromebook Cybersecurity Lab Setup (Crostini-Based)

This project documents how to set up a cybersecurity research and experimentation environment on a **Chromebook using Chrome OS's built-in Linux (Crostini)** feature.

---

## Contents

- [Overview](#overview)
- [Setup Goals](#setup-goals)
- [Environment Details](#environment-details)
- [Tools Installed](#tools-installed)
- [Usage Notes](#usage-notes)
- [Limitations](#limitations)
- [License](#license)

---

## Overview

This repository contains the full setup process used to prepare a **used Acer Chromebook CB715-1W** for cybersecurity projects using Chrome OS's Linux container (Crostini). It includes installation steps, tool usage, and limitations to be aware of.

---

## Setup Goals

- Create a safe and controlled cyber lab on a Chromebook
- Practice scripting, password auditing, and traffic analysis
- Learn and apply industry tools like Nmap, Wireshark, Hashcat, Hydra, etc.
- Use VS Code and terminal-based utilities effectively within Crostini

---

## Environment Details

- **Device:** Acer Chromebook CB715-1W
- **Linux:** Debian (Crostini container)
- **Tools:** CLI + GUI tools (via Flatpak)
- **Primary Language:** Bash & Python

---

## Tools Installed

| Tool        | Purpose                              |
|-------------|---------------------------------------|
| `nmap`      | Network scanning                      |
| `wireshark` | Packet capture (file analysis only)   |
| `tshark`    | CLI-based Wireshark                   |
| `hydra`     | Login brute-force testing             |
| `john`      | Password hash cracker                 |
| `hashcat`   | GPU/CPU password cracker              |
| `python3`   | Scripting language                    |
| `tmux`      | Terminal multiplexer                  |
| `htop`      | System monitoring                     |
| `net-tools` | Legacy commands like `ifconfig`       |
| `VS Code`   | Code editor (via Flatpak)             |

---

## Usage Notes

- **Wireshark cannot capture live traffic** due to Crostini sandboxing. Use `.pcap` files from external devices or labs.
- Use the `tshark` tool or open `.pcap` files directly in Wireshark for analysis.
- Transfer `.pcap` files to Crostini by sharing folders via the Chrome OS Files app.

---

## Limitations

| Feature                     | Supported in Crostini |
|----------------------------|------------------------|
| GUI Tools                  | ✅ Yes                 |
| Live packet capture        | ❌ No                  |
| USB Wi-Fi adapter support  | ❌ No                  |
| GPU acceleration (Hashcat) | ❌ No                  |
| Full root/kernel access    | ❌ No                  |

---

## License

This project is licensed for personal and educational use. Use all tools responsibly and ethically.

---

## Questions or Issues?

Open an issue or reach out via GitHub Discussions.
