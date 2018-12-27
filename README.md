# ip-rtsp
common ip camera endpoints
```
ReoLink RL420
blue iris:
model: ... Baseline RTMP
path: /bcs/channel0_main.bcs?channel=0&stream=0&user={id}&password={pw}

Amcrest:
model ProHD RTSP/HTTP
path: /cam/realmonitor
params: channel={CAMNO}&subtype=0&authbasic={AUTH64}

Starlite:
make: Generic
model: RTSP H.264...
/cam/realmonitor?channel=1&subtype=0&unicast=true&proto=Onvif

```
bash script to show sized windows of rtsp streams (ip cam security cam) in a 4 x 4 matrix 
```
#!/bin/bash

# First row
sleep 10
# omxplayer 'rtsp://USERNAME:PASSWORD@192.168.x.x/h264Preview_01_main'
screen -dmS camera1 sh -c 'omxplayer --win "0 0 960 540" rtsp://<USERNAME>:<PASSWORD>@192.168.x.x/h264Preview_01_main; exec bash'
screen -dmS camera2 sh -c 'omxplayer --win "960 0 1920 540" rtsp://<USERNAME>:<PASSWORD>@192.168.x.x/h264Preview_01_main; exec bash'

screen -dmS camera3 sh -c 'omxplayer --win "0 540 960 1080" rtsp://USERNAME:PASSWORD@192.168.x.x:554/cam/realmonitor?channel=3&subtype=0; exec bash'
#screen -dmS camera4 sh -c 'omxplayer --win "960 540 1920 1080" rtsp://USERNAME:PASSWORD@172.16.x.x:554/cam/realmonitor?channel=4&subtype=0; exec bash'

```
to kill all omxplayer windows created in the above bash script:
```sudo killall omxplayer.bin```

to get this script to show in x windows gui on raspberry pi stretch on boot:

edit:
`sudo vi /etc/xdg/lxsession/LXDE-pi/autostart`

add:
```
@lxterminal -e /home/pi/<bashFile>.sh
```
