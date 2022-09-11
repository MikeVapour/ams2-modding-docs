# chassis

Project Cars chassis translation by **JDougNY**

Version 1.02 - February 2022 - AMS2 revisions by **GvsE**

Version 1.01 - April 4, 2018 - added Front/Center differential code.  Defined "Authentic" driving assists and other revisions (rough notes version)

Version 1.0 - November 1, 2017 - Initial Release (rough notes version)

!!! note

    Use this translation as a general guide to locate data in the file search the hex strings. Just search using the first 3 bytes of the string. Sometimes there is no data entered after the hex string. When that occurs the string begins with `28....`


___

!!! note

    AMS2 Values are based mostly on Porsche 911 GT3 Cup Car, Mclaren Street and Camaro Street
    
There are varying amounts of data after each string as defined by how the bytes are set for the end of the string.

## Examples of Hex String Endings

A2` = float, float

03 00` = byte, byte, byte

03 02` = byte, byte, float

23 00` = float, byte, byte

23 02` = float, byte, float

83 00` = byte, float, byte

83 02` = byte, float, float

A3 00` = float, float, byte

A3 02` = float, float, float

05 00` = byte, byte, byte, byte, byte

A5 2A` = float, float, float, float, float

## Hex string beginnings

Hex strings generally begin with 20, 21, 22, 24 (usually begins a string of 6 bytes), 26, and 28 (there is no data after 28)

!!! note

    We sometimes provide alternative strings for the same entries: they may be calling bytes, integers and floats. For example, see **inertia** strings below.

## Byte Count Registers

0x0008-0x000B = {integer} // (little endian) Total byte count of entire file

___

0x0014-0x0017 = {integer} // (little endian) Total byte count from 0x0028 to beginning of end section (see 0x0020 for end section length)

___

0x0020-0x0023 = {integer} // (little endian) Total byte count of end section

___

0x0024-0x0027 = {integer} // (little endian) Total byte count from beginning of file to beginning of end section (see 0x0020 for end section length)


___

!!! attention

    When adding/removing bytes from any data before the end section, you must change 3 of the registers above: 0x0008-0x000B, 0x0014-0x0017, and 0x0024-0x0027


## GENERAL

`28 FA D6 67 78`      ??Unknown

___

`28 B9 1B 6F 6E`      ??Unknown

___

`20 9A 30 40 34`       GarageDisplayFlags={byte}X

___

`20 96 5B FF BF`       FeelerFlags={byte}X

___

### Mass

`22 67 0B 57 AB`       Mass={float}XXXX.xx

`21 67 0B 57 AB`      Mass={integer}XXXX
___

`24 C2 40 3A 15 83 00` ??Unknown={byte}x, {float}XXXX.xx, {byte}X

**ams2** `24 C2 40 3A 15 83 00` 		0, 1, 70

___

`28 12 6D 1F D1`       ??Unknown // Setting value for above. No byte in code, which means zero setting

___

### inertia

`24 BB B3 9F 0B A3 02` Inertia=({float}XXXX.XX,{float}XXXX.xx{float}XXX.xx)

`24 BB B3 9F 0B 53 01` Inertia={integer}XXXX, {integer}XXXX, {integer}XXX

___

### fuel tank

`24 A0 53 0C 50 83 02` FuelTankPos=({byte}X, {float}XXXX.xx) {float}0.220) 

`24 A0 53 0C 50 A3 02` FuelTankPos=({float}0.0, {float}0.200) {float}0.220)

`24 6F 70 F3 C7 A2`    FuelTankMotion=({float}560.0, {float}0.7)	**ams2**: 981, 0.67


___


`26 3A 17 96 C2`       {byte}0  // CDF_UNKN_001

### cg

`20 38 05 5C 3C`       Symmetric={byte}1

`22 18 24 EA A8`       CGHeight={float}0.280

**ams2** 1.2= lower cg height 911 cup 0.2775


`24 DF 8D 93 CF 23 00` CGRightRange={float}0.5, {byte}0, {byte}0

`24 DF 8D 93 CF A3 00` CGRightRange=({float}0.5, {float}0.0, {byte}0)

`28 00 9D 8A CF`       CGRightSetting= No byte in code, which means zero setting

`24 BE BA 67 7B 23 00` CGRearRange={float}0.XXX {byte}0, {byte}0

`24 BE BA 67 7B A3 00` CGRearRange=({float}0.XXX, {float}0.XXX, {byte}0)

`28 D4 4C 53 C4`       CGRearSetting= No byte in code, which means zero setting

___

### WeightJacker

`24 5B 5E C8 CD A3 01` WeightJackerRange=({float}x.xx, {float}x.xx, {integer}0)

`21 B4 AF A9 DF`       WeightJackerSetting={integer}

___

`22 1E 5C 8F 56`       {float}0.001 // Unknown

___

### Offsets: Visual and Collision 

`24 86 9A 77 97 03 00` GraphicalOffset={byte}0, {byte}0, {byte}0

**ams2** `22 0C DF CA 05` 		CD CC CC 3D

___

`24 D2 CF F4 3D 03 00` CollisionOffset={byte}0, {byte}0, {byte}0

`24 D2 CF F4 3D 83 00` CollisionOffset=({byte}0, {float}0.XXX, {byte}0)

___

### Undertray

`24 E9 DE D9 99 23 02` UndertrayZeroZero={float}X.XXX {byte}X {float}X.XXX

`24 E9 DE D9 99 A3 02` UndertrayZeroZero=({float}0.75, {float}0.02, {float}-1.40)

`24 BA 61 42 62 23 02` UndertrayZeroOne={float}X.XXX {byte}X {float}X.XXX

`24 BA 61 42 62 A3 02` UndertrayZeroOne=({float}-0.75, {float}0.02, {float}-1.40)

`24 AC 8D E9 39 23 02` UndertrayZeroTwo={float}X.XXX {byte}X {float}X.XXX

`24 AC 8D E9 39 A3 02` UndertrayZeroTwo=({float}0.75, {float}0.02, {float}1.0)

`24 C7 C2 3D 06 23 02` UndertrayZeroThree={float}X.XXX {byte}X {float}X.XXX

`24 C7 C2 3D 06 A3 02` UndertrayZeroThree=({float}-0.75, {float}0.02, {float}1.0)

`24 86 AE 66 2B 53 02` UndertrayParams={integer}XXXX {integer}XXXX {float}X.XXX

`24 86 AE 66 2B A3 02` UndertrayParams=({float}262500.00, {float}11600.00, {float}0.XXX)

___

**AMS2 additions**

___

ams `24 F3 14 15 24 A3 02`		0.35, 0.05, -0.6
___

ams `24 12 40 9D 39 A3 02`		-0.35, 0.05, -0.6
___

ams `24 FB 50 F7 6F A3 02`		 0.5, 0.05, 0.6
___

ams `24 42 34 18 59 A3 02`		-0.5, 0.05, 0.6
___

ams `24 A2 43 C6 15 A3 02`		0.2,  0.05, -1.6
___

ams `24 E4 F9 61 17 A3 02`		-0.2,  0.05, -1.6
___

ams `24 68 60 EB 06 83 00`		0, 0.1, 0
___

ams `24 86 AE 66 2B 53` 		02	
___

ams `20 A1 07 00 E8 03 00`		0, 0.35


!!! note

    UndertrayZeroZero TO UndertrayParams = 83 bytes (pc2) versus 201 (ams2) = 118
    
    undertray camaro ss 207 bytes
    undertray jaguar 83 bytes -124



___

### Tire Types


`26 E4 A7 89 37`       DryTireCompoundSetting={byte}X // used for auto selection when condition is right

`26 7B 83 4D 10`       WetTireCompoundSetting={byte}X  // used for auto selection when condition is right

`26 A4 F8 37 C0`       IceTireCompoundSetting={byte}X  // used for auto selection when condition is right

`26 F7 FA A8 5D`       AllTerrainTireCompoundSetting={byte}X  // used for auto selection when condition is right

___


413-395=18 mclaren 
413 - 482 = 69  camaro
422- 491 = 69 cayman
413- 491 = 78 (camaro replaced with Cayman)
482 - mclaren

___

### ams2: values below probably affect AI

___

ams `22 D2 F3 2A C0`		0.96							0.84		##1.2 (911cup) 0.825  (prev. 0.84)
___

ams `22 8E 3E 79 A1`		0.88 (AI cog multiplier?)		0.765		##1.2 (911cup) 0.745 (prev.0.76)
___

ams `22 3B CC 6A AF`		0.92							1
___

ams `22 42 76 E9 03`		0.82 (Ultima)					1.002	
___

ams `22 D2 64 1F 43`		0.8225 (Ultima)					1.005		##1.2 (911cup) 1.12 (prev.1.01)
___

ams `22 67 84 19 B2`		0.5								0.422

___

ams `20 2F 48 27 58` byte									50 	(post 1.1.1.1.)		##1.2 (911cup) 75 (prev.60)
___

ams `22 0B 6E A9 83`										0.07 (post 1.1.1.1.)
___

ams `22 8C 23 4A AB`		0.2	(start off the line?)		0.05
___

ams `22 A1 E3 C0 8F`		50								50
___

ams `28 09 FC D2 89`										no value (post 1.1.1.1.)
___

ams `22 FA CF 45 C7`		1								0.65
___

ams `22 6D C7 7D 59`		1.5								0.8
___

ams `22 F8 C2 B0 FD`		1.8								2.15		##1.2 (911cup) 1.35 (prev.1.25)
___

ams `22 11 00 04 90`		12								10			##1.2 (911cup) 6 (prev. 10)
___

ams `22 53 4E 46 23`		4								5			##1.2 (911cup) 3 (prev. 5)

___

new in 0.9.6 (new AI logic?)

___

ams `22 AB 00 EC BC`		0.88							0.965
___

ams `24 F1 5E D9 7A A3 02`	80, 100, 115					70, 100, 120

___

**new in 1.1.2.0**

___

`22 BD AC 12 AD` 	00 00 00 3F 
___

`22 79 68 2D 63` 	CD CC CC 3E 								1.1.2.5=0.45 (previously 0.4)
___

`22 5E 3F 89 F8` 	66 66 86 3F 
___

`22 99 21 AA 40` 	00 00 80 3E 
___

`22 ED 75 D0 08` 	00 00 C0 3F 
___

`22 DE F7 0D 39` 	A4 70 7D 3F 
___

`22 C1 F2 D7 45` 	48 E1 7A 3F 
___

`28 0B EC 7F 64` 
___

`22 B3 50 98 73` 	CD CC 4C 3F 
___

`22 8D C4 52 2C` 	9A 99 19 3E 
___

`22 E4 8F F7 78` 	CD CC CC 3E 
___

`22 23 9D 28 65` 	00 00 80 3F 							##1.2 (911cup) 0.7 (prev. 1)
___

`22 30 C3 44 03` 	00 00 80 3F 
___

`22 CE C8 DF 0A` 	29 5C 8F 3F 							##1.2 (911cup) 1.1 (prev. 1.12)
___

`22 82 25 69 C0` 	9A 99 99 3E 							##1.2 (911cup) 0.2775 (prev. 0.2795)
___

`22 B2 13 CD B5` 	00 00 00 3F 
___

`22 2B 0D 4D BD` 	66 66 66 3F 
___

`22 61 1F 8B C4` 	71 3D 0A 3E 
___

`22 B3 0C 9A FD` 	71 3D 0A 3E 
___

`22 F4 07 65 E3` 	71 3D 0A 3E
___

`22 C6 1D 63 0D` 	D7 A3 90 3E 							##1.2 (911cup) 0.35 (prev. 0.25)
___

`22 50 D4 76 7F` 	9A 99 99 3D 
___

`22 ED F4 7C 23` 	14 AE A7 3E									1.1.2.5=0.3225 (previously 0.0.3275) 		##1.2 (911cup) 0.03 (prev. 0.3225)

**end of new in 1.1.2.0**


___

ams `22 F8 CD A6 0A`										0.075 (post 1.1.1.1.)		##1.2 (911cup) 0.035 (prev. 0.05)

___

ams `22 A0 F8 5B 2C`		0.2								0.1

___

ams `22 F5 1B 34 23`										0.55 (post 1.1.1.1.)

___

**PC2** `24 19 38 99 74 03`	00  1,1,100	

___

### fuel

`24 19 38 99 74 A3 00` FuelRange=({float}1.0, {float}1.0, {byte}84)

`20 99 F0 BB F8`       FuelSetting={byte}49

___

### Pitstops

`24 F7 05 73 EA 03 00` NumPitstopsRange=({byte}0, {byte}1, {byte}4)

`20 6D DE 02 E8`       NumPitstopsSetting={byte}3

`24 9B FA 80 6D 83 00` PitstopOneRange=({byte}0, {float}1.0, {byte}84)

`20 03 EE A8 65`       PitstopOneSetting={byte}42

`24 55 DE D0 64 83 00` PitstopTwoRange=({byte}0, {float}1.0, {byte}84)

`20 85 22 52 46`       PitstopTwoSetting={byte}42

`24 E8 12 23 11 83 00` PitstopThreeRange=({byte}0, {float}1.0, {byte}84)

`20 26 BA 51 7D`       PitstopThreeSetting={byte}42

___

### AI: legacy values

`20 BB 1F 05 F3` AIMinPassesPerTick={byte}2

`22 26 A9 8C 99` AIRotationThreshold={float}0.12

`22 79 F4 A6 98` AIEvenSuspension={float}1.0

`22 BC C7 CE E7` AISpringRate={float}1.0

`22 2B 3F F8 6B` AIDamperSlow={float}0.1

`22 C4 89 77 69` AIDamperFast={float}0.1

`22 88 76 9A ED` AIDownforceZArm={float}0.150

`22 15 6B 48 37` AIDownforceBias{float}0.0

`24 2E 5D 54 E4 A3 02` AITorqueStab=({float}1.0, {float}1.0, {float}1.0)

___

`22 CA 88 11 AF` ??Unknown={float}X.XXX
___

`22 2E 9D EF 64` ??Unknown={float}X.XXX 
___

`28 F6 B9 76 CF` ??Unknown= No byte in code, which means zero setting

172-194=22


the whole aero: 610 bmw - 680 mclaren -699 ultima
bmw m1 754 
bmw gt3 749
ginetta g4- cup	587
ginetta gt4 supecup 592


## FRONT WING `E0 E4 12 24 BA`

`E0 E4 12 24 BA` 

!!! note

    FRONT WING (or FRONT LEFT WING when FRONT RIGHT WING exists)

___

### range

`24 AD 3C 20 13 83 00` FWRange=({byte}0, {float}1.0, {byte}4)

___

`20 06 A3 1F 94`       FWSetting={byte}1

___

`24 09 A8 52 D9 21`    FWMaxHeight={float}(0.10)

___

### drag

`24 2C FB 70 DA A3 02` FWDragParams=({float}0.005, {float}0.002, {float}0.00)

___

### lift

`24 23 EC 21 2A A3 02` FWLiftParams=({float}-0.264, {float}-0.021, {float}0.00002)	-0.095

___

ams 20 A1 3E B2 5A	01
___

`24 06 F4 58 AC 21`    FWLiftHeight=({float}0.335)	!!!!!!!!!!ams 0.1

___

`24 96 D3 8A 17 21`    FWLiftSideways={float}(0.0)				##1.2 (911cup) 0.5 (prev. 0.35)

___

ams 24 BE AD 3D 21 82		05, 1.001
 
___

### 3d plane

`24 54 6C CD BF A3 02` FWLeft=({float}-0.20, {float}0.0, {float}0.0)  !!!!!ams -0.15
___

`24 C5 19 77 0C A3 02` FWRight=({float}0.20, {float}0.0, {float}0.0)
___

`24 CD 98 5A 4C A3 02` FWUp=({float}0.0, {float}-0.30, {float}-0.001)		!!!ams 0
___

`24 82 6E D8 E3 A3 02` FWDown=({float}0.0, {float}0.15, {float}0.001)		ams 0
___

`24 E4 3E 99 D8 A3 02` FWAft=({float}0.0, {float}0.02, {float}-0.2)			0
___

`24 F5 42 E8 78 A3 02` FWFore=({float}0.0, {float}0.0, {float}0.0)			0
___

`24 3D FD AB 72 A3 02` FWRot=({float}0.5, {float}0.25, {float}0.35)		ams 0
___

`24 EB DD A8 12 A3 02` FWCenter=({float}0.00, {float}-0.100, {float}-0.50)		!!!ams last byte

___

`24 9C 84 12 FF 21`


### Front Right Wing `E0 BE 70 BE 88`

`E0 BE 70 BE 88` 

!!! attention

    This is not present in AMS2 in the cars I've examined so far.

    FRONT RIGHT WING // Same parameters as above
    Only included in some CDFbin files

___

`24 96 A7 D0 8D 83 00` FWRange=({byte}0, {float}1.0, {byte}10)
___

`20 B5 E8 1B 09`       RWSetting={byte}1
___

`24 29 1A 69 42 21`    FWMaxHeight={float}0.10
___

`24 CF 8B E1 A1 A3 02` FWDragParams=({float}0.005, {float}0.003, {float}0.00)
___

`24 76 29 1C 37 A3 02` FWLiftParams=({float}-0.000, {float}-0.030, {float}0.00)
___

`24 4B 1A 06 AD 21`    FWLiftHeight={float}0.335
___

`24 81 05 80 FE 21`    FWLiftSideways={float}0.00
___

`24 A3 72 BD EE A3 02` FWLeft=({float}-0.20, {float}0.0, {float}0.0)
___

`24 E3 C5 15 C2 A3 02` FWRight=({float}0.20, {float}0.0, {float}0.0)
___

`24 68 D5 13 6E A3 02` FWUp=({float}0.0, {float}-0.30, {float}-0.001)
___

`24 41 68 8B 03 A3 02` FWDown=({float}0.0, {float}0.15, {float}0.001)
___

`24 57 1E 68 BD A3 02` FWAft=({float}0.0, {float}0.02, {float}-0.2)
___

`24 91 B8 03 C5 A3 02` FWFore=({float}0.0, {float}0.0, {float}0.0)
___

`24 7B 00 64 6A A3 02` FWRot=({float}0.5, {float}0.25, {float}0.35)
___

`24 87 7F E1 43 A3 02` FWCenter=({float}0.00, {float}-0.100, {float}-0.50)

___

`24 7D 2B 67 E8 21 00`
___

`24 87 8C 07 BE A5 2A` 00 00 FWSettingSpeed
___

`24 BA 8F 41 41 A5 22` 00 00 FWSettingBraking
___

`24 7C 98 63 3A A5 2A` 00 00	FWSettingThrottle
___

`24 A3 37 75 01 05 00` 00 00 FW DRS Button

!!! note

    As I understand, 
    
    the first number is the speed (or the percentage of top speed) at which this effect will appear the second, it depends. Either it is a speed or this is a percentage of move (1 for full throttle, full steering etc)
    
    third, I don't really know.

    fourth is the the position of the wing before it moves setting
    
    fifth is the proper move setting

    the last one is the max angle?

    the settings are on the each wing range at the beginning

___

## REAR WING `E0 E1 83 3A A6` 

`E0 E1 83 3A A6` 

___

### range

`24 15 76 54 86 83 00` RWRange=({byte}0, {float}1.0, {byte}7)
___

`20 8A 98 EB 35`       RWSetting={byte}1
___

### drag

`24 67 DC B6 B3 A3 02` RWDragParams=({float}0.005, {float}0.003, {float}0.00			0,224/0,304=0,78
___

### lift

`24 83 D3 85 B9 A3 02` RWLiftParams=({float}-0.24, {float}-0.016, {float}0.00			0,264/0,336=0.78

___

ams2	20 6D B2 33 90 		01?


___

`24 7A 8F 77 C8 21`    RWLiftSideways={float}0.0			##1.2 (911cup) 0.65 (prev. 0.5)

___

ams 24 45 48 1D 86 82 02		1.01???????????????????????????

___

### yaw

`24 15 2E 20 37 A2`    RWPeakYaw={float}0.0, {float}0.00	$$$
___

### 3d plane

`24 34 3E C4 2F A3 02` RWLeft={float}-0.15, {float}0, {float}0
___

`24 42 3B C2 6A A3 02` RWRight={float}0.15, {float}0, {float}0
___

`24 EF B4 24 0A A3 02` RWUp={float}, {float}, {float}		!!! ams 0

___

`24 65 F8 14 22 A3 02` RWDown=({float}0.0, {float}0.20, {float}0.002)		!!! ams 0

___

`24 69 EC ED 3E A3 02` RWAft=({float}0.0, {float}0.03, {float}-0.4)		$$$		!!! ams 0
___

`24 D5 07 F8 FE A3 02` RWFore=({float}0.0, {float}0.0, {float}0.0)		---		!!! ams 0
___

`24 08 4B 50 B3 A3 02` RWRot=({float}0.7, {float}0.4, {float}0.5)		$$$		!!! ams 0
___

`24 17 44 ED 31 A3 02` RWCenter=({float}0.00, {float}0.200, {float}0.6) $$$		!!! ams 0

___

`24 DC 76 52 9B 21

