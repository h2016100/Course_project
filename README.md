# Course_project of Linux Device Drivers (EEE-G547)

Our original work was porting the ESP12E/F driver on Raspberry Pi for seemless wifi interface to Raspberry Pi. After trying a lot,debugging issues and testing the hardware and driver multiple times, we have come to the conclusion that the driver does not work. The link is as follows-
https://github.com/al177/esp8089

Conclusions-
- Build RPi kernel sources before installing the driver.
- The driver once installed cannot be removed ( rmmod removes the driver but reloads it again). This makes debugging the code a tedious      task.
- DO NOT connect resistors to SDIO connections as they do not let sufficient current to flow to the esp module. 
- This driver (https://github.com/al177/esp8089) will not work with 
   - NodeMCU as NodeMCU pulls down GPIO15 module which renders it incapable to boot in SDIO mode. Pulled down GPIO15 is for booting in 
      flash mode.
   - ESP01 as ESP01 does not have SDIO pins.
- Code can be debugged but will require a lot of time and persistence ( the original code has 41 files -good luck with that)

Finally we have built a code for demonstrating IoT application using NodeMCU and Raspberry Pi.
Data is sent and received from api.thingspeak.com. 
You can see the channel - https://thingspeak.com/channels/263048
Lua scripts are uploaded on NodeMCU which are called from a C Code to show system programming and application. Raspberry Pi data ( which will be the node here) can be sent and received from the channel in this manner.

