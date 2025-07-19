# Chromebook Cybersecurity Setup (Crostini-Based)

**Device:** Acer Chromebook CB715-1W  
**Purpose:** Cybersecurity lab, scripting, and .pcap analysis using Chrome OS + Crostini  
**Date:** 2025-07-19

---

## 1. Powerwash (Factory Reset Chromebook)

### From Chrome OS GUI:
1. Go to **Settings → Reset Settings**
2. Click **Powerwash → Restart**
3. Confirm Powerwash again after reboot

---

## 2. Enable Linux (Crostini)

1. Go to **Settings → Developers**
2. Click **Turn On** under **Linux development environment (Beta)**
3. Set disk size (recommend 10–15 GB+)
4. Follow prompts to install

---

## 3. Update System & Install Essentials

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install build-essential curl git net-tools -y
```

---

## 4. Install Cybersecurity Tools

```bash
sudo apt install nmap wireshark tshark hydra john hashcat -y
```

### Notes:
- `wireshark` GUI works but cannot capture live traffic in Crostini
- Use `tshark` for command-line pcap analysis
- Use another device to capture `.pcap` files

---

## 5. Install Scripting Tools

```bash
sudo apt install python3 python3-pip bash-completion -y
```

---

## 6. Install Terminal Utilities

```bash
sudo apt install htop tmux unzip neofetch -y
```

---

## 7. VS Code Setup via Flatpak

```bash
sudo apt install flatpak gnome-software gnome-software-plugin-flatpak -y
flatpak remote-add --user --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
flatpak install --user flathub com.visualstudio.code
flatpak run com.visualstudio.code
```

---

## 8. Transferring .pcap Files to Crostini

1. Save `.pcap` file in **Downloads** or **Google Drive**
2. Right-click → **Share with Linux**
3. Access from:
```bash
cd /mnt/chromeos/MyFiles/Downloads
```

---

## 9. Using TShark

```bash
tshark -D                    # List interfaces (usually none in Crostini)
tshark -r capture.pcap       # Analyze a .pcap file
tshark -r capture.pcap -Y http  # Apply display filter
```

---

## 10. ifconfig Not Found Fix

### Temporary Fix:
```bash
export PATH="$PATH:/sbin:/usr/sbin"
```

### Permanent Fix:
```bash
echo 'export PATH="$PATH:/sbin:/usr/sbin"' >> ~/.bashrc
source ~/.bashrc
```

---

## Limitations of Crostini

| Capability               | Supported |
|--------------------------|-----------|
| Analyze `.pcap` files    | ✅ Yes     |
| Capture live packets     | ❌ No      |
| GPU-accelerated hashcat  | ❌ No      |
| Visual Wireshark         | ✅ Partial |
| Full Linux control       | ❌ No      |