___

`24 D6 00 BE 0B A5 2A
___

`24 F1 54 C6 5F 05
___

`24 13 BF E2 BA A5 22
___

`24 38 01 84 A9 25 2A
___

`24 92 8C 3D DF 05
___

`24 A1 24 1A A8 A5 22
___

`24 2F 2D 7A FC 05


### REAR RIGHT WING `E0 3D D3 DA 1B`

`E0 3D D3 DA 1B` 

___


`24 1F 3D 69 0C 03 00` RWRange=00 00 00 
___

`28 85 98 3C 01`       RWSetting=
___

`24 6B 20 03 55 23 00` RWDragParams=CD CC CC 3D 00 00 
___

`24 B8 2D 4D C4 03 00` RWLiftParams=00 00 00 
___

`24 0A 2B 9B 22 01`    RWLiftSideways=00 
___

`24 BD CD 13 89 02`    RWPeakYaw=00 00 
___

`24 22 45 69 35 03 00` RWLeft=00 00 00 
___

`24 51 1B 19 80 03 00` RWRight=00 00 00 
___

`24 86 1A F2 5C 03 00` RWUp=00 00 00 
___

`24 51 EE 77 72 03 00` RWDown=00 00 00 
___

`24 46 77 39 74 03 00` RWAft=00 00 00 
___

`24 2B 7E E4 47 03 00` RWFore=00 00 00 
___

`24 99 E7 CC 64 03 00` RWRot=00 00 00 
___

`24 8D 6C 15 A3 83 02` RWCenter=00 00 00 00 3F CD CC 4C 3F 
___

`24 3F 66 C0 31 01` 00 
___

`24 85 28 FC 0B 05 00 00 00 00 00 00  RWSettingSpeed
___

