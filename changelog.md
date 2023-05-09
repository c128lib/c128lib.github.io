# Changelog

## Common

### 0.6.0 - 25/01/2023
* Added MoveCursor, PrintString* macros in video.asm
* Added div16By16 and div16By8

### 0.5.1 - 02/01/2023
* Fixed missing #importonce in common-global.asm
* Little in-code documentation for kernal and screen editor

### 0.5.0 - 29/11/2022
* Added screen editor labels

### 0.4.3 - 17/11/2022
* Breaking change: fixed some kernal labels

### 0.4.2 - 03/11/2022
* Added new kernal labels

### 0.4.1 - 18/10/2022
* Added BasicUpstart128 on common-global.asm

### 0.4.0 - 16/10/2022 (more later that day)
* Added BasicUpstart128
* Added kernal labels

### 0.3.0 - 16/10/2022 (later that day)
* Breaking change: moved mem labels and macros to chipset lib

### 0.2.0 - 16/10/2022
* Added mem labels and macros

### 0.1.0 - 12/10/2022
* First release

## Chipset

### 0.8.0 - Under development
* Bugfix: wrong implementation of ReadVdcWithKernal
* Breaking change: renamed define for Vdc predefind routine

### 0.7.0 - 27/03/2023
* Added predefined routines for Vdc (see readme file)
* Added space and return keypress macro
* Breaking change: renamed some Vdc macros (changed case)

### 0.6.1 - 31/01/2023
* Added $d02f $d030 labels to Vic2

### 0.6.0 - 26/01/2023
* Added SpriteMove macro
* Added Sprite(Disable|Enable), Sprite(Disable|Enable)Multicolor, SpriteColor, SpriteMultiColor*
* Added WriteToVdcMemory*, ReadFromVdcMemory*
* Breaking change: edited some macro name on sprites.asm
* Deps retro-assembler 1.6.0
* Deps common 0.6.0

### 0.5.0 - 19/12/2022
* Added io macros on globals
* Added vdc color codes
* Added vdc macro for color selection
* Added vdc read and write with kernal 
* Breaking change: fixing mmu labels
* Breaking change: added vic2 namespace
* Breaking change: added vdc namespace
* Breaking change: added cia namespace
* Breaking change: added sid namespace
* Breaking change: added Mos8502 namespace
* Breaking change: moved getTextOffset80Col to Vdc
* Deps common 0.5.0

### 0.4.0 - 06/11/2022
* Added cia macros for joystick
* Added sid labels
* Added more vic2 shadow registers macros
* Deps common 0.4.2

### 0.3.0 - 27/10/2022
* Added vic2 shadow registers labels and macros
* Added vdc interal registers labels
* Added vdc macros

### 0.2.0 - 21/10/2022
* Added vic2 macros
* Added mmu macros
* Added vdc macros
* Deps common 0.4.1

### 0.1.0 - 16/10/2022
* First release

## Framework

### 0.2.0 - Under development
* Deps chipset 0.7.0

### 0.1.0 - 09/05/2023
* Sorting: bubble sort
* Random number: pseudo random number generator
* String manipulation
* Deps chipset 0.6.1
* Deps retro-assembler 1.6.0
