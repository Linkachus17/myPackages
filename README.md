# MyPackages
This repo meant to store all of my required packages during Arch installation. DOES NOT INCLUDE KERNEL MODULE PACKAGES
# Pre-requisite
## NVIDIA driver
Remove kms from HOOKS on /etc/mkinitcpio.conf
## Multilib
Enable it from /etc/pacman.conf
# Additional configs
## Change Shell
```
chsh -s /full/path/to/shell
```
## Disable sudo timeout
using EDITOR=myeditor visudo, add:
"Defaults timestamp_timeout=-1"
## DRM Kernel mode settings
```
/etc/mkinitcpio.conf
MODULES=(…nvidia nvidia_modeset nvidia_uvm nvidia_drm…)
```
```
/etc/modprobe.d/nvidia.conf
options nvidia_drm modeset=1 fbdev=1
```

## Install Yay
```
pacman -S --needed git base-devel
git clone https://aur.archlinux.org/yay.git
cd yay
makepkg -si
```
