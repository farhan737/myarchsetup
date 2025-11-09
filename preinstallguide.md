# PRE-INSTALLATION GUIDE
## OVERVIEW:
1. INSTALLTING BALENA ETCHER
2. DOWNLOADING LINUX ISO FILE
3. CREATE A BOOT DRIVE USING BALENA ETCHER FOR THE ISO
4. DISABLE SECURE BOOT IN THE DEVICE'S BIOS SETTINGS
5. IN THE BIOS SETTINGS SET THE BOOT CONFIGURATION TO LOAD INTO THE BOOT DRIVE 
6. OS INSTALLTION  


### 1. INSTALLING BALENA ETCHER  
- firstly for arch linux system use this command:
    ```bash
    yay -S balena-etcher
    ``` 
- for debian and other debian based systems use this command:  
go to https://etcher.balena.io/#download-etcher   
and download the `.deb` package and after that run this command  
    ```bash
    sudo apt install ./balena-etcher_******_amd64.deb
    ```
- for windows the installer is located in the same link  
https://etcher.balena.io/#download-etcher 

### 2. DOWNLOADING LINUX ISO FILE
- the ISO file for arch linux is located at  
https://archlinux.org/download/  
and you'll need to scroll down and find the download files for your region
- the file you'll need to download will look like this
    ```script
    archlinux-2025.11.01-x86_64.iso 
    ``` 

### 3. CREATE A BOOT DRIVE USING BALENA ETCHER FOR THE ISO
- you'll need the flash drive plugged-in to your device from now on
- open balena fetcher and you'll need a flash drive (8GB one is enough)
- select the flash drive and the ISO you want to flash 
- write the flash drive and done.

### 4. DISABLE SECURE BOOT IN THE DEVICE'S BIOS SETTINGS
- boot into you devices BIOS settings and find the **Secure boot option**
- you'll need it disabled if you want to install the OS
- after disabling save the changes and then go to boot configuration section in the BIOS

### 5. IN THE BIOS SETTINGS SET THE BOOT CONFIGURATION TO LOAD INTO THE BOOT DRIVE 
- in boot configuration there is a section for boot sequence stack  
- put the flash drive on top of stack and save the changes
- now exit the BIOS and the device will boot into the flash drive
## continue to arch install [here](archinstallguide.md)