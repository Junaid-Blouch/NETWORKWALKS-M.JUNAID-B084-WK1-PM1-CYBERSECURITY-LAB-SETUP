# Cybersecurity Testing Lab Environment Setup

This repository contains the documentation and network verification for a dedicated cybersecurity testing laboratory environment running on a VirtualBox infrastructure.

## Environment Architecture & Layout
- **Hypervisor Platform:** Oracle VM VirtualBox (v7.x)
- **Attacker Machine:** Kali Linux
- **Network Mode:** Custom Isolated NATNetwork Boundary
- **Network CIDR Range:** 10.0.0.0/24
- **Allocated Manual IP:** 10.0.0.2
- **Assigned Gateway Default Route:** 10.0.0.1
- **DNS Server Resolution:** 8.8.8.8 (Google Public DNS)

## Virtual Machine Enhancements Enabled
- Dual-direction Shared Clipboard (Bidirectional)
- Dual-direction File Transfer Interface (Bidirectional Drag'n'Drop)
- Automation Directory Mounts (`/downloads` folder shared from host)

## Operational Reliability & Maintenance Notes
During the initial lab phase, a typical network interface caching layer glitch (common in Linux environments) caused a temporary name resolution mismatch. The persistence stack was successfully forced and stabilized into a continuous running state using the system's core NetworkManager control loops:
```bash
sudo nmcli connection modify "Wired connection 1" ipv4.dad-timeout 0
sudo nmcli connection down "Wired connection 1"
sudo nmcli connection up "Wired connection 1"
```
