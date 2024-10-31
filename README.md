# HP 15-fc0000 - Sequoia
HP Laptop 15-fc0000 series EFI - Created with Dortania's OpenCore Install Guide

**Processor:** Ryzen 7 7730U (This would probably work with [other processors HP produces the laptop with](https://support.hp.com/us-en/document/ish_7412013-7412050-16)).

### Note
I included a censored `config.plist` file named `censored_config.plist`. You will have to rename it and add your own MLB, ROM, SystemSerialNumber and SystemUUID, use [this guide](https://dortania.github.io/OpenCore-Install-Guide/AMD/zen.html#platforminfo) for doing so, I personally used `MacBookPro16,3` but it can be different depending on the processor.

### Troubleshooting
#### Post-Install Kernel Panic 
If you are using this EFI folder on a different laptop model, but similarly specced and get a kernel panic after installing MacOS, make sure to customize the USB port configuration to match your device.<br/> 
Also, you can avoid rebooting after a kernel panic by adding the following boot args: `debug=0x100` and `keepsyms=1` .
