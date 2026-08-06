# Audician 32 Plus Replica

This is a reverse-engineered sound card based on [Labway A151-A00](https://theretroweb.com/expansioncards/s/labway-corporation-labsound-a00-ide-power-a), which is a Yamaha OPL3-SAx based sound card. The OPL3-SAx is a single solution sound chip which provides Sound Blaster Pro 2.0 and Windows Sound System compatibility, and more importantly, a genuine OPL3 FM synthesizer. It's almost perfect (except ADPCM support) for PC-based retro gaming. Besides outstanding compatibility, this card is also noise-free and has acceptable frequency response.

As of August 2026, no one has published any schematic for this chip yet. This project aims to provide a reverse-engineered schematic and nearly 1:1 clone of the A151-A00 sound card with some modifications:

* Wavetable reverse channel bug is fixed
* Original FCC ID and CE logo are not used
* Silkscreen font is different
* Footprints are replaced with KiCad defaults plus some self-made ones
* Silkscreens for chip model are corrected
* Board is slightly longer and the ISA connector is moved slightly to comply with ISA standard

One configuration of the board is manufactured and validated to work perfectly fine.

![PCB Rendering](<Audician 32 Plus Replica.png>)

# Project Structure

* `bom/`: Interactive BOM
* `eeprom/`: EEPROM dump
* `gerber/`: Gerber files for the PCB
* `jlcpcb/`: JLCPCB production files
* `references/`: Reference documents, including datasheets for chips, ISA standard specification and photos of the original PCB
* Others: KiCad project files

# BOM

| References                                                   | Value                 | LCSC Part Number |
| ------------------------------------------------------------ | --------------------- | ---------------- |
| C4, C7                                                       | 150pF 0805            | C1716            |
| C5, C10                                                      | 220nF 0805            | C5378            |
| C11<sup>[1]</sup>, C12<sup>[1]</sup>, C19<sup>[1]</sup>, C20<sup>[1]</sup>, C44, C45 | 1nF 0805              | C46653           |
| C13, C21, C48, C49, C50, C51                                 | 10nF 0805             | C1710            |
| C14, C33, C37, CB5, CB9, CB15, CB16, CB17                    | 100nF 0805            | C49678           |
| C22, C23, C24, C25, C28, C42, C43, C46                       | 1uF 0805              | C28323           |
| C26, C27                                                     | 470pF 0805            | C1743            |
| C29, CA1                                                     | 100pF 0805            | C1790            |
| C38<sup>[2]</sup>, C39<sup>[2]</sup>                         | 4.7pF 0805            | C1820            |
| C40, C41                                                     | 22pF 0805             | C1804            |
| C47, C52, C54, C55, C58, C59                                 | 47pF 0805             | C14857           |
| CT1, CT2, CT4, CT7, CT8                                      | 100uF D6.3xL7         | C106447          |
| CT3, CT10                                                    | 470uF D8xL11          | C106735          |
| CT5, CT11                                                    | 22uF D5xL7            | C112508          |
| CT6, CT9, CT12, CT13, CT15, CT16                             | 10uF D4xL7            | C5123345         |
| CT14                                                         | 100uF D6.3xL7         | C2826426         |
| R7, R18                                                      | 510Ω 0805             | C17734           |
| R8, R9                                                       | 47kΩ 0805             | C17713           |
| R10, R11, R12, R13                                           | 20kΩ 0805             | C4328            |
| R14, R21, R35                                                | 220kΩ 0805            | C17556           |
| R15, R22, R36                                                | 33kΩ 0805             | C17633           |
| R16, R17, R19, R20                                           | 27kΩ 0805             | C17593           |
| R24, R25                                                     | 7.5kΩ 0805            | C17807           |
| R29<sup>[2]</sup>                                            | 3.9kΩ 0805            | C17614           |
| R30, R32                                                     | 75Ω 0805              | C20638           |
| R31                                                          | 0Ω 0805               | C17477           |
| R33                                                          | 1MΩ 0805              | C17514           |
| R37, R38, R39, R40                                           | 2.2kΩ 0805            | C17520           |
| RA1                                                          | 150Ω                  | C17471           |
| RP1<sup>[3]</sup>                                            | 0Ω 0603x4             | C52175182        |
| RP2                                                          | 2.2kΩ 0603x4          | C52175185        |
| SJ3<sup>[4]</sup>, SJ4<sup>[4]</sup>                         | 0Ω 0805               | C17477           |
| SJ5<sup>[3]</sup>                                            | 0Ω 0805<br>10kΩ 0805  | C17477<br>C17414 |
| D1, D2                                                       | 1N4001 DO-41          | C2456            |
| L2                                                           | Axial D3.5xL4.7       | C192456          |
| Q1                                                           | 78L05 TO-92           | C8608            |
| Q2                                                           | MMBT3904 SOT-23       | C364310          |
| U5                                                           | TEA2025B DIP-16       | C434515          |
| U6<sup>[5]</sup>                                             | OPL3-SAx LQFP-100     |                  |
| U9<sup>[3]</sup>                                             | 93C66 DIP-8           | C434597          |
| U10<sup>[3]</sup>                                            | 74LS138D              | C7736            |
| X2<sup>[2]</sup>                                             | 33.8688MHz HC-49U     |                  |
| X3                                                           | 24.576MHz HC-49U      |                  |
| CN1<sup>[3]</sup>                                            | 2x20pin Dupont 2.54mm | C5224014         |
| CN2                                                          | 2x13pin Dupont 2.54mm | C41430886        |
| J2, J3, J4                                                   | PJ-317                | C381121          |
| J5                                                           | DB-15 Female          | C77835           |
| J10                                                          | 1x4pin Dupont 2.54mm  | C2691448         |
| J11, J13                                                     | 1x4pin JST PH2.0      | C722763          |
| JP1                                                          | 2x3pin Dupont 2.54mm  | C492420          |

Notes:

1. [Low-Pass Filter Mod](https://www.vogons.org/viewtopic.php?p=527947#p527947): This is a mod for this card to make Sound Blaster effects sound more like a real Sound Blaster Pro 2.0. If you want to perform this mod, replace the two SBFLT caps with 6.8nF (LCSC part number C1755). For YMF711/718, the SBFLT caps are C12 and C20. For YMF715/719/741, the SBFLT caps are C11 and C19.
1. C38, C39, R29, X2: If using a 3rd overtone crystal, which most probably is for 33.8688MHz in HC-49U package, then go with the values above. If using a fundamental crystal, then replace C38, C39 and R29 according to the crystal's datasheet. If the card doesn't work correctly then I suggest measuring the crystal output with an oscilloscope.
1. RP1, SJ5, U9, U10, CN1: If you want to use the CD-ROM interface on the sound card, do **NOT** install RP1, install a 10kΩ resistor in SJ5's 1-2 position and a 0Ω in 3-4. Otherwise, install RP1, a 10kΩ resistor in SJ5's **1-3** position and a 0Ω in **2-4**, and do not install U10 and CN1. Then flash the EEPROM (U9) with a programmer. EEPROM images are in the `eeprom/` folder.
1. SJ3, SJ4: Install two 0Ω resistors in 2-3 position.
1. U6: This card supports YMF711 (OPL3-SA2), YMF718 (OPL3-SA2C), YMF715 (OPL3-SA3), YMF719 (OPL3-SA3C) and YMF741 (OPL3-SA3L) in LQFP-100 package. Note that YMF715**F**-S may not work correctly according to some report.

The BOM for the onboard QS1000 wavetable is not listed. Some components, like U7 and some capacitors / resistors, are not present on any variant of this card. I have no idea on what values they are.

As of August 2026, all of the components except the OPL3-SAx chip are still being manufactured. The crystals are not sold by LCSC but they can be sourced through other channels.

# Bracket

The replica should be compatible with the original bracket if the connectors are installed correctly. A model for 3D-printing will be available in the future.
