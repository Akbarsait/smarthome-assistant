# Enabling USB Drivers on Synology NAS for Zigbee Integration:
This is self-reference for enabling Zigbee USB Dongle Plus with Home Assistant. The HA is installed through VM in the Synology NAS. Starting the DSM 7 rollout, the USB drivers are disabled in Synology. This approach will guide in enabling it and utilizing. 

Thanks to the Author who put together this document for enabling serial drivers for Synology DSM NAS. 
https://giuliomenna.net/blog/synology-nas-usb-port-activation-for-sonoff-zigbee-dongle-and-zigbee2mqtt/#prerequisites


1. Enable SSH access to the Synology NAS by following this document. Ref: https://kb.synology.com/en-global/DSM/tutorial/How_to_login_to_DSM_with_root_permission_via_SSH_Telnet


```ssh
> ssh Akbarsait29@192.168.68.58 -p 22
> Akbarsait29@ABAA-NAS:~$ sudo -I
> Enter Admin password
> lsusb (to display all usb devices)
> cd /dev
> ls 
```

2. Find your Synology NAS CPU Architecture (For DSM218+, it will be Apollolake). Ref: https://kb.synology.com/en-global/DSM/tutorial/What_kind_of_CPU_does_my_NAS_have
3. Copy the files for the Architecture/version from the following github location. Ref:https://github.com/robertklep/dsm7-usb-serial-drivers/tree/main/modules/apollolake/dsm-7.1
4. Place the files to the your NAS location "/volume1/homes/USERNAME/drivers/". In case the drivers folder is not available, create one. For my DSM218+ "/volume1/homes/Akbarsait29/drivers/".
5. Next insert the downloaded modules into the Kernel using the following line commands. 

```ssh
cp /volume1/homes/Akbarsait29/drivers/ch341.ko /lib/modules/ch341.ko
sudo insmod /lib/modules/ch341.ko

cp /volume1/homes/Akbarsait29/drivers/cp210x.ko /lib/modules/cp210x.ko
sudo insmod /lib/modules/cp210x.ko

cp /volume1/homes/Akbarsait29/drivers/pl2303.ko /lib/modules/pl2303.ko
sudo insmod /lib/modules/pl2303.ko

cp /volume1/homes/Akbarsait29/drivers/ti_usb_3410_5052.ko /lib/modules/ti_usb_3410_5052.ko
sudo insmod /lib/modules/ti_usb_3410_5052.ko
```

6. Prepare the following start-up script name it as start_usb_drivers.sh with the following line of codes.

```ssh
#!/bin/sh
case $1 in
  start)
    insmod /lib/modules/usbserial.ko > /dev/null 2>&1
    insmod /lib/modules/ftdi_sio.ko > /dev/null 2>&1
    insmod /lib/modules/cdc-acm.ko > /dev/null 2>&1
    insmod /lib/modules/cp210x.ko > /dev/null 2>&1
    insmod /lib/modules/ch341.ko > /dev/null 2>&1
    insmod /lib/modules/pl2303.ko > /dev/null 2>&1
    insmod /lib/modules/ti_usb_3410_5052.ko > /dev/null 2>&1
    ;;
  stop)
    exit 0
    ;;
  *)
    exit 1
    ;;
esac
```

7. Now copy start_usb_drivers.sh to the /usr/local/etc/rc.d/ folder:

```ssh
cp /volume1/homes/Akbarsait29/drivers/start_usb_drivers.sh /usr/local/etc/rc.d/start_usb_drivers.sh
cd  /usr/local/etc/rc.d/
sudo chmod +x start_usb_drivers.sh
```

8. Now lets run and check USB-to-serial convertor is recognized by the system. You should now see **ttyUSB0** as listed below in the screenshot. 

```ssh
sudo /usr/local/etc/rc.d/start_usb_drivers.sh start

cd /dev

ls
```

![ttyUSB0](/images/serial-usb-covertor.png)

**Tips:**
1. In case if you are running HA as a VM in Synology NAS, first enable the USB device by selecting Action > Edit > Others. 

![ttyUSB0](/images/enable-usb-inVirtualM.png)

2. Select "USB Device" with an option from list. Otherwise, the enabled ttyUSB0 will not be visible in HA under Hardware > Devices. 