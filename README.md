# 🧱 Kali Linux Firewall Hardening (UFW)

This project demonstrates how to configure a secure Linux firewall using UFW (Uncomplicated Firewall) on Kali Linux. The goal was to block all incoming connections while still allowing essential services (like internet, SSH, and file sharing) to continue uninterrupted.

---

## ✅ Objectives

- Secure the Kali VM from external scans and unauthorized connections
- Allow only necessary inbound ports (e.g., SSH, HTTP/S)
- Preserve internet connectivity, GitHub access, and VirtualBox shared folders
- Practice real-world system hardening and firewall testing

---

## 🔧 Tools Used

- Kali Linux (You can use as root)
- UFW (`Uncomplicated Firewall`)
- Nmap (for before/after scanning)
- VirtualBox (host system with shared folder)

---

## 🛡️ UFW Rules Applied

```bash
sudo ufw default deny incoming
sudo ufw default allow outgoing

sudo ufw allow from 10.0.2.0/24 to any port 22 proto tcp    # SSH (local network only)
sudo ufw allow 80/tcp    # HTTP
sudo ufw allow 443/tcp   # HTTPS
sudo ufw allow 2049/tcp  # Shared folder/NFS (VirtualBox)
