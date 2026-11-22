# ScudFall: Atari 2600 Morse code city-defense ROM

An Atari 2600 game that teaches Morse code. Missiles fall on a city of six buildings; decode or send Morse to shoot the right one down.

`scudfall.bin` is a 4K NTSC ROM. It runs in Stella (open the file, or `stella scudfall.bin`) and on a real 2600 from a Harmony or other flash cart.

Video: https://www.youtube.com/watch?v=5v_iAk5qCfA

Made with Claude (Anthropic's AI), which wrote the 6502 assembly; the design, direction and testing are mine. The binary is free to play and share; the source is not published.


## Controls
- Left difficulty switch (Stella: F5 = A, F6 = B; the console defaults to B): **B is learning mode**, nothing speeds up from level to level; **A is pro mode**, bombs get faster through level 8 and groups and waves grow. The title screen shows PRO when the switch is on A. Read live, so it can be flipped any time.
- Right difficulty switch (Stella: F7 = A, F8 = B): **B is the campaign** (two new symbols per level, SAVED after level 18); **A is random mode**, every wave draws from all 36 letters and numbers, the level screen says RANDOM, and it runs endlessly. Good for drilling once the campaign is done.
- Title screen (SCUDFALL, with the radio keying the letters of the name): fire (Stella: Space) starts. Hold it for a full frame; the button is read once per frame.
- Level screen ("LVn AB" shows the two new letters while the radio keys them): the radio keys each letter while the HUD shows it; fire to skip ahead.
- Listen waves: joystick left/right (arrow keys) slides the gun to the next building; hold it to keep going lane by lane. Fire shoots. Joystick up replays the signal once the radio has gone quiet.
- Send waves: hold fire to key. 9 frames or less is a dot, longer is a dash. Half a second of silence ends the letter. A correct letter fires the gun by itself.

## How it plays
- **Listen waves (Missile Command):** 3 bombs fall together (2 on level 1, when only two letters are known; in pro mode 2 bombs, 3 from level 3, 4 from level 5). Each carries a letter tag. The enemy radio taps one letter: that bomb is armed, the others are decoys. One shot per group. A hit decoy puffs and vanishes with a buzz; the armed bomb keeps coming. Let the armed bomb land and the building under it is destroyed.
- **Send waves (Typo Attack):** one bomb at a time. Tap its letter in Morse before it lands. A garbled letter costs a 40-frame reload while the bomb keeps falling.
- Letters are drawn from everything learned so far, with half of all draws taken from the level's two new letters so a level practises its new pair while reviewing the old ones (random mode draws evenly).
- Waves alternate listen then send; then the level ends, two more letters unlock (E T I A N M S U R W D K G O H V F L P J B X C Y Z Q), bombs fall faster, and one lost building is rebuilt. Level 13 brings in the last letters, Z and Q. Levels 14-18 teach the numbers, two per level (1 2 3 4 5 6 7 8 9 0), in learning mode at the same speed as every other level: only the symbols change. In pro mode speed stops climbing at level 8. Clear level 18 and the city is SAVED (the radio keys O K), then back to the title. Lose all six buildings and it is GAME OVER.
- Bombs only fall over lanes that still have a building, and a group never has more bombs than there are buildings.
- Score: 1 point for each armed missile destroyed (no height bonus or streak multiplier).  The streak is still tracked for the miss sound.
- The dot/dash strip under the HUD shows the armed letter's pattern until you have answered that letter correctly once; a miss brings it back. In send waves the strip shows what you have keyed so far.
