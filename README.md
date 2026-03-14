# Lenovo ThinkPad T440p Official BIOS 2.56

This repository contains the official Lenovo BIOS version 2.56 (GLETA2WW) for ThinkPad T440p, extracted directly from the SPI flash chips.

## BIOS Chips Information

The T440p BIOS is stored in two separate SPI flash chips on the motherboard:

| Position | Chip Model | Size | File |
|----------|------------|------|------|
| U49 | Winbond W25Q32.V | 4MB | `4mb_bios_U49.bin` |
| U113 | Winbond W25Q64.V | 8MB | `8mb_bios_U113.bin` |

### Modified BIOS

- **Advanced BIOS for U49**: `advanced_bios_For_U49.bin` (signed modified version)

### Chip Locations

- **U49 (4MB)**: Located on the RAM side of the motherboard, easily accessible
- **U113 (8MB)**: Located near U49, may be partially covered by plastic housing

## File Contents

### 8MB BIOS (U113 - W25Q64)
- Flash Descriptor Region
- Intel Management Engine (ME) Region
- Required for system boot

### 4MB BIOS (U49 - W25Q32)
- Main BIOS Region
- UEFI Firmware Volumes
- System firmware

### Advanced BIOS (U49 - Modified)
- Based on original 4MB BIOS
- Signed modified version
- Enhanced features and capabilities

## Version Information

- **BIOS Version**: GLETA2WW (2.56)
- **Release Date**: 2021
- **Source**: Official Lenovo BIOS Update

## Flashing Instructions

### Requirements
- CH341A Flash Programmer
- SOIC8 Test Clip (1.27mm pitch)
- Computer with USB port
- Ensure your current BIOS version is 2.56

### Steps for Modified BIOS

1. **Power off the laptop completely** and disconnect the battery

2. **Connect CH341A to the U49 chip** (4MB):
   - Pin 1 indicator (dot) on chip aligns with clip pin 1
   - Ensure good contact with all 8 pins

3. **Read and backup current BIOS**:
   ```
   # Always backup first!
   Read from chip -> Save as backup.bin
   ```

4. **Flash the modified BIOS**:
   - For U49 (4MB chip): Write `advanced_bios_For_U49.bin` (signed modified version)

5. **Verify after writing**:
   - Use "Verify" function in CH341A software
   - Ensure no errors

### Special Case: Machine fails to pass POST

If your machine fails to pass POST (power light stays on but no error beeps), you need to:

1. **Completely remove the bottom case** of the laptop

2. **Locate the U113 flash chip**:
   - Position: South of U49 (away from battery side)
   - Model: Winbond W25Q64.V (8MB)

3. **Flash both chips**:
   - For U113 (8MB chip): Write `8mb_bios_U113.bin`
   - For U49 (4MB chip): Write `advanced_bios_For_U49.bin`

4. **Verify both chips after writing**



## Troubleshooting

### 5 Beeps on Boot
- BIOS checksum error
- Ensure both chips are flashed correctly
- Verify 4MB and 8MB files match

### Boot Loop (Fan spins then restarts)
- Flash Descriptor may be corrupted
- Re-flash the 8MB chip (U113)
- Ensure Flash Descriptor signature (5A A5 F0 0F) is present at offset 0x10

### No Display / Black Screen
- Check chip connections
- Verify both chips are properly seated
- Try re-flashing both chips

## Warning

⚠️ **BIOS flashing carries risk!**

- Always backup your current BIOS before flashing
- Ensure stable power during flashing process
- Use correct file for each chip (4MB vs 8MB)
- I am not responsible for any damage to your device

## References

- [Lenovo T440p Support Page](https://support.lenovo.com/)
- [CH341A Programmer](https://github.com/niccokunzmann/ch341a-programmer)
- [UEFITool](https://github.com/LongSoft/UEFITool)

## License

These BIOS files are property of Lenovo. This repository is for backup and educational purposes only.

## Credits

- Extracted and verified by community contribution
- BIOS version 2.56 (GLETA2WW)
