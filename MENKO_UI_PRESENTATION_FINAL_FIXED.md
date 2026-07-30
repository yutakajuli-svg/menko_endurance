# MENKO ENDURANCE UI / PRESENTATION FIXED

Fixed: 2026-07-30

This document records only the UI and presentation decisions approved so far.
Items that still require visual testing are separated at the end.

## Final reference files

- Menko design and animation: `animation_lab_v5_final.html`
- Menko design / animation notes: `MENKO_ANIMATION_DESIGN_FINAL_FIXED.md`
- Ring design: `design/ring-design-final.html`
- Player status panels: `design/player-status-panel-final.html`
- Approved full-screen layout: `design/full-screen-ui-layout-final.html`
- Approved technique overlay layout: `design/technique-overlay-layout-final.html`
- Technique illustration presentation: `move_effect_lab_final.html`

These files are references for later integration. They are not yet integrated
into `index.html`.

## Main screen layout

- Mobile portrait is the primary layout.
- BLUE status area is at the top.
- The strength bar is placed below the BLUE status area and above the ring.
- A large square ring is in the center and is the core play area.
- RED status area is at the bottom.
- RED: character portrait on the left, status information on the right.
- BLUE: status information on the left, character portrait on the right.
- The portrait is always visible, with expression changes for attacking and
  taking damage.
- The portrait window and information window are separate windows with a small
  horizontal overlap.
- Their top edges are aligned; there is no vertical offset.
- The portrait window is drawn in front of the information window.
- The portrait window must not overlap the ring.

## Strength bar

- Approved design: B, the thick pixel rail.
- The bar is placed below the BLUE status area and above the ring.
- The outer bar aligns with the ring width in the approved layout.
- The moving cursor is a wide rectangular pixel block rather than a thin line.
- A thinner low-contrast rail runs through the center of the bar.
- The six strength-result regions are not shown.
- Region widths may continue to vary by match without revealing the correct
  position to the player.

## Character and information window layers

Back to front:

1. Status information window and text
2. Fully opaque black portrait-window background
3. Character illustration
4. RED or BLUE frame

- RED frame: exact RGB red (`255, 0, 0`)
- BLUE frame: exact RGB blue (`0, 0, 255`)
- The information window must never show through the portrait window.
- The portrait and information windows behave as one group during hit effects.

## Status information

- Font: standard Misaki Gothic (`misaki_gothic.ttf`)
- Main information size: 20 px
- Secondary `NEW + CARRY` breakdown: 16 px in the approved reference
- Wrestler names are not required.
- Constantly displayed information:
  - Current HP / maximum HP
  - Continuous HP bar
  - Attack power
  - Current total defense
  - `NEW + CARRY` defense breakdown
- HP bars have no divider or tick lines.
- RED HP bar: exact RGB red (`255, 0, 0`)
- BLUE HP bar: exact RGB blue (`0, 0, 255`)
- Before a throw, NEW defense is displayed as `0`, not `?`.

## Ring design

- Square ring surface viewed from directly above.
- The ring posts use a slightly angled cylindrical view to add depth.
- Ropes:
  - Three ropes on the top edge
  - Two ropes on the left edge
  - Two ropes on the right edge
  - No ropes on the bottom edge
- Four cylindrical posts stand at the rope intersections.
- Posts visually extend from the ring toward the top of the screen.
- The posts sit slightly inside the ring and are drawn above the ropes.
- Top and bottom ends of the posts are rounded.
- Hidden rear-side bottom lines are not drawn.
- All four posts use the same approved length.
- Post colors:
  - Upper left: light gray
  - Upper right: exact RGB blue (`0, 0, 255`)
  - Lower left: exact RGB red (`255, 0, 0`)
  - Lower right: light gray
- Diamond-shaped corner parts are not used.

## Center-layer order

Back to front:

1. Ring and menko play area
2. Technique illustration window
3. Commentary / damage message window

- The technique illustration window uses the source-image aspect ratio of 4:3.
- The technique illustration and message windows use the same approved width,
  slightly wider than the ring.
- The message window is placed below the technique illustration with a small
  gap and does not overlap the illustration.
- The technique illustration and message group sits above the RED status area
  with a visible gap.
- The strength bar remains visible above the technique illustration.
- The ring itself does not flash during damage presentation.

## Technique illustration presentation

- Technique types:
  - `001`: throw
  - `002`: strike
  - `003`: submission
- Each type has levels 1 through 3.
- Frames are displayed in numeric order.
- The last frame is always the finish frame.
- Only the finish frame triggers screen shake.
- Current approved timing:
  - Frame duration: 320 ms
  - Finish hold: 700 ms
  - Shake strength: 7 px
  - Shake duration: 300 ms
- BLUE always uses the horizontal opposite of RED.

### Frame counts

- Throw Lv1: 4 frames
- Throw Lv2: 3 frames
- Throw Lv3: 3 frames
- Strike Lv1: 2 frames
- Strike Lv2: 2 frames
- Strike Lv3: 3 frames
- Submission Lv1: 2 frames
- Submission Lv2: 2 frames
- Submission Lv3: 3 frames

### RED illustration direction

- Throw Lv1: original
- Throw Lv2: original
- Throw Lv3: horizontally mirrored
- Strike Lv1: original
- Strike Lv2: horizontally mirrored
- Strike Lv3: original
- Submission Lv1: original
- Submission Lv2: horizontally mirrored
- Submission Lv3: original

## Damage and defense presentation

- Both wrestlers throw before final damage presentation begins.
- The final attack and defense values for both sides are calculated first.
- If both sides have an event, presentation follows initiative order:
  1. First attacker illustration / effect / message
  2. Second attacker illustration / effect / message
- If mutual damage causes a simultaneous knockout, RED (the player) loses.

### Result branches

- Attack value greater than defense:
  - Attack illustration
  - Damage message
  - If defense was used, commentary explains that the attack was reduced
- Attack value equal to or less than defense:
  - Defense illustration
  - Damage `0`
- Both sides have defense only:
  - Dedicated no-attack presentation
- One side flips nothing and the other has defense only:
  - Dedicated no-attack presentation
- Defense presentation appears only in response to an actual attack.

### Feedback

- Normal attack shake strength changes by attack level:
  - Lv1
  - Lv2
  - Lv3
- Clone maximum-damage attack uses a fourth, strongest shake.
- Damage received:
  - Shake
  - Red flash on the victim's portrait and information area
- Complete defense:
  - Shake based on the incoming attack level
  - White flash on the defender's portrait and information area
- Partial defense with remaining damage uses the red flash.
- No-attack presentation uses neither shake nor flash.

### Commentary style

- Use short, simple wrestling-style commentary.
- Keep it to approximately two lines.
- Example:
  - `REDの投げ技！しかし攻撃は浅い！`
  - `BLUEに 1 ダメージ！`
- Defense wording may vary with the technique, such as:
  - `BLUEは攻撃を防いだ！`
  - `うまくかわした！`
  - `うまく防いだ！`

## Still provisional / not fixed

- Exact automatic message closing time
- Whether tapping outside the ring also skips the message
- Exact HP-bar reduction timing after the finish-frame shake
- Character bust illustrations and expression variants
- Defense illustration assets
- No-attack illustration assets
- Final in-game light source and shadow integration
- Integration into `index.html`
