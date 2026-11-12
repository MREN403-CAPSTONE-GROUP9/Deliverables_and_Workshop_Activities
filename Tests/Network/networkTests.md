# Network Tests

Setup quick video stream and receive package in robotEnv to test network infrastructure.

Streamer was run on RaspberryPi 5 connected to a wifi 5 network. Receiver was run in a WSL environment run with network in mirror mode to enable the laptop ROS domain to be seen by the WSL.

network was observed to be uploading a constant 48Mbps from the pi while streaming was running at 22fps 720p.