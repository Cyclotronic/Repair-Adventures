## Repair and firmware update for unit 1, Model THM565, S/N B090062, Firmware 0.54

<p style="text-align:center;"><a href="img/img_0840.jpg"><img alt="Front of the THM565 TekMeter with the display and keypad" src="img/img_0840_1.jpg" /></a></p>

### The instrument

I bought this Tektronix THM565 TekMeter for a few dollars at a Goodwill thrift store in Beaverton, Oregon, in April 2026. Beaverton is where Tektronix is headquartered, so the instrument turned up in its manufacturer's home town. It worked, and it came with its original probes and carry case.

<p style="text-align:center;"><a href="img/img_0845.jpg"><img alt="The original carry case with the probes and leads inside" src="img/img_0845_1.jpg" /></a></p>

The case held two original probes with snap-on clips, a three-prong outlet socket tester, an anti-static wrist strap, and a mounting knob for the back of the instrument. I have no details on what the knob mounts to.

The label on the back reads S/N BU00112 with the words NOT FOR SALE, THM565 std, and the date Nov. 09 1993.

<p style="text-align:center;"><a href="img/img_0842_label.jpg"><img alt="Back label: S/N BU00112, NOT FOR SALE, THM565 std, Date Nov. 09 1993" src="img/img_0842_label_1.jpg" /></a></p>

I think this is a pre-production unit. The NOT FOR SALE label, the 1993 date, the early firmware and the place I found it all point that way, but I have no confirmation from Tektronix. The serial number stored inside the instrument is B090062, which is different from the label, and I use the stored number in the title. I do not know why the two differ.

The inputs are four 4 mm jacks marked DMM, COM, CH 1 and CH 2, rated 600 V rms max CAT II.

<p style="text-align:center;"><a href="img/img_0841.jpg"><img alt="Input jacks on the top edge: DMM (red), COM (black), CH 1 (yellow), CH 2 (blue), marked 600V rms max CAT II" src="img/img_0841_1.jpg" /></a></p>

<p style="text-align:center;"><a href="img/img_0843.jpg"><img alt="Battery compartment with six AA cells installed for testing, five Energizer and one Duracell" src="img/img_0843_1.jpg" /></a></p>

There were no batteries in it when I bought it and no sign of battery leakage.

The instrument reported firmware 0.54 at power-on. That is older than either of the two firmware images I have (1.04 and 2.0), so I think this is an early unit.

### The four boards

The instrument has four boards: the main logic board, the display board, a small daughter board that makes the AC voltage for the electroluminescent panel, and the I/O board. The main logic board is part number 679-0065-00. It carries a Zilog Z8018008VSC (Z180) MPU, an Analog Devices ADG309B and the 156-6599-00 ASIC (MM9371A).

<p style="text-align:center;"><a href="img/img_0822.jpg"><img alt="The instrument opened flat: the I/O board with the four input jacks and relays on the left, the main logic board on the right" src="img/img_0822_1.jpg" /></a></p>

<p style="text-align:center;"><a href="img/img_0818.jpg"><img alt="Main logic board 679-0065-00 with the Z180 MPU, the ADG309B and the 156-6599-00 ASIC" src="img/img_0818_1.jpg" /></a></p>

<p style="text-align:center;"><a href="img/img_0828.jpg"><img alt="The daughter board carrying a TDK EBX-504B transformer, the AC supply for the electroluminescent panel" src="img/img_0828_1.jpg" /></a></p>

The daughter board connects to the display board through a thin three-wire flex, which can be seen beside the solder joints for the electroluminescent panel.

<p style="text-align:center;"><a href="img/img_0836.jpg"><img alt="Back of the display board with Optrex DMF682A markings and the LCD driver ICs. The two new Rubycon capacitors at C1 and C2 lie on their sides, one above the other" src="img/img_0836_1.jpg" /></a></p>

The back of the main logic board has a diode soldered on the solder side, with its leads laid flat across two sets of pads. It is a factory modification, not something I added.

<p style="text-align:center;"><a href="img/img_0825.jpg"><img alt="Back of the main logic board, with the factory diode near the lower right and the battery contact clip below it" src="img/img_0825_1.jpg" /></a></p>

<p style="text-align:center;"><a href="img/img_0825_diode.jpg"><img alt="The diode on the solder side of the main logic board, soldered across two pads with its leads flat on the board" src="img/img_0825_diode_1.jpg" /></a></p>

