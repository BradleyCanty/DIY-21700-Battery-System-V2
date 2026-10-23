# DIY-21700-Battery-System-V2
A do-it-yourself 21700 battery for use in UAVs or UGVs. Scalable from 6s3p to 12s8p. Designed for automated battery swapping via SCARA robot arm.

STILL IN PROGRESS... CHECK BACK LATER!!!
CURRENT PROGRESS as of 2026/10/23...

(vehicle adapter and battery shown below)

<p align="center">
  <img src="Images/vehicle_adapter.jpg" width="48%">
  <img src="Images/battery_on_vehicle_adapter.jpg" width="48%">
</p>

(human hand and robot manipulator-compliant latching mechanism embedded in battery end plates shown below; note that the white arms are meant to represent the fingers of the robot manipulator)

<p align="center">
  <img src="Images/end_plate_mechanism_1.jpg" width="48%">
  <img src="Images/end_plate_mechanism_2.jpg" width="48%">
</p>


(battery PCB shown below; used for measuring voltages at each busbar and temperature at a single point in the battery (via thermistor), and reporting values in MAVLink BATTERY_STATUS message over UART to the flight controller) 

<p align="center">
  <img src="Images/battery_pcb_1.png" width="48%">
  <img src="Images/battery_pcb_2.png" width="48%">
</p>

(position lights and low battery voltage alarm PCB shown below; used for powering the position lights, orientation lights, and low battery voltage alarm lights and buzzer)

<p align="center">
  <img src="Images/position_lights_and_batt_low_voltage_alarm_pcb_1.png" width="48%">
  <img src="Images/position_lights_and_batt_low_voltage_alarm_pcb_2.png" width="48%">
</p>

(additional images of battery progress as of 2026/10/23)

<img width="4080" height="3072" alt="PXL_20261023_152130491~2" src="https://github.com/user-attachments/assets/a7392df0-47bf-413d-b4c9-120e16e1e378" />
<img width="4080" height="3072" alt="PXL_20261023_152154996~2" src="https://github.com/user-attachments/assets/5f130431-4f1d-448c-98da-9fea2a8f942d" />
<img width="4080" height="3072" alt="PXL_20261023_152228921~2" src="https://github.com/user-attachments/assets/461db30e-c5df-44e3-93d3-deba047a295f" />
<img width="4080" height="3072" alt="PXL_20261023_152218209~2" src="https://github.com/user-attachments/assets/32f9102a-8b7e-4c95-a59a-5cca56d8aa4b" />
<img width="4080" height="3072" alt="PXL_20261023_153041098~2" src="https://github.com/user-attachments/assets/30d65617-d144-4fb8-ad66-99b8cebaa466" />
<img width="4080" height="3072" alt="PXL_20261023_153941220" src="https://github.com/user-attachments/assets/45a4e4e7-436b-4d60-b5d1-5b8cb51a37dc" />
<img width="3072" height="3700" alt="PXL_20261023_154424698" src="https://github.com/user-attachments/assets/1b8eef8d-1ee5-4b2d-83d5-6d882b11901a" />
<img width="3072" height="4080" alt="PXL_20261023_160129843" src="https://github.com/user-attachments/assets/ccfa21c0-7910-4416-8ae4-00024d325eed" />
<img width="3072" height="4080" alt="PXL_20261023_160245169" src="https://github.com/user-attachments/assets/c668d0fb-968e-4113-a876-88e8afbfb398" />
<img width="4080" height="3072" alt="PXL_20261023_160451805" src="https://github.com/user-attachments/assets/2fe7c997-7408-44f8-b060-fa4f2f3ad180" />

(SCARA robot Solidworks assembly)

<img width="690" height="787" alt="battery_swap_scara" src="https://github.com/user-attachments/assets/d2c7feb8-2a87-48c0-b5d1-9ba59c8ef2fa" />

(SCARA robot manipulator for battery pick-and-place)

<img width="4080" height="3072" alt="PXL_20261023_152100001" src="https://github.com/user-attachments/assets/274ac4bc-a860-4051-9840-99b7512cabe1" />
<img width="4080" height="3072" alt="PXL_20261023_152111332~2" src="https://github.com/user-attachments/assets/173739bd-8d24-42ab-8d8a-9ff2cf7fa5a7" />


## IMMEDIATE TO DO
* Populate battery PCB and ground test
* Populate low voltage alarm PCB and ground test
* Create the components for demo quadrotor
* Complete the demo quadrotor and do ground testing on all functions
* Perform flight test
* Upload CAD files to GitHub only once its verified as working post flight test
* Upload PCB files to GitHub only once its verified as working post flight test
* Update the 3p, 4p, 5p end plates

## FUTURE TO DO (V3)
* Replace UART with CAN bus (use droneCAN?): this makes the signal more robust
* make an automated battery swapping system composed of a robot arm with a gripper and some way to precisely orient the gripper to actuate the latching mechanism on the battery (maybe can use RTK GPS to make the vehicle position very accurate, move robot arm over that position, then have a camera on the robot arm find an ArUco target located next to the battery and use it to 1) orient the gripper, 2) center gripper over battery)
* Eliminate balance pins entirely (such as Tattu Plus DroneCAN battery): the battery would instead have an internal battery management system that broadcasts telemetry (real-time individual cell voltages, cycles, capacity, and temperature) directly onto a Controller Area Network (CAN) bus (use DroneCAN protocol?). The charger would reads this data dynamically to manage current distribution safely. See https://ardupilot.org/copter/docs/common-tattu-dronecan-battery.html?st_source=ai_mode
* Extend battery configuration to 24 cells in series (~100V). Requires extra safety precautions for creepage and redesign of PCBs, specifically MOSFETs in antispark circuit
* Extend end plate cell widths to 7 up to 12
* Create circuit which has supercapacitors that power the quadrotor for ~45 seconds when the used battery is removed: this allows enough time for a fresh battery to be installed, preventing system shutdown
