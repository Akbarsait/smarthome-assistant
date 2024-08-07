# Adding Triggers to Aqara Mini Switch
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
The following code handles some automation for "double" tap action of the switch. 

```yaml
id: '1722999999631'
alias: AMiniSwitch - DoubleTap
description: 'Turn off the switches, toggle the lights and turn off a light. '
trigger:
  - platform: device
    domain: mqtt
    device_id: 6cbadc75aef8e55f39d3f26d0b1c29a9
    type: action
    subtype: double
condition: []
action:
  - service: switch.turn_off
    metadata: {}
    data: {}
    target:
      device_id:
        - f89f354664005c68272a3ca960639dd6
        - d0cca0e708d471c283fffc2418efd242
  - service: light.toggle
    metadata: {}
    data: {}
    target:
      device_id:
        - 107db0d4738a5964790d32d7e4e39702
  - service: light.turn_off
    metadata: {}
    data: {}
    target:
      device_id: 273ef34f0cd62e861b85f4a0302e04bf
mode: single
```