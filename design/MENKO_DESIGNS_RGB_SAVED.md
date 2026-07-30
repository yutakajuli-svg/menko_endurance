# MENKO RGB designs — saved reference

Saved: 2026-07-28

These are design checkpoints and are not yet integrated into `index.html`.

## Front / back rule (FIXED 2026-07-29)

- Normal attack / defense menko:
  - Front: RGB color face with the attack or defense icon
  - Back: plain, with no icon
- Clone menko:
  - Front: plain, with no icon
  - Back: RGB color face with the approved expression icon
- A clone placed on the field initially shows its plain front.
- The expression icon is revealed only after the clone is flipped.

## Ownership / availability rule (FIXED 2026-07-29)

- RGB red menko/cards are exclusive to the player (RED corner).
- RGB blue menko/cards are exclusive to the CPU (BLUE corner).
- Attack and defense require shared versions that both sides can use.
- Required normal attack / defense set:
  - Shared attack
  - Shared defense
  - Player-exclusive red attack
  - Player-exclusive red defense
  - CPU-exclusive blue attack
  - CPU-exclusive blue defense
- Clone menko remain corner-exclusive:
  - Red clone: player only
  - Blue clone: CPU only
- Shared attack / defense color: charcoal, RGB (`40, 40, 40`) — FIXED 2026-07-29.

## Normal attack / defense menko

- Base shape: approved B design (small chamfered square, thin side)
- Player-exclusive front: RGB red (`255, 0, 0`)
- CPU-exclusive front: RGB blue (`0, 0, 255`)
- Shared front: charcoal, RGB (`40, 40, 40`)
- Side thickness and fold lines: white
- Attack icon: approved pixelated `🤜`
- Defense icon: approved fixed 18 × 18 shield
- Back: plain, with no icon

Reference file:

- `menko-design-normal-rgb-reference.html`

## Clone menko

- Base shape: approved B design
- Player: RGB red (`255, 0, 0`)
- CPU: RGB blue (`0, 0, 255`)
- Side thickness and fold lines: white
- Face background: true white circle
- Face design: the selected second option from the comparison
- Eyes and eyebrows: pixelated, centered version before the later “move further inward” revision
- Mouth: pixelated frown at 80% size
- Front: plain, with no icon
- Back: approved expression icon

Reference file:

- `menko-design-clone-rgb-reference.html`
