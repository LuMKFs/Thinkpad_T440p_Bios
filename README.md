# Lenovo ThinkPad T440p Modded BIOS 2.56 (GLETA2WW)

This repository provides the official and modified BIOS firmware for the Lenovo ThinkPad T440p. This mod is specifically designed to unlock the hidden potential of this legendary workstation.

## ⚠️ CRITICAL REQUIREMENT

**Your ThinkPad T440p MUST already be running Official BIOS Version 2.56 (GLETA2WW) before flashing these files.**

* Using these files on a machine with a different BIOS version (e.g., 2.36 or 2.53) may result in a **brick** or **5-beep boot error** due to version mismatches in the Embedded Controller (EC) firmware.

---

## Mod Features

The `advanced_bios_For_U49.bin` includes the following professional modifications:

### 1. Wi-Fi & WWAN Whitelist Removal

* **Bypass Hardware Restrictions**: You can now install any M.2 Wi-Fi card (e.g., Intel AX210 Wi-Fi 6E) without the "Unauthorized network card" boot error.
* **WWAN Freedom**: Support for non-Lenovo branded cellular modems in the WWAN slot.

### 2. Unlocked "Advanced" Menu

Access the hidden BIOS settings previously reserved for Lenovo engineers:

* **CPU Tweaks**: Adjust Power Limits (PL1/PL2), ConfigTDP, and Turbo Activation Ratios.
* **Memory Timings**: Fine-tune RAM frequency and latency settings.
* **Video/Graphics**: Adjust Pre-Allocated Memory for Integrated Graphics (iGPU).
* **Thermal Management**: Advanced fan control and thermal trip point configurations.
* **Lake Tiny**: Toggle Intel I/O performance bottleneck bypass for faster storage response.

---

## BIOS Chips & Files Information

The T440p motherboard contains two SPI flash chips that must be handled correctly:

| Position | Chip Model | Size | File Name | Description |
| --- | --- | --- | --- | --- |
| **U49** | Winbond W25Q32 | 4MB | `4mb_bios_U49.bin` | Original BIOS Region |
| **U113** | Winbond W25Q64 | 8MB | `8mb_bios_U113.bin` | ME Region & Descriptor |
| **MOD** | **Winbond W25Q32** | **4MB** | `advanced_bios_For_U49.bin` | **Modified BIOS (Flash to U49)** |

---

## Flashing Instructions (Hardware Required)

### Hardware Tools

* **Programmer**: CH341A USB Programmer.
* **Clip**: SOIC8 Test Clip.
* **Software**: AsProgrammer or NeoProgrammer.

### Steps

1. **Preparation**: Remove all power sources (Battery and AC Adapter).
2. **Backup**: Always read and save your current U49 and U113 chips twice and compare their MD5 hashes to ensure a 100% valid backup.
3. **Flashing U49**:
* Open `advanced_bios_For_U49.bin`.
* Write and Verify to the **4MB chip (U49)**.


4. **Boot**: Reassemble and power on. If the system beeps 5 times or shows a black screen, proceed to flash the `8mb_bios_U113.bin` to the 8MB chip to ensure the entire SPI stack is synchronized.

---

## Troubleshooting

* **5 Beeps on Boot**: Indicates a digital signature/checksum mismatch. Ensure you are flashing the "Signed" mod provided in this repo.
* **Black Screen / No POST**: Check the seating of the SOIC8 clip. Ensure the red wire on the clip aligns with Pin 1 (dot) on the chip.
* **Boot Loop**: Try clearing the CMOS by removing the coin-cell battery for 30 seconds.

## Disclaimer

⚠️ **FLASH AT YOUR OWN RISK.**
BIOS flashing is a high-risk operation. I am not responsible for any hardware damage, data loss, or bricked devices. This repository is for educational and backup purposes only.
