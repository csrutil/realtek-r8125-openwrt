# OpenWrt NIC Drivers

The repository is for building the Realtek 8125b & Intel IGB drivers for OpenWrt stock firmwares

[![Build OpenWrt-NIC-Drivers](https://github.com/csrutil/OpenWrt-NIC-Drivers/actions/workflows/build.yaml/badge.svg)](https://github.com/csrutil/OpenWrt-NIC-Drivers/actions/workflows/build.yaml)

## Receive Side Scaling (RSS)

> When Receive Side Scaling (RSS) is enabled, all of the receive data processing for a particular TCP connection is shared across multiple processors or processor cores. Without RSS, all of the processing is performed by a single processor, resulting in inefficient system cache utilization.

You can check how many queues that nic has by `ethtool -S eth0`.

```bash
# two queues here for nic eth0
root@main:~# ethtool -S eth0 | grep queue_
     tx_queue_0_packets: 76237812
     tx_queue_0_bytes: 115366533619
     tx_queue_0_restart: 0
     tx_queue_1_packets: 13284570
     tx_queue_1_bytes: 11170423616
     tx_queue_1_restart: 0
     rx_queue_0_packets: 45949999
     rx_queue_0_bytes: 55390542647
     rx_queue_0_drops: 0
     rx_queue_0_csum_err: 0
     rx_queue_0_alloc_failed: 0
     rx_queue_1_packets: 44304833
     rx_queue_1_bytes: 56510279008
     rx_queue_1_drops: 0
     rx_queue_1_csum_err: 0
     rx_queue_1_alloc_failed: 0
```

You can check the `/proc/interrupts` file for RSS queues on intel i211 nic

![i211 RSS](https://i.imgur.com/D5ivSP7.png)


## Realtek RTL8125 / RTL8125B(S)(G)

> The RTL8125BG/RTL8125BGS supports Receive-Side Scaling (RSS) to hash incoming TCP connections and load-balance received data processing across multiple CPUs. RSS improves the number of transactions per second and number of connections per second, for increased network throughput.

There is a builtin driver called r8169 that supprt rtl8125b on linux, and I suppose you can't enable the Receive side scaling (RSS) on it, rtl8125b can support 32 queues. This version just enable the RSS.

```
ENABLE_RSS_SUPPORT = y
ENABLE_MULTIPLE_TX_QUEUE = y
CONFIG_ASPM = n
```

## Intel NICs

- I350-based adapters: 8 queues
- 82575-based adapters: 4 queues
- 82576-based and newer adapters: 8 queues
- I210-based adapters: 4 queues
- I211-based adapters: 2 queues

If you have an OpenWrt on a VM(ESXI or PVE) that has I211 nics, just set two cores on it, and enable `RSS=2`. that's it!

```bash
# set RSS to 2 on OpenWrt for two nics
root@main:~# cat /etc/modules.d/35-igb-intel
igb RSS=2,2
```

## How to use it

Download package from https://github.com/csrutil/OpenWrt-NIC-Drivers/releases page, scp into your router and install it.

## Notice

Those packages are ONLY for the official stock firmwares

## Donating 💸

- Feel free to [Buy Me a Coffee](https://www.buymeacoffee.com/csrutil)
- `XHV hvxyGJc7axz1hiQCiXVcrrLJbjhbkHHuuC4auW9oJTbCcWEg7x14VgmfWPkxEThLsSfq4Ss9uuTLqYGe8ugFqnQe6Daa2hj2L7`

## Credits

- https://sourceforge.net/projects/e1000/files/igb%20stable/
- https://www.realtek.com/zh/component/zoo/category/network-interface-controllers-10-100-1000m-gigabit-ethernet-pci-express-software
- https://www.realtek.com/en/products/communications-network-ics/item/rtl8125bg-s-cg
- https://www.realtek.com/en/component/zoo/category/network-interface-controllers-10-100-1000m-gigabit-ethernet-usb-3-0-software
