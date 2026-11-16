# Linux Server-Hardening Project

**Personal home-lab project · 2026**  
**Target:** Ubuntu Linux virtual machine in Oracle VirtualBox  
**Testing workstation:** Kali Linux

## Overview

This project documents a practical hardening exercise on an Ubuntu Linux virtual machine. The work focused on reducing unnecessary network exposure, tightening remote administration, applying least-privilege access practices, reducing the running-service attack surface, and improving security-relevant audit visibility.

The project was carried out in a personal lab. It is a learning and portfolio project, not a claim of a certified CIS benchmark assessment or production deployment.

## Lab layout

| Component | Role |
|---|---|
| Ubuntu Linux VM | System being hardened |
| Kali Linux VM | Separate testing/administration machine |
| Oracle VirtualBox | Virtualisation platform |
| UFW | Host firewall |
| OpenSSH | Remote administration |
| Auditd | Linux audit framework |

The portfolio evidence shows a VirtualBox network interface with a `10.0.2.x` address. The exact network mode, Ubuntu release, Kali release, VM resource allocation, and final addressing plan were not preserved in the available project material.

## Hardening areas documented

1. **Firewall:** enabled UFW, allowed SSH and HTTP where required, and used a default-deny incoming policy.
2. **SSH:** reviewed OpenSSH settings, addressed direct root access, restricted access to authorised users, and used key-based authentication where configured.
3. **Accounts and privilege:** reviewed local accounts, removed accounts considered unnecessary, and limited administrative activity through `sudo`.
4. **Service reduction:** enumerated running/listening services and disabled services considered unnecessary for the lab server.
5. **Audit logging:** configured Auditd to monitor authentication/system activity and sensitive files such as `/etc/passwd`.
6. **Verification:** compared port/service enumeration before and after the hardening work.

See [the control notes](docs/hardening-controls.md), [verification guide](docs/verification-guide.md), and [evidence register](docs/evidence-register.md).

## Evidence

Three original screenshots are linked from the project portfolio:
- [UFW configuration and status](https://naphtali-portfolio.netlify.app/images/linux-ufw.png)
- [VirtualBox network and `ip a` output](https://naphtali-portfolio.netlify.app/images/linux-networking.png)
- [OpenSSH configuration, sudo membership, and `/etc/passwd` permissions](https://naphtali-portfolio.netlify.app/images/linux-ssh.png)

The images are linked rather than bundled in this ZIP because the source image files could not be retrieved into the package during preparation. The portfolio case file is [available here](https://naphtali-portfolio.netlify.app/linux-hardening).

## Repository contents

```text
Linux-Server-Hardening-Upload/
├── README.md
├── UPLOAD-INSTRUCTIONS.md
├── .gitignore
├── docs/
│   ├── lab-overview.md
│   ├── hardening-controls.md
│   ├── verification-guide.md
│   ├── evidence-register.md
│   └── limitations-and-provenance.md
├── evidence/
│   └── README.md
├── scripts/
│   └── verify_hardening.sh
└── config-examples/
    └── README.md
```

## Read-only verification helper

A verification helper is included under `scripts/verify_hardening.sh`. It is a **newly prepared convenience script**, not an original script recovered from the lab. It does not change system settings; it prints a collection of checks that can help document a future validation run.

```bash
chmod +x scripts/verify_hardening.sh
sudo ./scripts/verify_hardening.sh
```

Review its output before sharing it publicly. It may contain usernames, addresses, service names, and other environment details.

## Important accuracy note

This repository documents the work and evidence currently available. It does not contain original VM snapshots, full command history, raw before/after scan output, Auditd event exports, or original configuration backups. Where exact settings or outputs were not preserved, this repository says so rather than inventing them.

## Author

Naphtali Peter  
[Portfolio](https://naphtali-portfolio.netlify.app) · [GitHub](https://github.com/naph1) · [LinkedIn](https://www.linkedin.com/in/naphtali-peter-501887298)
