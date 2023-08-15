# Configuring IP-Camera

## Check IP Camera IP's

1. Connect the NVR & IP Camera with PoE Switch and then connect it to Jetson or the RJ54 LAN supporting device.
2. Boot the NVR's firmware usin a Display
3. Enter the password and use the default IP Address as the Static IP for the camera.

## Configuring the IP Camera Locally to the Device

1. Connect the NVR & IP Camera with PoE Switch and then connect it to Jetson or the RJ54 LAN supporting device.
2. Then use the command `ifconfig` for Linux-based device and `ipconfig` for Windows based device.
3. After checking the Ethernet Status.
4. Go to the Network Section and change the IP Address according to the Local Network (for eg: If the IP Address of Camera is **192.168.0.41**, then change it to **192.168.0.1**).
5. Also, change the Subnet to **255.0.0.0**.
6. Then, try to check the device in the terminal by pinging the device using the command : `ping <ip_address>`
7. Then write the Python code below to capture the feed from the camera :
```
#!/usr/bin/python3
import cv2
cap = cv2.VideoCapture('rtsp://admin:123456789@192.168.0.41:554/stream1')
while True:
    ret, frame = cap.read()
    cv2.imshow('RTSP', frame)
    if cv2.waitKey(1) & 0xFF == ord('q'):
        break
cap.release()
cv2.destroyAllWindows()
```
