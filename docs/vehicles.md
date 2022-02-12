# vehicles vdfm

Project CARS/ AMS2
Translation for porsche_991_gt3rs.vdfm
By JDougNY

Translation for fordsgt.vdfm
by gvse

Version 1.0 - October 8, 2018 - Initial release
AMS2 additions by gvse

!!! note

	Address locations are typical for all VDFM files up to the beginning of the string data.
	Use this translation as a guide to editing any VDFM file.




## header

[HEADER - 0x000-0x02F (48 bytes)]

0x010-0x013 = 98010000 = 408// (Integer) Byte Length of offset/data section. Count from 0x030-0x1C7

___

**AMS2**
0x010-0x013 = 98010000 = 424// (Integer) Byte Length of offset/data section. Count from 0x030-0x1C7

___

0x15 = 08 // (byte) number of empty bytes after data section.  0x1C8-0x1CF

___

**AMS2**

0x15 = 08 // (byte) number of empty bytes after data section.  0x1D8-0x1DF

___

0x018-0x01B = 12000000 = 18 // (Integer) Byte length of String data Section. 0x1D0-0x1E1      

**If additional bytes are inserted into the string data section, this register
is incremented accordingly.**

0x01D = 0E = 14 // (Byte) number of empty bytes after String data section. 0x1E2-0x1EF          


**AMS2**

0x01D = 01 = 1 // (Byte) number of empty bytes after String data section. 0x21F-0x21F


**Any changes to String Data section requires a check of remaining empty bytes.
There is always one zero byte after last entry.  Empty byte count does not include
that last zero byte.**

**AMS2**
0x020 = 30 = 48 // (Byte) Byte length of Data Map Offsets. 0x220-0x25F

0x025 = 00 // (Byte) number of empty bytes after the Data Map Offsets.

0x028 = 0C = 12 // (Byte) Byte length of end section. 0x2260-0x26B

0x02D = 04 // (Byte) number of empty bytes after the end section. 0x26C-0x26F


## AMS2 data section

### calls to physics files

**[DATA SECTION - 0x030-0x1D8]**

[Offset 08 of Data Map]

0x038-0x03B = XX000000 = 0 // (Integer) Location in string data for Chassis filename (*.CDFBIN)

___

[Offset 18 of Data Map]

0x048-0x04B = XX000000 = 0 // (Integer) Location in string data for Engine filename (*.EDFBIN)


___

[Offset 20 of Data Map]


**PC2 location of turbo: this and the following entries change in AMS2 1.3.3.0**

0x050-0x053 = XX000000 = // (Integer) **PC2** Location in string data for turbo filename (*.TBFBIN)
  If Data Map does not call for Offset 20, then no turbo/supercharger is utilized.
  

**AMS2**

[Offset 20 of Data Map]

0x050-0x053 = XX000000 = // (Integer) Location in string data for **clutches** filename (*.CBFBIN)
  If Data Map does not call for Offset 20, then no clutches is utilized.

