# Adding Triggers to Aqara Mini Switch
This is a simple script to automate [Aqara Mini switch](https://www.aqara.com/en/product/wireless-mini-switch/) click events. The code below enables three power switches at my location. Identically, a light or an alarm could be enabled based on the click. 
- Single
- Double
- Hold
- Release

```yaml
alias: AqaraMini - SinglePress
description: "Turns on a sequence of Switches and bulbs"
trigger:
  - platform: device
    domain: mqtt
    device_id: 6cbadc75aef8e55f39d3f26d0b1c29a9
    type: action
    subtype: single
condition: []
action:
  - metadata: {}
    data: {}
    target:
      device_id: d0cca0e708d471c283fffc2418efd242
    action: switch.turn_on
  - metadata: {}
    data: {}
    action: switch.turn_on
    enabled: true
    target:
      device_id: e75d9094498591be4ac752788a323cd3
  - metadata: {}
    data: {}
    target:
      device_id: 13db1b7c7dcf9358724fc0dc1c4c7a84
    action: switch.turn_on
  - action: light.turn_on
    metadata: {}
    data: {}
    target:
      device_id: 129e0f48fb89bb125ccb2316409a295c
mode: single
```
The following code handles some automation for "double" tap action of the switch. 

```yaml
alias: AMiniSwitch - DoubleTap
description: "Turn off the switches, toggle the lights and turn off a light. "
trigger:
  - platform: device
    domain: mqtt
    device_id: 6cbadc75aef8e55f39d3f26d0b1c29a9
    type: action
    subtype: double
condition: []
action:
  - action: switch.turn_off
    metadata: {}
    data: {}
    target:
      device_id:
        - e75d9094498591be4ac752788a323cd3
        - d0cca0e708d471c283fffc2418efd242
  - action: light.turn_off
    metadata: {}
    data: {}
    target:
      device_id: 129e0f48fb89bb125ccb2316409a295c
mode: single
```