# rtw88-usb

This driver is forked from [neojou/rtw88-usb](https://github.com/neojou/rtw88-usb), which is based on Realtek's [rtw88 driver](https://github.com/torvalds/linux/tree/master/drivers/net/wireless/realtek/rtw88) in Linux main trunk.

The driver supports Realtek USB wifi IC 88x2bu and 88x2cu, and supports at least managed (i.e. client) and monitor mode.

## Build

```console
$ make clean
$ make
```
## Install
Load driver for test:
```console
$ sudo mkdir -p /lib/firmware/rtw88
$ sudo cp fw/rtw8822* /lib/firmware/rtw88/
$ sudo insmod rtw88.ko
$ sudo insmod rtwusb.ko
```
Load driver at boot:
```console
$ sudo mkdir -p /lib/firmware/rtw88
$ sudo cp fw/rtw8822* /lib/firmware/rtw88/
$ sudo mkdir /lib/modules/`uname -r`/kernel/drivers/net/wireless/realtek/rtw88
$ sudo cp rtw88.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless/
$ sudo cp rtwusb.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless/
```
## General Commands
Scan:
```console
$ sudo iw wlanX scan
```
Connect to the AP without security:
```console
$ sudo iw wlanX connect <AP name>
```
