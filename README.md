# Kingdom Hearts II - Function Library

---

## ShowInformation(TextLocation) -- Address: 0x179310
Shows the Information Bar with the given **TextLocation**. **TextLocation** must be the **absolute** address of the string to be shown.  
For instance, say **EXE_ADDRESS + 0x800000** has the data for the text **"This is good! I like this!"** on it:  
```lua
CallFunction(0x179310, EXE_ADDRESS + 0x800000)
```
And this will result of this in game:  
![image](https://github.com/TopazTK/KH2-Function-Library/assets/95656963/559f3fb9-e7e1-42f6-943b-d9b73aa5813c)

---

## ShowPuzzlePopup(TextLocation) -- Address: 0x1571D0
Shows the Puzzle Popup with the given **TextLocation**. **TextLocation** must be the **absolute** address of the string to be shown.  
For instance, say **EXE_ADDRESS + 0x800000** has the data for the text **"Skyland Piece"** on it:  
```lua
CallFunction(0x1571D0, EXE_ADDRESS + 0x800000)
```
And this will result of this in game:  
![image](https://github.com/TopazTK/KH2-Function-Library/assets/95656963/f5d4c241-2da4-4e03-9afe-4083f23dd573)

---

## PlaySFX(SoundID) -- Address: 0x1DADF0
Plays the given Sound Effect. The list of Sound Effects are still being constructed.
For instance, say you want to play the Moogle SFX, which is Sound ID 0x40:
```lua
CallFunction(0x1DADF0, 0x40)
```
And this will result of this in game: => https://www.youtube.com/watch?v=yWzoAV2hzMA

---

## FetchSoraPointer() -- Address: 0x03B16F0
Fetches Sora's pointed location. Needed for other functions down the road.
```lua
local _soraPoint = CallReturn(0x03B16F0)
```

---

## AddHP(MEMORY_OFFSET + CharacterPointer, Amount, 0x00, true) -- Address: 0x3D0720
Edits the HP of a given character. The edit **can** be negative.  
If the HP is reduced to 0 this way, the given character will die.  
**IMPORTANT:** This function must be jumped to!  
For instance, say we want to kill Sora:  
```lua
local _soraPoint = CallReturn(0x03B16F0)
JumpFunction(0x3D0720, MEMORY_OFFSET + _soraPoint, -120, 0, true)
```
And this will result in this in game: => https://youtu.be/TGfyO3uYQbo

---

## KillBGM() -- Address: 0x1305F0
Kills the background music.
```lua
CallFunction(0x1305F0)
```
---

## CampMenuStart(Type) -- Address: 0x2E23A0
Instantly boots a Camp Menu (Camp, Load, Save, etc.), no matter where you are. Should be used with caution.
```lua
CallFunction(0x2E23A0, 0)
```

---
