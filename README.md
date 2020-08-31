# My First Computer

## Settings
* Motherboard: [B450M MORTAR MAX](https://www.msi.com/Motherboard/B450M-MORTAR-MAX)
    * Note: `PCI_E4 slot will be unavailable when an M.2 SSD is installed in the M2_2 slot.` I finally figure out this from the output of `dmesg`.
* CPU: AMD Ryzen 5 360X
* GPU: ASUS DUAL-RTX2070S-O8G-EVO
* NIC: PCE-AC55BT PCI-E
    * Need `iwlwifi-8000C-13.ucode` firmware (<https://www.asus.com/Networking/PCE-AC55BT-B1/>)
    * Linux kernel 4.1+ (<https://www.intel.com/content/www/us/en/support/articles/000005511/network-and-i-o/wireless.html>)
* OS: [Ubuntu 18.04](http://old-releases.ubuntu.com/releases/18.04.2/ubuntu-18.04.2-desktop-amd64.iso)
    * I use [balenaEtcher](https://www.balena.io/etcher/) to create a bootable usb drive.
    * Make sure to tick `Install third-party software` when you install by the GUI.

## Installation

(all starting with `sudo`)
```
# Ctrl + Alt + F3: Enter the text mode (tty3)

# Update package databases
apt-get update

# Upgrade
apt-get upgrade

## Nvidia driver installation
apt-get purge nvidia* # remove other drivers
add-apt-repository ppa:graphics-drivers # add the repository
apt-get update
ubuntu-drivers devices # check which driver is recommended
apt-get install nvidia-driver-450 # for my GPU, the recommended driver is version 450
```

## Troubleshooting

(all starting with `sudo`)
* `modinfo iwlwifi`
* `lspci -v`
* `dmesg`
* `rfkill list`

## References
* <https://wiki.ubuntu.com/Kernel/Firmware>
* [Linux* Support for Intel® Wireless Adapters](https://www.intel.com/content/www/us/en/support/articles/000005511/network-and-i-o/wireless.html)
