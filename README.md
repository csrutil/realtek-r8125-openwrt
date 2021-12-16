# OpenWrtDrivers

realtek 8125b 2.5G and intel igb ethernet drivers for stock OpenWrt

[![Build OpenWrt drivers](https://github.com/csrutil/OpenWrtDrivers/actions/workflows/build.yaml/badge.svg)](https://github.com/csrutil/OpenWrtDrivers/actions/workflows/build.yaml)


## Why

- Realtek 8125b

There is a builtin driver called r8169 that supprt rtl8125b, and I suppose you can't enable the Receive side scaling (RSS) on it,
and also this ethernet can support 32 queues, this version enable the RSS

```
ENABLE_RSS_SUPPORT = y
ENABLE_MULTIPLE_TX_QUEUE = y
CONFIG_ASPM = n
```

- Intel igb

The latest version of IGB from downloads.sourceforge.net

## How to use it

You can download the kernel module into your router and try to install it

```bash
opkg install r8125b.ipk
```

## Notice

Those packages are ONLY for the official firmwares

## Donating 💸

- Feel free to [Buy Me a Coffee](https://www.buymeacoffee.com/csrutil)
- `XMR 4APxe9PpCgw2RdZjkiBqVk6mdyforWiQvGHGCXp6iWojTZaqmfuKcAgBEXTkshDLwo6zGu5yNVUBriyVuUV8jUr58nnkexR`
- `XHV hvxyGJc7axz1hiQCiXVcrrLJbjhbkHHuuC4auW9oJTbCcWEg7x14VgmfWPkxEThLsSfq4Ss9uuTLqYGe8ugFqnQe6Daa2hj2L7`
- `BTC bc1q7ryvvxuws4vhhuxpaddl82seq7ue03qq2p40qh`
