# r8125
realtek 2.5G ethernet driver for OpenWrt X64

[![Build r8125 kernel module](https://github.com/csrutil/r8125/actions/workflows/build.yaml/badge.svg)](https://github.com/csrutil/r8125/actions/workflows/build.yaml)

## How to use it

You can download the kernel module into your router and try to install it

```bash
opkg install kmod-r8125_your_version.ipk
```

## Notice

The modules are compiled by stock sdk, if you have self compiled firmware, it's not for you!

## On my router

```bash
BusyBox v1.33.1 (2021-09-13 16:49:38 UTC) built-in shell (ash)

  _______                     ________        __
 |       |.-----.-----.-----.|  |  |  |.----.|  |_
 |   -   ||  _  |  -__|     ||  |  |  ||   _||   _|
 |_______||   __|_____|__|__||________||__|  |____|
          |__| W I R E L E S S   F R E E D O M
 -----------------------------------------------------
 OpenWrt 21.02.0, r16279-5cc0535800
 -----------------------------------------------------
root@OpenWrt:~# modinfo r8125
module:   /lib/modules/5.4.143/r8125.ko
license:  GPL
depends:
retpoline:  Y
name:   r8125
vermagic: 5.4.143 SMP mod_unload
root@OpenWrt:~# dmesg | grep r8125
[    7.055225] r8125 2.5Gigabit Ethernet driver 9.006.04-NAPI-RSS loaded
[    7.112709] r8125: This product is covered by one or more of the following patents: US6,570,884, US6,115,776, and US6,327,625.
[    7.117808] r8125  Copyright (C) 2021  Realtek NIC software team <nicfae@realtek.com>
[    7.124716] r8125 2.5Gigabit Ethernet driver 9.006.04-NAPI-RSS loaded
[    7.180727] r8125: This product is covered by one or more of the following patents: US6,570,884, US6,115,776, and US6,327,625.
[    7.185940] r8125  Copyright (C) 2021  Realtek NIC software team <nicfae@realtek.com>
[   13.320417] r8125: eth0: link up
[   13.640444] r8125: eth1: link up
root@OpenWrt:~# speedtest

   Speedtest by Ookla

     Server: China Telecom ZheJiang Branch - Hangzhou (id = 7509)
        ISP: China Mobile Guangdong
    Latency:    22.62 ms   (0.06 ms jitter)
   Download:   944.39 Mbps (data used: 1.2 GB)
     Upload:   117.18 Mbps (data used: 208.7 MB)
Packet Loss:     0.0%
 Result URL: https://www.speedtest.net/result/c/e3e341ff-6215-4b2c-b439-71b2ce35dd6b
```
