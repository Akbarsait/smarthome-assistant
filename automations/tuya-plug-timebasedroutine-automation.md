# Toggle Tuya Plug to On/Off based on Time
This simple script will toggle a Tuya wifi switch at the given time. Routine can be scheduled daily or on a specific day of the week. I am utilizing this schedule to charge the Oral B electric tooth brush. 

Integrations & Devices Required: 
- [Time & Date](https://www.home-assistant.io/integrations/time_date) for handling time based schedule. 
- [Tuya](https://www.home-assistant.io/integrations/tuya)
- Any Smart Plug

Routine for Daily charging On:
```yaml
alias: OralBPlug Charging On Routine
description: Daily charging Time for OralB
trigger:
  - platform: time
    at: "22:00:00"
condition: []
action:
  - type: turn_on
    device_id: f89f354664005c68272a3ca960639dd6
    entity_id: 57956ead2f177ad082237c672ae78f67
    domain: switch
mode: single
```

Routine for Daily charging On:
```yaml
alias: OralBPlug Charging Off Routine
description: Daily OralB charging TurnOff
trigger:
  - platform: time
    at: "23:00:00"
condition: []
action:
  - action: switch.turn_off
    metadata: {}
    data: {}
    target:
      device_id: f89f354664005c68272a3ca960639dd6
mode: single
```