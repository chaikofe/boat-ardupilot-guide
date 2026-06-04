# Calibrations

All calibrations are under SETUP → Mandatory Hardware in Mission Planner.

## Radio Calibration

1. Click **Calibrate Radio**
2. Move every stick to all four extremes
3. Flip every switch through all positions
4. Click **Click When Done**

Verify: all channels reach ~1100 min and ~1900 max.

## Accelerometer Calibration

Boat on a flat surface.

1. Click **Calibrate Accel**
2. Position the boat in each orientation when prompted:
   - Level
   - Left side
   - Right side
   - Nose down
   - Nose up
   - On its back
3. Hold still each time, click Next

Then click **Calibrate Level** with the boat flat.

## Compass Calibration (OUTDOORS)

!!! Must be done outdoors, away from cars, metal, and buildings. Boat in final configuration.

1. Click **Start** under Onboard Mag Calibration
2. Slowly rotate the boat through **all** orientations
3. Watch the progress bars fill (X, Y, Z)
4. Wait for "Calibration successful."

If you see "Compass interference too high," move the Here2 farther from ESCs and repeat.

## Verify heading

1. Point the boat's bow at true north (use phone compass)
2. HUD should show ~0° heading
3. Rotate boat clockwise — heading increases smoothly toward 90°, 180°, 270°

If the heading is wrong, redo the compass calibration.

## GPS verification

Outdoors, wait for:
- 3D Fix
- 10+ satellites
- HDOP under 1.5
