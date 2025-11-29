# Asus Chromebox 3 (i7-8550U) macOS Tahoe 26.1 EFI

This repository contains the EFI files for running macOS Tahoe 26.1 on the Asus Chromebox 3 with an Intel i7-8550U CPU

![image](https://github.com/mnzaroo/Chromebox3CN65-Tahoe-EFI/blob/main/CN65Tahoe26.1.png)

### Specifications

- **Model:** Asus Chromebox 3
- **CPU:** Intel Core i7-8550U
- **GPU:** Intel UHD 620
- **RAM:** 16GB DDR4 (user-upgraded)
- **Storage:** 512GB NVMe SSD (user-upgraded)
- **Audio:** Realtek ALC5650
- **Wi-Fi:** Intel
- **macOS Version:** Tahoe 26.1
- **Drivers:** All of kexts up to date (28/11/2025)

### What's Working

- [x] Intel UHD 620 Graphics (with hardware acceleration)
- [x] Audio (internal speakers, microphone, headphone jack)
- [x] Wi-Fi via Heliport(Use Heliport.dmg)
- [x] USB Ports (Type-A and Type-C)
- [x] HDMI output
- [x] Sleep/Wake
- [x] Brightness Control
- [x] Ethernet
- [x] macOS Power Management (including CPU power states)

### Not Working / Issues

- [ ] SD Card Reader (if present, typically unsupported in macOS)
- [ ] Thunderbolt 3 (if present, hot-plug may not work)
- [ ] Occasional wake from sleep issues (depends on ACPI patch configuration)

### Coreboot Configuration

To run macOS smoothly on the Asus Chromebox 3, it is recommended to replace the stock firmware with Coreboot. Here's a brief overview of the process:

1. **Install and Configure MrChromebox Coreboot**:
    - Follow the instructions on [MrChromebox.tech](https://mrchromebox.tech) to flash Coreboot firmware.
    - Ensure the firmware is configured to allow UEFI boot mode.

2. **Bootloader Setup**:
    - Use OpenCore as the bootloader. The EFI folder provided in this repository is already configured for optimal compatibility with macOS Tahoe.

3. **Disable Write Protection**:
    - Before flashing, you may need to disable write protection by removing the WP screw on the motherboard.

4. **Update Firmware**:
    - Use the MrChromebox script to install the UEFI firmware. This will replace the factory BIOS with Coreboot.

### Installation

1. **Prepare macOS USB Installer**: Create a macOS Sequoia 15.4 installer using [macOS Recovery](https://support.apple.com/en-us/HT201372) or from a working macOS environment.

2. **Copy EFI Folder**: After creating the USB installer, replace the EFI folder on the USB drive with the one from this repository.

3. **Boot the Installer**: Boot from the USB installer and follow the standard macOS installation steps.

4. **Post-Installation**:
    - Copy the EFI folder from the USB to your system's EFI partition after installing macOS.
    - Generate your own SMBIOS using [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS) and replace the `SerialNumber`, `BoardSerialNumber`, and `SmUUID` in `config.plist`.

### Known Issues & Troubleshooting

- **Wake from Sleep Issues**: If the system does not wake from sleep properly, try adjusting the `Darkwake` settings in `config.plist`.
