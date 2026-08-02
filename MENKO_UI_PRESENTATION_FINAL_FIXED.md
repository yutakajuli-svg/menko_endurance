# MENKO ENDURANCE UI / PRESENTATION FIXED

Fixed: 2026-08-02

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

The approved references are integrated into `index.html` as of v20.

## v25 clone rescue, KO presentation, and illustration orientation

- A clone can be checked only while its owner is at one quarter HP or below.
- Its flip probability is one roll at 40% of the completed normal-menko flip
  probability.
- A successful flip activates the clone effect without a second activation
  lottery.
- The two-activation match limit, three-round shared cooldown, and random
  selection when both clones flip in one round remain unchanged.
- When the first attack presentation reduces the second attacker to zero HP,
  the second attack presentation is omitted. Damage calculation remains the
  approved simultaneous round resolution so the RED-loss mutual-KO rule is
  unchanged.
- Complete-defense illustration orientation: RED defense is horizontally
  mirrored; BLUE defense uses the original image orientation.
- Throw-technique Lv1 orientation: RED attack is horizontally mirrored; BLUE
  attack uses the original image orientation.

## v20 integration checkpoint

- Main file: `index.html`
- In-game UI, ring, strength bar, menko designs, animation, character portraits,
  technique illustrations, messages, flashes, and HP animation are integrated.
- The ring and menko scale have been adjusted for the final mobile layout.
- The weak-success animation uses the approved fixed lower edge.
- Overlapping menko react as one impact group without delayed lower-layer chain
  reactions.
- The test controls are consolidated under one `検証` button below the RED
  status window. `進行`, `数値設定`, and `ログ` open from that button.
- This state is the v20 UI integration FIX checkpoint.

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
- Secondary `THIS ROUND ONLY` notice: 16 px
- Wrestler names are not required.
- Constantly displayed information:
  - Current HP / maximum HP
  - Continuous HP bar
  - Attack power
  - Defense obtained in the current round
  - `THIS ROUND ONLY` notice
- HP bars have no divider or tick lines.
- RED HP bar: exact RGB red (`255, 0, 0`)
- BLUE HP bar: exact RGB blue (`0, 0, 255`)
- Before a throw, current-round defense is displayed as `0`.
- Defense never carries into the next round.

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

## Lighting and ground shadows

- Use one fixed parallel light from the upper-left / rear of the screen.
- Menko shadows fall toward the lower-right.
- A shadow moves farther toward the lower-right as its menko rises.
- Shadow size is approximately 100% while the menko is on the ground and
  decreases to approximately 70% at maximum height.
- Shadow corners remain slightly rounded while preserving the square menko
  silhouette.
- Shadow orientation and shape are projected from the fixed light, menko height,
  tilt, and rotation; do not force the shadow to copy or reverse the menko
  rotation.
- Combine all menko shadow shapes into one mask and draw the mask once at low
  opacity.
- Overlapping shadows remain the same opacity instead of becoming darker.
- Random menko overlap in the lighting test is not part of the final placement
  rule and does not need to be reproduced.

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
  - Maximum damage has three technique types with four frames each:
    throw, strike, and submission
  - Maximum damage ignores defense and equals attack power plus the attacker's
    total number of attack menko
  - One of the three maximum-damage techniques is selected at random
  - Healing uses one frame
  - For maximum damage and healing, RED uses the original artwork and BLUE uses
    a horizontal mirror
  - When the final frame appears, the feedback and message begin together
  - Maximum damage:
    - Two strong red flashes over approximately 0.52 seconds
    - The fourth and strongest shake
    - Only the victim status group flashes and shakes
    - The victim HP number and HP bar decrease during the two flashes
    - The victim's current-round defense display resets to zero when the
      feedback begins
  - Healing:
    - Two soft white flashes over approximately 0.52 seconds
    - Only the healing side's status group flashes
    - No shake
    - HP increases by one third of maximum HP during the two flashes
- The ring does not flash for either clone effect

- Complete-defense artwork uses two frames:
  - RED uses a horizontal mirror
  - BLUE uses the original artwork
- No-attack artwork uses three frames:
  - RED initiative uses the original artwork
  - BLUE initiative uses a horizontal mirror

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

## Still provisional / requires play testing

- Final confirmation of character-expression timing with completed artwork
- Rare presentation branches such as mutual attacks, full defense, no attack,
  clone maximum damage, clone healing, and simultaneous knockout
- Final play-feel adjustment of normal and clone menko flip frequency
