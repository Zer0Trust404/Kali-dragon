# 🔋 Kali Dragon - Power Management Investigation

[← Return to Project Overview](README.md)

## Investigation Overview

Following the successful conversion of a Lenovo 100e Chromebook into a Kali Linux workstation, I observed unexpected battery discharge and inconsistent startup behavior.

This investigation focuses on identifying potential hardware, firmware, embedded controller, and operating system power management issues through controlled testing and Linux diagnostic tools.

**Investigation Status:** Active / Ongoing

## 1. Observed Symptoms

- Unexpected overnight battery depletion.
- Battery discharge while the system was believed to be powered off.
- Automatic startup when opening the laptop lid.
- Intermittent startup failures.
- Flashing red charging indicator.
- Occasional need for manual power cycling.
- Inconsistent battery retention between shutdown tests.

## 2. Hardware Environment

| Component | Specification |
|---|---|
| Device | Lenovo 100e Chromebook |
| Board | Google Robo Rev3 / Coral |
| Processor | Intel Celeron N3350 |
| Memory | 4 GB RAM |
| Internal Storage | 16 GB eMMC |
| Operating System | Kali Linux Rolling 2026.3 |
| Kernel | 7.2.15+kali-amd64 |
| Firmware | MrChromebox UEFI Full ROM |
| Firmware Version | MrChromebox-2609.3 |
| Power Adapter | 45W USB-C |

## 3. Battery Diagnostics

Battery information was collected directly from the Linux kernel power supply subsystem on November 25, 2026.

### Diagnostic Command

```bash
cat /sys/class/power_supply/BAT0/uevent
```

### Verified Battery Information

| Parameter | Result |
|---|---|
| Battery Model | L17L3PB |
| Manufacturer | LGC |
| Technology | Lithium-ion |
| Cycle Count | 226 |
| Design Capacity | 3685 mAh |
| Full Charge Capacity | 2585 mAh |
| Current Charge | 1968 mAh |
| Charge Percentage | 76% |
| Battery Voltage | 11.875 V |
| Discharge Current | 219 mA |
| Charge Threshold | 100% |
| Battery Status | Discharging |
| Capacity Level | Normal |

## 4. Battery Health Analysis

Battery health was estimated by comparing the current full charge capacity against the original design capacity.

### Calculation

```text
Battery Health = (Full Charge Capacity / Design Capacity) x 100

Battery Health = (2585 / 3685) x 100

Battery Health = 70.1%
```

| Metric | Result |
|---|---|
| Estimated Battery Health | 70.1% |
| Estimated Capacity Loss | 29.9% |
| Lost Charge Capacity | 1100 mAh |

The battery has experienced measurable degradation. However, reduced battery capacity alone does not establish the cause of the unexpected overnight discharge.

## 5. Controlled Shutdown Testing

Several shutdown and battery retention tests were performed to investigate whether the system continued consuming power while inactive.

| Test | Starting Charge | Ending Charge | Duration | Observation |
|---|---|---|---|---|
| Overnight Test | 100% | 0% | Overnight | Unexpected battery depletion |
| Overnight Test | 85% | 0% | Overnight | Unexpected battery depletion |
| Controlled Test 1 | 81% | 79% | Approximately 1 hour | 2 percentage point decrease |
| Controlled Test 2 | 79% | 78% | Approximately 1 hour | 1 percentage point decrease |

The shorter controlled tests showed substantially less battery depletion than the overnight observations.

Additional testing is required to determine whether the device consistently enters a complete shutdown state.

## 6. Power Supply Detection

The Linux kernel successfully identified the following power supply interfaces:

```bash
ls /sys/class/power_supply/
```

Detected interfaces:

```text
AC
BAT0
CROS_USBPD_CHARGER0
CROS_USBPD_CHARGER1
```

These results confirm that Linux recognizes the internal battery, AC power interface, and Chromebook USB-C power delivery interfaces.

Detection alone does not confirm that all power management functions operate correctly.

## 7. Potential Root Causes

| Potential Cause | Investigation Status |
|---|---|
| Battery degradation | Confirmed capacity loss |
| Incomplete system shutdown | Under Investigation |
| Firmware power management behavior | Under Investigation |
| Embedded controller behavior | Under Investigation |
| Lid-triggered startup | Observed |
| ACPI compatibility | Under Investigation |
| Abnormal standby power consumption | Under Investigation |

No definitive root cause has been established.

## 8. Diagnostic Commands

### Check Battery Percentage

```bash
cat /sys/class/power_supply/BAT0/capacity
```

### Check Battery Status

```bash
cat /sys/class/power_supply/BAT0/status
```

### Check Battery Design Capacity

```bash
cat /sys/class/power_supply/BAT0/charge_full_design
```

### Check Current Full Charge Capacity

```bash
cat /sys/class/power_supply/BAT0/charge_full
```

### Check AC Power Status

```bash
cat /sys/class/power_supply/AC/online
```

### Review Firmware Information

```bash
sudo dmidecode -t bios
```

### Initiate System Power Off

```bash
sudo systemctl poweroff
```

### Review Previous Boot Logs

```bash
journalctl -b -1
```

Previous boot logs are available only if the system retained them.

## 9. Future Investigation Plan

- [x] Verify battery detection.
- [x] Identify battery model and manufacturer.
- [x] Calculate estimated battery health.
- [x] Verify installed firmware version.
- [x] Perform initial controlled shutdown tests.
- [ ] Perform additional overnight shutdown tests.
- [ ] Record battery retention over extended periods.
- [ ] Investigate lid-triggered startup behavior.
- [ ] Review ACPI and embedded controller behavior.
- [ ] Determine whether battery replacement is necessary.
- [ ] Identify and verify the root cause.

## 10. Skills Demonstrated

- Hardware diagnostics
- Battery health analysis
- Linux kernel interface inspection
- Firmware verification
- Power management troubleshooting
- Controlled testing
- Data collection and analysis
- Root cause investigation
- Technical documentation

## 11. Preliminary Conclusion

Kali Dragon remains operational as a portable cybersecurity workstation despite ongoing power management concerns.

The investigation has confirmed battery capacity degradation and identified inconsistent battery retention and startup behavior.

Further testing is necessary before determining whether the primary issue is related to the battery, firmware, embedded controller, or operating system power management.

This investigation will continue as part of the ongoing development of Kali Dragon.

---

**Project:** Kali Dragon

**Developer:** Zer0Trust404

**Last Updated:** November 25, 2026

**Status:** Investigation Ongoing

*Trust Nothing. Verify Everything.*