`24 93 CA AE FA 05 00 00 00 00 00 00  RWSettingButton1
___

`24 A3 F6 05 9E 05 00 00 00 00 00 00  RWSettingBraking
___

`24 BE 57 73 DA 05 00 00 00 00 00 00  RWSetting??
___

`24 C7 39 90 0B 05 00 00 00 00 00 00  RWSettingThrottle
___

`24 7D 95 1C A7 05 00 00 00 00 00 00  RWSettingSteering
___

`24 17 75 D3 04 05 00 00 00 00 00 00  RWSetting??

___

178-493=315


### Unknowns below are in some cdfbins


___

`24 DC 76 52 9B 21` 100 
___

`24 13 BF E2 BA A5 2A` 17.9, 0.5, 1000, -30, 30

could be some of the attributes below?

___

RWSettingLongG
___

RWSettingLateralG
___

RWSettingSteering
___

RWSettingRate
___

RWSettingButton1
___

RWSettingForwardVel
___

RWSettingThrottle
___

RWSettingBraking
___

RWMaxHeight
___

RWLiftHeight



___


## BODY AERO `E0 2B DA 95 42`


`E0 2B DA 95 42` 

___


### drag

`24 33 63 ED FD 21`    BodyDragBase={float}0.30

___

`24 67 CA A0 92 21`    BodyDragHeightAvg={float}0.2

___

`24 1F 13 C1 85 21`    BodyDragHeightDiff={float}0.47		ams 0

___

`24 56 E0 A3 AB 21`    BodyMaxHeight={float}0.2

___

ams `20 3F D7 58 A3`		1
___

ams `20 7A 5A 13 BD`		1

___

### 3d plane

`24 C5 A5 4E CE A3 02` BodyLeft={float}-0.80, {float}0.0, {float}0.0	$$$	ams -1.1

___

`24 6A 08 2A D4 A3 02` BodyRight=({float}0.80, {float}0.0, {float}0.0)	$$$

___

`24 DC 57 D2 48 A3 02` BodyUp=({float}0.0, {float}-1.00, {float}0.0)	$$$		!!ams 0
___

`24 E3 A1 65 97 A3 02` BodyDown=({float}0.0, {float}0.5, {float}0.0)			!!ams 0

___

`24 08 B1 B6 50 A3 02` BodyAft=({float}0.0, {float}0.5, {float}-0.2)	$$$
___

`24 DC 2F 52 E4 A3 02` BodyFore=({float}0.0, {float}-0.060, {float}0.435)	--		!!ams 0
___

`24 F8 26 31 A8 A3 02` BodyRot=({float}3.45, {float}3.0, {float}1.30)		-		!!ams bytes high values
___

`24 38 D1 8E E7 A3 02` BodyCenter=({float}0.0, {float}0.50, {float}-1.40)	$$$

___

### radiator

`24 8E 02 D1 67 83 00` RadiatorRange=({byte}0, {float}1.0, {byte}4)
___

`20 F7 CF 3C A8`       RadiatorSetting={byte}3
___

`24 CD 9B D5 4E 21`    RadiatorDrag=({float}0.000)
___

`24 0A 98 AA BD 21`    RadiatorLift=({float}0.00)
___

### brake ducts

`24 67 64 39 31 83 00` BrakeDuctRange=({byte}0, {float}1.0, {byte}5)

___

`20 CF 01 35 71`       BrakeDuctSetting={byte}1
___

`24 50 2D C5 AE 21`    BrakeDuctDrag=({float}0.000)

___

`24 B7 28 36 3E 21`    BrakeDuctLift=({float}0.00)




## DIFFUSER `E0 C9 41 A8 1C`

`E0 C9 41 A8 1C` 


106 114

	

___

`24 BE 0F 28 99 A3 02` DiffuserBase=({float}-0.00, {float}-0.50, {float}5.0)
___

`24 47 D0 B1 DE 21`    DiffuserFrontHeight=({float}0.000)
___

`24 20 B9 8D FF A3 02` DiffuserRake=({float}0.000, {float}-00.0, {float}00.0)
___

`24 FF 59 46 C8 A3 02` DiffuserLimits=({float}0.000, {float}0.100, {float}0.055)
___

`24 E0 A1 25 DE A2`    DiffuserStall=({float}0.0, {float}0.5)

___

`20 56 8D F4 59`		01?


___

`24 E1 76 32 24 21`    DiffuserSideways=({float}0.0)								##1.2 (911cup) 0.5 (prev. 0.4)
___

`24 B8 97 56 8E A3 02` DiffuserCenter=({float}0.0, {float}0.10, {float}-1.30)		##1.2 (911cup) -0.8 (prev. -0.75)

115-344=229

___

## SUSPENSION `E0 C8 15 E2 23`

!!! attention 

    AdjustSuspRates=1 // Adjust suspension rates due to motion ratio (0 = direct measure of spring/damper rates, 1 = wheel rates).
    
    Switch to permit the spring and damper rates at the wheels to be changed between two modes.

    =0 means the wheel rates are adjusted for the geometry of the pushrod and the location of the lower end of the pushrod relative to the inner and outer mounts of the wishbones.

    =1 means the wheel rates are adjusted only for the location the lower end of the pushrod relative to the inner and outer mounts of the wishbones.

    Note that =1 does not remove all the geometric implications from the pushrod definition. Only removing the definitions of the pushrods themselves from the `CORNER` sections will do that.


`E0 C8 15 E2 23` SUSPENSION begins



___

`28 6B 45 97 72`      ??Unknown
___

AMS2 `20 6B 45 97 72` byte 01
___

`20 E1 FF 94 B3` FF   ??Unknown
___

ams `28 41 A8 35 03`

___

### suspension rate

`20 7D E0 90 64`       AdjustSuspRates={byte}1
___

`20 B2 B4 93 40`       AlignWheels={byte}1

___

### rollbars

`20 26 E9 82 B6`       SpringBasedAntiSway={byte}1

___

ams `20 70 FA E1 77` byte 01
___

ams `28 4A 05 C9 38`


___

`28 89 92 C5 F3`       FrontAntiSwayBase= // no value

___

`24 E5 B9 A9 D6 A3 00` FrontAntiSwayRange=({float}10000.0, {float}10000.0, {byte}2)

___

`20 7F C7 58 D5`       FrontAntiSwaySetting={byte}5

___

`24 2E 06 8D A5 A2`    FrontAntiSwayRate=({float}1.36e11, {float}4.0)

___

`20 70 FA E1 77`       FrontAntiSwaySetting={byte}5

___

`28 F3 9C 93 F0`      Unknown data
___

`24 66 00 1E 25 A3 00` RearAntiSwayRange=({float}5000.0, {float}5000.0, {byte}8)

___

`20 04 78 E9 91`       RearAntiSwaySetting={byte}3

___

`24 50 E0 77 73 A2`    RearAntiSwayRate=({float}1.36e11, {float}4.0)
___

### toe

`24 69 D4 9B 3B A3 00` FrontToeInRange=({float}2.0, {float}-0.1, {byte}41)

___

`20 C3 36 57 CC`       FrontToeInSetting={byte}21

___

`24 55 C9 EA 65 A3 00` RearToeInRange=({float}2.0, {float}-0.1, {byte}41)

___

`20 FD F7 43 4F`       RearToeInSetting={byte}19

___

### caster

`24 1A 73 FE 3E A3 00` LeftCasterRange=({float}0.0, {float}0.1, {byte}100)
___

`20 FF D7 A7 D9`       LeftCastersetting={byte}20

___

`24 33 76 33 73 A3 00` RightCasterRange=({float}0.0, {float}0.1, {byte}100)

___

`20 A6 B8 E3 8F`       RightCastersetting={byte}20

___

###  trackbar

`24 34 A8 C5 EB A3 00`LeftTrackbarRange=({float}x.x, {float}x.x, {byte}X)
___

`20 69 CB F2 CA`      LeftTrackbarSetting={byte}X
___

`24 E6 68 17 75 A3 00`RightTrackbarRange=({float}x.x, {float}x.x, {byte}X)
___

`20 AA 2B 55 28`      RightTrackbarSetting={byte}X



## CONTROLS `E0 08 0A 14 C5`

`E0 08 0A 14 C5` CONTROLS

___

`E0 3F 9E 45 98` Unknown Section

___

`E0 9E F7 67 84` DRIVELINE begins



___

### Legacy FFb settings

`22 24 F5 34 B3`       SteeringFFBMult={float}0.9

___

`22 FB 38 19 1C`       FFBGripMulti{float}0.11

___

### ams2 FFB new section

___

`21 01 C1 8B 82` 		FFB grip integer 2420 / 116 (camaro) working: -64; bad 116
___

`22 3E 53 B5 CF`		float 4e-06		in 1.1.2.0  8e-06 (911 gt3 2)	in 1.1.5.0  8.5e-06 	6e-06 Lexus
___

`22 00 AB 3E 9B`		float 2.5
___

`20 60 DD 9A 44`		byte 2 Lexus  || 1 911 R
___

`22 5B AC 62 D2`		float 0.4	/ camaro 0.8	0.7 Lexus ||  0.8 911R
___

`22 03 52 2B 9D`		float 0.025	/ camaro .0.4
___

`22 AA 43 60 CF`		float 0.35	/ camaro 0.6
___

