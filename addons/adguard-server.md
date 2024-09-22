# AdGuard

[AdGuard Home](https://adguard.com/adguard-home/overview.html) is a powerful ad-blocking server that enhances your browsing experience by filtering out ads and trackers. Installing it in Home Assistant is straightforward, just like adding any other add-on. With a simple setup, you can easily integrate AdGuard Home into your network to block ads across all devices.

## Installation 
1. Navigate to Home Assistant > Settings > Add-ons > Click ADD-ON Store
2. Search for AddGaurd Home
3. Click Installation 

## Configuration
AdGuard offers various configuration options to suit different needs, but the recommended approach is to set it up at the router level. This ensures that all devices connected to the network are protected, eliminating the need to configure each device individually.

1. Open your router admin access link. 
2. It will be either http://192.168.0.1/ or http://192.168.1.1/ based on how it is configured. 
3. Find DHCP/DNS Settings. 
4. Enter your AdGaurd Home IP addresses. This can be visible by accessing AdGaurd Home > Setup Guide

## Links
- [AdGuard Home](https://github.com/hassio-addons/addon-adguard-home)
- [AdGuard Documentation](https://github.com/hassio-addons/addon-adguard-home/blob/v5.1.2/README.md)


![AdGuard](/images/AdGaurd.png)