I did not investigate the diode and I do not know whether production units have it. If this is a pre-production unit, it is unlikely that they do.

### Leaking capacitors

Posts on the EEVblog forum say that the electrolytic capacitors in these units all go bad and leak. My first look during teardown showed nothing, and I thought this one had escaped or been repaired before. A closer look showed the usual signs: residue around the capacitors and corrosion on the nearby pads. At C907 the damage reaches well past the capacitor pads: the pins of U906, the vias and the pads of the chip resistors beside it are crusted.

<p style="text-align:center;"><a href="img/img_0116.jpg"><img alt="Original capacitors C907 (22 uF 16 V) and C908 (10 uF 35 V) near U906 on the I/O board, before the repair. Tan crust covers the U906 pins and the pads and vias around C907, with a green-tinged patch between U906 and C907" src="img/img_0116_1.jpg" /></a></p>

<p style="text-align:center;"><a href="img/img_0115.jpg"><img alt="Two of the original 150 uF 10 V capacitors in place on the main logic board. The pad in front of the left capacitor is dull, pitted and crusted" src="img/img_0115_1.jpg" /></a></p>

The main logic, display and I/O boards all carry electrolytic capacitors, and I replaced them on all three. If they have not leaked yet, they will. The 22 uF 16 V and 10 uF 35 V parts (C907 and C908) are on the I/O board, the one with the relays. The four 150 uF 10 V parts are on the main logic board, the one with the CPU. The display board has two 10 uF 25 V capacitors.

I identified the capacitors, removed them and cleaned the boards. Where the solder and pads had been attacked I removed the old solder with wick and resoldered the pads.

<p style="text-align:center;"><a href="img/img_0117.jpg"><img alt="I/O board after the capacitors were removed and the pads cleaned. The empty pads for C907 and C908 are below U906" src="img/img_0117_1.jpg" /></a></p>

<p style="text-align:center;"><a href="img/img_0118.jpg"><img alt="The whole I/O board with the relays and input jacks, C907 and C908 removed and the area cleaned" src="img/img_0118_1.jpg" /></a></p>

<p style="text-align:center;"><a href="img/img_0119.jpg"><img alt="Main logic board with the four 150 uF capacitors removed and the pads cleaned. Empty pads at C600, C603 and C616" src="img/img_0119_1.jpg" /></a></p>

<p style="text-align:center;"><a href="img/img_0122.jpg"><img alt="Four original capacitors removed from the board" src="img/img_0122_1.jpg" /></a></p>

The four large ones are marked Nichicon 150 uF 10 V. I measured the originals with calipers before ordering replacements and compared the readings with the Panasonic datasheet sizes.

| Photo | Reading | What was measured | Datasheet |
| --- | --- | --- | --- |
| [img_0124](img/img_0124.jpg) | 8.3 mm | Width across the base of a 150 uF capacitor | EEE-FC1A151P, 8.0 mm diameter, base 8.3 mm |
| [img_0125](img/img_0125.jpg) | 6.9 mm | Height of a 150 uF capacitor lying on its side | EEE-FC1A151P, 6.2 mm high |
| [img_0126](img/img_0126.jpg) | 5.3 mm | Width across the base of a small capacitor | EEE-FK1C220R and EEE-FK1V100R, 5.0 mm diameter, base 5.3 mm |
| [img_0127](img/img_0127.jpg) | 6.0 mm | Height of a small capacitor lying on its side | EEE-FK1C220R and EEE-FK1V100R, 5.8 mm high |

The base widths match the datasheet exactly, so the replacements have the same footprint as the originals. The heights are within about 0.7 mm of the datasheet. The 150 uF original reads 0.7 mm above the datasheet height of 6.2 mm, and I think that is the seating plate, or the Nichicon part being slightly taller than the Panasonic one. I did not check it against a fitted replacement.

The replacements for the main logic and I/O boards are Panasonic SMD electrolytics. I like Panasonic, but any quality capacitor with the right values, voltage and case size will do. The new capacitors at C907 and C908 on the I/O board are marked as FK series parts, and the pads and vias around U906 are clean. The new 150 uF capacitors on the main logic board are marked FC.

