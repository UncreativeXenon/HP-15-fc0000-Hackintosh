# HP 15-fc0000 - Sequoia
HP Laptop 15-fc0000 series EFI - Created with Dortania's OpenCore Install Guide

**Processor:** Ryzen 7 7730U (This would probably work with [other processors HP produces the laptop with](https://support.hp.com/us-en/document/ish_7412013-7412050-16)).

### Notes (MUST DO)
I included a censored `config.plist` file named `censored_config.plist`. You will have to rename it and add your own MLB, ROM, SystemSerialNumber and SystemUUID, use [this guide](https://dortania.github.io/OpenCore-Install-Guide/AMD/zen.html#platforminfo) for doing so, I personally used `MacBookPro16,3` but it can be different depending on the processor.

Another very important thing you **must** do is raise iGPU vram to 2GB or otherwise most apps won't work or they'll be very slow, usually this option is available within UEFI settings but unfortunately HP likes to lock settings like this behind (on some laptops).

Hence we're gonna need to use a tool called [Smokeless_UMAF](https://github.com/DavidS95/Smokeless_UMAF) (DO **NOT** USE THE BETA VERSION), navigate through **Device Manager > AMD CBS > NBIO Common Options > GFX Configuration**.

Set iGPU Configuration to "__UMA_GAME_OPTIMIZED__", then save and exit. 

**Important note:** usually people would set it to UMA_SPECIFIED and select 2G, however for some reason that doesn't work on this HP Laptop, possibly has to do with the UEFI reverting the change, **so a very good act would be to avoid *ever* updating the UEFI firmware as this might get patched eventually, be careful**.

### Troubleshooting
#### Post-Install Kernel Panic 
If you are using this EFI folder on a different laptop model, but similarly specced and get a kernel panic after installing MacOS, make sure to customize the USB port configuration to match your device.<br/> 
Also, you can avoid rebooting after a kernel panic by adding the following boot args: `debug=0x100` and `keepsyms=1` .
