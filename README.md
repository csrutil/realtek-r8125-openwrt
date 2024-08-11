# RTL8125B OpenWrt Driver

The repository is for building the Realtek 8125b driver for OpenWrt firmwares

[![Build Realtek r8125 driver for OpenWrt](https://github.com/csrutil/realtek-r8125-openwrt/actions/workflows/r8125.yaml/badge.svg?branch=main)](https://github.com/csrutil/realtek-r8125-openwrt/actions/workflows/r8125.yaml)

## Realtek RTL8125 / RTL8125B(S)(G)

The latest version of the driver has the RSS feature enable by default🎉

```
root@main:~# cat /proc/interrupts | grep 'CPU\|eth' | grep -v '0          0'
           CPU0       CPU1
 48:          1    8359439   PCI-MSI 3407888-edge      eth0-16
 50:    4146137    4039293   PCI-MSI 3407890-edge      eth0-18
 53:          0          1   PCI-MSI 3407893-edge      eth0-21
 64:    9385347          0   PCI-MSI 3424256-edge      eth1-0
 65:    3943462    3345782   PCI-MSI 3424257-edge      eth1-1
 80:          1    9252867   PCI-MSI 3424272-edge      eth1-16
 82:    3606778    3428598   PCI-MSI 3424274-edge      eth1-18
 85:          0          1   PCI-MSI 3424277-edge      eth1-21

root@main:~# cat /proc/net/r8125/eth*/debug/driver_var  | grep Rss
EnableRss       0x1
EnableRss       0x1
```

## Setup

Attention⚠️, only support official firmware. If you are compiling your own firmware, please refer to the scripts in the action.

First, download the corresponding ipk file according to your version, scp it to your device, and then run

```
opkg -i kmod-r8125_4.14.275+9.011.01-x86-0_x86_64.ipk
```

If you are using the 5.15 kernel, the r8196 driver should automatically drive your network card. If you want to force the use of the driver from this project, you can delete the r8196 driver.

## QA

if you're not the right speed, please check this command.

```
# https://forum.openwrt.org/t/realtek-8156b-2-5g-for-pi-4-and-openwrt-21-02-2/125102/11
ethtool -s eth1 autoneg on advertise 0x80000000002f
```

## Donating 💸

- Feel free to [Buy Me a Coffee](https://www.buymeacoffee.com/csrutil)
- `XHV hvxyGJc7axz1hiQCiXVcrrLJbjhbkHHuuC4auW9oJTbCcWEg7x14VgmfWPkxEThLsSfq4Ss9uuTLqYGe8ugFqnQe6Daa2hj2L7`

## Credits

- https://sourceforge.net/projects/e1000/files/igb%20stable/
- [https://www.realtek.com/en/component/zoo/category/network-interface-controllers-10-100-1000m-gigabit-ethernet-usb-3-0-software](https://www.realtek.com/Download/Index?cate_id=194&menu_id=297)
