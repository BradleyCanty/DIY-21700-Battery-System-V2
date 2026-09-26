# DIY-21700-Battery-System-V2
A do-it-yourself 21700 battery for use in UAVs or UGVs

## VERSION 2 TO DO
* Have a single common PCB for all battery configurations
* implement the voltage sensing functionality and report over MAVLink via UART
* Implement temperature measurement via two thermistors and report over MAVLink via UART
* rework the end plate latching mechanism, which in its current form unlatches by pinching from the side, with a latching mechanism that unlatches by pinching from the top: this would facilitate ingress to/egress from the top surface, but requires load bearing on the interior top and bottom of the latching mechanism cutout. The point is to make it easy to vertically lift away/toward a sky-facing cutout in an airframe, such that the battery is suitable for use in a fixed-wing UAV. The current manifestation, where lifting from side handles, precludes this possibility. Keep in mind that it must be robot-gripper friendly for automated battery swapping, but also human hand compatible.
* Complete the battery low voltage alarm circuit (flashing orange LED lights and loud buzzer) and add the details to this project
* Replace JST-XH connector interface (used between battery and charging station/vehicle adapter) with machine pin headers

## TENTATIVE TO DO
* make an automated battery swapping system composed of a robot arm with a gripper and some way to precisely orient the gripper to actuate the latching mechanism on the battery (maybe can use RTK GPS to make the vehicle position very accurate, move robot arm over that position, then have a camera on the robot arm find an ArUco target located next to the battery and use it to 1) orient the gripper, 2) center gripper over battery)
* Eliminate balance pins entirely (such as Tattu Plus DroneCAN battery): the battery would instead have an internal battery management system that broadcasts telemetry (real-time individual cell voltages, cycles, capacity, and temperature) directly onto a Controller Area Network (CAN) bus (use DroneCAN protocol?). The charger would reads this data dynamically to manage current distribution safely. See https://ardupilot.org/copter/docs/common-tattu-dronecan-battery.html?st_source=ai_mode
* Extend battery configuration to 24 cells in series (~100V). Requires extra safety precautions for creepage and redesign of PCBs, specifically MOSFETs in antispark circuit
