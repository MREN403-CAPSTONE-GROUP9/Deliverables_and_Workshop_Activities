# Network Tests

Setup quick video stream and receive package in robotEnv to test network infrastructure.

Streamer was run on RaspberryPi 5 connected to a wifi 5 network. Receiver was run in a WSL environment run with network in mirror mode to enable the laptop ROS domain to be seen by the WSL.

network was observed to be uploading a constant 48Mbps from the pi while streaming was running at 22fps 720p.

assuming 22fps * 8 bit * 3 channels * 720 * 1280 = 486,604,800 bits per second (486 MB) of uncompressed data would suggest video compression reduces file size by 90% or data is being lost 48 Mbps observed. Further investigation is planned to be confirmed

## Known limitations

Online sources suggest max wifi speed for pi is around 200Mbps
https://www.tomshardware.com/news/raspberry-pi-5-wi-fi-faster however this should be further rested

For remote processing of 1 or 2 camera feeds this should be possible to offload work on the pi (assuming lidar is similar data load or can be processed on pi). If more cameras are needed or other large network traffic is added alternatives to the pi may need to be investigated to ensure the video can be processed in real time. 

There may be an option to add a graphics card to the raspberry pi to increase compute.