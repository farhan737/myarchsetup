# POST INSTALLATION GUIDE:

### install `git`
```bash
sudo pacman -S git
```  
### install `yay`
```bash
sudo pacman -S --needed base-devel git 
git clone https://aur.archlinux.org/yay.git
cd yay
makepkg -si
```
### install `chrome`
```bash
yay -S google-chrome
```

### install `visual-studio`

```bash
yay -S visual-studio-code-bin
```
### setup `multilib`
```bash
sudo nano /etc/pacman.conf
```
uncomment and save
```bash
[multilib]
Include = /etc/pacman.d/mirrorlist
```
### install `github-cli`
```bash
yay -S github-cli
```
### install `eclipse-j2ee` and `spring-tool-suite`
```bash
yay -S eclipse-installer
yay -S spring-tools-for-eclipse
```