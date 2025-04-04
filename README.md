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

- Kali Linux (as root)
- UFW (`Uncomplicated Firewall`)
- Nmap (for attack simulation)
- scrot (for screenshots)
- rsyslog (for logging firewall events)
- VirtualBox (host with shared folder access)

---

## 🔍 Firewall Effectiveness Testing (Red Team Simulation)

After configuring UFW, I simulated real-world attack techniques to test the effectiveness of the firewall.

### 🧪 Nmap Attack Simulations:

| Type of Scan        | Command Used                                      |
|---------------------|--------------------------------------------------|
| Regular SYN Scan    | `nmap -sS 192.168.1.134 -oN regular_scan.txt`        |
| Stealth Scan        | `nmap -sS -T4 -Pn -f 192.168.1.134 -oN stealth_scan.txt` |
| Aggressive Scan     | `nmap -A 192.168.1.134 -oN aggressive_scan.txt`      |
| Full Port Scan      | `nmap -p- 192.168.1.134 -oN full_port_scan.txt`      |

Each scan was run **after enabling UFW** to observe which connections were blocked vs. allowed.

---

## 🗂 Log Capture & Analysis

UFW logs were captured from `/var/log/syslog` using:
```bash
sudo grep 'UFW' /var/log/syslog > ufw_attack_log.txt
