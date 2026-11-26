
# 🐉 Kali Dragon | Hardware Specifications

[← Return to Project Overview](README.md)

> Trust Nothing. Verify Everything.

## Project Information

This document contains the hardware and software
specifications collected directly from the Kali Dragon
workstation using Linux diagnostic commands.

**Developer:** Zer0Trust404  
**Verification Date:** November 25, 2026  
**Project Status:** Operational / Ongoing Development

---

## 💻 System Identification

| Component | Specification |
|---|---|
| Manufacturer | Lenovo |
| Model | 100e Chromebook |
| Board | Google Robo Rev3 / Coral |
| Architecture | x86_64 |
| Operating System | Kali GNU/Linux Rolling |
| OS Release | 2026.3 |
| Kernel | 7.2.15+kali-amd64 |

## ⚙️ Processor

| Component | Specification |
|---|---|
| Manufacturer | Intel |
| Processor | Celeron N3350 |
| Base Frequency | 1.10 GHz |
| Maximum Frequency | 2.40 GHz |
| Minimum Frequency | 800 MHz |
| Physical Cores | 2 |
| Threads | 2 |
| L2 Cache | 2 MiB |
| Virtualization | Intel VT-x |
| Architecture | 64-bit |

## 🧠 Memory

| Component | Specification |
|---|---|
| Estimated Installed RAM | 4 GB |
| Verified Usable RAM | 3.7 GiB |
| Memory Used During Testing | 855 MiB |
| Available Memory During Testing | 2.9 GiB |
| Swap Capacity | 789 MiB |
| Swap Used During Testing | 0 B |

## 💾 Internal Storage

| Component | Specification |
|---|---|
| Storage Technology | eMMC |
| Nominal Capacity | 16 GB |
| Detected Capacity | 14.7 GiB |
| Device Identifier | mmcblk1 |
| Root Filesystem | ext4 |

### Partition Configuration

| Partition | Capacity | Filesystem | Mount Point |
|---|---|---|---|
| mmcblk1p1 | 856 MiB | vfat | /boot/efi |
| mmcblk1p2 | 13.1 GiB | ext4 | / |
| mmcblk1p3 | 790 MiB | swap | SWAP |

## 🔧 Firmware

| Component | Specification |
|---|---|
| Firmware Vendor | coreboot |
| Firmware | MrChromebox UEFI Full ROM |
| Firmware Version | MrChromebox-2609.3 |
| Release Date | October 28, 2026 |
| ROM Size | 16 MiB |
| SMBIOS Version | 3.1.0 |
| UEFI Support | Yes |
| ACPI Support | Yes |
| Selectable Boot | Yes |

## 🔋 Battery and Power Management

| Component | Specification |
|---|---|
| Manufacturer | LGC |
| Model | L17L3PB |
| Technology | Lithium-ion |
| Design Capacity | 3,685 mAh |
| Current Full Capacity | 2,585 mAh |
| Estimated Battery Health | 70.1% |
| Estimated Battery Degradation | 29.9% |
| Charge Cycles | 226 |
| Design Voltage | 11.4 V |
| Charge During Testing | 76% |
| Charging Adapter | 45W USB-C |

### Battery Health Calculation

Battery Health = Current Full Capacity / Design Capacity x 100

2,585 / 3,685 x 100 = 70.1%

The battery exhibits measurable capacity degradation.
Unexpected battery discharge during shutdown or
inactivity remains under investigation.

## 🛡️ Preliminary Security Findings

CPU diagnostics identified a reported vulnerability
associated with Register File Data Sampling (RFDS).

Reported status: Vulnerable: No microcode

Further investigation is required to determine
available mitigation options and firmware or
microcode compatibility.

This finding does not indicate that the system
has been compromised.

## 🔍 Verification Commands

The following read-only Linux commands were used
to collect system information:

```bash
lscpu
free -h
lsblk -o NAME,SIZE,TYPE,FSTYPE,MOUNTPOINTS
cat /etc/os-release
uname -r
sudo dmidecode -t bios
ls /sys/class/power_supply/
cat /sys/class/power_supply/BAT0/uevent
```

## 📋 Technical Skills Demonstrated

- Linux command-line administration
- Hardware identification
- Firmware verification
- Storage and partition analysis
- System resource monitoring
- Battery diagnostics
- Preliminary vulnerability identification
- Technical documentation
- Evidence-based troubleshooting

## 📌 Ongoing Investigations

- Unexpected battery discharge
- Shutdown and power management behavior
- CPU microcode mitigation
- Storage optimization
- System performance optimization

---

**Zer0Trust404**

*Trust Nothing. Verify Everything.*