<p style="text-align:center;"><a href="img/img_0823.jpg"><img alt="New capacitors at C907 (22 uF 16 V) and C908 (10 uF 35 V) beside U906 on the I/O board, marked FK, with the surrounding pads cleaned" src="img/img_0823_1.jpg" /></a></p>

<p style="text-align:center;"><a href="img/img_0819.jpg"><img alt="New Panasonic 150 uF 10 V capacitors, marked 150 AFC, on the main logic board near the buzzer, with clean pads" src="img/img_0819_1.jpg" /></a></p>

The display board has two 10 uF 25 V capacitors, which I replaced with Rubycon 25MH510MEFC5X5 from DigiKey (part number 1189-2227-ND, 10 uF 20% 25 V radial). On the back of the display board they are fitted lying on their sides, one above the other.

<p style="text-align:center;"><a href="img/img_0835.jpg"><img alt="The two new Rubycon 10 uF 25 V capacitors at C1 and C2 lying on their sides among the OKI driver ICs" src="img/img_0835_1.jpg" /></a></p>

I have no photos of the original display-board capacitors.

I powered the instrument up on the bench, still disassembled. It started and worked normally.

### Capacitor list

The main logic and I/O boards use three Panasonic SMD aluminum electrolytics from DigiKey, ten of each ordered. The display board uses a Rubycon radial part.

| Board | Designators | Original | Replacement | DigiKey P/N |
| --- | --- | --- | --- | --- |
| I/O | C907 | 22 uF 16 V SMD | Panasonic EEE-FK1C220R, 22 uF 20% 16 V | PCE3785CT-ND |
| I/O | C908 | 10 uF 35 V SMD | Panasonic EEE-FK1V100R, 10 uF 20% 35 V | PCE3833CT-ND |
| Main logic | C600, C603, C616, C618 | Nichicon 150 uF 10 V SMD, four removed | Panasonic EEE-FC1A151P, 150 uF 20% 10 V | PCE3991CT-ND |
| Display | C1, C2 | 10 uF 25 V, type and size not recorded | Rubycon 25MH510MEFC5X5, 10 uF 20% 25 V radial, fitted lying on its side | 1189-2227-ND |

Sizes from the Panasonic datasheets are 8.0 mm diameter by 6.2 mm high with an 8.3 mm base for the EEE-FC1A151P, and 5.0 mm by 5.8 mm with a 5.3 mm base for the EEE-FK1C220R and EEE-FK1V100R. The caliper readings on the originals give the same base widths, so the footprints match. Photos of the fitted parts show FK-series capacitors marked 22 and 10 at C907 and C908 on the I/O board, and four capacitors marked 150 AFC on the main logic board.

### Backlight

The backlight is an electroluminescent panel and it looked dim. The community advice is not to remove the LCD, because doing so causes problems and the display cannot be brought back to fully working order. That leaves chemicals and time as the only way to remove the existing EL panel. I softened the adhesive with IPA and small amounts of acetone and lifted the old panel out slowly. Cleaning the residue off the panel area and the back of the display took patience.

<p style="text-align:center;"><a href="img/img_0826.jpg"><img alt="Back of the display assembly with the white shielding film over the panel and the connecting flex on the left. The metal rings on the posts show that the film is shielding" src="img/img_0826_1.jpg" /></a></p>

<p style="text-align:center;"><a href="img/img_0827.jpg"><img alt="Display board with the shielding film folded back, showing the LCD driver ICs and the OPTREX JAPAN marking. The long ribbon cable connects to the daughter board that powers the EL panel" src="img/img_0827_1.jpg" /></a></p>

<p style="text-align:center;"><a href="img/img_0831.jpg"><img alt="Front side of the display board with the LCD attached" src="img/img_0831_1.jpg" /></a></p>

<p style="text-align:center;"><a href="img/img_0830.jpg"><img alt="Inside of the front of the instrument, showing the display window and the keypad membrane in some areas" src="img/img_0830_1.jpg" /></a></p>

The white film over the display board is shielding, and the I/O board has similar shielding around it. I have no photos of the old panel or of the adhesive residue.

I measured the new panel against a ruler and calipers before fitting.

<p style="text-align:center;"><a href="img/img_0833.jpg"><img alt="The new panel with calipers and a ruler. The caliper shows the height of the panel, 30 mm, and the ruler shows the width, 140 mm" src="img/img_0833_1.jpg" /></a></p>

The panel is 140 mm wide and 30 mm high. I bought it through AliExpress.

