# Real-time Streaming with Tapo Camera using WebRTC Approach
This guide provides configuration details for real-time streaming of the Tapo C110 camera using the WebRTC approach.

### Devices & Integrations Required: 
- [go2rtc](https://github.com/AlexxIT/go2rtc)
- [WebRTC](https://github.com/AlexxIT/WebRTC)
- [Tapo C110](https://www.tapo.com/us/product/smart-camera/tapo-c110/)


### Configuration Steps: 
1. Install [WebRTC](https://github.com/AlexxIT/WebRTC) via HACS or following the manual approach. 
2. WebRTC utilizes [go2rtc](https://github.com/AlexxIT/go2rtc) as Streaming Server. Install go2rtc as an addon in HA. 
3. Start go2rtc Addon. 
4. Add a custom card with the IP address of your camera in the following format. 
   1. Install the TP-Link Tapo app on your mobile. [Android](https://play.google.com/store/apps/details?id=com.tplink.iot&hl=en_CA) | [iOS](https://apps.apple.com/us/app/tp-link-tapo/id1472718009)
   2. Follow the instructions on the configure the Tapo C110 camera. 
   3. Create the camera account with the username and password in the TP-Link App. 
   4. Replace the username, password and IP address from the Tapo C110 from the app. 
   5. Utilize the following website to generate C110 Steam URL [Tapo Camera Steam URL](https://www.ispyconnect.com/camera/tapo).
   
```yaml
type: custom:webrtc-camera
url: rtsp://username:pwd@192.168.18.21:524/stream1
``` 

### Installation Screenshots:
![WebRTC Instatllation](/images/Tapo-WebRTC-1.png)

![go2rts Instatllation](/images/Tapo-WebRTC-2.png)

![go2rts Instatllation Success](/images/Tapo-WebRTC-3.png)
