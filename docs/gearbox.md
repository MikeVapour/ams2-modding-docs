# gearbox

**Project CARS and AMS2**

Audi A1 Quattro Gearbox translation

by **JDougNY**

Version 1.1 - 2/13/2016 - Text revisions  for PC2

Version 1.0 - 8/24/2015 - Initial Release for PC2

This translation can be used to understand any gearbox file, no matter the amount of gears contained within the file.

___

0x00-0x07 = **common data** for every GDF

___

0x08-0x0B = 66000000 (Little Endian) = 102 // (Decimal) **Total byte length** of entire file.

Can vary depending upon amount of primary and final gears you want to have.

___

0x0C-0x0F = 01000000 (Little Endian) = 1 // (Decimal) **common data** for every GDF

___

0x10-0x13 = BABA1010 // **common data** for every GDF

___

0x14-0x17 = 4A000000 (Little Endian) = 74 // (Decimal) **Total # of bytes** for gearbox/bevel/final data.

The byte count starts at address `0x1C` and ends at the end of the file.

This value will vary based upon the amount of gears included in the file.

___

0x18-0x1B = 1C000000 (Little Endian)// common data for every GDF

___

## Gear Ratios Data

0x1C-0x20 = `60 88 DE 24 0F` // common data for every GDF.


**Indicates the beginning of gear data.**

!!! note 

    Each primary gear is flagged by this string of bytes `24 9D 58 F9 64 02`.

    After that flag, the 2 bytes following represent the 2 cogs, which in the old text form would read "ratio=(xx,xx)".  Each byte is in hex and needs to be converted to decimal to get the correct cog value.

___

0x21-0x26 = `24 9D 58 F9 64 02` // Hex string for **1st gear**
___

0x27 = 0E = 14 // (Decimal) 1st gear cog #1 (Driver)
___

0x28 = 3C = 60 // (Decimal) 1st gear cog #2 (Driven)

*1st gear Ratio=(14,60) // 4.2857*

___

0x29-0x2E = `24 9D 58 F9 64 02` // Hex string for **2nd gear**
___

0x2F = 0C = 12 // (Decimal) 2nd gear cog #1 (Driver)
___

0x30 = 20 = 32 // (Decimal) 2nd gear cog #2 (Driven)

*2nd gear Ratio=(12,32) // 2.6666*

___

0x31-0x36 = `24 9D 58 F9 64 02` // Hex string for **3rd gear**
___

0x37 = 1C = 28 // (Decimal) 3rd gear cog #1 (Driver)
___

0x38 = 35 = 53 // (Decimal) 3rd gear cog #2 (Driven)

*3rd gear Ratio=(28,53) // 1.8928*

___

0x39-0x3E = `24 9D 58 F9 64 02` // Hex string for **4th gear**
___

0x3F = 12 = 18 // (Decimal) 4th gear cog #1 (Driver)
___

0x40 = 19 = 25 // (Decimal) 4th gear cog #2 (Driven)

*4th gear Ratio=(18,25) // 1.3888*

___

0x41-0x46 = `24 9D 58 F9 64 02` // Hex string for **5th gear**
___

0x47 = 1F = 31 // (Decimal) 5th gear cog #1 (Driver)
___

0x48 = 22 = 34 // (Decimal) 5th gear cog #2 (Driven)

*5th gear Ratio=(31,34) // 1.0967*

___

0x49-0x4E = `24 9D 58 F9 64 02` // Hex string for **6th gear**
___

0x4F = 22 = 34 // (Decimal) 6th gear cog #1 (Driver)
___

0x50 = 1F = 31 // (Decimal) 6th gear cog #2 (Driven)

*6th gear Ratio=(34,31) // 0.9117*

___

0x51-55 = `E0 97 65 B7 AF` // **common data** for every GDF.

Indicates the **end of primary gear data**.  Begin Bevel data.

## Final Drive Ratios

!!! note

    The bevel is flagged by this string of bytes `24 3C 5B EF 62 02`.
    After that flag, the 2 bytes following represent the 2 cogs, which in the old text form
    would read "bevel=(xx,xx)".  Each byte is in hex and needs to be converted to
    decimal to get the correct cog value.

0x56-0x5B = `24 3C 5B EF 62 02` // Hex string for bevel

0x5C = 01 = 1 // (Decimal) bevel cog #1 (Driver)

0x5D = 01 = 1 // (Decimal) bevel cog #2 (Driven)

bevel=(1,1)

!!! note 

    Final drive gear(s) is(are) flagged by this string of bytes `24 9D 58 F9 64 02`.
    After that flag, the 2 bytes following represent the 2 cogs, which in the old text form
    would read "ratio=(xx,xx)".  Each byte is in hex and needs to be converted to
    decimal to get the correct cog value.


0x5E-0x63 = `24 9D 58 F9 64 02` // Hex string for final gear

0x64 = 17 = 23 // (Decimal) Final gear cog #1 (Driver)

0x65 = 47 = 71 // (Decimal) Final gear cog #2 (Driven)

*Final gear ratio=(23,71) // 3.0869*


<script src="https://hypothes.is/embed.js" async></script>