## Opencore Config for Intel SandyBridge + NVIDIA GeForce 210
### Tested on macOS Mojave 10.14
#### Overview:
&radic;  NVIDIA GeForce 210 Working [ [Legacy Video Patch](https://github.com/chris1111/Legacy-Video-patch "Legacy Video Patch") ]<br>
&radic;  Audio + Mic<br>
&radic;  Sleeping<br>
&radic;  USB Mapping<br>

#### Specification :
• Mainboard : MSI MS-7788 H61M-P31 (G3)<br>
• Chipset : Intel® H61 (B3)<br>
• Processor : Intel® Core&trade; i3-200 CPU @ 3.10GHz (4 CPUs)<br>
• RAM : 6GB DDR3<br>
• BIOS : UEFI MSI-Built In V 3.6<br>
• Audio : Realtek® ALC887<br>
• Ethernet : PCI Express LAN 10/100/1000 Fast Ethernet by Realtek 8111E<br>
• VGA : NVIDIA GeForce 210 - PCI Express 1024MB<br>
• Bootloader : **OpenCore version 0.7.5**<br>


## OpenCore Starting Point : [Install Guide](https://dortania.github.io/OpenCore-Install-Guide/ "Install Guide")

#### ACPI
- Add

SSDTs | Description | 
--- | --- |
SSDT-EC | *[Fixing Embedded Controllers](https://dortania.github.io/Getting-Started-With-ACPI/Universal/ec-methods/prebuilt.html "Fixing Embedded Controllers")*
SSDT-PLUG | Plugin
SSDT-PM | Power management, generated by [ssdtPRGen](https://dortania.github.io/OpenCore-Post-Install/universal/pm.html#sandy-and-ivy-bridge-power-management "ssdtPRGen")
SSDT-PMC | Fixing NVRAM
SSDT-SBUS-MCHC | Fixing SMbus Support

- Delete

Delete | Description
--- | --- |
CpuPm | Power management for Sandy Bridge
Cpu0lst | Power management for Sandy Bridge

- Patch

Patch | Description
--- | --- |
EHC1 -> EH01 | USB rename
EHC2 -> EH02 | USB rename

#### Kexts
Kext | Description
--- | --- |
RealtekRTL8111.kext | Ethernet Driver
USBMapLegacy.kext |  *[USB Mapping](https://dortania.github.io/OpenCore-Post-Install/usb/intel-mapping/intel.html "USB Mapping")*

## Directories
```
├── EFI
│   └── OC
│       ├── ACPI
│       │   ├── SSDT-EC.aml
│       │   ├── SSDT-PLUG.aml
│       │   ├── SSDT-PM.aml
│       │   ├── SSDT-PMC.aml
│       │   └── SSDT-SBUS-MCHC.aml
│       ├── Drivers
│       │   ├── AudioDxe.efi
│       │   ├── OpenCanopy.efi
│       │   ├── OpenHfsPlus.efi
│       │   └── OpenRuntime.efi
│       ├── Kexts
│       │   ├── AppleALC.kext
│       │   ├── Lilu.kext
│       │   ├── SMCProcessor.kext
│       │   ├── SMCSuperIO.kext
│       │   ├── NVMeFix.kext.kext
│       │   ├── VirtualSMC.kext
│       │   ├── RealtekRTL8111.kext
│       │   └── USBMapLegacy.kext
│       │   └── WhateverGreen.kext
│       ├── OpenCore.efi
│       └── config.plist
```



