# Ryzen-5950X-X570-PRO-WIFI-OpenCore



# Spec

- CPU: Ryzen 9 5950X
- Motherboard: Gigabyte AORUS X570 Pro (Bios Revision - F33a) (overclock)
- RAM: Corsair Pro Vengeance 32GB (16GB * 2) DDR4 3600Mhz
- Graphics: Sapphire RX 6800 XT 
- Case : Lian Li PC-O11DW Dynamic
- SSD: 
    - Samsung 990 PRO SSD PCIe 4.0~~WD SN850 1TB PCIE4~~ (m.2 slot 1) - macOS 
    - ~~Samsung 970 EVO PLUS 1T (m.2 slot 2) - storage~~
    - WD SN770 2TB PCIE4 (m.2 slot 2) - storage
- PSU: Corsair RM1000x 80 Plus Gold 1000W
- WiFi-Bluetooth: Fenvi T919 BCM94360CD 802.11AC WI-FI With Bluetooth 4.0 PCIe
- Cooling : Thermaltake TH 360 ARGB AIO 
- Network Card: ~~Comfast Aquantia AQC107~~ Intel x520-DA1 (with RJ45 adaptor)
- Installed Operating Systems: Ventura 13.3.1
- Bootloader: OpenCore 0.9.1

<!--more--> 

Note

- If I insert WD SN850 1TB PCIE4 into m.2 slot 2，and insert WD SN770 2TB PCIE4 into m.2 slot 2，the speed of SN850 PCIE4 decreases. Considering WD SN850 1TB PCIE4 is the system disk, SN850 should be inserted into slot 1(refer to the detailed benchmark)

# Works and Not-works

Things that don't work

- Sound including the case's front and back headphones 3.5mm port

Things that work

- Airdrop
- WiFi / Bluetooth
- iCloud
- Hardware Acceleration
- Facetime
- Handoff

# BIOS Setting

**Bios Settings**

- *Enter BIOS* -> Press Delete -> Enter Setup
- Save & Exit -> Load Optimized Defaults
- Boot -> CSM Support -> Disabled
    - **Must be off, GPU errors like `gIO` are common when this option in enabled**

- Boot -> Fast boot -> Disabled
- Boot -> Secure boot -> Disabled
- Tweaker -  Advanced CPU Settings - SVM Mode Enable
- Settings -> IO Ports -> Above 4G Decoding -> Enable
- Settings - IO Ports - Onboard LAN Controller Disable
- Settings -> IO Ports - Disable onboard network adapter
- Settings -> IO Ports -> USB Configuration -> Legacy USB Support -> Auto
- Settings -> IO Ports -> USB Configuration -> XHCI Hand-off: enable

**Disable**

- Serial/COM Port
- Parallel Port

**Enable**

- Above 4G decoding(This must be on, if you can't find the option then add `npci=0x2000` to boot-args. Do not have both this option and npci enabled at the same time.)

    - If you are on a Gigabyte/Aorus or an AsRock motherboard, enabling this option may break certain drivers(ie. Ethernet) and/or boot failures on other OSes, if it does happen then disable this option and opt for npci instead
- 2020+ BIOS Notes: When enabling Above4G, Resizable BAR Support may become an available on some X570 and newer motherboards. Please ensure this is **Disabled** instead of set to Auto.

- EHCI/XHCI Hand-off

- OS type: Windows 8.1/10 UEFI Mode （my motherboard doesn't have this setting）

- SATA Mode: AHCI

# Update Notes

- [2023-4-10] tried to upgrade to macOS Monterey 12.6.4
    - failed，because Monterey requires OC 0.7.4 or newer, from https://forum.amd-osx.com/threads/audiogods-gigabyte-aorus-x570-pro-pro-wifi-ultra-master-big-sur-monterey-beta-opencore-0-7-4-efi.1344/page-55

- [2023-4-12] upgrade to Ventura 13.3.1
    - Don't forget to update `cpuid_cores_per_package` as per https://github.com/AMD-OSX/AMD_Vanilla , since for >=13.3，a new `cpuid_cores_per_package` is added

# Benchmark

Refer to https://swsmile.info/post/amd-ryzen-hackintosh-5950x-x570/

# Details 

Refer to https://swsmile.info/post/amd-ryzen-hackintosh-5950x-x570/