`20 BA 21 2D A8`   	byte	3



### ams2 new section comparison:	inverted / correct

___


`22 FB 38 19 1C`    FFBGripMulti{float}	0.048 / 0.025
c 		integer 2420 / -1600
___

`22 3E 53 B5 CF`		float 4.75e-06 / 5e-06
___

`22 00 AB 3E 9B`		float 2.5  /  2.5
___

`22 4E 2A 4E 0D`		float 2.5 (kingpin multiplier `reduces ffb pendulum`added to super v8 in 1.2)???
___

`28 60 DD 9A 44`		byte 0 / 20 60 DD 9A 44		byte 1
___

`22 5B AC 62 D2`		float 0.8	/ 0.8
___

`22 03 52 2B 9D`		float 0.04	/ 28 03 52 2B 9D  	byte missing
___

`22 AA 43 60 CF`		float 0.65	/ 0.6
___

`20 BA 21 2D A8`   	byte	3 / 3



### AMS2 controls

`E0 08 0A 14 C5` 
___

`22 FB 38 19 1C` 			A6 9B 44 3D 
___

`21 01 C1 8B 82`		C0 F9 FF FF 
___

`22 3E 53 B5 CF` 			30 62 9F 36
___

`22 00 AB 3E 9B` 			00 00 20 40 
___

`28 60 DD 9A 44` 
___

`22 5B AC 62 D2` 			CD CC 4C 3F 
___

`22 03 52 2B 9D` 			0A D7 23 3D
___

`22 AA 43 60 CF` 			66 66 26 3F 
___

`20 BA 21 2D A8` 			03 
___


`24 6B 4E A0 77 A3 00` 	00 00 C0 40 	00 00 00 3F 	3C 
___

`20 0F 6A B7 B6 16` 
___

`24 F7 34 A1 FE 13 00` 66 03 00 	00 	00 	01 
___

`28 52 8D 8C F7` 
___

`22 27 A0 D3 AC` 			00 00 00 3F
___

`28 31 7B 74 DC` 
___

`28 B1 21 88 BF` 
___

`22 E8 09 B9 01` 			00 00 80 3F 
___

`24 E0 D9 C8 5B` 
___

`22 35 5E 7A 3F` 			00 
___

`24 A6 8D 9C E2 A3 02` 	9A 99 59 3F 	66 66 26 3F 	66 66 26 3F 	DownshiftAlgorithm
___

`24 30 43 CE 21 03 00` 	14 		01 		0A 								SteeringLockRange
___

`20 B7 C2 C5 7E` 			06 
___

`22 05 CF 7B 77` 			00 00 80 3F 
___

`22 52 FA 34 11` 			00 00 D0 40 
___

`24 A6 32 13 57 83 00` 	00 	0A D7 23 3C 	64
___

`20 FD BA 64 73` 			28 
___

`24 D0 00 38 59 A3 00` 	00 00 00 3F 0A D7 23 3C 32 
___

`20 DA BD B9 81` 			46 
___

`24 96 4B 29 B4 83 01` 	00 0A D7 23 3C C8 00 00 00 						HandbrakeRange
___

`20 52 30 1F D2` 			32 
___

`22 E3 5A 1D CA` 			CD CC CC 3E 
___

`22 33 DE 0B C9` 			CD CC CC 3E 
___

`24 B3 D2 E5 A0 A3 00` 	0A D7 23 3C 0A D7 23 3C 63 						Traction Control
___

`20 63 9D 2B D2` 			09 
___

`22 20 D5 05 AC` 			00 00 40 40 
___

`20 6E DD B4 80` 			2D 
___

`28 05 CF 7B 77` 
___

`22 52 FA 34 11` 			00 00 A0 40 
___

`24 07 F7 6E 47 A2 CD` CC 4C 3D 0A D7 A3 3D 
___

`24 25 5A FB 23 A2 CD` CC 4C 3D 0A D7 A3 3D 
___

`24 24 9E 03 13 83 00` 	00 0A D7 23 3C 64								ABS Strength Range
___

`20 B2 BE 8E 7E` 			55 
___

`20 BC 12 66 E0` 			01 												"Authentic" ABSFourWheel assist
___

`20 BC 90 7F 88` 			01 
___

`20 F2 9A F8 10` 			01 
___

`20 FA CE 76 12` 			01 
___

`20 D5 DD 9C 9B` 			01 
___

`20 5B D1 F7 C8` 			01 

## unknown section `E0 3F 9E 45 98`

`20 D5 B3 F7 87` 			01 
___

`20 12 FA B3 EB` 			01 

___

### HP multiplier

`22 A3 BF 1E 60`	increases HP / HP multiplier. Set it to 1.0: `00 00 80 3F`

___

`22 C3 66 7D 2E` 		5C 8F 82 3F



___

###  steering

`24 6B 4E A0 77 A3 00` SteeringRatioRange={float}3.5, {float}0.5, {byte}35
___

`20 0F 6A B7 B6`       SteeringRatioSetting={byte}24

___

### steering wheel degrees of turn

**AMS2** `24 F7 34 A1 FE 13 00`	integer; byte; byte

___

### steering lock

`24 30 43 CE 21 23 00` SteeringLockRange={float}34.0, {byte}0, {byte}0

___

`20 B7 C2 C5 7E`	//no value set. steeringlocksetting

___

`22 27 A0 D3 AC`       {float}0.5         // CDF_UNKN_006


___

`20 31 7B 74 DC`       {byte}1            // CDF_UNKN_007

___

`28 B1 21 88 BF`      ??Unknown // no data in code, which means zero. 

___

`22 E8 09 B9 01`       {float}1.0         // CDF_UNKN_008

___

AMS 1.2.2.0 		`20 66 0C A5 14` byte 01

___

### new code Traction Control after 1.2.1.4

AMS2 `24 AA AD DA 30 A2` 	33 33 93 3F (1.15) 	9A 99 19 3E	(0.15)		

___

AMS2 1.2.3.0 new `20 66 0C A5 14` 		01

___

`24 B3 D2 E5 A0 A3 00` Traction Control Range={float}0.01, {float}0.01, {byte}99 // (ECU			##1.2 (911cup) 0.9 (prev. 0.1)

																									##1.2 camaro 0, 0.099, 10
___

`20 63 9D 2B D2`       Traction Control Setting= {byte}9         // (ECU)																									##1.2 camaro 5


___

ams2 `20 6E DD B4 80` 		byte 45						1.2.1.0  50		1.2 (911cup) 40 (prev.45) 

___

ams2 `22 20 D5 05 AC`       {float}20.0     // CDF_UNKN_011	 1.2 (911cup) 3 (prev. 4)

___

aMS2 `24 8B 0A F9 4E A2` 	66 66 E6 3E (0.45)	66 66 66 3F	(0.9)		new code Traction Control after 1.2.1.4 

replaces ams2 `20 6E DD B4 80` 	and ams2 `22 20 D5 05 AC`


___

**AMS2  TC=47bytes**


___

`22 48 E1 7A 3F`       {byte}0	// CDF_UNKN_012

___

### shifting

`24 E0 D9 C8 5B 22`    UpshiftAlgorithm={float}0.99, {byte}0
___

`24 A6 8D 9C E2 A3 02` DownshiftAlgorithm={float}0.85, {float}0.8, {float}0.8

___

`24 30 43 CE 21 23 00` SteeringLockRange={float}34.0, {byte}0, {byte}0

___

`20 B7 C2 C5 7E`	 steering lock setting
___

`22 05 CF 7B 77`      ??Unknown={float}-1.0 
___

`22 52 FA 34 11`      ??Unknown={float}5.0			##1.2 (911cup) 7 (prev. 6.5)
___

`20 C8 F6 B3 E5` 	byte 02		ams 1.2.4.1 
___

### brakes

`24 A6 32 13 57 83 00` RearBrakeRange={byte}0, {float}0.01, {byte}100
___

`20 FD BA 64 73`       RearBrakeSetting={byte}45
___

`24 D0 00 38 59 A3 00` BrakePressureRange={float}0.00, {float}0.02, {byte}100

___

`20 DA BD B9 81`       BrakePressureSetting={byte}60
___

### handbrake / e-brake

`24 96 4B 29 B4 83 00` HandbrakeRange={byte}0, {float}0.01, {byte}100
15-19= 4
___

`20 52 30 1F D2`       HandbrakePressSetting={byte}60

___

`21 52 30 1F D2` same as above, but in integer
___

### AutoUpshift

`22 E3 5A 1D CA`    AutoUpshiftGripThresh={float}0.6			##1.2 (911cup) 0.5 (prev. 0.4)

___

`22 33 DE 0B C9`    AutoDownshiftGripThresh={float}0.6			##1.2 (911cup) 0.5 (prev. 0.4)

___

### TC grip

`24 07 F7 6E 47 A2` TractionControlGrip=({float}0.06, {float}0.16)
___

`24 25 5A FB 23 A2` TractionControlLevel=({float}0.06, {float}0.16}


!!! note 

    TractionControlGrip=
    TractionControlLevel=

    The first one is the 'aggressiveness' of the traction control system (how much wheelspin is allowed before TC engages). Forgive me but I can't specifically remember whether it's a higher value that allows for more wheelspin or a lower one... I believe (and only believe) that higher values mean the traction control system engages LATER, with lower values allowing the traction control to kick in earlier.

    The second value is the strength of the traction control. There are two values - the first is the strength on the LOW setting, the second is the strength of the HIGH setting.

    Essentially it's about balancing the numbers. If you have a car with low power at pretty much anything but peak revs, lower the efficiency to allow for smoother clutch engagement (0.79 in my case), make sure only low traction control is allowed on launch, and then balance the TractionControlGrip and TractionControlLevel figures.

    If you want a smooth launch without too much traction control interference, set the TC GRIP level to a lower number (0.5, for example, to allow it to kick in earlier) as well as setting the TC LEVEL to a low number (in my case, 0.07) - this essentially meant that the TC kicked in early to keep the car pointing straight and true on launch, but the low LEVEL meant it only had a slight effect.


## New to PC2

`24 24 9E 03 13 83 00` {byte}0, {float}0.01, {byte}100 // (ECU) ABS Strength Range		##1.2 (911cup) {byte}0, {float}0.1, {byte}100 (prev. {byte}0, {float}0.01, {byte}100)
																##1.2 camaro 0, 0.1, 10
___

`20 B2 BE 8E 7E` {byte}85 // (ECU) ABS Strength Setting			##1.2 (911cup) 0.8 (prev. 75) ##1.2 camaro 8


### AUTHENTIC DRIVING ASSIST OPTIONS

___

`20 BC 12 66 E0`   {byte}1   // "Authentic" ABSFourWheel assist
___

`20 BC 90 7F 88`   {byte}1   // "Authentic" TC Traction Control assist (disable/enable)
___

