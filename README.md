# SMS to Telegram Gateway
A lightweight script to send received messages (SMS) to a Telegram Group.

## Devices
- Raspberry Pi
- Huawei USB Modem

## Setup
1. Setup the Raspberry Pi
2. Connect to it via SSH
3. Setup the Modem
```bash
nano /etc/udev/rules.d/41-usb_modeswitch.rules
```

The file must contain the following line:
```bash
ACTION=="add", SUBSYSTEM=="usb", ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1446", RUN+="/usr/sbin/usb_modeswitch -v 12d1 -p 1446 -M '55534243123456780000000000000011062000000100000000000000000000'"
```

If you have a another modem as the E1552, get the id of the pruduct via `lsusb`.
The output shows something like this:
```
                   idVendor:idProduct
                        V    V
Bus 001 Device 005: ID 12d1:1446 Huawei Technologies Co., Ltd. E180v 
Bus 001 Device 003: ID 0424:ec00 Standard Microsystems Corp. SMSC9512/9514 Fast Ethernet Adapter
Bus 001 Device 002: ID 0424:9512 Standard Microsystems Corp. LAN9500 Ethernet 10/100 Adapter / SMSC9512/9514 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```
4. Install gammu and gammu-smsd
```bash
apt install gammu gammu-smsd
```
