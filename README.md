# Ghost Ruler

A cartoony, spooky-fun strategy game played in the browser. You command a small crew of ghosts, send them into the rooms of a house, and scare the family living there until everyone runs out the front door before dawn.

## Play

Open `index.html` and pick a version. Each version is one file in `versions/`. r2 is real 3D and needs the `vendor/` folder next to `versions/` (three.js). It runs from GitHub Pages or straight from your computer. r1 is a single flat 2D file.

If this repo has GitHub Pages turned on, the start page is the site's home page.

## How to play

- Pick a ghost, then tap a room to send it there. Your first placement of each ghost is free; moves after that cost a little Belief.
- Use the ghost's quick scare or big scare. Fear fills each person's meter. At 70% they scream and spook the rooms next door. At 100% they run.
- Scares cost **Belief**, and scaring people earns it back. Belief also trickles in slowly.
- Everyone has a weak spot (Dark, Noise or Cold) that takes double fear. It shows after you scare them once.
- Room objects boost one scare type. The skeptic calms people near him and drains Belief while sharing a room with a ghost. The radio in the Parlor calms people. The last person left inside is jumpier.
- Keys: `1` `2` `3` pick a ghost, `Q` quick scare, `E` big scare, `Space` or `Esc` pause, `R` reset the camera.
- r2 camera: drag to spin the house, scroll or pinch to zoom, or use the + / - / reset buttons. Tap a ghost to pick it, tap a room to send it.
- The night clock waits until you place your first ghost.

## Add a new version

1. Save the new game file as `versions/ghost-ruler-rN.html` (r2, r3, and so on). Leave older files in place.
2. In `index.html`, add one line at the top of the `VERSIONS` list:

   ```js
   { id: 'r2', date: 'YYYY-MM-DD', file: 'versions/ghost-ruler-r2.html', what: 'One line on what changed.' },
   ```

3. Set the version label inside the new game file (`const VERSION = 'r2'`) so it shows on screen.

All links are relative, so the site works on GitHub Pages under a sub-path.

## Swapping in real 3D models (r2)

r2 draws its own cartoon stand-ins. Any piece can be replaced by a `.glb` model without touching the rest:

1. Put the model in `assets/models/` and add its license to `CREDITS.md`.
2. In `versions/ghost-ruler-r2.html`, add a line to `ASSET_MAP`, for example `rocking_horse: { url: '../assets/models/rocking-horse.glb' }`. Optional: `scale`, `rotY`, `toon: false`, `outline: false`.
3. The model is sized to fit where the stand-in was. If it fails to load, the stand-in stays.

Slot names: tree, bush, pumpkin, fence_post, rocking_horse, boxes, bed, wardrobe, nightstand, rug, bathtub, mirror, sink, bath_mat, fridge, counter, wall_clock, table, sofa, radio, rug_round, picture, grandfather_clock, coat_rack, plant, front_door, doormat.

Models load only over http(s) (GitHub Pages), not from a double-clicked file.

## Files

- `index.html` is the start page and version picker.
- `versions/` holds one playable file per version.
- `vendor/` holds three.js and its model loader (MIT).
- `CREDITS.md` lists everything made by others and its license.
