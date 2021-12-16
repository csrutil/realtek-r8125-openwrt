# OpenWrtDrivers

realtek 2.5G ethernet driver for OpenWrt X64 / latest intel igb driver

[![Build r8125 kernel module](https://github.com/csrutil/OpenWrtDrivers/actions/workflows/build.yaml/badge.svg)](https://github.com/csrutil/OpenWrtDrivers/actions/workflows/build.yaml)

## How to use it

You can download the kernel module into your router and try to install it

```bash
opkg install kmod-r8125_your_version.ipk
```

## Notice

The modules are compiled by stock sdk, if you have self compiled firmware, it's not for you!

## On my router

```bash
root@OpenWrt:~# modinfo r8125
module:		/lib/modules/5.4.154/r8125.ko
license:	GPL
depends:
retpoline:	Y
name:		r8125
vermagic:	5.4.154 SMP mod_unload
root@OpenWrt:~# dmesg | grep r8125
[    7.119890] r8125 2.5Gigabit Ethernet driver 9.006.04-NAPI-RSS loaded
[    7.177030] r8125: This product is covered by one or more of the following patents: US6,570,884, US6,115,776, and US6,327,625.
[    7.182093] r8125  Copyright (C) 2021  Realtek NIC software team <nicfae@realtek.com>
[    7.189126] r8125 2.5Gigabit Ethernet driver 9.006.04-NAPI-RSS loaded
[    7.245019] r8125: This product is covered by one or more of the following patents: US6,570,884, US6,115,776, and US6,327,625.
[    7.250329] r8125  Copyright (C) 2021  Realtek NIC software team <nicfae@realtek.com>
[   13.384830] r8125: eth0: link up
[   13.640644] r8125: eth1: link up
root@OpenWrt:~# speedtest

   Speedtest by Ookla

     Server: IdeaTek Telcom - Hutchinson, KS (id = 20794)
        ISP: Stacks-inc-01
    Latency:   227.98 ms   (0.15 ms jitter)
   Download:   912.37 Mbps (data used: 1.3 GB)
     Upload:   113.22 Mbps (data used: 146.1 MB)
Packet Loss:     0.0%
 Result URL: https://www.speedtest.net/result/c/c808d0ee-2735-4e42-bb02-5a353ce913bd
 ```
