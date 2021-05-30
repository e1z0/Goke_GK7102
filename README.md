# Goke_GK7102
Goke based chipset cameras research
# Password
Default root password for Goke cameras is "cxlinux"

# Recovery after soft brick (corrupted scripts)
* Format SD Card using FAT32 file system
* Put this script named "my-custom_init.sh"

```
#!/bin/sh

net() {
sleep 40
killall udhcpc
ifconfig eth0 192.168.1.100 # camera ip address
ifconfig eth0 up
/bin/busybox telnetd -p 24 -l /bin/sh
route add default gw 192.168.1.1 # your network gateway
}

net &
```
Now insert the sd card to the camera boot it up, first time it just copies file, after second boot it will execute it. Now you can connect via telnet to port 24 to it, there will be no user/pass prompt.
