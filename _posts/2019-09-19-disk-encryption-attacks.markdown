---
layout: single
title:  "Disk Encryption Attacks"
date:   2019-09-19 15:27:36 -0400
categories: disk encryption attacks
---

A study guide describing disk encryption attack and defense methods.

### Breaking Cryptoalgorithms and Brute Force Attacks   
- cascade encryption options to make decryption more difficult  
- brute force attacks are currently the most viable strategy 
- [Popular Tools for Brute Force](https://resources.infosecinstitute.com/popular-tools-for-brute-force-attacks/)  
- [Brute Force Attacks Explained](https://www.howtogeek.com/166832/brute-force-attacks-explained-how-all-encryption-is-vulnerable/)  
- [Brute Forcing Linux Full Disk Encryption with Hashcat](https://articles.forensicfocus.com/2018/02/22/bruteforcing-linux-full-disk-encryption-luks-with-hashcat/)  

### Cryptography vs. Quantum Computers  
- cracking symmetric algorithms  
    - 128-bit keys can be broken on a supercomputer  
    - 256-bit keys provide future protection from quantum computers  
- current asymmetric algorithms will eventually need to be replaced   
- [Will Quantum Computers Break Encryption?](https://youtu.be/6H_9l9N3IXU)  
- [How Quantum Computers Break Encryption](https://youtu.be/lvTqbM5Dq4Q)  
- [IBM Warns of Instant Breaking of Encryption by Quantum Computers](https://www.zdnet.com/article/ibm-warns-of-instant-breaking-of-encryption-by-quantum-computers-move-your-data-today/)  

### General Vulnerabilities  
- encryption is hard to get right  
    - it must be arduously tested  
- open source options allow users to scrutinize and update code  
- prone to configuration issues  
    - encryption software is easy to misconfigure  
    - can create vulnerabilities  
- consider nation state backdoors and implementation weakening
- [ScienceDirect - Full Disk Encryption](https://www.sciencedirect.com/topics/computer-science/full-disk-encryption)  
- [Tales from the Crypt: Hardware vs. Software](https://www.infosecurity-magazine.com/magazine-features/tales-crypt-hardware-software/)  

### Software Based Attacks  
- bad design can result in private info being stored in easily accessible areas  
    - there are many attacks we are unaware of  

### Physical Attacks On Disk Encryption  
- hardware keyloggers  
- firmware rootkits  
- spying/shoulder surfing  

- mitigating physical threats  
    - keep your adversaries away from your devices  
    - conceal your device  
    - completely power down your device  
    - always keep your device with you  
- [Ten Simple Steps for Keeping Your Laptop Secure](https://elie.net/blog/privacy/ten-simple-steps-for-keeping-your-laptop-secure/)  
- [Hardware Keyloggers](https://www.sans.org/reading-room/whitepapers/physical/hardware-keyloggers-37125)  
- [Reviews of the Best USB Keyloggers](https://nerdtechy.com/reviews-best-usb-keyloggers)  
- [Rootkits As Fast As Possible](https://youtu.be/0LvF0KtBWxY)  
- [Shoulder Surfing](https://youtu.be/gLKeYf2zLCQ)  
- [Shoulder Surfing from a Distance](https://youtu.be/nyl-Ksc5XG4)  

- [DMA - Direct Memory Access Attacks](https://guides.codepath.com/websecurity/DMA-Attack)  
    - ports that support DMA:  
        - PCI  
        - PCI express  
        - firewire  
        - thunderbolt  
    - if a user gains access to these ports he may be able to obtain your key  
        - can also inject commands to the OS  
    - github: inception - allows DMA attacks  
    - Passware Kit Enterprise  
        - can decrypt disks encrypted with BitLocker, TrueCrypt, FileVault2, or PGP  
        - $1000  
    - WindowsSCOPE Phantom Probe USB Dongle  
        - USB dongle that captures memory screenshot  
    - [Practical DMA Attack on Windows 10](https://www.synacktiv.com/posts/pentest/practical-dma-attack-on-windows-10.html)  
    - [PrivateCore PCI DMA Attack](https://youtu.be/L8nLeQWONSQ)  
    - [Direct Memory Attack the Kernel](https://youtu.be/fXthwl6ShOg)  
    - [PCILeech](https://github.com/ufrisk/pcileech)  
    - [PCILeech - Ulf Fritz interview](https://youtu.be/MIfY8g73xms)  
    - [Why You Should Not Leave Your Computer Unsupervised](https://youtu.be/HDhpy7RpUjM)  
    - [Inception](https://github.com/carmaa/inception)  


- Direct Memory Access Mitigations  
    - MAC OSX 10.7.2/Windows 8.1 and newer  
        - DMA is disabled when the user has locked the OS  
            - prevents firmware DMA attacks  
        - DMA attacks still work while the user is logged on  
    - Windows 10  
        - OS has DMA port protection  
        - can use DataProtection/AllowDirectMemoryAccess MDM policy to block DMA ports at startup  
        - makes DMA attacks more difficult  
    - Macs Newer than 2012  
        - enable VT-D  
            - blocks DMA requests  
    - Qubes OS  
        - provides protection against DMA attacks  
    - [DMA Attack Mitigation](https://en.wikipedia.org/wiki/DMA_attack#Mitigations)  
    - [Stop DMA Attacks](https://www.csoonline.com/article/2607924/stop-sneaky-hackers-from-launching-dma-attacks.html)  
    - [Preventing DMA Attacks](https://security.stackexchange.com/questions/88629/preventing-dma-attacks)  
    - [Intel Virtualization Technology](https://software.intel.com/en-us/articles/intel-virtualization-technology-for-directed-io-vt-d-enhancing-intel-platforms-for-efficient-virtualization-of-io-devices)  

### BootKey Problem  
- the blocks where the OS is stored must be decrypted before the OS can boot  
    - the key must be available before there is a user interface to ask for the password  
        - provides an attack surface  
    - most disk encryption options offer pre-boot authentication  
        - pre-boot environment can be swapped with a less secure option  
        - BootKits can be used to circumvent the pre-boot  
        - the key cannot be decrypted until an external key is input  
    - LUKS and BitLocker can use hardware for encryption  
        - TPM - Trusted Platform Module  
            - ensures the integrity of the boot environment  
            - mitigates attacks that attempt to replace the bootloader with a modified version  
    - Cold Boot Attack  
        - provides a means to obtain a dump of the computer's memory  
            - memory can be reconstructed to reveal the key  
        - a can of duster is used to freeze the memory for longer data retention  
            - memory stays accessible for a short time after shutdown  
            - the memory is removed and placed into another machine where it is dumped  
        - works on DDR1, DDR2, and DDR3 ram  
        - the boot partitions cannot be encrypted with the software implementations of disk encryption  
            - BitLocker needs an unencrypted volume to boot from  
    - [Pre-boot Authentication](https://en.wikipedia.org/wiki/Pre-boot_authentication)  
    - [BitLocker Countermeasurers](https://docs.microsoft.com/en-us/windows/security/information-protection/bitlocker/bitlocker-countermeasures)  
    - [Does Microsoft Claim Pre-boot Authentication is Not Necessary?](https://www.winmagic.com/blog/microsoft-preboot-authenticate-not-necessary/)  
    - [Bootkit](https://attack.mitre.org/techniques/T1067/)  
    - [Attacking Encryption Systems](https://www.secjuice.com/attacking-encryption-systems/)  
    - [TPM - Trusted Platform Module](https://en.wikipedia.org/wiki/Trusted_Platform_Module)  
    - [Cold Boot Attacks On Encryption Keys](https://youtu.be/Ej-Nr79bVjg)  
    - [The Chilling Reality of Cold Boot Attacks](https://youtu.be/E6gzVVjW4yY)  

### Evil Maid Attack  
- attacker boots device using a live CD/USB and changes the bootloader to a hacked version  
- hacked bootloader will save the key and send to attackers  
- if the bootloader is compromised, the entire system is compromised  
- Knowledgeable Evil Maid Attack  
    - adversary with physical access to the machine and knowledge of the where specific files are located on the disk  
    - files can be modified to allow changes to the OS  
- [The Evil Maid Attack](https://youtu.be/0uRxRIJc8zU)  
- [Defend Your MacOS Computer from Malware and Evil Maid Attacks](https://youtu.be/DdHK0TOJp98)  
- [Evil Maid Attack - Wikipedia](https://en.wikipedia.org/wiki/Evil_maid_attack)  
- [F-Secure's Guide to Evil Maid Attacks](https://blog.f-secure.com/f-secures-guide-to-evil-maid-attacks/)  

### Other Hardware Attacks  
- remove storage, place storage unit in similar device with hacked bootloader  
- modified hardware may be installed to capture input  
    - hardware keyloggers, bus mastering device capturing memory, firmware rootkits  
    - hotswapping drives and cables  
- [Hardware Attacks, Backdoors and Electronic Component Qualification](https://resources.infosecinstitute.com/hardware-attacks-backdoors-and-electronic-component-qualification/)  
- [Hardware Cyberattacks: How Worried Should You Be?](https://www.darkreading.com/vulnerabilities---threats/hardware-cyberattacks-how-worried-should-you-be/d/d-id/1333167)  
- [Top 5 Firmware and Hardware Attack Vectors](https://eclypsium.com/2018/12/28/the-top-5-firmware-and-hardware-attack-vectors/)  

### Attacks On Encrypted Containers, Volumes, and Partitions  
- increased attack surface compared to full disk encryption  
- most attacks still apply  
- may fail to encrypt private files  
- opt for whole disk encryption  
- containers allow us to have multiple levels of security  
- containers do not contain any signature of encryption  
    - may allow for plausible deniability  
- use VeraCrypt for encrypted containers  
    - Windows, Mac and Linux  
- [How to Use VeraCrypt Containers to Secure Your Data](https://youtu.be/LMM90jFG30M)  

### Defense Against Disk Decryption Attacks  
- prevent physical access to your device  
    - hide your device  
- setup alerts to notify you of tampering  
    - set up subtle traps to detect tampering  
- do not use the device if you suspect that it has been tampered with  
- do not leave your device unattended and unlocked  
    - consider powering down your device when you are not near  
    - bring your device with you  
- disable ports that support DMA  
    - PCI  
    - PCI Express  
    - FireWire  
    - Thunderbolt  
- use full disk encryption  
- use pre-boot authentication  
    - use multifactor authentication if possible  
    - tokens and keys  
- encrypt bootloader or place on usb  
- use secure boot and tpm where available  
- avoid SSD drives  
- don't put sensitive data on the device until the device is encrypted  
    - always encrypt first  
- make your memory hard to remove from your system  
    - tape, superglue, etc.  
- enable POST in BIOS  
    - mitigates cold boot attacks by overwriting RAM  
- use a BIOS password  
- disable sleep and hibernation  
    - delete hiberfil.sys  
- find where your OS dumps memory and disable memory dumps  
- swap files may contain sensitive information  
    - encrypt your swap  
- read the VeraCrypt documentation  
- [Physical Attacks to Your Computers and Disk Encryption](https://looseleafsecurity.com/episodes/physical-attacks-to-your-computers-and-disk-encryption.html)  
- [Laptop Security Tips](https://www.computerweekly.com/tip/Laptop-security-tips-The-physical-perspective)  

### Additional Resources  
- The clock is ticking for encryption  
    - [https://www.csoonline.com/article/2127865/the-clock-is-ticking-for-encryption.amp.html](https://www.csoonline.com/article/2127865/the-clock-is-ticking-for-encryption.amp.html)