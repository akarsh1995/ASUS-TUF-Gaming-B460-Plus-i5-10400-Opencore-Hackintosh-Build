# ASUS TUF Gaming B460 Plus i5-10400 Opencore Hackintosh Build.

![OpenCore Icon](https://github.com/acidanthera/OpenCorePkg/raw/master/Docs/Logos/OpenCore_with_text_Small.png)

![desktop](screenshots/desktop.png)
![benchmark-cpu](screenshots/benchmark-cpu.png)

## OpenCore Version: 0.6.2 (DEBUG)

## Guide Link: [Dortania's](https://dortania.github.io/OpenCore-Install-Guide/)


### Specifications 

| Part        | Specs                                       |
|-------------|---------------------------------------------|
| CPU         | Intel® Core™ i5-10400                       |
| iGPU        | Intel® UHD Graphics 630                     |
| dGPU        | NVIDIA 1650 Super (Disabled)                |
| Audio       | Realtek S1200A codec *layout-id: 1*         |
| Ethernet    | Intel® I219-V LAN                           |
| WiFi        | **Will update once I receive module**       |
| RAM         | HyperX FURY DDR4 HX432C16FB3/8 (X2)         |
| SSD         | Crucial P5 500GB 3D NAND NVMe CT500P5SSD8   |
| Motherboard | ASUS TUF Gaming B460 Plus BIOS Version 1401 |

### Working/Not working

| Works              | Feature                                      |
|--------------------|----------------------------------------------|
| :white_check_mark: | Apple TV+, Siri, iTunes, Appstore, Facetime  |
| :white_check_mark: | All USB External Ports including F-Panel [1] |
| :white_check_mark: | Sound + Mic                                  |
| :white_check_mark: | HDMI (Audio + Graphics)                      |
| :white_check_mark: | DRM Content                                  |
| :white_check_mark: | Power Management (1300 MHz TFM)              |
| :white_check_mark: | iGPU Stability                               |
| :white_check_mark: | Sleep (also with peripherals plugged in)     |
| :white_check_mark: | Ethernet                                     |
| :x:                | External HDD via USB3.0 [2]                  |

[1] NOTE: Internal Ports need to be mapped in `USBMap.kext`. Once I receive my Fenvi T919 I'll remap and update the repo. Kindly map if you plan to use internal usb ports. Generate a pull request.  

[2] Perhaps power issue (Will try my best resolving.)

### Installation Notes
- Rename [sample_config.plist](OC/sample_config.plist#L899) to config.plist
- Replace the SMBIOS Information generating a new one. [iMac20,1](https://dortania.github.io/OpenCore-Install-Guide/config.plist/comet-lake.html#platforminfo)

### BIOS Profile.

- Load [BIOS profile](BIOS/HackintoshBuild.CMO) file using utility provided in ASUS BIOS (BIOS version 1401).
- XMP Enabled 

### Benchmarks:
- [CPU GeekBench](https://browser.geekbench.com/v5/cpu/4534195)
- [GPU GeekBench](https://browser.geekbench.com/v5/compute/1771511)

### What not goes along with the Dortania's Guide.

- `XHCI-unsupported.kext` needed to be added (probably B460 chipset issue).
- `DeviceProperties -> PciRoot(0x0)/Pci(0x2,0x0) - device-id = 983E0000` alongwith framebuffer patching. 
  *Stumbled this error when app:* 
  - Alacritty: Thrown ```Assertion failed: (0), function CreateCompiler, file /Library/Caches/com.apple.xbs/Sources/GPUDriversIntel/GPUDriversIntel-14.7.8/GLRenderer/kbl/usc_interface.cpp, line 1676.``` 
  - Safari: Pages were crashing. 

### Other References: 
  - [Intel® UHD Graphics 630 fix](https://www.reddit.com/r/hackintosh/comments/gx4oyk/uhd_630_graphics_fix_for_open_core/)
