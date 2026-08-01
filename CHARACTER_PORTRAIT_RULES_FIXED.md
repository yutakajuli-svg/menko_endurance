# MENKO ENDURANCE CHARACTER PORTRAIT RULES / FIXED

Fixed: 2026-07-31

## Source assets

- Character source size: 600 x 600 px.
- `hair` contains the hairstyle, head outline, and body.
- `face` contains the facial features and expression.
- The transparent face PNG is placed over the hair/body layer at the same size and position.
- The original JPEG files remain unchanged.

## Face-set rule

Each sequential face number is one character set. Numbers must never be mixed.

- `face_01_normal`, `face_01_attack`, and `face_01_damage` are one set.
- `face_02_normal`, `face_02_attack`, and `face_02_damage` are one set.
- `face_03_normal`, `face_03_attack`, and `face_03_damage` are one set.

After a face set has been selected for a wrestler, expression changes use only
the normal, attack, and damage images from that same set.

## RED / player selection

- The player hair/body layer is always `player`.
- Select one face set when a new 15-match run begins.
- Keep that face set for the entire run.
- Do not redraw the player's face set at the start of each match.

## BLUE / random opponent selection

- Select one combination of `hair_01` through `hair_07` and face set `01`
  through `03` when a normal match begins.
- Keep that hair and face combination for the entire match.
- Use a shuffle bag containing all 21 combinations.
- Do not repeat an exact combination until all 21 combinations have been used.
- Refill and reshuffle the bag after it becomes empty.

## Bosses

- Boss portraits will use fixed character illustrations when their assets are
  complete.
- The random BLUE combination system is not used for bosses.

## Approved portrait-window presentation

- Portrait-window background: white.
- Character image scale: 150%.
- Character vertical offset: 20% upward.
- Hair/body and face layers always use the same scale and offset.
- RED frame: exact RGB red (`255, 0, 0`).
- BLUE frame: exact RGB blue (`0, 0, 255`).

## Reference implementation

- `character_portrait_lab.html`
- `assets/character_portrait_lab/hair_png/`
- `assets/character_portrait_lab/face_png/`

These files are a display and behavior reference. They are not yet integrated
into `index.html`.
