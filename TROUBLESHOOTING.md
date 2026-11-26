# 🛠️ Kali Dragon - Troubleshooting Log

[← Return to Project Overview](README.md)

## Overview

Throughout the development of Kali Dragon, I encountered several hardware, firmware, and operating system challenges. This document records the issues, diagnostic methods, resolutions, and lessons learned during the conversion process.

## Issue Summary

| Issue | Category | Status |
|---|---|---|
| Hardware write protection | Firmware | Resolved |
| Firmware utility execution | Linux | Resolved |
| USB boot configuration | Boot Process | Resolved |
| Internal audio functionality | Drivers | Resolved |
| Wireless connectivity | Networking | Resolved |
| MicroSD recognition | Storage | Resolved |
| Unexpected battery drain | Power Management | Under Investigation |
| Inconsistent startup behavior | Hardware / Firmware | Under Investigation |

---

## 1. Hardware Write Protection

### Problem
The Chromebook's factory write protection prevented modification of the original firmware.

### Investigation
- Enabled Chromebook Developer Mode.
- Investigated hardware write protection requirements.
- Identified battery disconnection as the method for disabling write protection on this device.

### Resolution
- Powered down the Chromebook.
- Disconnected the internal battery.
- Successfully disabled firmware write protection.
- Proceeded with firmware modification.

**Status:** Resolved

---

## 2. Firmware Utility Execution

### Problem
The MrChromebox firmware utility encountered execution restrictions associated with a noexec-mounted filesystem.

### Resolution
- Identified the filesystem execution restriction.
- Executed the firmware utility from a suitable temporary directory.
- Successfully installed MrChromebox UEFI Full ROM firmware.

**Status:** Resolved

---

## 3. USB Boot and Operating System Installation

### Problem
The original Chromebook firmware restricted conventional operating system installation.

### Resolution
- Installed compatible UEFI firmware.
- Created bootable Kali Linux installation media using Rufus.
- Configured USB boot.
- Successfully installed Kali Linux using the graphical installer.

**Status:** Resolved

---

## 4. Internal Audio Functionality

### Problem
Internal speakers did not initially produce sound after installing Kali Linux.

### Diagnostic Tools
- ALSA
- PulseAudio
- pactl
- amixer

### Investigation
- Identified available audio devices.
- Examined audio profiles and mixer controls.
- Investigated the Intel audio subsystem and DA7219 codec configuration.

### Resolution
Audio configuration troubleshooting restored functionality through the internal speakers and headphones.

**Status:** Resolved

---

## 5. Wireless Connectivity

### Problem
Wireless connectivity required troubleshooting following the operating system conversion.

### Resolution
- Investigated wireless network configuration.
- Established successful wireless connectivity.
- Verified internet access.

**Status:** Resolved

---

## 6. MicroSD Storage Recognition

### Problem
A 64 GB microSD card was initially unavailable within the operating system.

### Resolution
- Investigated removable storage recognition.
- Successfully enabled and mounted the storage device.
- Verified accessibility within Kali Linux.

**Status:** Resolved

---

## 7. Unexpected Battery Drain

### Problem
The Chromebook experienced unexpected battery depletion while believed to be shut down or inactive.

### Verified Battery Diagnostics

| Parameter | Result |
|---|---|
| Battery Model | L17L3PB |
| Manufacturer | LGC |
| Technology | Lithium-ion |
| Cycle Count | 226 |
| Original Design Capacity | 3685 mAh |
| Current Full Charge Capacity | 2585 mAh |
| Estimated Battery Health | 70.1% |
| Estimated Capacity Degradation | 29.9% |

### Diagnostic Methods
- Controlled battery discharge observations.
- Shutdown and startup testing.
- AC power and charging observations.
- Linux power supply subsystem inspection.

Diagnostic command:

```bash
cat /sys/class/power_supply/BAT0/uevent
```

### Preliminary Findings
The battery exhibits measurable capacity degradation. However, battery degradation alone has not been established as the cause of the unexpected overnight discharge.

Further investigation is required to distinguish battery deterioration from firmware, embedded controller, or operating system power management behavior.

**Status:** Under Investigation

---

## 8. Inconsistent Startup Behavior

### Problem
The system occasionally powers on automatically when the lid is opened and has experienced intermittent startup failures.

### Investigation
- Observed lid-triggered startup behavior.
- Tested manual power button recovery.
- Monitored charging indicator behavior.
- Compared battery levels before and after controlled shutdown periods.

### Current Findings
The system remains operational, but the underlying cause of intermittent startup behavior has not been confirmed.

**Status:** Under Investigation

---

## Skills Demonstrated

- Systematic troubleshooting
- Hardware diagnostics
- Firmware modification
- Linux administration
- Command-line diagnostics
- Audio subsystem investigation
- Storage management
- Power management analysis
- Technical documentation
- Root cause investigation

## Lessons Learned

This project reinforced the importance of approaching technical problems systematically, verifying assumptions, documenting results, and distinguishing confirmed findings from potential causes.

Not every technical issue has an immediate solution. Continued investigation and accurate documentation are essential parts of the troubleshooting process.

---

**Project:** Kali Dragon

**Developer:** Zer0Trust404

**Last Updated:** November 25, 2026

*Trust Nothing. Verify Everything.*