The new panel fitted well and I soldered it in.

It did not make a large difference. It is good enough for low light, and this LCD reads well in bright light anyway.

<p style="text-align:center;"><a href="img/img_0817.jpg"><img alt="The instrument in dim light with the new backlight on, in V-AC mode showing 0.015 V, connected by ribbon cable to the fixture" src="img/img_0817_1.jpg" /></a></p>

### Battery contacts

The battery terminals connect to the main board through push-on pin connectors. They are not very secure. I had to spring the receptacles open a little to get a snug fit. Someone repeating this repair might consider replacing them with a different connector.

<p style="text-align:center;"><a href="img/img_0837.jpg"><img alt="A white lead with a crimped pin terminal from the battery contacts, beside the main board" src="img/img_0837_1.jpg" /></a></p>

<p style="text-align:center;"><a href="img/img_0838.jpg"><img alt="A battery lead with its pin terminal beside the W601 pad, next to the TEK M1 marking" src="img/img_0838_1.jpg" /></a></p>

<p style="text-align:center;"><a href="img/img_0839.jpg"><img alt="The W600 connection beside F600 with a battery lead attached" src="img/img_0839_1.jpg" /></a></p>

### Firmware fixture

Firmware 0.54 is old. Updating it needs the 067-1446-99 fixture. TERRA Operative on EEVblog posted the gerbers and plans for it:
<https://www.eevblog.com/forum/testgear/tektronix-thm56x-portable-scope-hackteardowndiscussion/msg6265840/#msg6265840>

Tektronix sold a serial and power adapter for these instruments, the THMCOM1 Communications Adapter (RS-232). Units turn up on the secondary market. Do not buy one expecting to program the instrument with it. The fixture switches the flash programming voltage (VPP) on, which is what lets the memory be erased and written, and the THMCOM1 does not. The fixture also powers the instrument.

<p style="text-align:center;"><a href="img/thmcom1.jpg"><img alt="Rendering of the Tektronix THMCOM1 Communications Adapter, showing its label, the DC power jack and the DB9 RS-232 connector" src="img/thmcom1_1.jpg" /></a></p>

