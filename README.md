# My First Computer

## Settings
* Motherboard: [B450M MORTAR MAX](https://www.msi.com/Motherboard/B450M-MORTAR-MAX)
    * Note: `PCI_E4 slot will be unavailable when an M.2 SSD is installed in the M2_2 slot.` I finally figure out this from the output of `dmesg`.
* CPU: AMD Ryzen 5 3600X
* Memory: Kingston 8GBx2 DDR4-3200 HyperX Fury
* SSD: Kingston A2000 500GB (M.2 PCIe 2280)
* HDD: WD (Blue Label) 2TB
* GPU: ASUS DUAL-RTX2070S-O8G-EVO
* Power Supply Unit: Cool Master MWE 650W Bronze V2
* Chassis: Cool Master Silencio S400/M-ATX
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

* Chinese Input Installation:
Follow the tutorial in <https://medium.com/@racktar7743/ubuntu-%E5%9C%A8-ubuntu-18-04-%E4%B8%AD%E6%96%B0%E5%A2%9E%E6%96%B0%E9%85%B7%E9%9F%B3%E8%BC%B8%E5%85%A5%E6%B3%95-4aa85782f656>

* DRAM Setting: Set A-XMP to `Profile 1 DDR4 3200MHz`
Thanks to [leovincentseles](https://github.com/leovincentseles)'s teaching.

## Troubleshooting

(all starting with `sudo`)
* `modinfo iwlwifi`
* `lspci -v`
* `dmesg`
* `rfkill list`

## References
* <https://wiki.ubuntu.com/Kernel/Firmware>
* [Linux* Support for Intel® Wireless Adapters](https://www.intel.com/content/www/us/en/support/articles/000005511/network-and-i-o/wireless.html)
* [MSI®如何用M-FLASH更新單BIOS](https://www.youtube.com/watch?v=zVPxzWeEjUA)
