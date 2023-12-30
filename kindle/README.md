# docs

The following is a collection of notes for jailbreaking an amazon kindle.  
There is no structure.  
A long, rambling stream of consciousness of gathered information hoping to be useful. 

### Usb storage device
Device may is recogniezd as a usb mass storage device, because I have disabled it.  

To set USB mode default again, edit the file `/mnt/us/usbnet/auto` and remame to `DISABLE_auto`
Having this file automatially actives USBnet, which is convenient. 


### Personal notes:
`ssh root@192.168.15.244`
Should work right out of the box.

### Transfer files over scp:
Straight to the point:
- Use the usb slot top left on the front.   
- Usb cables are tricky, the black one (with Klett) works   
`ifconfig -a` should yield `enxee4900000000
then run:


`sudo ifconfig enxee4900000000 192.168.15.201`
 ssh root@192.168.15.244`
 
 Should be welcomed by the following banner.


```
#################################################
#  N O T I C E  *  N O T I C E  *  N O T I C E  # 
#################################################
Rootfs is mounted read-only. Invoke mntroot rw to
switch back to a writable rootfs.
#################################################
[root@kindle root]# 
```
You can now copy files:
```
scp book.epub root@192.168.15.244:/mnt/us/documents
```

Kindle K4 Jailbreak
====================


## follow instructions:

https://gist.github.com/estysdesu/c90478aac75b732820be6720254aeda7

from Linux, using NetworkManager 

- Open your network settings
- Open "USB Ethernet" settings
- (Optional) In the "Identity" tab, set "Name" to something to remind you that it's your Kindle
- In the "IPv4" tab:
    - Set "IPv4 Method" to "Manual"
    - Under "Addresses", set "Address" to 192.168.15.201 and "Netmask" to 255.255.255.0 
- Click "Apply"
- Restart the connection by disabling it and re-enabling it 

# usbNetwork 
The following notes mainly concern usbNetwork, an implementation of [Ethernet over USB](https://www.wikiwand.com/en/Ethernet_over_USB)

*The default IP's for Kindle K4 are as follows:*

HOST_IP=`192.168.15.201`
KINDLE_IP=`192.168.15.244`


```bash
ifconfig -a # find the usb device

sudo ifconfig enxee4900000000 192.168.15.201

ssh root@192.168.15.244

```


I had to manually activate USB-Ethernet in Ubuntu network settings. Then it worked. Now I'm going to install python on kindle. Because you know, why not. 

# For the paranoid: disable updates:
If you are interested in jailbreaking the kindle and _keeping it that way_, firmware updates are not your friend. 
Setting the device to airplane mode is not enough. There have been reported cases where kindle was updated, even though it was on airplane mode!

To prevent software updates from occuring, you can edit /etc/uks` 

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

