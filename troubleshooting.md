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
- Verify `FRAME_CLASS = 2` (Boat)
- Verify `SERVO1_FUNCTION = 74` AND `SERVO3_FUNCTION = 73`
- In Motor Test, try **Test motor C/A or All** (drives MAIN OUT 3), not Motor B (empty)

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
- Go Basic Tuning in Config Tuning, ATC_STR_RAT_FF to
  
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

## Different PC or Param File — Does It Actually Matter?

**Connecting a different laptop or Mission Planner install never changes your vehicle's behavior by itself.** Mission Planner only *reads* whatever parameters are currently stored on the Cube's flash — it doesn't push, sync, or overwrite anything just by connecting, no matter what that laptop's Mission Planner has done before or on other projects. Nothing is written unless you explicitly click **Write Params**, use **Load from File → Write Params**, or manually edit a value and press Enter.

So if behavior changes between sessions where different PCs or param files were involved, it's because one of these deliberate actions happened — not because of the PC itself. The most common cause is a **stale `.param` file getting loaded and written**, easy to do mid-troubleshooting without realizing it, especially if a laptop has old backups sitting in its Downloads folder from an earlier, less-complete stage of the build. Other causes: radio or compass calibration was rerun and overwrote the working values, or a parameter got manually edited and left in place.

Before trusting any `.param` file, check a few sanity values — or in a bad case, compare all the key parameters between the suspect file and your last known-good backup: `COMPASS_DEV_ID` / `COMPASS_DEV_ID2` should be real numbers, not `0` (0 means the compass was never actually bound to the hardware); `GPS1_CAN_NODEID` should be a real node ID, not `0`; and `RC*_TRIM` values should look like sane centers (~1500), not extreme values near a channel's min or max. A quick spot-check of these three catches most bad files, but if something still feels wrong after loading, do a full diff of every parameter against your working backup — that's the only way to catch a subtler issue hiding outside the usual suspects.

**Practical rule:** keep one authoritative `.param` file (version-controlled, e.g. in this repo) and only ever load from that, regardless of which laptop you're using. After every successful session, re-export the current parameters and update that one backup. If something breaks after switching machines, export params before and after and diff the two files — that tells you definitively whether the Cube's stored parameters actually changed, or whether the cause was physical (a loose connector) or environmental (compass interference at the new location) instead.
