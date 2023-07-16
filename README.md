# OpenWrt NIC Drivers

The repository is for building the Realtek 8125b driver for OpenWrt firmwares

[![Build Realtek r8125 driver for OpenWrt](https://github.com/csrutil/realtek-r8125-openwrt/actions/workflows/r8125.yaml/badge.svg?branch=main)](https://github.com/csrutil/realtek-r8125-openwrt/actions/workflows/r8125.yaml)

## Realtek RTL8125 / RTL8125B(S)(G)

The latest version of the driver has the RSS feature disabled by default, even if the compilation option is enabled, it will not take effect.

```
root@main:~/misc# cat /proc/interrupts | grep 'CPU\|eth' | grep -v '0          0'
           CPU0       CPU1
 27:  183637666          0   PCI-MSI 262144-edge      eth0-0
 43:          1  101037815   PCI-MSI 262160-edge      eth0-16
 45:   98181298          0   PCI-MSI 262162-edge      eth0-18
 48:          0          2   PCI-MSI 262165-edge      eth0-21
 59:  175493469          0   PCI-MSI 278528-edge      eth1-0
 75:          1   89978815   PCI-MSI 278544-edge      eth1-16
 77:   97193843          0   PCI-MSI 278546-edge      eth1-18
 80:          0          6   PCI-MSI 278549-edge      eth1-21

root@main:~# cat /proc/net/r8125/eth0/driver_var  | grep EnableRss
driver version 9.011.01-NAPI-RSS
chipset_name   RTL8125B
EnableRss 0x0
```

## Setup

Attention⚠️, the ipk files in this repository only support official firmware. If you are compiling your own firmware, please refer to the scripts in the action.

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
- https://www.realtek.com/zh/component/zoo/category/network-interface-controllers-10-100-1000m-gigabit-ethernet-pci-express-software
- https://www.realtek.com/en/products/communications-network-ics/item/rtl8125bg-s-cg
- https://www.realtek.com/en/component/zoo/category/network-interface-controllers-10-100-1000m-gigabit-ethernet-usb-3-0-software
