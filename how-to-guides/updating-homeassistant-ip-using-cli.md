# Updating IP address of HA through CLI
Last week while enabling **[Two routers with one Home Network](https://github.com/Akbarsait/todayilearned/blob/master/network/adding-two-routers-in-homenetwork.md)**, I forget to update the mapped IP address to my Home Assistant. After the switchover of the IPs based on the Main router, I lost the access to my Home Assistant. The following approach resolved my issue and came in handy. 

1. Check the network adapter and find your current IP address set for HA. Refer the command and image below for details. 
```ssh
ha > network info
```
 ![HA Network Info](/images/ha-networkinfo.png)

2. Execute the following command by replacing (“en3sp2”) with your HA network adapter name. 

```ssh
ha > network update en3sp2 --ipv4-method auto --ipv6-method disabled
```

For more reading, refer the following thread at the [Home Assistant Community](https://community.home-assistant.io/t/how-to-change-ip-adresse-in-cli/332205/24?u=akbar) forum. 


### Quick Reference Commands

1. Displays CLI banner with the Home Assistant URL, OS version, System information with IPv4 and IPv6
```ssh
ha > banner
```