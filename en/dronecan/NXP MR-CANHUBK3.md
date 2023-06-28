# NXP MR-CANHUBK3
The MR-CANHUK3 is an open-source evaluation kit and development board for redundant networking and safety applications in mobile robotics. It is based on the S32K344 general-purpose automotive microcontroller with lockstep Arm Cortex-M7 core. The main target for this board is mobile robotics, however it can certainly be used for multiple purposes where automotive lockstep cores may be desired. This is just an evaluation kit, it is meant to be used for testing and not used for a finished product. The board includes several different features, some of the main features are six CAN FD ports, as well as a 100BASE-T1 Ethernet PHY. Most of the other features are accessible on DroneCode standards JST-GH connectors. The board is fully compatible with the Dronecode standards.
![Front side of the board]( https://www.nxp.com/assets/images/en/dev-board-image/MR-CANHUBK344-TOP.png) 
![Back side of the board]( https://www.nxp.com/assets/images/en/dev-board-image/MR-CANHUBK344-BOTTOM.png)
### Quick Summary
**Main Processor**
- S32k344 Automotive General-Purpose MCU running a 160MHz Lockstep Arm® Cortex®-M7

**Authentication**
- SE050 EdgeLock Secure Element, supporting NFC interface

**Features/Interfaces**
- 6x CAN FD (each with 2 connectors, for easy daisy-chaining):
    - 2x TJA1463 (Signal Improvement Capabilities) 
    - 2x TJA1443 (High-Speed) 
    - 2x TJA1453 (Secure High-Speed) 
- DCD-LZ debug interface with SWD+Console/UART
- Arm 10-pin JTAG/SWD header for debugging*
    - *Can be extended to 20-pin
- Programmable user buttons
- 6x UART:
    - 2x with handshake 
    - 4x without handshake
- 3x I2C:
    - 2x general purpose 
    - 1x secure element
- 2x SPI
- 100Base-T1 2-Wire Ethernet PHY
- RC-PWM power output with internal or BEC/external power
- GPIO pins
- Optional Pixhawk IMU connector

**Power**
- FS26 Safety System Basis Chip with Low Power Fit (ASIL-D)
- 5V – 40V

### DroneCAN
The UCANS32K1 is not used as an autopilot. One way of using it is to build a PX4 distributed architecture. The same peripheral drivers running on an FMU can be reused here on the UCAN board, with only the CAN bus separating them. This means a common codebase is developed and used for something like a sensor or actuator. This board has a lot of extra features and different ways of using it.

All this is thanks to DroneCAN used as a CAN protocol. For more information on DroneCAN go to this [link](https://dronecan.github.io/).


### Where to buy
Use the following links to order: [MR-CANHUBK3](https://www.nxp.com/design/development-boards/automotive-development-platforms/s32k-mcu-platforms/s32k344-evaluation-board-for-mobile-robotics-with-100baset1-and-six-can-fd:MR-CANHUBK344)

## Board Setup
### Building Firmware
To build PX4 for this target:
```
make nxp_mrcanhubk3_fmu
```
### Debug Port
The [PX4 System Console]( https://docs.px4.io/main/en/debug/system_console.html) and the [SWD interface]( https://docs.px4.io/main/en/debug/swd_debug.html) run on the [DCD-LZ FMU Debug]( https://nxp.gitbook.io/hovergames/rddrone-fmuk66/connectors/debug-interface-dcd-lz) port.
NXP's DCD-LZ is a 7 pin JST-GH connector and adds the nRST/MCU_RESET pin to the [Pixhawk 6-Pin standard debug port]( https://github.com/pixhawk/Pixhawk-Standards/blob/master/DS-009%20Pixhawk%20Connector%20Standard.pdf).
The DCD-LZ breakout adapter permits the use of a standard 10 pin JTAG/SWD interface (i.e. using the Segger Jlink) and a standard 5 pin FTDI USB-TTL-3V3 type cable

### Further Info
Visit our [GitBook page](https://nxp.gitbook.io/mr-canhubk3/) for more detailed explanation on the CANHUBK3 board.
Check other boards developed by NXP that support the PX4 framework:
- [RDDRONE-FMUK66](https://www.nxp.com/design/designs/px4-robotic-drone-vehicle-flight-management-unit-vmu-fmu-rddrone-fmuk66:RDDRONE-FMUK66): Flight management unit.
- [UCANS32K1](https://www.nxp.com/products/interfaces/can-transceivers/can-signal-improvement/can-sic-evaluation-board:UCANS32K1SIC): General purpose CAN node. 
- [8MPNAVQ](https://www.nxp.com/design/designs/navqplus-ai-ml-companion-computer-evk-for-mobile-robotics-ros-ground-stations-and-camera-heads:8MPNAVQ): Small companion computer for mobile robotics application.
- [RDDRONE-BMS772](https://www.nxp.com/design/designs/smart-battery-management-for-mobile-robotics:RDDRONE-BMS772): Battery management System for Mobile Robotics.
