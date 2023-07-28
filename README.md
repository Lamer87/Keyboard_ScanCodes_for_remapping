## Keyboard ScanCodes for remapping ⌨️

### This is a simple guide for remapping (rebinding) keyboard keys,  
### whitout using a tool, just system registry.
<!-- ### `v1.0` -->
[<img src="https://i.ibb.co/h7hwpbn/Empty-png.png" width="1"/>](https://github.com/Lamer87/Space_Engineers_DLC_unlocker#space-engineers-dlc-unlocker)
---
❗ Note: this is only for changing one key to another, it is NOT possible to map combinations  
(example CTRL+C) to a key, to do this you need a tool.

---

- 💡 You can download all (this readme, the example and the remover) [here 💾](https://github.com/Lamer87/Keyboard_ScanCodes_for_remapping/archive/refs/heads/main.zip),  
or just click on "Code" then "Download ZIP".

  - The EXAMPLE file (Rebind.reg) it's meant to be edited by you.  
This file is ALREADY modified and will add the necessary "hex" value to the registry,  
so before applying it you have to EDIT IT properly.

  - If you want to get rid of the remapping, use the file "remover.reg",  
it can be even used to create just the empty hex value.

  - Every time you apply the values, you must AT LEAST logout and login (or restart), for the changes to take effect.

---

- 📜 How to manually create the value in the registry:  
  - 1- Open "C:\Windows\regedit.exe"  
  - 2- Go to "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Keyboard Layout" (not \Keyboard Layout**S**)  
  - 3- Create a new "binary value" here, named "Scancode Map" (without quotes).

- ✔️ What goes inside the binary value is described below in the regedit file format,
so you don't have to manually enter values via regedit.exe, but just modify Rebind.reg then exec it.

---

## ⚠️ Example: ##

```
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Keyboard Layout]
"Scancode Map"=hex:00,00,00,00,00,00,00,00,02,00,00,00,3A,00,5D,E0,00,00,00,00
```

What means an entire regedit code:  

| 00,00,00,00, | 00,00,00,00, | 02,00,00,00, | 3A,00,5D,E0, | 00,00,00,00 |
| --- | --- | --- | --- | --- |
| 1st 8 bits | 2nd 8 bits | 3rd 8 bits | 4th 8 bits | 5th 8 bits
| version | flag | number of rebinds +1! | rebind n1 | final bits (null)

Version: always 8 zeroes  
Flag: always 8 zeroes  
Final bits: always 8 zeroes

Number of rebinds:  
only the first 2 bits count, the value must be made up of the number of rebinds (8 bits for each one),  
plus one for the final 8 bits.  
For example, if we want to rebind 4 keys, the value number of rebinds will be 05,00,00,00,  
if the rebinds are 12 the value will be 13,00,00,00,

[<img src="https://i.ibb.co/h7hwpbn/Empty-png.png" width="1"/>](https://github.com/Lamer87/Space_Engineers_DLC_unlocker#space-engineers-dlc-unlocker)
---
What means rebind n1:  

| 3A,00, | 5D,E0, |
| --- | --- |
| 1st part: it's the keycode of the remapping | 2nd part: the button you actually press

[<img src="https://i.ibb.co/h7hwpbn/Empty-png.png" width="1"/>](https://github.com/Lamer87/Space_Engineers_DLC_unlocker#space-engineers-dlc-unlocker)
---
What means the single code "5D,EO":  

5D: scancode of the key  
E0: can be 00 or E0 (or E1 for button Pause)  
    some keys share the scancode, changing only the second part


[<img src="https://i.ibb.co/h7hwpbn/Empty-png.png" width="1"/>](https://github.com/Lamer87/Space_Engineers_DLC_unlocker#space-engineers-dlc-unlocker)
---
This is an example with 3 rebinds:
```
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Keyboard Layout]
"Scancode Map"=hex:00,00,00,00,00,00,00,00,04,00,00,00,3A,00,5D,E0,3E,00,46,00,3F,00,45,E1,00,00,00,00
```

[<img src="https://i.ibb.co/h7hwpbn/Empty-png.png" width="1"/>](https://github.com/Lamer87/Space_Engineers_DLC_unlocker#space-engineers-dlc-unlocker)
---
for a better demonstration view (do not use!)
```
"Scancode Map"=hex:
00,00,00,00,    version
00,00,00,00,    flag
04,00,00,00,    rebinds number +1
3A,00,5D,E0,    rebind n1
3E,00,46,00,    rebind n2
3F,00,45,E1,    rebind n3
00,00,00,00     final bits
```


[<img src="https://i.ibb.co/h7hwpbn/Empty-png.png" width="1"/>](https://github.com/Lamer87/Space_Engineers_DLC_unlocker#space-engineers-dlc-unlocker)

---

- 🕹️ A good tool to show keycodes for your keyboard is [Keyboard Key Info](https://dennisbabkin.com/kbdkeyinfo/)  
it shows what keycode (1st part) are you pressing on the keyboard.  
Example: "ScanCode=0x4F" where the keycode 1st part is "4F" but you don't know if the second part is 00 or E0,  
so I'll help you with the table below :)

---

### 📌 In this table, secondary code is always "00" when there are only 2 digits, others are specified.
[<img src="https://i.ibb.co/h7hwpbn/Empty-png.png" width="1"/>](https://github.com/Lamer87/Space_Engineers_DLC_unlocker#space-engineers-dlc-unlocker)

| Code | Key (+ shift) | ITA layout (+ shift and altGR) |
| --- | --- | --- |
| |
| 1st Row: |
| 01 | Esc
| 3B | F1
| 3C | F2
| 3D | F3
| 3E | F4
| 3F | F5
| 40 | F6
| 41 | F7
| 42 | F8
| 43 | F9
| 44 | F10
| 57 | F11
| 58 | F12
| |
| 2nd Row:
| 29 | ` ~ | \ and vertical bar
| 02 | 1 !
| 03 | 2 @ | "
| 04 | 3 # | £
| 05 | 4 $
| 06 | 5 %
| 07 | 6 ^ | &
| 08 | 7 & | /
| 09 | 8 * | (
| 0A | 9 ( | )
| 0B | 0 ) | =
| 0C | - _ | ' ?
| 0D | = + | ì ^
| 0E | Backspace
| |
| 3rd Row:
| 0F | Tab
| 10 | Q
| 11 | W
| 12 | E
| 13 | R
| 14 | T
| 15 | Y
| 16 | U
| 17 | I
| 18 | O
| 19 | P
| 1A | [ { | è é [
| 1B | ] } | + * ]
| 2B | \ and vert. bar | ù §
| |
| 4th Row:
| 3A | CapsLock
| 1E | A
| 1F | S
| 20 | D
| 21 | F
| 22 | G
| 23 | H
| 24 | J
| 25 | K
| 26 | L
| 27 | ; : | ò ç @
| 28 | ' " | à ° #
| 1C | Enter
| |
| 5th Row:
| 2A | LeftShift
| 56 | | < >
| 2C | Z
| 2D | X
| 2E | C
| 2F | V
| 30 | B
| 31 | N
| 32 | M
| 33 | , ;
| 34 | . :
| 35 | / ? | - _
| 36 | RightShift
| |
| 6th Row:
| 1D | LeftCtrl
| 5B-E0 | LeftWin
| 38 | LeftAlt
| 39 | Space
| 38-E0 | RightAlt
| 5C-E0 | RightWin
| 5D-E0 | Menu
| 1D-E0 | RightCtrl
| |
| Middle:
| 37-E0 | PrintScreen
| 46 | ScrollLock
| 45-E1 | Pause
| 52-E0 | Insert
| 53-E0 | Delete (Canc)
| 47-E0 | Home
| 4F-E0 | End
| 49-E0 | PageUp
| 51-E0 | PageDown
| 48-E0 | Up
| 50-E0 | Down
| 4B-E0 | Left
| 4D-E0 | Right
| |
| KeyPad:
| 45 | NumLock
| 35-E0 | /
| 37 | *
| 4A | -
| 4E | +
| 1C-E0 | Enter
| 53 | . / Del
| 52 | 0 / Ins
| 4F | 1 / End
| 50 | 2 / Down
| 51 | 3 / PgDn
| 4B | 4 / Left
| 4C | 5
| 4D | 6 / Right
| 47 | 7 / Home
| 48 | 8 / Up
| 49 | 9 / PgUp

---

<!-- _ -->
<!-- Useless code to use occasionally:
💡🚧❗✔️⚠️🕹️🔄📜⛔📌🇮🇹💾

img empty:
[<img src="https://i.ibb.co/h7hwpbn/Empty-png.png" width="1"/>](https://github.com/Lamer87/Space_Engineers_DLC_unlocker#space-engineers-dlc-unlocker)
 -->
