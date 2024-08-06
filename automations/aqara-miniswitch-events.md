# Adding Triggers to Aqara Mini Switch Aqara Mini Switch
This is a simple script to automate [Aqara Mini switch](https://www.aqara.com/en/product/wireless-mini-switch/) click events. The code below enables three power switches at my location. Identically, a light or an alarm could be enabled based on the click. 
- Single
- Double
- Hold
- Release

```yaml
alias: AqaraMini - SinglePress
description: ""
trigger:
  - platform: device
    domain: mqtt
    device_id: 6cbadc75aef8e55f39d3f26d0b1c29a9
    type: action
    subtype: single
condition: []
action:
  - service: switch.turn_on
    metadata: {}
    data: {}
    target:
      device_id: d0cca0e708d471c283fffc2418efd242
  - service: switch.turn_on
    metadata: {}
    data: {}
    target:
      device_id: f89f354664005c68272a3ca960639dd6
  - service: switch.turn_on
    metadata: {}
    data: {}
    target:
      device_id: 13db1b7c7dcf9358724fc0dc1c4c7a84
mode: single

```