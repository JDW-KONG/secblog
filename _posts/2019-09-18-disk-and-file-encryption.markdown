---
layout: single
title:  "File and Disk Encryption"
date:   2019-09-18 23:39:36 -0400
categories: disk encryption file security
---

A study guide introducing readers to file and disk encryption.

### What is Disk Encryption Good for?  
- protects data by converting it into an unreadable format  
    - restricts access to only certain users  
    - offers cryptographic protection of data on multiple mediums
- [Encrypting Your Laptop Like You Mean It](https://theintercept.com/2015/04/27/encrypting-laptop-like-mean/)  
- [Drive Encryption: Your Computer is at Risk](https://youtu.be/0NfvKci3WF0)  
- [How Does Encryption Work?](https://youtu.be/clWEKq8CVOk)  
- [What is Data Encryption?](https://heimdalsecurity.com/blog/free-encryption-software-tools/)  
- [Should You Encrypt Your Computer's Hard Drive?](https://youtu.be/12pQG8sHILY)  
- [Disk Encryption: Why You Still Need It](https://youtu.be/_rBA4xRj5sY)  


### Software Based Disk Encryption  
- [dm-crypt](https://wiki.archlinux.org/index.php/dm-crypt) and [LUKS: Linux Unified Key Setup](https://gitlab.com/cryptsetup/cryptsetup/)  
- [VeraCrypt](https://www.veracrypt.fr/en/Home.html) - Windows, MacOS, and Linux  
- [FileVault2](https://support.apple.com/en-us/HT204837) - MacOS  
- [Bitlocker](https://docs.microsoft.com/en-us/windows/security/information-protection/bitlocker/bitlocker-overview) - Windows  
- [The Best Encryption Software for 2019](https://www.pcmag.com/article/347066/the-best-encryption-software)  


### Hardware Based Disk Encryption  
- SED : [Self Encrypting Drives](https://youtu.be/sxfuCmzE5Ok)  
- some SSDs come with hardware encryption  
    - always use a password  
- can be effective when combined with other forms of encryption  
- [Understanding Hardware Based Encryption](https://youtu.be/sxfuCmzE5Ok)  
- [Self Encrypting Drives are Hardly Any Better Than Software-Based Encryption](https://www.pcworld.com/article/3004670/self-encrypting-drives-are-hardly-any-better-than-software-based-encryption.html)  
- [Flaws in Self Encrypting SSDs Let Attackers Bypass Disk Encryption](https://www.zdnet.com/article/flaws-in-self-encrypting-ssds-let-attackers-bypass-disk-encryption/)  
- [Bypassing Self-Encrypting Drives in Enterprise Environments](https://www.blackhat.com/docs/eu-15/materials/eu-15-Boteanu-Bypassing-Self-Encrypting-Drives-SED-In-Enterprise-Environments-wp.pdf)  


### Whole Disk Encryption  
- encrypts the OS and the user's data  
- boot and swap partitions can be decrypted  
    - master boot record may still be vulnerable  
- SEDs can provide true full disk encryption  
- partitions and containers on a disk can be encrypted  
- [How Does Full Disk Encryption Work?](https://youtu.be/UPW1Hqvx6zo)  
- [Full Disk Encryption: Do We Need It?](https://www.csoonline.com/article/3247707/full-disk-encryption-do-we-need-it.html)  


### File Encryption  
- [PeaZip](https://www.peazip.org/)  
    - free  
    - archiver that offers encryption  
    - multi platform: Win, OSX, Linux  
    - multifactor authentication  
    - [PeaZip FAQ  
](https://www.peazip.org/peazip-help-faq.html#file_compression_questions_and_answers)  

- [Keka - MacOS](https://www.keka.io/en/)  
    - supports multiple compression formats  
    - defaults to AES-256  
    - [Keka Wiki](https://github.com/aonez/Keka/wiki)  

- [AES Crypt](https://www.aescrypt.com/)  
    - multiplatform  
    - files can only be decrypted by another instance of AES Crypt  
    - [AES Crypt Documentation](https://www.aescrypt.com/documentation/)  

- [GPG - The GNU Privacy Guard](https://gnupg.org/)  
    - can be encrypted with public keys  
    - public/private key encryption  
    - complete and free implementation of the OpenPGP standard  
    - multiplatform: Windows, MacOS, and Linux  
    - [GNU Privacy Guard Mini Howto](https://www.dewinter.com/gnupg_howto/english/GPGMiniHowto.html)  
    - [The Complete PGP Tutorial](https://youtu.be/CEADq-B8KtI)  
- [Should You Encrypt Your Entire Hard Drive or Only a Partition?](https://security.stackexchange.com/questions/189587/should-i-encrypt-my-entire-hard-drive-or-only-a-partition)  
- [How Does Individual File Encryption Work?](https://youtu.be/Re8IK--TMdk)  
- [How to Encrypt Your Files and Why You Should](https://www.lifewire.com/how-to-encrypt-your-files-2487243)  


### What Does Disk Encryption Protect You From?  
- protects you when adversaries gain physcial access to your device  
    - all files on the disk will be unreadable without the key  
- protects data when:  
    - its lost or stolen  
    - the device is seized by law enforcement  
    - the device is left unattended  
    - the device is sent in for hardware repair  
    - crossing borders  
    - you want to discard the data  
- maintains the integrity of all files on the filesystem  
    - mitigates the effects of tampering  
    - can prevent the installation of malware  
- [What Are The Benefits of Full Disk Encryption?](https://specopssoft.com/blog/what-are-the-benefits-of-full-disk-encryption/)  


### Operating Systems and Physical Security  
- provide very little protection against an adversary with physical access  
    - password can be bypassed by booting into a live OS  
        - the file system can be explored without the key  
- [Techniques for Securing the Operating System](https://www.ibm.com/support/knowledgecenter/en/SSEP7J_10.2.1/com.ibm.swg.ba.cognos.crn_arch.10.2.1.doc/c_securing_the_operating_system.html)  
- [Hard Disk Passwords Explained](https://www.howtogeek.com/186881/hard-disk-passwords-explained-should-you-set-one-to-secure-your-files/)  
- [How to Secure Your Computer with a BIOS or UEFI Password](https://www.howtogeek.com/186235/how-to-secure-your-computer-with-a-bios-or-uefi-password/)  
- [How Secure Boot Works](https://www.howtogeek.com/116569/htg-explains-how-windows-8s-secure-boot-feature-works-what-it-means-for-linux/)  
- [Laptop Security Locks](https://www.amazon.com/Laptop-Security-Locks/b?ie=UTF8&node=3012924011)  
- [10 Laptop Security Products](https://www.pcmag.com/feature/232717/10-laptop-security-products)  


### What Does Disk Encryption Not Protect You From?  
- does protect against most threats  
    - only protects against attacks that require physical access  
- no protection against:  
    - traffic being observed  
    - ssl stripping  
    - browser attacks  
    - malware  
    - rootkits  
- no protection when your system is powered on and the key has been entered  
    - the key is stored in memory  
    - anyone with access to memory can recover the key  
    - key can also be recovered shortly after shutdown  
- no protection from mandatory key disclosure  
    - laws that force you to give up your key  
    - [Key Disclosure Law](https://en.wikipedia.org/wiki/Key_disclosure_law)  
- no protection from nation state tampering  
- data is vulnerable if backed up and unencrypted  
- [Why Full Disk Encryption Isn't Enough](https://www.digitaluppercut.com/2018/12/why-full-disk-encryption-isnt-enough/)  
- [Exploiting Full Disk Encryption](https://www.secureidnews.com/news-item/exploiting-full-disk-encryption/)  
- [Researchers Break Full Disk Encryption of Popular SSDs](https://www.securityweek.com/researchers-break-full-disk-encryption-popular-ssds)  
- [Advantages and Disadvantages of Full Disk Encryption](https://www.datanumen.com/blogs/6-advantages-disadvantages-full-disk-encryption-fde/)  
- [Five Eyes Threaten to Force Encryption Backdoors](https://www.csoonline.com/article/3301353/five-eyes-threatens-to-force-encryption-backdoors-says-privacy-is-not-absolute.html)