The THMCOM1 is described with the other accessories on the [Tektronix THM565 datasheet page](https://www.tek.com/en/datasheet/thm565-tekmeter). It is a DC power jack and a DB9 RS-232 port in a housing, with a mounting plate that appears to replace the battery door, which I have not confirmed. The label in the rendering reads THM400 SERIES. The THM5AC power adapter listed with it is a separate accessory.

I had the boards made at a PCB house and built two fixtures. If you need one, contact me at the email address on the repository. The parts came from DigiKey. It is all through-hole and easy to build. The design of the programming adapter is sound and it worked when first powered. After that the project sat on the shelf for a while.

<p style="text-align:center;"><a href="img/img_0813.jpg"><img alt="Assembled 067-1446-99 fixture board, RS232-to-PC version, designed by TERRA Operative" src="img/img_0813_1.jpg" /></a></p>

<p style="text-align:center;"><a href="img/img_0814.jpg"><img alt="Two fixture boards on the bench, one connected to the instrument by ribbon cable and USB serial adapter" src="img/img_0814_1.jpg" /></a></p>

The second board in the photo is the other fixture I built.

<p style="text-align:center;"><a href="img/img_0816.jpg"><img alt="Back of the programming adapter board, with the solder side and the DB9 connector visible" src="img/img_0816_1.jpg" /></a></p>

<p style="text-align:center;"><a href="img/img_0811.jpg"><img alt="The THM565 running in scope mode, powered from the programming adapter through the ribbon cable, with the USB serial adapter on the right" src="img/img_0811_1.jpg" /></a></p>

### Capturing the vendor loader

Tektronix's loader, QLOADER.EXE, is a DOS program. I built a bridge that runs it in DOSBox and forwards its serial traffic to the real instrument, logging both directions. Running QLOADER through it against the instrument, with VPP on, took the unit from 0.54 to 2.0. The transfer was 359,308 bytes and took about 12 minutes.

Two mistakes from those runs. With VPP off, `$RELOAD CODE` gets no reply and the loader waits forever, and I had to pull power. And I left VPP off for the config burn that follows the reload, which failed. The instrument then identified itself as `THM??? SW VERSION 2.00`. I repeated the config and calibration steps with VPP on and it came back as `THM565 SW VERSION 2.00`. The calibration constants matched the backup I took before flashing.

### Tools and command table

From the captures, the loader and the firmware I wrote two Python tools, one for firmware flashing and one for calibration, and a table of the serial commands. The tools are in [THM565-Flash](https://github.com/Cyclotronic/THM565-Flash) and the command table follows.

### Serial command table

The 60 commands the V2_0 firmware accepts on its serial port, taken from the command list in the ROM image. What each one does was worked out from the firmware and, for the calibration, config and reload commands, checked against captures from the instrument and against emulation. Commands marked "not traced" are listed from the name only. I have not run them on the instrument.

#### Port and framing

- 1200 baud, 8N1 after power-on and after `INIT`. `BAUD 3` switches the instrument to 9600 8N1.
- Commands end with CR. Anything after the CR waits in an 80-byte receive buffer, and bytes that overflow it are dropped.
- Commands are handled one at a time. The next one is not read until the previous handler finishes.
- A line that starts with `*` is ignored, with no reply.
- A line that matches nothing gets `COMMAND NOT DEFINED 0`.
- Lines longer than 128 characters are discarded.

#### Command patterns

In the table, upper-case letters must be typed and lower-case letters are optional. Input case does not matter. `#` is a number and `@` is a channel digit. `?` is literal. I have only sent full-length commands, so treat the abbreviations as read from the firmware, not tested.

#### Replies

Most replies end with a space, a status digit and CR: ` 0` is success and ` 1` is failure. Exceptions are noted in the table.

#### Identity, power and system

| Command | What it does | Reply |
| --- | --- | --- |
| `ID?` | Model and firmware version. Model is `THM` plus 550, 560 or 565 from the stored config type. If no config type is stored it prints `???`. Also printed at power-on. | `THM565 SW VERSION 2.00 0` |
| `INIT` | Restarts the instrument and returns the port to 1200 baud. | None, then the power-on banner (about 5.7 s) |
| `BAUD #` | 0 selects 1200, 3 selects 9600. Other values are rejected. The instrument replies first, then changes speed after about 200 ms. | ` 0`, or ` 1` for other values |
| `POWER OFF` | Turns the instrument off. | ` 0` |
| `POWEROff TimeOut #` | 0 disables the auto-off timer, 1 sets 300000 (units not confirmed). | ` 0` |
| `LOW BATtery?` | Battery state. | ` 1` low, ` 0` not low |
| `$STB?` | Fixed status string. | `110 0` |
| `BACK LIGHT ON #` | Backlight control. Not traced. | ` 0` |
| `KEY BOARD LOCK #` | 0 unlocks the keys, non-zero locks them. | ` 0` |
| `$KEY INPUT # #` | Injects a key event. Not traced beyond the arguments. QLOADER only uses it for the THM571. | ` 0` |
| `PRINT?` | Print routine. Not traced. | Values then ` 0` |

#### Clock and date

| Command | What it does |
| --- | --- |
| `CLocK ReaD?` | Reads the clock. |
| `CLocK WRite # # #` | Sets the clock. |
| `CLocK ALARM RUN # #` | Alarm setting. Not traced. |
| `DaTe ReaD?` | Reads the date. |
| `DaTe WRite # # #` | Sets the date. |

Clock and date replies are the values followed by ` 0`. Field order was not checked.

#### Calibration, config and firmware

These are the commands the flash and calibration tools use. The `$` commands are not documented by the manufacturer.

| Command | What it does | Reply |
| --- | --- | --- |
| `$DUMP CAL #?` | 0 returns the DMM calibration record, 1 the scope record, both as hex text. 2 returns the config type (2 hex digits) and the 36-character identity string. | Data, then ` 0` |
| `$LOAD CAL #` | Followed by the record as hex text. 0 is DMM (103 bytes), 1 is scope (195 bytes). Writes to RAM only. The checksum is not checked by the instrument. | Bare CR |
| `$BURN CAL` | Commits both RAM records to the next free flash slot. Needs VPP. Each record has 10 slots and they are never rewritten in place. | ` 0`, or ` 1` on failure |
| `$BURN CONFIG` | Followed by 2 hex digits (type) and 36 characters (identity). Programs the single config slot, only if it is still blank. Needs VPP. | ` 0` or ` 1` |
| `$RELOAD CODE` | Hands the port to the firmware loader, which takes Motorola S-records. The display shows `CLS`. On the current firmware it does not erase or program anything (see Firmware 2.0 does not flash, below). | The loader's own bytes |
| `$TEST #?` | 0 and 1 return the number of free calibration slots. 2 runs the display test then resets. 4 runs the RAM test. 5 repeats 2 and 4 until an error. 3 and 100 to 112 were not traced. | Number then CR |

The calibration records are hex text, 206 characters for DMM. Send `$LOAD CAL` in two writes with a pause after the command (2 s), not one. The same applies to `$BURN CONFIG` (1 s). Both are handled in [THM565-Flash](https://github.com/Cyclotronic/THM565-Flash).

#### Screens, settings and waveforms

Not traced beyond their names. Each takes a screen, setting or waveform block number and replies ` 0`.

| Command | Likely purpose |
| --- | --- |
| `UPLOAD #?` | Send stored data to the host. |
| `DOWNLOAD #` | Receive stored data from the host. |
| `LOAD SCReen #`, `LOAD SETting #`, `LOAD WFM #` | Load a stored item onto the instrument. |
| `GET SCReen #`, `GET SETting #`, `GET WFM #` | Read a stored item. |

#### Multimeter

Function taken from the command names. None traced in detail. Several reject bad arguments with ` 1`.

| Command | Likely purpose |
| --- | --- |
| `Dmm Mode #` | Select the meter function. |
| `Dmm MEasurement?` | Read the current measurement. |
| `$DMM ON #` | Meter on or off. |
| `$DMM DEBUG?` | Debug readout. |
| `$DMM CALIBRATE` | Calibration step. Reply is a bare CR. |

#### Oscilloscope

Function taken from the command names. `@` is the channel, 1 or 2.

| Command | Likely purpose |
| --- | --- |
| `Scope CHannel@ Coupling #` | Input coupling. |
| `Scope CHannel@ Volts/Div #` and `?` | Vertical scale, set and read. |
| `Scope Seconds/Div #` and `?` | Timebase, set and read. |
| `TPOS #` and `TPOS?` | Trigger position, set and read. |
| `Scope TRiGger@ Source #`, `Level #`, `Slope #` | Trigger source, level and slope. |
| `Scope TRiGger Mode #` | Trigger mode. |
| `Scope WaveForMs@ Displayed #` | Which waveforms are displayed. |
| `Scope WaveForM@ Source #`, `Position #`, `Position?`, `Envelope #`, `Scope WaveForM@?` | Waveform source, position, envelope and readout. |
| `Scope Turbo #` | Turbo acquisition mode. |
| `SOPmode #` and `SOPmode?` | Operating mode, set and read. |
| `SACQ #` and `SACQ?` | Scope acquisition setting, set and read. |
| `$Scope WaveForM TEST #?` | Waveform test. |
| `$SCOPE CHannel@ CALIBRATE OFFSET` | Channel offset calibration. Bare CR reply. |
| `$SCOPE CHannel@ CALIBRATE GAIN` | Channel gain calibration. Bare CR reply. |

### Firmware 2.0 does not flash

To test the flashing tool without risking the instrument I built a Z180 emulator and ran QLOADER and my tool against emulated 2.0 and 1.04 firmware. With 1.04 in the emulator, the code erases and reprograms the flash, and the traffic matches what I captured going from 0.54 to 2.0.

With 2.0 running, the reload command accepts the transfer and reports success but issues no erase or program commands. The emulated flash is identical whether or not the code is sent. QLOADER cannot tell the difference.

This means 2.0 cannot be reflashed over serial, and there is no way back to an older version this way. Any new firmware would have to be programmed with the flash chip removed or with a direct programming method. It does not matter to me. I do not plan to write firmware for it, and I doubt Tektronix will. This result comes from emulation. I have not tried it on the instrument.

### Summary

| Fault | Cause | Fix |
| --- | --- | --- |
| Corroded pads around the electrolytic capacitors | Leaking electrolytic capacitors | Removed the capacitors, cleaned the board, resoldered affected pads, fitted new SMD electrolytics |
| Dim electroluminescent backlight | Age | Replaced the panel. Improvement was small |
| Firmware 0.54 | Early unit | Flashed 2.0 through the 067-1446-99 fixture |

The instrument works normally on firmware 2.0.
