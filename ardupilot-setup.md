# ArduPilot Setup

Software configuration in Mission Planner.

## Install Mission Planner

Download from **https://ardupilot.org/planner/** and install on a Windows PC.

## Connect Cube

1. USB cable from Cube to laptop
2. Mission Planner → top right → select Cube's COM port, baud **115200**
3. Click **Connect**
4. HUD becomes live

## Flash ArduRover firmware

1. Disconnect Mission Planner
2. SETUP → **Install Firmware**
3. Click **ArduRover** icon
4. When prompted, unplug and replug the USB
5. Wait for completion
6. Reconnect — title bar shows **"ArduRover Vx.x.x"**

## Load parameter file

1. Download [boat_params.param](boat_params.param)
2. CONFIG → **Full Parameter List**
3. Click **Load from File** (right panel)
4. Select the file → review changes → OK
5. Click **Write Params**
6. **Reboot Cube** (Ctrl+F → Reboot Pixhawk)

## Verify critical parameters

After loading, confirm these in the parameter list:

| Parameter | Value |
|---|---|
| FRAME_TYPE | 2 |
| MOT_PWM_TYPE | 0 |
| SERVO1_FUNCTION | 73 |
| SERVO3_FUNCTION | 74 |
| RCMAP_ROLL | 1 |
| RCMAP_THROTTLE | 3 |
| MODE_CH | 6 |
| RC5_OPTION | 41 |

!!! **MOT_PWM_TYPE must be 0**, not 6. If it's 6, the Cube sends brushed-motor signals, and your ESCs won't work.

## Next steps

Go to [Calibrations](calibrations.md).