for other AMS2 offsets see the [data map offsets section](#DATA-MAP-SECTION-for-AMS2)
___

[Offset 28 of Data Map]

0x058-0x05B = XX000000 = // (Integer)  Location in string data for turbo filename (*.TBFBIN)
  If Data Map does not call for Offset 20, then no turbo/supercharger is utilized.
  
  
___

[Offset 38 of Data Map]

0x068-0x06B = XX000000 = 0 // (Integer) Location in string data for Gearbox filename (*.GDFBIN)0 // 

___

[Offset 40 of Data Map]

0x070-0x073 = XX000000 = 0 // (Integer) Location in string data for Suspension filename (*.SDFBIN)


___

[Offset 48 of Data Map]

0x078-0x07B = XX000000 = 0 // (Integer) Location in string data for Collision filenames (*.XML)

___

[Offset 50 of Data Map]

0x080-0x084 = XX000000 = 0 // (Integer) Location in string data for Tyre filename (*.HDTBIN)




### wheel and tire setup

0x088-0x08B = B072483F = 0.783 // (Float) FL Wheel/Tyre lateral offset in Meters

0x08C-0x08F = 3333B33E = 0.350 // (Float) FL Wheel/Tyre vertical offset in Meters

0x090-0x093 = 1B2F9DBF = -1.228 // (Float) FL Wheel/Tyre fore/aft offset in Meters

0x094-0x097 = B07248BF = -0.783 // (Float) FR Wheel/Tyre lateral offset in Meters

0x098-0x09B = 3333B33E = 0.350 // (Float) FR Wheel/Tyre vertical offset in Meters

0x09C-0x09F = 1B2F9DBF = -1.228 // (Float) FR Wheel/Tyre fore/aft offset in Meters

0x0A0-0x0A3 = 4260453F = 0.771 // (Float) RL Wheel/Tyre lateral offset in Meters

0x0A4-0x0A7 = 6DE7BB3E = 0.367 // (Float) RL Wheel/Tyre vertical offset in Meters

0x0A8-0x0AB = 1B2F9D3F = 1.228 // (Float) RL Wheel/Tyre fore/aft offset in Meters

0x0AC-0x0AF = 426045BF = -0.771 // (Float) RR Wheel/Tyre lateral offset in Meters

0x0B0-0x0B3 = 6DE7BB3E = 0.367 // (Float) RR Wheel/Tyre vertical offset in Meters

0x0B4-0x0B7 = 1B2F9D3F = 1.228 // (Float) RR Wheel/Tyre fore/aft offset in Meters

0x0B8-0x0BB = 14AE873E = 0.265 // (Float) FL Tyre width in Meters

0x0BC-0x0BF = 0E2D323F = 0.696 // (Float) FL Tyre height in Meters

0x0C0-0x0C3 = 14AE873E = 0.265 // (Float) FR Tyre width in Meters

0x0C4-0x0C7 = 0E2D323F = 0.696 // (Float) FR Tyre height in Meters

0x0C8-0x0CB = 6666A63E = 0.325 // (Float) RL Tyre width in Meters

0x0CC-0x0CF = 48E13A3F = 0.730 // (Float) RL Tyre height in Meters

0x0D0-0x0D3 = 6666A63E = 0.325 // (Float) RR Tyre width in Meters

0x0D4-0x0D7 = 48E13A3F = 0.730 // (Float) RR Tyre height in Meters


## Offsets B8 and C0 in Data Map

0x0E8-0x0EB = XX000000 = // (Integer) Location in string data for KERS,DRS and Hybrid filename (*.BBFBIN)

If Data Map does not call for Offset B8, then no *.BFFBIN is utilized.
___

0x0C0-0x0C4 = XX000000 = // (Integer) Location in string data for *Push to Pass* filename

If Data Map does not call for Offset C0, then no *.BFFBIN is utilized.
  
___

## brake discs

0x138-0x013B = 00400344 = 525.0  // (Float) Brake Disc Glow Min (Start to glow slightly)

0x13C-0x013F = 00007A44 = 1000.0 // (Float) Brake Disc Glow Max (Full glow effect)

## unknown

0x140-0x0144 = 0000803F = 1.0       // (Float) ??

0x13C-0x013F = 0000803F = 1.0       // (Float) ??

0x140-0x143 = 0000803F = 1.0 // (Float) ??

0x144-0x147 = FFFFFFFF       // Beginning of Container...appears to be

0x148-0x14B = 01000000 = 1   // (Integer) ??

0x14C-0x14F = 01000000 = 1   // (Integer) ??

0x150-0x153 = 01000000 = 1 // (Integer) ??

0x154-0x157 = 01000000 = 1 // (Integer) ??

0x158-0x15B = 01000000 = 1 // (Integer) ??

0x15C-0x15F = 01000000 = 1 // (Integer) ??

0x160-0x163 = 01000000 = 1 // (Integer) ??

0x164-0x167 = 01000000 = 1 // (Integer) ??

0x168-0x16B = 01000000 = 1 // (Integer) ??

0x16C-0x16F = 01000000 = 1 // (Integer) ??

0x170-0x173 = 01000000 = 1    // (Integer) ??

0x174-0x177 = 01000000 = 1    // (Integer) ??

0x178-0x17B = 01000000 = 1    // (Integer) ??

0x17C-0x17F = 0000B841 = 23.0 // (Float) ??

0x180-0x183 = 00000000 = 0

0x184-0x187 = 0000803F = 1.0 // (Float) ??

0x188-0x18B = 0000803F = 1.0 // (Float) ??

0x18C-0x18F = 0000803F = 1.0 // (Float) ??

0x190-0x193 = 0000803F = 1.0  // (Float) ??

0x194-0x197 = 8FC2753E = 0.24 // (Float) ??

0x198-0x19B = 8FC2753D = 0.06 // (Float) ??

0x19C-0x19F = CDCC8C40 = 4.4  // (Float) ??

0x1A0-0x1A3 = 00008040 = 4.0  // (Float) ??

0x1A4-0x1A7 = C3F5A83E = 0.33 // (Float) ??

0x1A8-0x1AB = 6666E63E = 0.45 // (Float) ??

0x1AC-0x1AF = 6666863F = 1.05 // (Float) ??

0x1B0-0x1B3 = CDCC4C3F = 0.8 // (Float) ??

0x1B4-0x1B7 = 00000000 = 0

0x1B8-0x1BB = 3333333F = 0.7 // (Float) ??

0x1BC-0x1BF = 00000000 = 0

0x1C0-0x1C3 = 0AD7233C = 0.01 // (Float) ??

0x1C4-0x1C7 = 00000000 = 0

0x1C8-0x1CB = 00000000 = 0

0x1CC-0x1CF = 00000000 = 0

0x1D0-0x1D7 = unknown

0x1D8-0x1DF = 8 empty bytes before the string section

!!! note

	From this point onward the adddresses can change, due to both the
	byte length of the String data section and the size of the data map section.
	No matter the addresses the code will flow the same as follows.
	
	String Data
	
	empty bytes for String data
	
	Data Map
	
	empty bytes for Data map (if any)
	
	End Section
	
	Empty bytes for End Section

## STRING DATA SECTION

0x1E0-0x21E = fordsgt String Data Section.

``fordsgt`` = 8 bytes (``fordsgt.`` or ``fordsgt00``) starts at byte 0 of the string section

``GT_Cup`` clutches entry starts at byte 27

``chevrolet_corvette_c7_z06`` tire starts at byte 37

This string section has the total of 63 bytes. There is 1 empty byte before the Data Map Offsets section.

Anything called by data map will look for this text for each physics file type.  There is always one "zero" byte after each entry in this section.

0x21E-0x21F =  // empty bytes for String Data section.

These bytes are ignored, unless offsets 0x018 and 0x01D are adjusted.



## DATA MAP SECTION for AMS2

08 = 0x038 = Chassis file lookup // In all VDFM

18 = 0x048 = Engine file lookup  // In all VDFM

20 = 0x050 = *Clutches* file lookup   // only when needed. New file in AMS2 1.3.3.*

28 = 0x058 = Turbo file lookup   // only when needed

38 = 0x068 = Gearbox file lookup // In all VDFM

40 = 0x070 = Suspension file lookup // In all VDFM

48 = 0x078 = Collision file lookup  // In all VDFM

50 = 0x080 = Tyre file lookup    // In all VDFM

B8 = 0x0E8 = KERS, DRS, Hybrid file lookup // only when needed

C0 = 0x0F0 = push to pass

## END SECTION

0x220-0x22F // end section and empty bytes for end section






<script src="https://hypothes.is/embed.js" async></script>