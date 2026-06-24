# Field Operations Guide

Everything you need to know for a successful session at the water.

## Before leaving home

- [ ] Charge all batteries fully
- [ ] Pre-cache the map in Mission Planner (right-click map → Prefetch, zoom 15-19)
- [ ] Confirm parameter file is saved as backup
- [ ] Charge laptop
- [ ] Pack tether line (long, light — fishing line works)

## Equipment checklist

- [ ] Boat (fully assembled, waterproofed)
- [ ] Batteries (charged, secured in boat)
- [ ] RC transmitter (charged)
- [ ] Windows laptop + Mission Planner
- [ ] RFD900x ground unit + USB cable
- [ ] Multimeter
- [ ] Spare props
- [ ] Tether line
- [ ] Tools (hex keys, screwdriver)

## At the water — power up sequence

Power up in this order every time:

1. Place the boat in water (or on the ground near water)
2. Connect battery — boat powers up
3. Wait for ESC startup beeps (3 rising tones from each ESC)
4. Turn on the RC transmitter
5. Confirm the receiver's green LED is flashing (linked)
6. Connect RFD900x to laptop
7. Open Mission Planner → connect
8. Wait for GPS 3D Fix (10+ satellites, HDOP < 1.5)
9. Confirm HUD heading matches reality (point bow north → HUD shows ~0°)
10. Confirm battery voltage shows correctly in HUD

**Do not arm until all 10 steps are confirmed**

## GPS fix — what to expect

- First fix of the day: 1-5 minutes (cold start)
- Subsequent fixes: 30-60 seconds (warm start)
- Stand away from the antenna while waiting — your body blocks the GPS signal
- Move away from cars, buildings, and metal structures

## Arming

1. Mode switch → **Manual**
2. SD switch → **Arm position**
3. HUD confirms **Armed**
4. If arm fails → read PreArm message in HUD, fix the issue

Common PreArm failures:
- "GPS" → wait for a better fix
- "Compass" → redo compass calibration
- "Battery" → charge battery

## First session — Manual mode only

For the very first water session:

1. Attach tether line to boat
2. Arm in Manual
3. Very gentle throttle — confirm boat goes forward
4. Gentle steering — confirm boat turns correctly
5. Test reverse
6. Test failsafe — turn off radio, boat should stop within 1.5 seconds
7. Turn radio back on — control returns
8. Disarm

Do not proceed to Hold or Auto until Manual is confirmed working.

## Hold mode test

1. Get GPS fix (10+ sats)
2. Drive the boat to open water
3. Switch to **Hold**
4. Release sticks
5. The boat should maintain its position
6. Push the boat by hand (or with a stick) — it should resist and return
7. Switch back to Manual — control returns

## Auto mode — first mission

Plan a simple mission before going to the water:

1. Mission Planner → PLAN tab
2. Drop 3-4 waypoints in a small square (20-30m sides)
3. Set speed to **1 m/s** (slow for first test)
4. Save mission → Write WPs to the vehicle
5. At the water:
   - Arm in Manual
   - Drive to the start area
   - Switch to **Auto**
   - Watch the boat run the mission
   - Keep your hand on the mode switch — back to Manual if anything goes wrong

## Power down sequence

Always power down in this order:

1. Disarm (SD switch)
2. Confirm HUD shows **Disarmed**
3. Disconnect Mission Planner
4. Turn off RC transmitter
5. Disconnect battery from boat
6. Remove boat from water

**Never disconnect battery while armed.** Always disarm first.

## After each session

- [ ] Download logs (Mission Planner → DATA → DataFlash Logs)
- [ ] Check battery voltage — recharge if below storage voltage
- [ ] Rinse boat with fresh water (salt water especially)
- [ ] Check props for damage or debris
- [ ] Check all connectors for corrosion
- [ ] Note any issues for next session

## Map without internet

Mission Planner and QGC work without an internet connection. Pre-cache your area at home:

**Mission Planner:** right-click map → Map Tool → Prefetch → zoom levels 15-19

Without cached maps, the background is grey, but GPS position, waypoints, and all telemetry still work normally.
