# UBUNTU 18.04 and RTL-SDR Dongle Setup

RTLSDR installation on Ubuntu:

Check if USB RTLSDR is detected and what are Product_ID and Vendor_ID (f.ex. idVendor=0bda, idProduct=2832 )

```bash
lsusb

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 8087:0a2b Intel Corp. Bluetooth wireless interface
Bus 001 Device 004: ID 18f8:0f99 [Maxxter] Optical gaming mouse
Bus 001 Device 003: ID 413c:2003 Dell Computer Corp. Keyboard SK-8115
Bus 001 Device 008: ID 0bda:2838 Realtek Semiconductor Corp. RTL2838 DVB-T  <---
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Blacklist ordinary DVB-T drivers in Linux Kernel not to interfere with rtlsdr library

```bash
vi /etc/modprobe.d/blacklist.conf
```

Add in this file  following lines (add line respectively to ProductID value) :

```bash
blacklist dvb_usb_rtl28xxu 
blacklist rtl2832 
blacklist rtl2830
```

Restart Computer

Install the RTL-SDR package: [https://launchpad.net/ubuntu/bionic/+...](https://launchpad.net/ubuntu/bionic/+package/rtl-sdr)

```bash
sudo apt-get install rtl-sdr
```
