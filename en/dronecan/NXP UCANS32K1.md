# NXP UCANS32K1
The UCANS32K1SIC is a reference design development board used as a general purpose CAN node. This board uses specific software for drones, rovers and other small (autonomous) vehicles. This software allows it to act as a bridge between a CAN bus (with UAVCAN) and I2C, SPI, UART, GPIO on any other feature supported by the MCU. This allows sensors, actuators and other peripherals to be controlled by other devices on the same CAN bus. The board is also DroneCode connector standard compliant.
![Front side of UCANS32K1 board](../../assets/hardware/can_nodes/NXP_UCANS32K1(front).jpg)
![Back side of UCANS32K1 board](../../assets/hardware/can_nodes/NXP_UCANSS32K1(back).jpg)
### Quick Summary
**Main Processor:**
- S32K1 running  a 80 MHz 32-bit Arm® Cortex®-M4F (ASIL-B compliant)

**Transceiver:**
- TJA1463 (CAN Signal Improvement Capabilities) with Sleep Mode

**Authentication:**
- SE050 EdgeLock Secure Element, supporting NFC interface

**Features/Interfaces:**
- Dual CAN FD PHYs with dual connector for daisy chain
- DCD-LZ debug interface with SWD+Console/UART
- Programmable user buttons
- UART with full handshaking and 5V/3V switchable voltage level
- I2C, SPI
- RC-PWM power output with internal or BEC/external power

**Power:**
- 5V – 12V
- Overcurrent protection

### DroneCAN
The MR-CANHUBK3 is not used as an autopilot. One way of using it is to build a PX4 distributed architecture. The same peripheral drivers running on an FMU can be reused here on the UCAN board, with only the CAN bus separating them. This means a common codebase is developed and used for something like a sensor or actuator. 

All this is thanks to DroneCAN used as a CAN protocol. For more information on DroneCAN go to this [link](https://dronecan.github.io/).

### Where to buy
Use the following links to order: [UCANS32K1SIC]( https://www.nxp.com/products/interfaces/can-transceivers/can-signal-improvement/can-sic-evaluation-board:UCANS32K1SIC)
## Board Setup
### Building Firmware
To build PX4 for this target:
```
make nxp_ucans32k1sic
```
### Debug Port
The [PX4 System Console]( https://docs.px4.io/main/en/debug/system_console.html) and the [SWD interface]( https://docs.px4.io/main/en/debug/swd_debug.html) run on the [DCD-LZ FMU Debug]( https://nxp.gitbook.io/hovergames/rddrone-fmuk66/connectors/debug-interface-dcd-lz) port.
NXP's DCD-LZ is a 7 pin JST-GH connector and adds the nRST/MCU_RESET pin to the [Pixhawk 6-Pin standard debug port]( https://github.com/pixhawk/Pixhawk-Standards/blob/master/DS-009%20Pixhawk%20Connector%20Standard.pdf).
The DCD-LZ breakout adapter permits the use of a standard 10 pin JTAG/SWD interface (i.e. using the Segger Jlink) and a standard 5 pin FTDI USB-TTL-3V3 type cable

### Further Info

Visit our [GitBook page](https://nxp.gitbook.io/ucans32k1/) for more detailed explanation on the UCANS32K1 board.
Check other boards developed by NXP that support the PX4 framework:

-	[RDDRONE-FMUK66](https://www.nxp.com/design/designs/px4-robotic-drone-vehicle-flight-management-unit-vmu-fmu-rddrone-fmuk66:RDDRONE-FMUK66): Flight management unit
-	[MR-CANHUBK3](https://www.nxp.com/design/development-boards/automotive-development-platforms/s32k-mcu-platforms/s32k344-evaluation-board-for-mobile-robotics-with-100baset1-and-six-can-fd:MR-CANHUBK344): Evaluation board used for redundant networking 
-	[8MPNAVQ](https://www.nxp.com/design/designs/navqplus-ai-ml-companion-computer-evk-for-mobile-robotics-ros-ground-stations-and-camera-heads:8MPNAVQ): Small companion computer for mobile robotics application
-	[RDDRONE-BMS772](https://www.nxp.com/design/designs/smart-battery-management-for-mobile-robotics:RDDRONE-BMS772): Battery management System for Mobile Robotics
