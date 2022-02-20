# statistics mrdf


## About

Project CARS 2 statistics MRDF translation by **JDougNY**

___

AMS2 revisions by **GvsE**

Version 1.0 - 13/2/2022 - Initial Release 

This translation provides the common address locations for statistics data used in the game.

___

## Data

0x20-0x23 = 0000C342(Little Endian)= 97.50 // (Float) Top Speed expressed in Meters per Second.  Formula is (MPH * 0.447)

___

0x24-0x27 = 66662640(Little Endian)= 2.60 // (Float) Accel 0-100kmh

___

0x28-0x2B = 01000000(Little Endian)= 1 // (Decimal) Gear needed to reach 100kmh

___

0x2C-0x2F = 7AC7D940(Little Endian)= 6.8056 // (Float) Accel 0-160kmh

___

0x30-0x33 = 03000000(Little Endian)= 3 // (Decimal) Gear needed to reach 160kmh

___

0x34-0x37 = E17A0440(Little Endian)= 2.07 // (Float) Braking 100-0kmh

___

0x38-0x3B = 66668241(Little Endian)= 16.3 // (Float) Performance Rating (P.I.).  Not used in the game, though.

___

0x3C-0x3F = 00C08544(Little Endian)= 1070.0 // (Float) Mass in KG

___

0x40-0x43 = 06000000(Little Endian)= 6 // (Decimal) Number of Gears in transmission

___

0x44-0x47 = E79A0644(Little Endian)= 538.4 // (Float) Torque in lb-ft

___

0x48-0x4B = 00004844(Little Endian)= 800.0 // (Float) HP using American SAE Net (not the higher metric rating of CV or PS)

___

0x4C-0x4F = 00000000(Little Endian)= 0 // (Decimal) Drivetrain type (see below)

!!! note

    Drivetrain type for address 0x4C***
    
    00 = RWD
    
    01 = AWD
    
    02 = FWD


___

0x50-0x53 = 00000000(Little Endian)= 0 // Boost Type, 0=Natural Aspiration, 1=Supercharged, 2=Turbo

___

0x54-0x57 = 00000000(Little Endian)= 0 // Aspiration, 0=Natural Aspiration, 1=boosted

___

0x58-0x5B = 95D49B40(Little Endian)= 4.87 // (Float) Handling performance

___

0x5C-0x5F = 00000000(Little Endian)= 0 // ??Unknown??

___

0x60-0x63 = 00000000(Little Endian)= 0 // ??Unknown??

___

0x64-0x67 = 04000000(Little Endian)= 4 // (Decimal) Engine type (see below)

!!! note

    Engine Type for address 0x64

    00 = don't use

    01 = V6 

    02 = V8

    03 = V10

    04 = V12
    
    05 = Straight 4
    
    06 = Straight 5
    
    07 = Straight 6
    
    08 = Rotary 2
    
    09 = Rotary 3
    
    0A = Flat 4
    
    0B = Flat 6
    
    0C = W16
    
    0D = W12
    
    0E = Single Cylinder
    
    0F = Twin Cylinder


___

0x68-0x6B = 05000000(Little Endian)= 5 // (Decimal) Tier Level

___

0x6C-0x6F = AC8B5BBD(Little Endian)= -0.0536

___

0x70-0x73 = FAEDEB3A(Little Endian)= 0.0018

___

0x74-0x77 = 00000080(Little Endian)=

___

0x78-0x7B = CDCC4C3C(Little Endian)= 0.0125

___

0x7C-0x7F = B37B723C(Little Endian)= 0.0148

0x80-0x83 = 00000000(Little Endian)= 0 // (Float) Body height adjust (in Meters) when viewing car in menus.  Does not affect body height on the track.

___

0x84-0x87 = 986E3240(Little Endian)= 2.788 // (Float) Wheelbase in Meters

___

0x88-0x8B = 713D0A3F(Little Endian)= 0.54 // (Float) Rear Weight Distribution

___

0x8C-0x8F = 01000000(Little Endian)= 1 // Antilock Braking (ABS) 01 = true

___

0x90-0x93 = 01000000(Little Endian)= 1 // Traction Control (TC) 01 = true

___

0x94-0x97 = 01000000(Little Endian)= 1 // Stability Control (SC) 01 = true

___

0x98-0x9B = 01000000(Little Endian)= 1 // Cornering Difficulty (01, 02, 03)

___

0x9C-0x9F = 01000000(Little Endian)= 1 // Cornering Speed (01, 02, 03)

___

0x0A0-0xA3  engine displacement

___

0xA4-0xA7 = 01000000 = 1 // Shift type (see below)

!!! note

    Shift type
    
    00 = H Pattern
    
    01 = Sequential

## AMS2 Data

0xB0-0xB4 - adjustable turbo?

___

0xB8-0xBB = 01000000(Little Endian)= 1 on board roll bars and brake bias

___

0xBC-0xBF = 11000000(Little Endian)= soft and wet tires. || 40000000(Little Endian) = all weather

___

0xC0-0xC4 = 1 headlights?

___

0xC4-0xC8 = 1 

___

0xD0-0xD4 = 


<script src="https://hypothes.is/embed.js" async></script>