# Turn Lights On/Off with Zigbee Motion Sensors Detection
This script toggles a switch connected to a lamp whenever motion is detected by the sensor. The code is divided into two sections: one defines the trigger based on the sensor's condition, and the other triggers an action to turn on the light, play audio, or perform another response.

The triggers available from the sensor are as follows:
- Occupancy become Occupied: Motion detected in the location. 
- Occupancy become not Occupied: Motion cleared in the location. 
- battery low
- battery normal
- battery level changes

The Actions available for a zigbee/wifi switch:  
- switch.turn_off
- switch.turn_on
- switch.toggle


```yaml
alias: Motion Sensor To Hall Light
description: "Switch On the Hall light when MotionSensor1 Occupancy detected occupancy "
trigger:
  - type: occupied
    platform: device
    device_id: 847c1b7dd4572b0e58adafeb1b288814
    entity_id: 1ab9f2dbf929101a7ffb124aa2c93b10
    domain: binary_sensor
condition: []
action:
  - action: switch.toggle
    metadata: {}
    data: {}
    target:
      device_id: f89f354664005c68272a3ca960639dd6
mode: single
```