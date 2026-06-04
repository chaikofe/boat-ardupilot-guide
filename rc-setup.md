# RC Setup (FrSky)

Configuring the Taranis X9D+, R9M module, and R9 SX receiver.

## Install the R9M module

- Slide the R9M into the radio's module bay
- **Attach the antenna before powering on** — running without an antenna damages the module

## Register and bind the receiver

The R9 SX uses the ACCESS protocol — registration first, then bind.

### Registration

1. On radio: MODEL SETUP → External RF → Mode = **R9M ACCESS**, Region = **EU** (for LBT)
2. Scroll to **[Reg]**
3. Power the R9 SX **while holding its F/S button!!!** — RED + GREEN LEDs both solid
4. Press ENT on [Reg]
5. Receiver LEDs flash, radio says "Registration OK"
6. Power off the receiver

### Bind

1. Radio: scroll to **Receiver 1 → [Bind]**
2. Power receiver normally (no button held) — GREEN LED solid
3. Select the RX from the list — the radio says "Bind successful."
4. **Exit [Bind] on the radio** (this step is critical)
5. Power-cycle the receiver
6. Green LED should now be **flashing** (not solid) = working

## Radio MIXER

MODEL SETUP → MIXER page. Set each channel:
