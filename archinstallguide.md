# ARCH INSTALLATION GUIDE  
the guide that i used for installing arch linux was  
https://www.youtube.com/watch?v=AYxaNjbC1wg
## OVERVIEW: 
1. CONNECTING TO A NETWORK
2. SETTING UP FOR `archinstall`
3. CONFIGURING DISK
4. SETTING UP THE INSTALLATION
5. START INSTALLATION AND COMPLETE

### 1. CONNECTING TO A NETWORK:  
- before doing anything for better readability increase the font size using this command:
    ```bash
    setfont ter-132n
    ```
- check if you are connected to internet by using:
    ```bash
    ping google.com
    ```
    if it fails then that mean you are not connected to a ethernet and you need a internet connection
- start by entering this command:
    ```bash
    iwctl
    ```
    by this you'll enter the `iwd` shell and in there us this command to list the network devices:
    ```bash
    device list
    ```    
    check if `wlan0` exists in that list and this is the wireless network interface we'll need for internet
- now we need to establish a connection and for that start by listing all the wifi networks:
    ```bash
    station wlan0 get-networks
    ```
    connect to a wifi by this command:
    ```bash
    station wlan0 connect <wifi-network-name>
    ```
    and enter the wifi password
- after successfully connecting you can again check the connection using the `ping` command

### 2. SETTING UP FOR `archinstall`:
- synchronize the packages using these commands:
    ```bash
    pacman -Sy
    ```
    ```bash
    pacman -Syy
    ```
- use this command to test the authenticity and integrity of the packages:
    ```bash
    pacman -Sy archlinux-keyring
    ```
- setup the `archinstall` script using this command:

    ```bash
    pacman -Sy archinstall
    ```
    and run this command to run archinstall:
    ```bash
    archinstall
    ```
### 3. CONFIGURING DISK:
- in the `Disk configuration` > `Partitioning` > `Use a best-effort default partition layout` select the disk for installation
- choose `btrfs` > `Use compression` > and select `Back` to return to the main page   

### 4. SETTING UP THE INSTALLATION:
- use `systemd-boot` for bootloader
- set root password and a user (add this user to the `sudoers` list)
- select `Kde-plasma` for Desktop Environment
- in graphic drivers select `Nvidis (proprietary)`
- select `NetworkManager` for Network configuration
- select the appropriate timezone

### 5. START INSTALLATION AND COMPLETE

