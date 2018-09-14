# Goke_GK7102
Hacks for various Goke GK7102 based IP Cameras, incl Domoticz connection

This reposirory is based on https://github.com/ant-thomas/zsgx1hacks , I made this copy to avoid messing things up.

Features:
Startup made more robust (especialy waiting for the network to become available)
Introduced native Domoticz logging based on Camera EVENTs (probably sensitivity needs tweaking)
Included jpeg snapshot
Improved webui page (includes snapshot and manual IRCut operation)

NOTE: ONLY the persistent hack (ie. where you do not need the SD card for R/W capable cameras) is tested to be working.

Instructions: (note 192.168.1.117 is my camera IP, adapt to your own)
Shell login: root / cxlinux
OnVif: rtsp://192.168.1.117 (1280x720 resolution), username admin/no password
Snapshot: http://192.168.1,117:554/snapshot (320x180 resolution)
Webui: http://192.168.1.117:8080/cgi-bin/webui

If you do not need Domoticz logging, you have to comment out two lines in the /home/p2pcam.sh script. These lines are marked with "#Comment out next line if NO Domoticz logging is needed"

Configure Domoticz logging:
In Domoticz: Create a virtual device of type "Sensor", remember the index of that device!
On your camera:
Edit /home/p2pcam.sh using vi and modify:
"770" to the index of your Domotcz Alert sensor (2 locations)
"192.168.1.211" to the ip of your Domoticz (4 locations)
"192.168.1.117" to the ip of your camera (2 locations)
