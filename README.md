# OpenWrtDrivers

Realtek 8125b 2.5G and intel igb ethernet drivers for stock OpenWrt

[![Build OpenWrt drivers](https://github.com/csrutil/OpenWrtDrivers/actions/workflows/build.yaml/badge.svg)](https://github.com/csrutil/OpenWrtDrivers/actions/workflows/build.yaml)


## Why

**Realtek RTL8125 / RTL8125B(S)(G)**

There is a builtin driver called r8169 that supprt rtl8125b on linux, and I suppose you can't enable the Receive side scaling (RSS) on it, rtl8125b can support 32 queues. So this version just enable the RSS.

```
ENABLE_RSS_SUPPORT = y
ENABLE_MULTIPLE_TX_QUEUE = y
CONFIG_ASPM = n
```

**Intel IGB**

The latest version of IGB from downloads.sourceforge.net

## How to use it

Check the https://github.com/csrutil/OpenWrtDrivers/blob/main/.github/workflows/build.yaml and build it by yourself.

Download ipk from the https://github.com/csrutil/OpenWrtDrivers/releases page, scp into your router and install it.

## Notice

Those packages are ONLY for the official firmwares

## Donating 💸

- Feel free to [Buy Me a Coffee](https://www.buymeacoffee.com/csrutil)
- `XMR 4APxe9PpCgw2RdZjkiBqVk6mdyforWiQvGHGCXp6iWojTZaqmfuKcAgBEXTkshDLwo6zGu5yNVUBriyVuUV8jUr58nnkexR`
- `XHV hvxyGJc7axz1hiQCiXVcrrLJbjhbkHHuuC4auW9oJTbCcWEg7x14VgmfWPkxEThLsSfq4Ss9uuTLqYGe8ugFqnQe6Daa2hj2L7`
- `BTC bc1q7ryvvxuws4vhhuxpaddl82seq7ue03qq2p40qh`

## Credits

- https://www.realtek.com/zh/component/zoo/category/network-interface-controllers-10-100-1000m-gigabit-ethernet-pci-express-software
