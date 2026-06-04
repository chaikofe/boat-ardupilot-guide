# Troubleshooting

Common problems and fixes.

## ESC beeps continuously

**Cause:** No valid signal on RC IN, or servo rail not powered, or `MOT_PWM_TYPE` is wrong.

**Fix:**
- Verify 5V BEC is powering the servo rail (multimeter on MAIN OUT middle pin)
- Check `MOT_PWM_TYPE = 0` in parameters
- Confirm ESC signal connector orientation

## Only one motor responds

**Cause:** SERVO function not set, or skid-steer mixing not engaged.

**Fix:**
- Verify `FRAME_TYPE = 2` (Boat)
- Verify `SERVO1_FUNCTION = 73` AND `SERVO3_FUNCTION = 74`
- In Motor Test, try **Test motor C** (drives MAIN OUT 3), not Motor B (empty)

## Receiver bound but no signal to Cube

**Cause:** Wrong pad used or receiver still in bind mode.

**Fix:**
- Use the 6-pin connector's SBUS_OUT (not CH5/CH6 pads)
- Confirm receiver green LED is **flashing** (linked) not **solid** (still in bind)
- Re-do registration + bind, ensure you exit [Bind] mode on the radio

## Can't arm — "PreArm:" message

**Cause:** A safety check is failing.

**Fix:** Read the specific message in the HUD or Messages tab. Common ones:
- "GPS" → no fix, go outdoors or wait
- "Compass" → redo compass calibration outdoors
- "Safety switch" → press the Here2's safety button until the LED is solid

For bench testing only, set `ARMING_CHECK = 0`. **Set back to 1 before water.**

## Mode switch doesn't change mode

**Cause:** All flight mode slots are set to the same mode, or CH6 is not routed.

**Fix:**
- Setup → Flight Modes → confirm slots are set to **different** modes (Manual, Hold, Auto)
- Verify `MODE_CH = 6`
- Confirm CH6 is mapped to a switch in the radio MIXER

## Manual works, Auto circles

**Cause:** Heading error or navigation tuning too aggressive.

**Fix:**
- Verify compass: point bow north, HUD shows ~0°. If wrong, redo compass cal outdoors.
- If the compass is fine: increase `WP_RADIUS` to 5, increase `NAVL1_PERIOD` to 15 (if the parameter exists)
- Check that the mission has valid waypoints in the PLAN tab

## Boat reverses one motor during a turn at speed

**Cause:** Standard skid-steer math — at high throttle + high steering, one motor reverses to create the differential.

**Fix:**
- Apply Func|x| curve in radio MIXER for car-like behavior (see [RC Setup](rc-setup.md))
- Or reduce steering Weight (CH01) to 50-60 in the mixer
- Or lower `ACRO_TURN_RATE` to 60-90

## ESC beeps differently between the two

**Cause:** Different firmware versions or calibrated ranges.

**Fix:** Run ESC calibration manually:
1. Props off
2. Arm in Manual
3. Throttle full forward → connect ESC battery → ESC registers max
4. Throttle full back → ESC registers min  
5. Throttle center → ESC registers neutral
6. Disarm

Both ESCs are now calibrated to the same range.
