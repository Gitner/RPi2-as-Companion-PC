# RPi2-as-Companion-PC
Everything needed to set up a Raspberry Pi 2 as a server for streaming and telemetry
# Raspberry Pi Camera Module 3
# Streaming
on server (RPi2):
$ rpicam-vid -t 0 --inline -o udp://<client-ip>:<port>
on client:
$ ffplay udp://<server-ip>:<port> -fflags nobuffer -flags low_delay -framedrop
# Mavlink
$ sudo raspi-config
Interface Options -> Serial Port -> Serial Login Shell [NO] Serial Interface [YES]
$ sudo nano /boot/firmware/config.txt
enable_uart=1
$ sudo reboot
$ sudo apt update
$ sudo apt install python3-pip
$ sudo apt install python3-dev python3-opencv python3-wxgtk4.0 python3-matplotlib python3-lxml libxml2-dev libxslt-dev
$ sudo pip install PyYAML mavproxy
$ sudo mavproxy.py --master=/dev/ttyAMA0
