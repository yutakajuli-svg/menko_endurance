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
- Approved damage feedback: `design/damage-feedback-final.html`
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
- The BLUE status-group right edge aligns with the strength-bar right edge.
- The RED status-group left edge aligns with the strength-bar left edge.
- Each status information window, portrait window, colored frame, and feedback
  layer moves together as one group.
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

### Provisional expression timing

- The relevant character expression changes when the first feedback flash
  begins.
- For clone maximum damage and healing, the expression changes with the first
  of the two flashes.
- The changed expression remains visible after the flash and throughout the
  1.2-second message display.
- The portrait returns to its normal expression when the message window closes.
- Recheck the perceived timing after the final portrait and expression assets
  are available.
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
- The first attack presentation finishes completely before the second begins.
- Use the approved short transition pause of approximately 0.18 seconds
  between the two attack presentations.
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
- Defense and no-attack illustrations may use two or three frames.
- When the final illustration frame appears, the corresponding feedback and
  message begin at the same moment.

### Feedback

- Normal attack shake strength changes by attack level:
  - Lv1
  - Lv2
  - Lv3
- Clone maximum-damage attack uses a fourth, strongest shake.
- Damage received:
  - One short shake
  - One red flash on the victim's portrait and information area
  - Approved duration: approximately 0.36 seconds
  - HP number and HP bar start decreasing at the same moment as the flash and
    shake
  - HP number and HP bar finish decreasing in the same approximately
    0.36-second duration
  - Only the victim status group moves and flashes
  - The ring, technique illustration, and attacker status group do not flash
- Complete defense:
  - Shake based on the incoming attack level
  - One white flash on the defender's portrait and information area
  - The approved flash range and duration are the same as damage feedback
  - Only the defender status group moves and flashes
  - HP number and HP bar do not decrease
- Partial defense with remaining damage uses the red flash.
- No-attack presentation:
  - RED and BLUE portrait and information areas flash white simultaneously
  - The white flash is slightly softer than the complete-defense flash
  - Neither status group shakes
  - The ring does not flash
  - Neither HP number nor HP bar changes
- Clone effect presentation:
  - Clone maximum damage and healing use the same illustration-window sequence
    as techniques
  - The placeholder test uses three frames for maximum damage and two frames
    for healing; the final assets may use two or three frames
  - When the final frame appears, the feedback and message begin together
  - Maximum damage:
    - Two strong red flashes over approximately 0.52 seconds
    - The fourth and strongest shake
    - Only the victim status group flashes and shakes
    - The victim HP number and HP bar decrease during the two flashes
    - The victim's carry and new defense values reset to zero when the feedback
      begins
  - Healing:
    - Two soft white flashes over approximately 0.52 seconds
    - Only the healing side's status group flashes
    - No shake
    - HP increases by one third of maximum HP during the two flashes
  - The ring does not flash for either clone effect

### Commentary style

- Use short, simple wrestling-style commentary.
- Keep normal attack, defense, and no-attack messages to approximately two
  lines.
- Clone effect messages use three lines and a slightly taller message window.
- The message window opens when the finishing frame appears and the damage
  feedback begins.
- The message window closes automatically after 1.2 seconds.
- The message cannot be dismissed or skipped by tapping; it closes
  automatically only.
- Example:
  - `REDの投げ技！しかし攻撃は浅い！`
  - `BLUEに 1 ダメージ！`
- Defense wording may vary with the technique, such as:
  - `BLUEは攻撃を防いだ！`
  - `うまくかわした！`
  - `うまく防いだ！`
- Clone maximum-damage example:
  - `REDの得意技が決まったーっ！`
  - `BLUEは大ダメージ！`
  - `3ダメージ`
- Clone healing example:
  - `REDは呼吸を整えている！`
  - `REDの体力が回復！`
  - `体力+6`

## Still provisional / not fixed

- Character bust illustrations, expression variants, and final timing
  confirmation with the completed assets
- Defense illustration assets
- No-attack illustration assets
- Clone maximum-damage and healing illustration assets
- Final in-game light source and shadow integration
- Integration into `index.html`
