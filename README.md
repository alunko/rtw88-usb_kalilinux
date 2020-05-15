# rtw88-usb for kalilinux
 copy from https://github.com/neojou/rtw88-usb

# Description
 modify source for error in kalilinux.

# Supported Devices

* TPLink Archer T4U v3 (monitor mode)

## Build

```console
apt install sparse linux-headers-amd64 build-essential
make clean
make
```

## Installation

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
$ sudo cp rtw88.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless/realtek/rtw88
$ sudo cp rtwusb.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless/realtek/rtw88
$ sudo depmod -a
$ sudo echo -e "rtw88\nrtwusb" > /etc/modules-load.d/rtwusb.conf
$ sudo systemctl start systemd-modules-load
```

# Enable Monitor Mode

```
sudo ip link set wlan0 down
sudo iwconfig wlan0 mode monitor
sudo ip link set wlan0 up
````
