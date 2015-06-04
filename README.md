python_buzz
===========

Python Library to handle PS2 USB Buzz! controllers

Instructions for Ubuntu 14.04
==============================

First open a terminal and login as sudo
```bash
sudo -i
```

Ensure the system is up to date
```bash
apt-get update && apt-get upgrade
```

Install dependencies
```bash
apt-get install python python-pip libusb-dev libusb-1.0* git
```

update python package manager (pip)
```bash
pip install --upgrade pip
```

install pyusb (I think the lib is not yet stable)
```bash
pip install --pre pyusb
```

exit root
```bash
exit
```

checkout this repo with git
```bash
git clone https://github.com/LewisCowles1986/python_buzz
```

Run the script via python
```bash
cd python_buzz && python buzz.py
```

alternatively 
```bash
chmod+x buzz.py && sudo ./buzz.py
```

Troubleshooting
================
N.b. This is only really for users that understand the basics of devices, the lsusb command and modifying a python script

Check Device Vendor ID and Device ID using lsusb & update in the program
```bash
lsusb
```

should produce output like this
```
Bus 002 Device 003: ID 0cf3:3004 Atheros Communications, Inc.
Bus 002 Device 010: ID 054c:0002 Sony Corp. Standard HUB
Bus 002 Device 002: ID 054c:0001 Sony Corp. Wireless Buzz! Receiver
```

modify the following string
```python
self.device = usb.core.find(idVendor=0x054c, idProduct=0x0002) # PS2 SCEH-0005 USB Wired Receiver
```
to
```python
self.device = usb.core.find(idVendor=0x054c, idProduct=0x1000) # Wireless Receiver
```

Feel free to checkout the original repo and let me know how you get on, what you do ;)
