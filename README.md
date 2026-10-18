# QwiicBus_MPU
Hardware Modifications from the Original SparkFun QwiicBus Endpoint

Integrated Onboard MPU-6050-A IMU Sensor: Added the MPU-6050-A accelerometer/gyroscope and its supporting passive components (0.1uF and 2.2nF decoupling capacitors, 4.7k pull-up resistors, and JUMPER-SMT_3_2-NC_TRACE_SILK I2C pull-up jumper) directly onto the PCB alongside the PCA9615 differential transceiver. What it does: Turns the board into a single, self-contained differential I2C sensor node, eliminating the need for an external Qwiic cable and separate sensor breakout board.

Phoenix Contact 1770940 Terminal Block Integration: Replaced the original board's off-board connectors and top/bottom through-hole breakout headers with an 8-position, 16-pin footprint (1_1/1_2 through 8_1/8_2) for the Phoenix Contact 1770940 spring-cage connector. What it does: Provides direct, secure multi-wire cable termination while bridging each pair of through-hole pins (1_1 to 1_2, etc.) for added mechanical pad strength and current capacity.

Parallel Differential Pair Pinout (DSDA_N / DSDA_P Alignment): Assigned DSDA_N to terminal position 8 (8_1/8_2) and DSDA_P to position 7 (7_1/7_2), with DSCL_P on position 2 (2_1/2_2) and DSCL_N on position 1 (1_1/1_2). What it does: Aligns the connector pinout directly with the output pins of the PCA9615 and the 100 ohm termination resistors so all differential traces route straight across the top layer (ct Top) in parallel without crossing over each other or needing layer-jumping vias.

Isolated Split-Power Routing (VCC & VCC_1): Routed dedicated copper power traces for the local 3.3V sensor side (VCC) and the bus cable side (VCC_1), bridged through normally-closed SMT solder jumpers (VCC1, GND, and JUMPER-SMT_2_NC_TRACE_SILK). What it does: Allows the endpoint to be powered directly over the differential bus cable by default, while retaining the option to cut the jumper traces to isolate local sensor power or ground loops.

Removed Redundant Headers & Added Dual-Layer GND Pours: Stripped out unused 0.1" breakout header pins (GRN_P, GRN_N, extra VCC_1/GND holes, and the 5-pin I2C header) and original manufacturer silkscreen logos, filling both the top (ct Top) and bottom (cb Bottom) layers with solid GND polygon pours. What it does: Frees up routing space, simplifies all surface-mount ground returns, and surrounds the high-speed differential I2C lines and IMU sensor with grounded copper shielding to reduce electromagnetic interference (EMI). 

These modifications were made to the SparkFun_QwiicBus_Endpoint(https://github.com/sparkfun/QwiicBus_EndPoint/tree/main.)
