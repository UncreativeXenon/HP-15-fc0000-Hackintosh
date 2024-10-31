# HP 15-fc0000 - Sequoia
HP Laptop 15-fc0000 series EFI - Created with Dortania's OpenCore Install Guide

**Processor:** Ryzen 7 7730U (This would probably work with [other processors HP produces the laptop with](https://support.hp.com/us-en/document/ish_7412013-7412050-16)).

### Notes (MUST DO)
I included two censored `config.plist` files named `censored_config.plist` and `censored_config_no_nootedred.plist` (second is for installation process only). You will have to rename it and add your own MLB, ROM, SystemSerialNumber and SystemUUID, use [this guide](https://dortania.github.io/OpenCore-Install-Guide/AMD/zen.html#platforminfo) for doing so, I personally used `MacBookPro16,3` but it can be different depending on the processor.

The installer only won't work due to the NootedRed kext, for some reason it causes the installation to not work on Sonomo and above (Ventura works fine), for this NootedRed needs to be removed temporarily from the current config.plist then re-added after the installation is complete, to make things easier you can just use the `censored_config_no_nootedred.plist` file for installation and switch to the other after being done.

**The installer will also need Android USB Tethering for installation**.

Another very important thing you **must** do is raise iGPU vram to 2GB or otherwise most apps won't work or they'll be very slow, usually this option is available within UEFI settings but unfortunately HP likes to lock settings like this behind (on some laptops).

Hence we're gonna need to use a tool called [Smokeless_UMAF](https://github.com/DavidS95/Smokeless_UMAF) (DO **NOT** USE THE BETA VERSION), navigate through **Device Manager > AMD CBS > NBIO Common Options > GFX Configuration**.

Set iGPU Configuration to "**UMA_GAME_OPTIMIZED**", then save and exit. 

**Important note:** usually people would set this to "UMA_SPECIFIED" and select 2G, however for some reason that doesn't work on this HP Laptop, possibly has to do with the UEFI reverting the change, **so a very good act would be to avoid *ever* updating the UEFI firmware as the current solution might get patched eventually**, be careful.

### Troubleshooting
#### Post-Install Kernel Panic 
If you are using this EFI folder on a different laptop model, but similarly specced and get a kernel panic after installing MacOS, make sure to customize the USB port configuration to match your device.<br/> 
Also, you can avoid rebooting after a kernel panic by adding the following boot args: `debug=0x100` and `keepsyms=1`.

#### Apps won't work or they're very slow
[Refer to the notes above](https://github.com/Isaac-zsh/HP-15-fc0000-Ryzentosh-Hackintosh/tree/main?tab=readme-ov-file#notes-must-do).

### Post-Install
#### Wi-Fi 
Since there are no MacOS drivers for Realtek cards you will need to use an external adapter, and for the adapter to work you will most likely need to use [this](https://github.com/chris1111/Wireless-USB-Big-Sur-Adapter) too.

#### Bluetooth 
Bluetooth also doesn't work so you will need a dongle, I personally use a CSR V4.0 and it works out of the box, bluetooth needs to be turned off and on after the dongle is connected for it to work.

if you have a CSR V5.0 and you're experiencing issues [try this](https://www.reddit.com/r/hackintosh/comments/1g4z5te/how_to_make_generic_csr_usb_bluetooth_5040_dongle/).

#### Microphone
Microphone works perfectly fine, but to make it work you need to use [this](https://github.com/qhuyduong/AMDMicrophone).

### Contact
If you need help or for any issues add me on discord: **isaac.zsh** (sometimes isaac.one).

I'm also in the [AMD OS X Discord Server](https://discord.com/invite/EfCYAJW).
