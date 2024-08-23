# Adding Media Notificaiton/Alerts to Zigbee Door Sensors
The goal is to trigger an alert with a custom audio message or notification whenever a door or window is opened. The code uses two inputs: the device and entity ID, which then trigger an action to play the audio through one of the connected media players.


```yaml
alias: Door Open Alert
description: "Play a custom audio whenever door opens"
trigger:
  - type: opened
    platform: device
    device_id: d005f924c6808115e0eae9d995719f75
    entity_id: a8a20ab5cfd230c2a4c229c0f96f9900
    domain: binary_sensor
condition: []
action:
  - action: media_extractor.play_media
    target:
      device_id:
        - 81a35acf44191df9cc0fad9dfef21b8c
    data:
      media_content_type: MUSIC
      media_content_id: http://localip:8123/local/alertsounds/main-door-open.m4a
  - action: media_player.volume_set
    metadata: {}
    data:
      volume_level: 0.7
    target:
      device_id: 81a35acf44191df9cc0fad9dfef21b8c
mode: single
```