`20 F2 9A F8 10`   {byte}1   // "Authentic" SC Stability Control assist (disable/enable)

___

`20 FA CE 76 12`    {byte}1   //CDF_UNKN_016

___

`20 D5 DD 9C 9B`    {byte}1   //CDF_UNKN_017

___

`20 5B D1 F7 C8`    {byte}1   //CDF_UNKN_018






**ams2 section below is removed all the way down to ams2 section above is removed 379bytes**

___

`24 64 70 F5 FD 83 02` ({byte}0, {float}0.01, {float}200)  //CDF_UNKN_019

___

`20 34 76 EE E3`       {byte}25 //CDF_UNKN_020

___

`24 C8 1B AC AF 83 02` ({byte}0, {float}0.01, {float}200)  //CDF_UNKN_021

___

`20 61 5A 10 D6`       {byte}100 //CDF_UNKN_022

___

`24 D2 2F 18 AF 83 02` {byte}0, {float}0.01, {float}200)  //CDF_UNKN_023

___

`20 4D CA 34 17`       {byte}100      // CDF_UNKN_024

___

`24 B3 85 4E E0 83 02` {byte}0, {float}0.01, {float}200)  //CDF_UNKN_025

___

`20 6C E5 6E 1B`       {byte}100      // CDF_UNKN_026

___

`24 72 DE E1 17 83 02` {byte}0, {float}0.01, {float}200)  //CDF_UNKN_027

___

`20 99 3F 2A 3F`       {byte}100      // CDF_UNKN_028

___

`24 5A AE 27 42 83 02` {byte}0, {float}0.1, {float}20)  //CDF_UNKN_029

___

`20 25 F7 FA 9E`       {byte}1  //CDF_UNKN_030

___

`24 7A 49 7E 24 83 02` {byte}0, {float}0.1, {float}20)  //CDF_UNKN_031
Setting=(no value)

___

`28 99 85 60 E9`
___

`24 25 8E 3F 20 83 02` {byte}0, {float}0.1, {float}20)  //CDF_UNKN_032
Setting=(no value)

___

`28 3C 50 F8 D7` 
___

`24 6A 7D 42 63 83 02` {byte}0, {float}0.1, {float}20)  //CDF_UNKN_033
Setting=(no value)

___

`28 A9 F7 13 BD` 

___

`24 98 CA 4E 61 03 02` {byte}231, {byte}1, {byte}50 //CDF_UNKN_034
___

`20 77 E8 4F 5C` {byte}25

___

`24 09 DE B7 68 83 02` {byte}0, {float}0.01, {float}200)  //CDF_UNKN_035
Setting=(no value)

___

`28 FF 26 A3 2B`
___

`24 4B D5 82 72 83 02` {byte}0, {float}0.01, {float}200)  //CDF_UNKN_036
Setting=(no value)

___

`28 E5 12 C1 5D` 
___

`24 22 AC 0C 3A 83 02` {byte}0, {float}0.01, {float}200)  //CDF_UNKN_037

___

`20 17 7A 98 F5` {byte}100
___

`24 9F C7 1E D1 83 02` {byte}0, {float}0.01, {float}200)  //CDF_UNKN_039

___

`20 C7 D5 99 C6`       {byte}100 //CDF_UNKN_040

___

`24 67 8C A5 99 83 02` {byte}0, {float}0.01, {float}200)  //CDF_UNKN_041
Setting=(no value)

___

`28 BE A1 5C E1` 
___

`24 8E 47 3C 20 83 02` {byte}0, {float}0.1, {float}20)  //CDF_UNKN_042
Setting=(no value)

___

`28 ED 5F B5 79` 
___

`24 23 F0 43 98 83 02` {byte}0, {float}0.1, {float}20)  //CDF_UNKN_043
Setting=(no value)

___

`28 CA E1 FE 39` 
___

`24 E7 6C F5 65 83 02` {byte}0, {float}0.1, {float}20)  //CDF_UNKN_044

___

`28 31 6F DC CC` 

___

**ams2 section above is removed**





## Unknown Section `E0 3F 9E 45 98`

18 bytes

___

`20 D5 B3 F7 87` 01
___

`28 12 FA B3 EB` 



## DRIVELINE `E0 9E F7 67 84`



### clutch 

`22 1B CA 33 55` ClutchEngageRate={float}0.8  
___

ams `20 2E BF 88 AA`		01
___

 `20 1B CA 33 55`

___

