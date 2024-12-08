# MyPackages
This repo meant to store all of my own required packages during Arch installation. DOES NOT INCLUDE KERNEL MODULE PACKAGES<br>
[barebone](https://github.com/Linkachus17/myPackages/blob/main/barebone) is list of packages that is required to run KDE Plasma

# Pre-requisite
## Install Yay
```
pacman -S --needed git base-devel
git clone https://aur.archlinux.org/yay.git
cd yay
makepkg -si
```

## NVIDIA driver
Remove ``kms`` from HOOKS on ``/etc/mkinitcpio.conf``

### DRM Kernel mode settings for NVIDIA
Necessarry for Wayland
```
/etc/mkinitcpio.conf
MODULES=(…nvidia nvidia_modeset nvidia_uvm nvidia_drm…)
```
```
/etc/modprobe.d/nvidia.conf
options nvidia_drm modeset=1 fbdev=1
```

## Multilib
Uncomment multilib repo
```
/etc/pacman.conf
[multilib]
Include = /etc/pacman.d/mirrorlist
```

# Installing Packages
## Using curl
```
pacman -Sy $(curl -s https://raw.githubusercontent.com/Linkachus17/myPackages/refs/heads/main/pacman)
```
```
yay -S $(curl -s https://raw.githubusercontent.com/Linkachus17/myPackages/refs/heads/main/yay)
```

# Additional configs
## Change Shell
```
chsh -s /full/path/to/shell
```
## Disable sudo timeout
``EDITOR=youreditor visudo``
```
...
Defaults timestamp_timeout=-1
...
```

## ~~Replace KDE Notification with dunst~~ Doesn't work!
```
/usr/share/dbus-1/services/org.kde.plasma.Notifications.service
[D-BUS Service]
Name=org.freedesktop.Notifications
Exec=/usr/bin/dunst
```
