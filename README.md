# Linux-VM-Hardening-Practical-System-Security-Project
This project demonstrates basic to intermediate Linux VM hardening on Debian. It covers OS baseline security, user and permission management, SSH hardening, logging with journalctl, and brute-force protection using Fail2ban.
# Linux VM Hardening – Practical Security Project

## Overview

This repository contains a **practical Linux VM hardening project** performed on a Debian-based system.
The project demonstrates hands-on experience with system security fundamentals, focusing on
realistic hardening techniques commonly expected from **junior to mid-level Linux / System / Security engineers**.

The goal was not enterprise overengineering, but **solid baseline security** aligned with best practices.

---

## Key Skills Demonstrated

- Linux system administration
- Secure system configuration
- SSH hardening
- User and permission management
- Log analysis and monitoring
- Brute-force attack mitigation
- Security-oriented mindset

---

## Environment

| Component | Value |
|--------|------|
| OS | Debian 12 |
| VM Platform | VMware / VirtualBox |
| Init system | systemd |
| SSH | OpenSSH |
| Firewall | UFW / nftables |
| Logging | systemd-journald |

---

## Threat Model (Simplified)

This VM is hardened against:

- SSH brute-force attacks
- Unauthorized user access
- Weak default configurations
- Privilege escalation risks
- Insufficient logging and auditing

---

## Hardening Areas

### Operating System Baseline Hardening

**Objective:** Reduce attack surface and enforce safer defaults.

**Actions:**
- Full system update
- Removal / disabling of unnecessary services
- Kernel and network hardening via `sysctl`

**Examples:**
- Disabled IP forwarding
- Disabled ICMP redirects
- Disabled source routing
- Stopped unused services (e.g. printing, discovery services)

---

###  User & Permission Hardening

**Objective:** Enforce least privilege and proper access control.

**Actions:**
- Created non-root administrative user
- Restricted `sudo` access to specific users
- Disabled direct root login
- Audited home directory permissions
- Removed unnecessary users and groups

**Security Principles Applied:**
- Least privilege
- Separation of duties
- Accountability

---

###  SSH Hardening

**Objective:** Secure the primary remote access vector.

**Hardening Measures:**
- Default SSH port changed (22 → custom port)
- Root login disabled
- Password authentication disabled
- Public key authentication enforced
- Login attempts limited
- SSH features reduced to minimum

**Key SSH Configuration Options:**
- `PermitRootLogin no`
- `PasswordAuthentication no`
- `PubkeyAuthentication yes`
- `AllowUsers <authorized_user>`
- `MaxAuthTries 3`
- `LoginGraceTime 30`
- `X11Forwarding no`
- `AllowTcpForwarding no`

---

###  Logging & Auditing

**Objective:** Ensure visibility and traceability.

**Actions:**
- Enabled persistent system logs
- Configured journal size limits
- Enabled compression
- Reviewed authentication and SSH events using `journalctl`

**Benefits:**
- Improved incident investigation capability
- Reduced blind spots
- Controlled disk usage

---

###  Fail2ban Protection

**Objective:** Automatically block malicious login attempts.

**Implementation:**
- Fail2ban installed and configured
- SSH jail enabled
- Custom SSH port monitored
- Aggressive retry limits applied

**Sample Policy:**
- `maxretry`: 3
- `findtime`: 10 minutes
- `bantime`: 1 hour

**Result:**
- Effective mitigation of SSH brute-force attempts

---

## Testing & Validation

The following tests were successfully performed:

- Repeated failed SSH login attempts
- Verification of IP bans via Fail2ban
- SSH access attempts from unauthorized users
- Log inspection and correlation using `journalctl`

---

## Project Outcome

✔ Secure baseline Linux VM  
✔ Hardened remote access  
✔ Improved monitoring and visibility  
✔ Realistic security posture for small environments  

---

## What This Project Is (and Is Not)

✔ Practical  
✔ Hands-on  
✔ Portfolio-ready  

❌ Not enterprise-level  
❌ Not a compliance framework (CIS/ISO)  
❌ Not production hardened  

---

## Possible Future Improvements

- Firewall rule optimization
- CIS benchmark alignment
- Automated hardening scripts
- Centralized logging
- Intrusion detection integration

---

## Author

This project was created as part of a structured Linux learning and hardening path,
focusing on real-world skills applicable to system administration and security roles.
