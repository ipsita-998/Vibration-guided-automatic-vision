# Introduction

The camera module was made to rotate and point to an area where  the vibration sensor sensed maximum disturbance 
and the video recorded by the camera was streamed live on an android device using IOT.
The main aim of implementing this project was to provide security surveillance in an economical manner 
where only one camera module can cover the entire area instead of having multiple camera being 
implemented for surveillance. 

The video link of the working model of this project is as follows

https://drive.google.com/file/d/1-4YlXo5mPkwj5zYY585xsM7c_UXSeJ5X/view?usp=sharing

# hardware Requirements

- Arduino 
- Raspberry pi 
- Raspberry pi camera module, 
- Digital output vibration sensor 
- Stepper motors

# Software Requirements
- Arduino IDE
- VLC media player app
- Putty (for ssh in windows, note if using mac OS putty is not required)

# Instructions

- Connect the stepper motor to the i/o pin 9 of the arduino
- Mount the camera module onto the stepper motor using the camera mount
- Connect the  two vibraton sensors to the i/o pin  7 and 8 of the arduino
- Connect the camera cable to the camera port of the raspberry pi 
- download the vlc media app to your android device

## Configurating Raspberry pi for ssh
- before ssh we need to connect raspberry pi to the internet
- make sure that the raspberry pi and the android device where you whish to live atream your video 
  must be connect to the same wifi network
- get the IP address of the pi
   -we can get the ip address of the PI by using the "FING" app
- WIndows users follow the link below for ssh to pi

 https://www.youtube.com/watch?v=uNStEDWnPxY
 
- Mac users follow the link below fo ssh to pi

 https://www.youtube.com/watch?v=0wn44MbxtZw

- After the conficuration of ssh to pi type the below command in putty (for windows) or the terminal (for mac)

raspivid -o - -t 0 -hf -w 800 -h 400 -fps 24 |cvlc -vvv stream:///dev/stdin --sout '#standard{access=http,mux=ts,dst=:8160}' :demux=h264

- in the  vlc app goto the "stream" option and enter the follwing url

http://IP address of your raspberry pi :8160 

for example : http://192.168.1.19:8160 

where 192.168.1.19 is the IP of the raspbery pi





 
 
 
 



