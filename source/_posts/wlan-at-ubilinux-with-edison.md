title: wlan at ubilinux with edison
date: 2015-10-13 01:56:07
tags:
---

# ubilinux な edison で wlan

```
> wpa_passphrase koya ${your_wpa_passwd} > koya-wlan.conf
> cp ./koya-wlan.conf /etc/wpa_supplicant/
> vi /etc/network/interfaces
auto wlan0
iface wlan0 inet dhcp
    # For WPA
+   wpa-conf /etc/wpa_supplicant/koya-wlan.conf
-   wpa-ssid test
-   wpa-psk pass
+   #wpa-ssid test
+   #wpa-psk pass
    # For WEP
    #wireless-essid Emutex
    #wireless-mode Managed
    #wireless-key s:passwordk

> ifdown wlan0
nternet Systems Consortium DHCP Client 4.2.2
Copyright 2004-2011 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/wlan0/78:4b:87:a8:f0:e9
Sending on   LPF/wlan0/78:4b:87:a8:f0:e9
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.11.1 port 67

> ifup wlan0
Internet Systems Consortium DHCP Client 4.2.2
Copyright 2004-2011 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/wlan0/78:4b:87:a8:f0:e9
Sending on   LPF/wlan0/78:4b:87:a8:f0:e9
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPOFFER from 192.168.11.1
DHCPACK from 192.168.11.1
bound to 192.168.11.11 -- renewal in 76747 seconds.

> iwconfig wlan0
wlan0     IEEE 802.11abgn  ESSID:"koya"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 4C:E6:76:3E:BE:A1
          Bit Rate=54 Mb/s   Tx-Power=31 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          Link Quality=56/70  Signal level=-54 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:14  Invalid misc:1   Missed beacon:0

```
