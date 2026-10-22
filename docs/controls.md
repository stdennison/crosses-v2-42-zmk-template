# Current controls

Thumb positions, in keymap order:

| Position | Tap | Hold |
| --- | --- | --- |
| 36, left | Space | Function; right trackball scrolls |
| 37, left | Backspace | Numbers |
| 38, left | Delete | Media |
| 39, right | Enter | Media |
| 40, right | Space | Shift |
| 41, right | Escape | Numpad; left trackball scrolls |

The existing thumb bindings and tap/hold settings are unchanged. Function and
Numpad keep their key assignments; each now enables the opposite hand's ball
for scrolling. Vertical scroll is reversed relative to that ball's cursor
orientation. Both scroll overrides use a `1/16` scaler and 16 ms rate limit.

## Media

Holding Delete or Enter enables Media without enabling scrolling. An independently
held Function or Numpad layer still enables its associated scroll override.

```text
                   LEFT                                 RIGHT
 —       —       —       —     ALT   LCLICK | LCLICK ALT    F7    F8    F9   F12
 —       —       —     WIN←   WIN→  RCLICK | RCLICK SLCK   F4    F5    F6   F11
 —     WIN↑    WIN↓   CAPTURE    —      —   | INSERT PAUSE  F1    F2    F3   F10
```

`—` means disabled. Media's click, Alt, function-key, window-switching, and
capture bindings retain their previous positions.

## Maintenance

From Base, press either pair within 50 ms and hold it for about 500 ms:

```text
LEFT THUMBS                          RIGHT THUMBS
[36 Space] [37 Backspace] [38 Delete] | [39 Enter] [40 Space] [41 Escape]
 \--------- Maintenance ----------/    \--------- Maintenance --------/
```

After the guard expires, keep both thumbs held and press the command key.
Releasing either participating thumb exits Maintenance. A short recognized
chord does nothing: its constituent tap actions are consumed. Other key presses
cannot shorten the guard, but hold/tap processing may buffer them; wait for the
guard to finish before pressing a command. Entry is available from Base only.

```text
                   LEFT                                 RIGHT
 BT0    BT1    BT2    BT3    BT4    —  |   —     BT4    BT3    BT2    BT1    BT0
 PREV   NEXT   OUTPUT STUDIO  —     —  |   —      —    STUDIO OUTPUT NEXT   PREV
 RESET  BOOT   CLEAR   —      —     —  |   —      —      —    CLEAR  BOOT   RESET
```

All six thumb positions and unused finger positions are disabled on this layer.
Bluetooth commands operate on the central keyboard's host profiles, whichever
half provides the command key. CLEAR clears the selected profile's pairing.
Reset and bootloader commands target the half where the command key is pressed.
OUTPUT toggles USB/Bluetooth output, and STUDIO unlocks ZMK Studio.

The right half is central. Its 39+41 combo remains usable when the left half
is disconnected. A disconnected left half cannot receive software reset/boot
commands and needs its physical recovery mechanism.

Positions 37 and 40 are not added to any new combos. Existing combos, including
38+39 Undo and 1+2+37+40 Tab, are unchanged. Positions 36 and 41 now participate
in a 50 ms combo window on Base, which can briefly defer their normal actions.

## Hardware checks

1. Confirm the left, right, and settings-reset CI builds pass before flashing
   the regular firmware artifacts to the matching halves.
2. Check all six thumb taps and holds, especially rapid Backspace and Space,
   Space/Delete overlaps, Enter/Escape overlaps, and the existing Undo combo.
3. On Media, exercise every formerly dangerous position: none should select a
   profile, clear pairing, reset, or enter bootloader. Check both click/Alt groups.
4. Hold Function and move each ball: only the right ball should scroll. Hold
   Numpad and repeat: only the left ball should scroll. Check vertical direction,
   horizontal direction, sensitivity, and return to cursor movement on release.
5. Try each maintenance chord briefly: no command or thumb tap should occur.
   Hold for 500 ms, select a profile, release either thumb, and verify exit.
   Repeat with the other release order and the other half's entry chord.
6. With the left half off, verify the right chord still opens Maintenance.
   Test mirrored reset/bootloader commands one half at a time when ready to
   reconnect or flash that half; clearing pairing requires pairing again.