`22 D3 1C F6 C6` ClutchInertia={float}0.0111
clutch itself + `main shaft from engine to gearbox, if applicable` + gearbox (when in gear - I'd take something like an average from inertia values from 3 to last gear and use it),

___

`22 2E 33 DB 70` ClutchTorque={float}500.0 how much torque can be transfered through clutch without slip
___

`28 7E 93 96 8C` //??

___

`22 9B 56 A1 18` ClutchFriction={float}10.00
- ClutchFriction: clutch itself (very small though) + gearbox friction (when in gear - I'd take something like an average from friction values from 3 to last gear and use it),


___

`22 36 6E 87 07` BaulkTorque={float}575.0

___

### shifting

`28 01 B6 85 A9` //?? might be related to shifting/clutch
___

`20 1D EA 4C 3D` SemiAutomatic={byte}1 // 1=sequential/semiauto & 0=h pattern

___

`20 74 73 B2 00` {byte}1        // ??related to shifting/clutch, CDF_UNKN_046 #######AURIEL

___

`20 B5 19 EF 5C` {byte}1	// ??related to shifting/clutch, 

___

`20 B9 E1 14 02` {byte}1	//??related to shifting/clutch auto clutch for semi automatic. 0 = clutch needs to be engaged (or 28 B9 E1 14 02).
___

`22 67 F7 AD 20` UpshiftDelay={float}0.1

___

`22 9D 78 9E C9` UpshiftClutchTime={float}0.1

___

ams `28 30 F2 DF 1E`

___

`22 07 50 AF 26` DownshiftDelay={float}0.3

___

`22 DB 0B FC 09` DownshiftClutchTime={float}0.3

___

### throttle blip

`22 3B 62 D3 1C` DownshiftBlipThrottle={float}0.7


___

Ams `20 3B 62 D3 1C`		byte 1


___

`26 94 35 F2 CB` {byte}9	// ??related to shifting/clutch
___

### final drive

`20 C1 EB DC 28` FinalDriveSetting={byte}29

___

`28 D6 71 85 B0` ReverseGearSetting // no value, which means zero
___

### number of gears + gears

`20 FF 0C 22 07` ForwardGears={byte}6

___

`28 F4 CC 2F 1D` GearOneSetting={byte}1

___

`20 8D 69 C2 DA` GearTwoSetting={byte}25

___

`20 C0 25 93 C3` GearThreeSetting={byte}42

___

`20 78 92 B7 5A` GearFourSetting={byte}57

___

`20 78 4E 48 36` GearFiveSetting={byte}71

___

`20 5F 2B A9 EE` GearSixSetting={byte}82

___

`20 49 EE 13 F6` GearSevenSetting={byte}6


___

ams2 `24 EE 7A B8 C2 03 00`	byte,byte,byte 0,1,2 

___

(rear diff of Ultima: in ams all non-existent diffs are removed))


## FRONT DIFFERENTIAL CODE

### spool

`24 39 9D AB CC 03 00` DiffFrontSpoolOption={byte},{byte},{byte} 
___

`28 54 97 E2 18`       DiffFrontSpoolSetting=   
___

15 bytes            

### geared        

`24 37 9D CD EF 03 00` DiffFrontGearedLsdOption={byte},{byte},{byte} 
___

`20 90 F8 1A C8`       DiffFrontGearedLsdSetting={byte} 
___

`24 8D A5 C0 7B 83 00` DiffFrontBiasRatioPowerRange={byte},{float},{byte} 
___

`20 8A F4 79 B8`       DiffFrontBiasRatioPowerSetting={byte} 
___

`24 1D 41 94 BF 83 00` DiffFrontBiasRatioCoastRange={byte},{float},{byte} 
___

`20 19 55 52 B5`       DiffFrontBiasRatioCoastSetting={byte}

54 bytes

### clutch

`24 41 E0 CD AE 03 00` DiffFrontClutchLsdOption={byte},{byte},{byte} 
___

`28 4F A8 A9 16`       DiffFrontClutchLsdSetting=                     
___

`24 F3 3F D6 98 03 00` DiffFrontClutchLsdPreloadRange={byte},{byte},{byte}
___

`20 2A F6 3D 02`       DiffFrontClutchLsdPreloadSetting={byte}
___

`24 CD 58 72 0A 03 00` DiffFrontClutchLsdPowerRampRange={byte},{byte},{byte}
___

`20 09 AD 40 97`       DiffFrontClutchLsdPowerRampSetting={byte}
___

`24 1E 69 4E 19 03 00` DiffFrontClutchLsdCoastRampRange={byte},{byte},{byte}
___

`20 05 A4 AB 0A`       DiffFrontClutchLsdCoastRampSetting={byte}
___

`24 89 07 4E C0 03 00` DiffFrontClutchLsd#ofClutchesRange={byte},{byte},{byte}
___

`20 AB FF 0F D6`       DiffFrontClutchLsd#ofClutchesSetting={byte}

77 bytes
79

-147-15=-162

### viscous

`24 FB 34 85 B9 03 00` DiffFrontViscousLsdOption={byte},{byte},{byte}
___

`28 81 B8 D8 08`       DiffFrontViscousLsdOptionSetting=                  
___

`24 EC C5 0A D7 03 00` DiffFrontViscousLockRange={byte},{byte},{byte}
___

`20 41 35 D2 61`       DiffFrontViscousLsdSetting={byte}

31 bytes

___

`24 68 29 C2 1B 03 00` DiffFrontRatchetingRange={byte},{byte},{byte}
___

`28 45 17 11 37`       DiffFrontRatchetingSetting

15 bytes

only geared = -138

## CENTER DIFFERENTIAL CODE

### spool

`24 B2 DD 18 AC 03 00` DiffCenterSpoolOption={byte},{byte},{byte}
___

`28 70 21 63 66`       DiffCenterSpoolSetting=       
                  
___

### geared

`24 5E D1 39 36 03 00` DiffCenterGearedLsdOption={byte},{byte},{byte}
___

`28 BF 2A 7E 62`       DiffCenterGearedLsdSetting=
___

`24 E1 71 4A 7B 83 00` DiffCenterBiasRatioPowerRange={byte},{float},{byte} 
___

`28 66 5F E2 43`       DiffCenterBiasRatioPowerSetting=
___

`24 3A 92 1E B0 83 00` DiffCenterBiasRatioCoastRange={byte},{float},{byte} 
___

`28 FA EC CB BF`       DiffCenterBiasRatioCoastSetting={byte}

___

### clutch

`24 69 82 0A 41 03 00` DiffCenterClutchLsdOption={byte},{byte},{byte}
___

`20 01 A1 6B F9`       DiffCenterClutchLsdSetting={byte}
___

`24 73 9E 1C 3E 03 00` DiffCenterClutchLsdPreloadRange={byte},{byte},{byte}
___

`20 9F F9 B4 26`       DiffCenterClutchLsdPreloadSetting={byte}
___

`24 71 52 76 47 03 00` DiffCenterClutchLsdPowerRampRange={byte},{byte},{byte}
___

`20 08 15 99 DF`       DiffCenterClutchLsdPowerRampSetting={byte}
___

`24 97 AE 26 09 03 00` DiffCenterClutchLsdCoastRampRange={byte},{byte},{byte}
___

`20 78 3A DD DA`       DiffCenterClutchLsdCoastRampSetting={byte}
___

`24 94 D1 29 37 03 00` DiffCenterClutchLsd#ofClutchesRange={byte},{byte},{byte}
___

`20 72 19 2E B0`       DiffCenterClutchLsd#ofClutchesSetting={byte}

___

### viscous

`24 AF 28 23 3F 03 00` DiffCenterViscousLsdOption={byte},{byte},{byte}
___

`28 6A 83 DD EA`       DiffCenterViscousLsdOptionSetting=                  
___

___

`24 C4 A7 09 F9 03 00` DiffCenterViscousLockRange={byte},{byte},{byte}
___

`20 B2 B4 67 3D`       DiffCenterViscousLsdSetting={byte}

___

### ratcheting

`24 AB 12 1A 20 03 00` DiffCenterRatchetingRange={byte},{byte},{byte}
___

`28 74 65 6C DA`       DiffCenterRatchetingSetting=
___

### power balance

`24 05 9C B8 6E 83 00` RearPowerBalance={byte},{float},{byte}
___

`20 5A D1 7D 93`       RearPowerBalanceSettinh={byte}

## REAR DIFFERENTIAL CODE

### spool

`24 EE 7A B8 C2 03 00` DiffRearSpoolOption={byte},{byte},{byte} // Rear Diff Spool Option off/on
___

`28 5C 91 A5 85`       DiffRearSpoolSetting=                    // Rear Diff Spool setting.  No byte in code means zero (off)

___

### geared

`24 9B E9 BD BB 03 00` DiffRearGearedLsdOption={byte},{byte},{byte}       // Rear Diff Geared LSD Option off/on
___

`20 DC 47 B2 CE`       DiffRearGearedLsdSetting={byte}                    // Rear Diff Geared LSD setting.
___

`24 25 9E 18 D6 83 00` DiffRearBiasRatioPowerRange={byte},{float},{byte}  // Rear Diff Bias Ratio Pwr(accel) Range
___

`20 0A C0 52 BA`       DiffRearBiasRatioPowerSetting={byte}               // 
___

`24 29 7D 8B D8 83 00` DiffRearBiasRatioCoastRange={byte},{float},{byte}  // Rear Diff Bias Ratio Coast(decel) Range
___

`20 76 86 1F CA`       DiffRearBiasRatioCoastSetting={byte}               // Rear Diff Bias Ratio Coast(decel) Setting

-66
-68Auriel
-69



### clutch lsd

`24 04 80 3B 71 03 00` DiffRearClutchLsdOption={byte},{byte},{byte}       // Rear Diff Clutch LSD Option (off/on)
___

`20 18 9A 45 B8`       DiffRearClutchLsdSetting={byte}                    // Rear Diff Clutch LSD Setting
___

#### preload

`24 AE 9E A6 41 03 00` DiffRearClutchLsdPreloadRange={byte},{byte},{byte} // Rear Diff Clutch LSD Preload Range
___

ams2 `24 AE 9E A6 41 83 02`  DiffRearClutchLsdPreloadRange={byte},{float},{float} 


!!! attention

    Fix base value by setting to zero.  Then change max range and setting values.

___

`20 67 71 FD BF`       DiffRearClutchLsdPreloadSetting={byte}                 // Rear Diff Clutch LSD Preload Setting
___

#### power

`24 16 B6 6F 96 03 00` DiffRearClutchLsdPowerRampRange={byte},{byte},{byte}   // Rear Diff Clutch LSD Pwr(accel) Ramp Range
___

`20 81 2D 38 81`       DiffRearClutchLsdPowerRampSetting={byte}               // Rear Diff Clutch LSD Pwr(Accel) Ramp Setting
___

#### coast

`24 A6 F6 18 10 03 00` DiffRearClutchLsdCoastRampRange={byte},{byte},{byte}   // Rear Diff Clutch LSD Coast(decel) Ramp Range
___

`20 71 BB 6F 28`       DiffRearClutchLsdCoastRampSetting={byte}               // Rear Diff Clutch LSD Coast(decel) Ramp Setting
___

#### clutches

`24 1C 63 D7 1C 03 00` DiffRearClutchLsd#ofClutchesRange={byte},{byte},{byte} // Rear Diff Clutch LSD # of Clutches Range
___

`20 D9 D4 45 63`       DiffRearClutchLsd#ofClutchesSetting={byte}             // Rear Diff Clutch LSD # of Clutches Setting

-45A

### Viscous	

`24 F4 97 51 CF 03 00` DiffRearViscousLsdOption={byte},{byte},{byte} // Rear Diff Viscous LSD Option (off/on)
___

`28 5A 2F 78 7C`       DiffRearViscousLsdOptionSetting=              // Rear Diff Viscous LSD Setting
___

`24 1E 6F 8D B1 03 00` DiffRearViscousLockRange={byte},{byte},{byte} // Note: 2nd value is x50. So "1" x50 = x50nm multiplier per ViscousLsdSetting
___

`20 E0 EE A4 80`       DiffRearViscousLsdSetting={byte}              // a setting of "4" yields 4 x50 = 200nm lock

___

### ratcheting

`24 A6 12 F9 62 03 00` DiffRearRatchetingOption={byte},{byte},{byte} // Rear Diff Ratcheting Option (on/off)
___

`28 F1 8A 0F 35`       DiffRearRatchetingSetting=                    // Rear Diff Ratcheting Setting.  No byte in code, which means zero(off)

only clutch lsd = -112 || -116 || -118 || -114 || -115 || -116 || -113 || 194 -479=285

## AI DIFFERENTIALS (Patch 1.4)

!!! note "AI Diffs added in patch 1.4"

    Reiza have added differential setting for AI in patch 1.4. this works well for all AI cars and aids their cornering:


`24 1D F5 6C 5C 83 00`: `00`, `0A D7 23 3C`, `64` 

_______

`20 53 D4 19 A9`: `19` 
_______

`24 F2 FF 04 F5 83 00`: `00`, `0A D7 23 3C`, `64`
_______

`20 79 F8 06 9F`: `28` 
_______

`24 05 1D 5E 8B 03 00`: `00`, `0A`, `64`
_______

`20 8B 90 E1 61`: `05`
_______


The above can be translated into:

- 0, 0.01, 100 (range)
- 25 (setting)
- 0, 0.01, 100 (range)
- 40 (setting)
- 0, 10, 100 (range)
- 5 (setting)


You can just insert this code (54 bytes):

```
24 1D F5 6C 5C 83 00 00 0A D7 23 3C 64 20 53 D4 19 A9 19 24 F2 FF 04 F5 83 00 00 0A D7 23 3C 64 20 79 F8 06 9F 28 24 05 1D 5E 8B 03 00 00 0A 64 20 8B 90 E1 61 05
```

###  shifting 

`22 D0 6B 69 F2` {float}1000.00 //RPM Governor for semi-auto gearchange. 1000 is added to idle rpm (shift must occur at or below ~5000 rpm) add 10000 to have semi-auto dual clutch engage 1st gear from idle
___

`22 69 56 28 63` {float}50.0    //??relates to shifting/clutch,CDF_UNKN_049

___

`22 F9 8C C1 66` {float}0.5     // Lift & Shift or Full throttle shift.  Percentage of throttle allowed for upshift (1.0 = 100% or full throttle)

___

`22 2E 33 BD 4C` {float}0.25     //??relates to shifting/clutch,CDF_UNKN_051

___

`22 2D 62 77 4E` {float}0.001  //??relates to shifting/clutch,CDF_UNKN_052

___

`22 C4 F7 E7 93` {float}0.001  //??relates to shifting/clutch,CDF_UNKN_053



## NEW SECTION FOR PC2 `E0 12 BC 36 7D` 

ams2 = 18 bytes total only 

___

`24 09 A8 D0 1D 03 02` {byte}0, {byte}0, {float}-0.25 

pc2 (21 bytes)


`E0 12 BC 36 7D` 
___

`22 2C 1D 1F 2F` {float}1.3 
___

`21 D1 35 A6 C8` {integer}1000 
___

`21 2D D9 FE 0F` {integer}1000 
___

`24 09 A8 D0 1D 03 02` {byte}0, {byte}0, {float}0.15 
___

`22 37 F3 B5 B2` {float}0.9 
___

`22 AF AB 0F 8E` {float}1.0 
___

`21 42 FD F1 BF` {integer}500 
___

`21 AE BE 7F FA` {integer}200
___

`24 3F BF 68 D5 03 02` {byte}0, {byte}0, {float}-0.45 
___

`22 6A BC 43 1B` {float}0.9

57


## `E0 7D 16 E2 9F` = FRONT LEFT CORNER

2284 -2615=331

**FRONT LEFT**

___

`22 B3 D8 21 F7` BumpTravel={float}-0.00
___


`22 17 7B 8A 89` ReboundTravel={float}-0.18

___

`21 7F C6 F8 41` BumpStopSpring={integer}150000 // ***hex string dictating integer data**
___

`22 7F C6 F8 41` BumpStopSpring={float}150000.0 //***Same as above but with float data**

___

`22 CB 91 F1 63` BumpStopRisingSpring={float}4000000

___

AM2 `20 23 57 04 E9` 		byte 02

___

`22 71 74 6E EB` {float}50.0

___

`22 DD D6 E1 75` {float}20.0

___

`22 70 02 6D 2B` BumpStageTwo={float}0.09
AMS2 0.4

___

`22 1F 7D 2D 8E` ReboundStageTwo={float}-0.09

___

### friction and spin

`22 7F 0E 4C A5` FrictionTorque={float}9.5

- FrictionTorque (for driven wheels): (<gearbox friction when in N> / 2) + (<diff friction> / 2) + ball bearing friction (loaded)

- FrictionTorque (for non-driven wheels): just ball bearing friction (loaded) 

___

`22 57 51 0F 51` SpinInertia={float}1.35

- SpinInertia (for driven wheels): `main shaft from gearbox to diff, if applicable` + (differential inertia/2) + halfaxle + wheel + disc bell

- SpinInertia (for non-driven wheels): wheel + disc bell

___

AMS2 `22 DF D4 F6 3D` float

in 1.3.3.1 changed to `22 25 99 CD 41`

___

`22 C9 2A 02 BB` {float}x.xx ??unknown
___

`28 C9 2A 02 BB` unknown like above but with zero value
___

### pushrod

`24 BE B9 BB AB A3 02` PushrodSpindle=({float}-0.10, {float}-0.150, {float}0.000)


___

`24 19 11 EA CE A3 02` PushrodBody=({float}-0.10, {float}0.320, {float}0.000)
___

### camber

`24 24 E1 9C B2 A3 00` CamberRange=({float}-3.5, {float}0.1, {byte}60)

___

`20 C1 72 F3 09`       CamberSetting={byte}20

___

### tire pressure

`24 A6 DA C6 BF A3 00` PressureRange={float}180.0, {float}1.0, {byte}106

___

`20 BB 96 16 F6`       PressureSetting={byte}50

___

### bump stop

`24 BB 59 2C D5 83 00` PackerRange / bump stop=({byte}0, {float}0.001, {byte}30)

___

`20 D8 7D 17 14`       PackerSetting / bump stop={byte}1

___

### Springs

`22 44 49 5D 88`       SpringMult={float}1.0								7D E0 90 64 suspension motion
___

`24 A5 12 3D 0D A3 00` SpringRange=({float}60000.0, {float}5000.0, {byte}6)

___

`20 CE AA 7A 97`       SpringSetting={byte}1

___

### ride height

`24 D7 C6 0D 7A A3 00` RideHeightRange=({float}0.105, {float}-0.0055, {byte}10)

___

`20 6D 04 94 05`       RideHeightSetting={byte}1

___

### dampers

`22 51 37 41 53`       DamperMult={float}1.0
___

#### slow 

`24 0C 43 D9 D0 A3 00` SlowBumpRange=({float}3000.0, {float}300.0, {byte}6)
___

`20 D1 9E 2C 0A`       SlowBumpSetting={byte}1

___

#### fast

`24 30 89 EC 3D A3 00` FastBumpRange=({float}1500.0, {float}200.0, {byte}6)
___

`20 38 38 25 87`       FastBumpSetting={byte}1
___

#### slow rebound

`24 BC C0 A2 91 A3 00` SlowReboundRange=({float}6000.0, {float}300.0, {byte}6)
___

`20 22 73 D7 81`       SlowReboundSetting={byte}1

___

#### fast rebound

`24 BC 6D 0E F7 A3 00` FastReboundRange{float}4400, {float}250, {byte}16
___

`20 B8 B0 02 2E`       FastReboundSetting={byte}10

___

`24 5E 57 34 B3 13 00` BumpTransitionRange={integer}XXXX, {byte}x, {byte}x
___

`20 36 84 0B 9B`       BumpTransitionSetting={byte}x
___

`24 5C 47 9E 9E 13 00` ReboundTransitionRange{integer}XXXX, {byte}x, {byte}x 
___

`20 D6 CD E0 06`       ReboundTransitionSetting={byte}x
___

### Brakes

`24 09 7A D2 4B 23 00` BrakeDiscRange={float}0.035, {byte}0, {byte}0

ams2 911 gt3 cup2: 0.05, 0.005, 10. 	Mclaren 0.032, 0.005, 10. Camaro SS 0.03, 0, 0.

___

ams2 `28 95 7D FB 9D`
___

`24 ED 3F C2 21 03 00` BrakePadRange=({byte}0, {byte}1, {byte}5)
___

`20 64 D7 A9 E6`       BrakePadSetting={byte}2
___

`22 B9 CF 18 D1` BrakeDiscInertia={float}0.001
___

#### temps

`22 AB 02 4B 3C` BrakeOptimumTemp={float}500.0
___

ams2 `24 AB 02 4B 3C 52` BrakeOptimumTemp=integ, integ. 400, 650


___

`22 02 3F 01 F1` {float}0.34	//CDF_UNKN_059
ams2 0.75

___

`22 45 81 36 93` {float}0.95	//CDF_UNKN_060
ams 0.9

___

`21 E7 95 A8 D0` {float}900.0
Ams2 500, 

___

`21 D0 03 18 55` {float}950.0
ams 900,

___

#### wear

`22 1E E5 B6 4C`    BrakeWearRate={float}3e-11
ams 6e-11

___

`24 BD 59 C8 42 A2` BrakeFailure={float}0.01, {float}0.003

___

#### torque

`22 4B A4 81 7A`    BrakeTorque={float}3200

___

#### heating and cooling

`22 6E A6 0D FB`    BrakeHeating={float}0.000275

___

`24 1C D5 5C 78 A2` BrakeCooling({float}0.007, {float}7e-06)

___

`22 A2 67 26 E9`    BrakeDuctCooling={float}5e-07

___

new in ams2

`22 6C 82 E4 02` = 2.69
___

`22 EE 67 FD 55` = 0.26
___

`24 5D 9E 9A 9F A2` = 0.0014, 5.1e-05
___

`22 CE A0 75 6B` = 2e-06

193-191x2
193-194
pc2 563 ams2 576

150-198
195-198
191-198 

				
## FRONT RIGHT	E0 D6 53 79 08

`22 B3 D8 21 F7` BumpTravel={float}-0.00

`22 17 7B 8A 89` ReboundTravel={float}-0.18

`21 7F C6 F8 41` BumpStopSpring={integer}150000 // ***hex string dictating integer data**
`22 7F C6 F8 41` BumpStopSpring={float}150000.0 //***Same as above but with float data**

`22 CB 91 F1 63` BumpStopRisingSpring={float}4000000

AMS2 `20 23 57 04 E9`	byte 2 

`22 71 74 6E EB` {float}50.0

`22 DD D6 E1 75` {float}20.0

`22 70 02 6D 2B` BumpStageTwo={float}0.09

`22 1F 7D 2D 8E` ReboundStageTwo={float}-0.09

`22 7F 0E 4C A5` FrictionTorque={float}9.5

`22 57 51 0F 51` SpinInertia={float}1.35

AMS2 `22 DF D4 F6 3D` float

`22 C9 2A 02 BB` {float}x.xx ??unknown
`28 C9 2A 02 BB` unknown like above but with zero value
`24 BE B9 BB AB A3 02` PushrodSpindle=({float}0.10, {float}-0.150, {float}0.000)

`24 19 11 EA CE A3 02` PushrodBody=({float}0.10, {float}0.320, {float}0.000)
`24 24 E1 9C B2 A3 00` CamberRange=({float}-3.5, {float}0.1, {byte}60)

`20 C1 72 F3 09`       CamberSetting={byte}20

`24 A6 DA C6 BF A3 00` PressureRange={float}180.0, {float}1.0, {byte}106

`20 BB 96 16 F6`       PressureSetting={byte}50

`24 BB 59 2C D5 83 00` PackerRange=({byte}0, {float}0.001, {byte}30)

`20 D8 7D 17 14`       PackerSetting={byte}1

`22 44 49 5D 88`       SpringMult={float}1.0

AMS2 `24 B5 12 D4 FA 13 00`	
AMS2 `28 59 B6 5E C0`
AMS2 `22 C3 AF F6 51`

`24 A5 12 3D 0D A3 00` SpringRange=({float}60000.0, {float}5000.0, {byte}6)

`20 CE AA 7A 97`       SpringSetting={byte}1

`24 D7 C6 0D 7A A3 00` RideHeightRange=({float}0.105, {float}-0.0055, {byte}10)

`20 6D 04 94 05`       RideHeightSetting={byte}1

`22 51 37 41 53`       DamperMult={float}1.0
`24 0C 43 D9 D0 A3 00` SlowBumpRange=({float}3000.0, {float}300.0, {byte}6)
`20 D1 9E 2C 0A`       SlowBumpSetting={byte}1

`24 30 89 EC 3D A3 00` FastBumpRange=({float}1500.0, {float}200.0, {byte}6)
`20 38 38 25 87`       FastBumpSetting={byte}1

`24 BC C0 A2 91 A3 00` SlowReboundRange=({float}6000.0, {float}300.0, {byte}6)
`20 22 73 D7 81`       SlowReboundSetting={byte}1

`24 BC 6D 0E F7 A3 00` FastReboundRange{float}4400, {float}250, {byte}16

`20 B8 B0 02 2E`       FastReboundSetting={byte}10

AMS2 `28 D1 9E 2C 0A` 
AMS2 `28 38 38 25 87` 
AMS2 `28 22 73 D7 81` 
AMS2 `28 B8 B0 02 2E`

`24 5E 57 34 B3 13 00` BumpTransitionRange={integer}XXXX, {byte}x, {byte}x
`20 36 84 0B 9B`       BumpTransitionSetting={byte}x
`24 5C 47 9E 9E 13 00` ReboundTransitionRange{integer}XXXX, {byte}x, {byte}x 
`20 D6 CD E0 06`       ReboundTransitionSetting={byte}x
`24 09 7A D2 4B 23 00` BrakeDiscRange={float}0.035, {byte}0, {byte}0

`24 ED 3F C2 21 03 00` BrakePadRange=({byte}0, {byte}1, {byte}5)
`20 64 D7 A9 E6`       BrakePadSetting={byte}2
`22 B9 CF 18 D1` BrakeDiscInertia={float}0.001

`22 AB 02 4B 3C` BrakeOptimumTemp={float}500.0
`22 02 3F 01 F1` {float}0.34		//CDF_UNKN_059

`22 45 81 36 93` {float}0.95		//CDF_UNKN_060

`22 E7 95 A8 D0` {float}900.0

`22 D0 03 18 55` {float}950.0

`22 1E E5 B6 4C`    BrakeWearRate={float}3e-11

`24 BD 59 C8 42 A2` BrakeFailure={float}0.01, {float}0.003

`22 4B A4 81 7A`    BrakeTorque={float}3200

`22 6E A6 0D FB`    BrakeHeating={float}0.000275

`24 1C D5 5C 78 A2` BrakeCooling({float}0.007, {float}7e-06)

`22 A2 67 26 E9`    BrakeDuctCooling={float}5e-07


new in ams2
 
`22 6C 82 E4 02` = 2.69
`22 EE 67 FD 55` = 0.26
`24 5D 9E 9A 9F A2` = 0.0014, 5.1e-05
`22 CE A0 75 6B` = 2e-06




## REAR LEFT		E0 BF 9F 5B A2

`22 B3 D8 21 F7` BumpTravel={float}-0.00

`22 17 7B 8A 89` ReboundTravel={float}-0.2

`21 7F C6 F8 41` BumpStopSpring={integer}150000 // ***hex string dictating integer data**
`22 7F C6 F8 41` BumpStopSpring={float}150000.0 //***Same as above but with float data**

`22 CB 91 F1 63` BumpStopRisingSpring={float}4000000

`22 71 74 6E EB` {float}50.0

`22 DD D6 E1 75` {float}20.0

`22 70 02 6D 2B` BumpStageTwo={float}0.09

`22 1F 7D 2D 8E` ReboundStageTwo={float}-0.09

`22 7F 0E 4C A5` FrictionTorque={float}12.5

`22 57 51 0F 51` SpinInertia={float}1.427

AMS2 `22 DF D4 F6 3D` float

`22 C9 2A 02 BB` {float}x.xx ??unknown
`28 C9 2A 02 BB` unknown like above but with zero value
`24 BE B9 BB AB A3 02` PushrodSpindle=({float}-0.10, {float}-0.150, {float}0.000)

`24 19 11 EA CE A3 02` PushrodBody=({float}-0.10, {float}0.320, {float}0.000)
`24 24 E1 9C B2 A3 00` CamberRange=({float}-3.5, {float}0.1, {byte}60)

`20 C1 72 F3 09`       CamberSetting={byte}25

`24 A6 DA C6 BF A3 00` PressureRange={float}180.0, {float}1.0, {byte}106

`20 BB 96 16 F6`       PressureSetting={byte}50

`24 BB 59 2C D5 83 00` PackerRange=({byte}0, {float}0.001, {byte}30)

`20 D8 7D 17 14`       PackerSetting={byte}1

`22 44 49 5D 88`       SpringMult={float}1.0
`24 A5 12 3D 0D A3 00` SpringRange=({float}50000.0, {float}4166.0, {byte}6)

`20 CE AA 7A 97`       SpringSetting={byte}1

`24 D7 C6 0D 7A A3 00` RideHeightRange=({float}0.11, {float}-0.0055, {byte}10)

`20 6D 04 94 05`       RideHeightSetting={byte}1

`22 51 37 41 53`       DamperMult={float}1.0
`24 0C 43 D9 D0 A3 00` SlowBumpRange=({float}2500.0, {float}300.0, {byte}6)
`20 D1 9E 2C 0A`       SlowBumpSetting={byte}1

`24 30 89 EC 3D A3 00` FastBumpRange=({float}1200.0, {float}200.0, {byte}6)
`20 38 38 25 87`       FastBumpSetting={byte}1

`24 BC C0 A2 91 A3 00` SlowReboundRange=({float}5000.0, {float}300.0, {byte}6)
`20 22 73 D7 81`       SlowReboundSetting={byte}1

`24 BC 6D 0E F7 A3 00` FastReboundRange{float}2500, {float}250, {byte}16
`20 B8 B0 02 2E`       FastReboundSetting={byte}10
`24 5E 57 34 B3 13 00` BumpTransitionRange={integer}XXXX, {byte}x, {byte}x
`20 36 84 0B 9B`       BumpTransitionSetting={byte}x
`24 5C 47 9E 9E 13 00` ReboundTransitionRange{integer}XXXX, {byte}x, {byte}x 
`20 D6 CD E0 06`       ReboundTransitionSetting={byte}x
`24 09 7A D2 4B 23 00` BrakeDiscRange={float}0.032, {byte}0, {byte}0

`24 ED 3F C2 21 03 00` BrakePadRange=({byte}0, {byte}1, {byte}5)
`20 64 D7 A9 E6`       BrakePadSetting={byte}2
`22 B9 CF 18 D1` BrakeDiscInertia={float}0.001
`22 AB 02 4B 3C` BrakeOptimumTemp={float}500.0
`22 02 3F 01 F1` {float}0.34		//CDF_UNKN_059

`22 45 81 36 93` {float}0.95		//CDF_UNKN_060

`22 E7 95 A8 D0` {float}900.0

`22 D0 03 18 55` {float}950.0

`22 1E E5 B6 4C`    BrakeWearRate={float}3e-11

`24 BD 59 C8 42 A2` BrakeFailure={float}0.01, {float}0.003

`22 4B A4 81 7A`    BrakeTorque={float}2200

`22 6E A6 0D FB`    BrakeHeating={float}0.000275

`24 1C D5 5C 78 A2` BrakeCooling({float}0.007, {float}7e-06)

`22 A2 67 26 E9`    BrakeDuctCooling={float}5e-07

new in ams2

`22 6C 82 E4 02` = 2.91
`22 EE 67 FD 55` = 0.31
`24 5D 9E 9A 9F A2` = 0.0015, 3.4e-05
`22 CE A0 75 6B` = 1.3e-06




## REAR RIGHT		E0 CF F2 C9 32

`22 B3 D8 21 F7` BumpTravel={float}-0.00

`22 17 7B 8A 89` ReboundTravel={float}-0.2

`21 7F C6 F8 41` BumpStopSpring={integer}150000 // ***hex string dictating integer data**
`22 7F C6 F8 41` BumpStopSpring={float}150000.0 //***Same as above but with float data**

`22 CB 91 F1 63` BumpStopRisingSpring={float}4000000

`22 71 74 6E EB` {float}50.0

`22 DD D6 E1 75` {float}20.0

`22 70 02 6D 2B` BumpStageTwo={float}0.09

`22 1F 7D 2D 8E` ReboundStageTwo={float}-0.09

`22 7F 0E 4C A5` FrictionTorque={float}12.5

`22 57 51 0F 51` SpinInertia={float}1.427

AMS2 `22 DF D4 F6 3D` float

`22 C9 2A 02 BB` {float}x.xx ??unknown
`28 C9 2A 02 BB` ?? unknown like above but with zero value
`24 BE B9 BB AB A3 02` PushrodSpindle=({float}0.10, {float}-0.150, {float}0.000)

`24 19 11 EA CE A3 02` PushrodBody=({float}0.10, {float}0.320, {float}0.000)
`24 24 E1 9C B2 A3 00` CamberRange=({float}-3.5, {float}0.1, {byte}60)

`20 C1 72 F3 09`       CamberSetting={byte}25

`24 A6 DA C6 BF A3 00` PressureRange={float}180.0, {float}1.0, {byte}106

`20 BB 96 16 F6`       PressureSetting={byte}50

`24 BB 59 2C D5 83 00` PackerRange=({byte}0, {float}0.001, {byte}30)

`20 D8 7D 17 14`       PackerSetting={byte}1

`22 44 49 5D 88`       SpringMult={float}1.0
`24 A5 12 3D 0D A3 00` SpringRange=({float}50000.0, {float}4166.0, {byte}6)

`20 CE AA 7A 97`       SpringSetting={byte}1

`24 D7 C6 0D 7A A3 00` RideHeightRange=({float}0.11, {float}-0.0055, {byte}10)

`20 6D 04 94 05`       RideHeightSetting={byte}1

`22 51 37 41 53`       DamperMult={float}1.0
`24 0C 43 D9 D0 A3 00` SlowBumpRange=({float}2500.0, {float}300.0, {byte}6)
`20 D1 9E 2C 0A`       SlowBumpSetting={byte}1

`24 30 89 EC 3D A3 00` FastBumpRange=({float}1200.0, {float}200.0, {byte}6)
`20 38 38 25 87`       FastBumpSetting={byte}1

`24 BC C0 A2 91 A3 00` SlowReboundRange=({float}5000.0, {float}300.0, {byte}6)
`20 22 73 D7 81`       SlowReboundSetting={byte}1

`24 BC 6D 0E F7 A3 00` FastReboundRange{float}2500, {float}250, {byte}16
`20 B8 B0 02 2E`       FastReboundSetting={byte}10
`24 5E 57 34 B3 13 00` BumpTransitionRange={integer}XXXX, {byte}x, {byte}x
`20 36 84 0B 9B`       BumpTransitionSetting={byte}x
`24 5C 47 9E 9E 13 00` ReboundTransitionRange{integer}XXXX, {byte}x, {byte}x 
`20 D6 CD E0 06`       ReboundTransitionSetting={byte}x
`24 09 7A D2 4B 23 00` BrakeDiscRange={float}0.032, {byte}0, {byte}0

`24 ED 3F C2 21 03 00` BrakePadRange=({byte}0, {byte}1, {byte}5)
`20 64 D7 A9 E6`       BrakePadSetting={byte}2
`22 B9 CF 18 D1` BrakeDiscInertia={float}0.001

`22 AB 02 4B 3C` BrakeOptimumTemp={float}500.0
AMS2 `24 AB 02 4B 3C 52` BrakeOptimumTemp={integ}400.0, {integ}650.0

`22 02 3F 01 F1` {float}0.34		//CDF_UNKN_059

`22 45 81 36 93` {float}0.95		//CDF_UNKN_060

`22 E7 95 A8 D0` {float}900.0

`22 D0 03 18 55` {float}950.0

`22 1E E5 B6 4C`    BrakeWearRate={float}3e-11

`24 BD 59 C8 42 A2` BrakeFailure={float}0.01, {float}0.003

`22 4B A4 81 7A`    BrakeTorque={float}2200

`22 6E A6 0D FB`    BrakeHeating={float}0.000275

`24 1C D5 5C 78 A2` BrakeCooling({float}0.007, {float}7e-06)

`22 A2 67 26 E9`    BrakeDuctCooling={float}5e-07


new in ams2

`22 6C 82 E4 02` = 2.91

`22 EE 67 FD 55` = 0.31

`24 5D 9E 9A 9F A2` = 0.0015, 3.4e-05

`22 CE A0 75 6B` = 1.3e-06




## end of 4 corners `E0 91 FD 30 91` 

!!! attention

    After the 4 corners PC2 has the section that counts 324 bytes. This section has been removed in AMS2


!!! note

    when using road car chassis to make a race car, automatic tire selection will not work, unless you swap 6 bytes at the following address EDIT: only change the first byte from `2F` to `35`

`84 4A 54 49 9B 4F` automatic tire selection for race cars (slicks, wets, etc.): the following 6 bytes enable auto tires `35 E6 5F C3 48 15`. EDIT: only change the first byte from e.g. `2F` to `35`


### footer bytes. 

!!! note

    the total number of bytes varies; the number is defined in the third register at the top of the file: 0x0020-0x0023


-324

### end data examples

- camaro	 `84 4A 54 49 9B 4F` 	`30 C6 6A 91 0D`

- mclaren	 `84 54 5E 4B 86 3A` 	`0F 83 79 86 4C 3F 28`

- caymgt4	 `84 51 5A 5D 8B 4F` 	`35 E6 5F C3 5F 28 69 29 0D`

- por cup2 `84 51 5A 5D 8B 4F` 	`35 E6 5F C3 5F 28 69 29 0D`

- porsche R	 `84 4A 54 49 9B 4F` 	`2F E6 5F C3 5F 28 69 29 0D`



<script src="https://hypothes.is/embed.js" async></script>