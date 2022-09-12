Kindle k4 JAILBREAK
====================

## follow instructions: https://gist.github.com/estysdesu/c90478aac75b732820be6720254aeda7

from Linux, using NetworkManager 

    Open your network settings
    Open "USB Ethernet" settings
    (Optional) In the "Identity" tab, set "Name" to something to remind you that it's your Kindle
    In the "IPv4" tab:
        Set "IPv4 Method" to "Manual"
        Under "Addresses", set "Address" to 192.168.15.201 and "Netmask" to 255.255.255.0 
    Click "Apply"
    Restart the connection by disabling it and re-enabling it 

# usbNetwork notes
These notes primarily concern usbNetwork [Ethernet over USB](https://www.wikiwand.com/en/Ethernet_over_USB)

*The default IP's for Kindle K4 are*

HOST_IP=`192.168.15.201`
KINDLE_IP=`192.168.15.244`


```bash
ifconfig -a # find the usb device

sudo ifconfig enxee4900000000 192.168.15.201

ssh root@192.168.15.244

```


I had to manually activate USB-Ethernet in Ubuntu network settings. Then it worked. Now I'm going to install python on kindle. Because you know, why not. 

# For the paranoid: disable updates:

This prevents software updates from occuring. 
source: https://wiki.mobileread.com/wiki/Kindle4NTHacking#Disabling_updates
Remember to switch it back when installing new stuff. 
```bash
# Make the root partition writable 
mntroot rw
mv /etc/uks /etc/uks.disabled
# Make the root filesystem read-only again and reboot your kindle
mntroot ro
```

# Useful to know

`/mnt/us/`  user directory
`/mnt/us/documents`   contains the actual ebooks etc. 

Copying stuff over
scp Update_KUALBooklet_v2.7.26_install.bin root@192.168.15.244:/mnt/us


*Following command can be run from an ssh session to refresh documents. (useful if you have copied e-books over via a non-USB method e.g scp):*

`dbus-send --system /default com.lab126.powerd.resuming int32:1`

# Attention
Very important notes:
never boot kindle while it is plugged a computer, it causes various funny / interesting behaviour. 


# What I installed

- Jailbreak
- USB Networking, changed the config
- python3.9

- Mobileread Kindlet Kit:
http://www.mobileread.com/forums/showthread.php?t=233932
- KUAL



# usbNetwork / Toggle USB mode

To set USB mode default again, edit the file usbnet/auto and remame to DISABLE_auto

