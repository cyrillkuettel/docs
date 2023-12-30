# docs


### Usb storage device
Device may is recogniezd as a usb mass storage device, because I have disabled it.
To set USB mode default again, edit the file usbnet/auto and remame to DISABLE_auto


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

On Ubuntu this sometimes takes one minute or two before this appears in the settings, then you're good to go! ![pci_ethernet](https://github.com/cyrillkuettel/docs/assets/36520284/e569948b-4f03-4cef-acf2-1225625decb4).

this may help but I'm not 100% sure:
```bash
sudo systemctl restart NetworkManager
```

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
