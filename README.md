# uwb-beacon
High Precision Drone Landing Utilizing UWB Beacons

## Objective 

The goal of the project is to have the drone land autonomously on a platform using UWB beacons. We are doing so by Interfacing the beacons with the intel UP board. The intel board would then interface with the Pixhawk to be able to send signals to the drone to land autonomously at the right positions.

### Components   

Drone: DIY F550 Hexacopter Frame Kit with Pixhawk Fight Controller+7M +Simonk 30A ESC + 2212 920KV Motor

Computer: Intel UP Squared Series (Intel Atom® x7-E3950 Processor, 8GB memory, 64GB eMMC/Storage) 

PCB: A voltage regulator goes into the intel board to make sure it is getting the correct Volt and amps which are 4 Volts and 5 to 6 Amps.

Beacons: MDEK1001
RF Design Kit from Qorvo
UWB Dev Kit, Using 12 Dev DWM1001DEV Dev Board

### Programs Used
Robot operating system (Ros) 
ROS Noetic Linux install: https://wiki.ros.org/noetic/Installation/Ubuntu
*How to create ROS workspace: http://wiki.ros.org/catkin/Tutorials/create_a_workspace

Ubuntu version 22.04: https://ubuntu.com/download/desktop

Q Ground control: https://docs.qgroundcontrol.com/master/en/qgc-user-guide/getting_started/download_and_install.html

## Programs necessary to interface the beacons

Any serial port monitor that you desire. We only used the serial port to configure the beacon network. 

We used screen inside the Ubuntu default terminal.

### Commands to set up beacons
1. Open terminal in Ubuntu 
2. to find the serial port of your device, Type 'ls -l /dev/ttvUSB* /dev/ttvACM*'
2.1. you might have to change some permissions, to do this run the following command 'sudo usermod -a -G dialout $USER'
2.2. verify by running 'groups'. This should show 'dialout' as one of the outputs
3. Type 'screen /dev/ttyACM0 115200'
4. At this point, press the enter key twice in quick succession. Now you are connected to the beacon. Inside this terminal, we can make changes to interface with all the beacons in our network. Our network consists of 5 anchors and 1 tag. 
5. We start with configuring the initiator beacon. To do this type 'nis 0x1234' and then click enter. 
5.1. Next is to configure the position of the initiator. Type 'aps 0 0 0' this configures the location to x,y,z. 
5.2. type 'nmi' and press the enter button twice. this refreshes the beacon and loads in the updated parameters. 
6. configure anchors it is a similar process. follow steps 5.0 and 5.1. The command that is different is 'nma', make sure to hit enter twice. this configures the beacon as an anchor. make sure to set up the positions you would like. 
7. for a tag, follow step 5.0 and type 'nmt' and click enter twice.
This should configure your network.

### Getting data from your beacons
Now that you have your network set up, we can test to check the location of the tag to the anchors. 
in the same terminal, type 'les' and press enter.
This will show the different anchors and their position inside brackets. this is the anchor position in x,y,z. the number after is the range between the tag and the anchor. at the end of the output, the estimate shows the estimated position of the tag in x,y,z, quality factor--quality factor is the measurement of confidence in the accuracy of the estimate based on the ranges received. 

# Future Work

We want to improve our project by implementing the remote control via our Intel board and have the drone fly autonomously. 


# References

These are the reference links to all documentation of our project. [*Reference List*](https://github.com/mchang-13/uwb-beacon/blob/main/references.md)




