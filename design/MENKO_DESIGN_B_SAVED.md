# MENKO design B — saved reference

Saved: 2026-07-28

This is a design checkpoint, not yet an integration into the game.

## Body

- Small chamfered square
- Thin side thickness
- Right-side thickness is narrow
- Left-side thickness is slightly wider
- Simple folded-paper lines
- Back side is blank
- Fold lines must not show through either icon

## Attack icon

- Based directly on the `🤜` emoji silhouette
- Faces from left to right
- 24 × 24 pixel conversion
- Flat white / gray / black treatment
- This icon is approved as complete

## Defense icon

- 18 × 18 fixed pixel map
- Symmetrical outer silhouette
- White outer and right area
- Gray inner-left area
- Stepped taper toward a two-pixel-wide tip
- No transparent or black notch inside the shield

Pixel-map row bounds used for the shield:

```text
00  white x=2..15
01  white x=1..16
02  white x=1..16; gray x=2..8
03  white x=1..16; gray x=2..8
04  white x=1..16; gray x=2..8
05  white x=1..16; gray x=2..8
06  white x=1..16; gray x=2..8
07  white x=1..16; gray x=2..8
08  white x=1..16; gray x=2..8
09  white x=1..16; gray x=2..8
10  white x=2..15; gray x=3..8
11  white x=3..14; gray x=4..8
12  white x=4..13; gray x=5..8
13  white x=5..12; gray x=6..8
14  white x=6..11; gray x=7..8
15  white x=7..10
16  white x=8..9
17  empty
```

## Files

- `menko-design-b-reference.html`: visual reference with front/back and attack/defense controls.
