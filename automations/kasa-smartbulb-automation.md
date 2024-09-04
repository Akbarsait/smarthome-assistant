# Kasa Smart Bulb Automation
This script helps automate turning on the Kasa Smart Wi-Fi bulb daily at 6 PM. Additionally, you can customize settings such as brightness, color, and other preferences.

**Device Configuration:**
1. Tapo Link App: Add the device through the Kasa/Tapo App for Google Play or Apple Store. The other way to configure is by following the python discovery mode using [kasa command-line tool](https://python-kasa.readthedocs.io/en/latest/cli.html#provisioning). 
2. Home Assistant Integration: Add the integration by navigating to *Settings > Device & Services > Integration > Add Integration* or using the link https://www.home-assistant.io/integrations/tplink/
3. Enter the IP of the device. You can find it through the Tapo App > Select Device > Device Info > IP Address

![Step 1](/images/AddingTapoDevice-1.png)

![Step 2](/images/AddingTapoDevice-2.png)


**Metadata Options:**
- *brightness_pct*: Number indicating the percentage of full brightness, where 0 turns the light off, 1 is the minimum brightness, and 100 is the maximum brightness.
- *rgb_color*: The color in RGB format. A list of three integers between 0 and 255 representing the values of red, green, and blue.
- *kelvin*: Color temperature

**Integrations & Devices Required:** 
- [TP-Link Smart Home](https://www.home-assistant.io/integrations/tplink)
- [Kasa Smart Light Bulb - KL125P2](https://www.amazon.ca/Kasa-Smart-Compatible-KL125P2-Multicolour/dp/B08TB6VXFL/)

**Routine for Daily charging On:**
```yaml
alias: Lights On Routine
description: Turns Hall, Room lights at 6PM using the connected switches
trigger:
  - platform: time
    at: "18:00:00"
condition: []
action:
  - action: light.turn_on
    metadata: {}
    data:
      brightness_pct: 81
      rgb_color:
        - 105
        - 185
        - 195
      kelvin: 4862
    target:
      device_id: 129e0f48fb89bb125ccb2316409a295c
      device_id: e75d9094498591be4ac752788a323cd3
mode: single
```