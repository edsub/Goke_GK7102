# Goke_GK7102
Hacks for various Goke GK7102 based IP Cameras, incl Domoticz connection

This works on the cheap DG-MYQ cloudcam from Digoo (at least version 3.2.8.0121 that appears to have a R/W /home folder)

This reposirory is based on https://github.com/ant-thomas/zsgx1hacks , I made this copy to avoid messing things up.
Additionalinfo can be found in https://github.com/yuvadm/DG-M1Q

Features:

    Startup made more robust (especialy waiting for the network to become available)
  
    Introduced native Domoticz logging based on Camera EVENTs (probably sensitivity needs tweaking)
  
    Included jpeg snapshot
  
    Improved webui page (includes snapshot and manual IRCut operation)


NOTE: ONLY the persistent hack (ie. where you do not need the SD card for R/W capable cameras) is tested to be working.

Instructions: (note 192.168.1.117 is my camera IP, adapt to your own)

    Copy the contents of sdcard.rar to am empty SD card, put it in your camera and start the thing up.
    
    It is advised to have the camera configured for your WiFi using the Digoo app beforehand, OR you can use following instructions:
    
      run /home/hack/goke_p2pcam_param -f /home/devParam.dat -wtest -ktest. 
      Any SSID and PSK are fine, this is not used at all AFAIK, but without this wpa_supplicant is never started.
      Set your SSID and PSK in /home/wpa_supplicant.conf.
      Device should connect to your WiFi after reboot.
    
    You can start an SSH (or serial if you use the serial port of the camera board) shell to the camera
    
    Shell login: root / cxlinux
  
    OnVif: rtsp://192.168.1.117 (1280x720 resolution), username admin/no password
  
    Snapshot: http://192.168.1.117:554/snapshot (320x180 resolution)
  
    Webui: http://192.168.1.117:8080/cgi-bin/webui
  

If you do not need Domoticz logging, you have to comment out two lines in the /home/p2pcam.sh script. These lines are marked with "#Comment out next line if NO Domoticz logging is needed"

Configure Domoticz logging:

  In Domoticz: 
  
    Create a virtual device of type "Sensor", remember the index of that device!
  
  On your camera:
  
    Edit /home/p2pcam.sh using vi and modify:
    
    "770" to the index of your Domotcz Alert sensor (2 locations)
    
    "192.168.1.211" to the ip of your Domoticz (4 locations)
    
    "192.168.1.117" to the ip of your camera (2 locations)
