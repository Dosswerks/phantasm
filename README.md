# Phantasm: Silver Spheres

*The Tall Man is waiting. Mike needs you.*

Phantasm: Silver Spheres is an arcade platformer inspired by Donkey Kong, Keystone Kapers, and Jumpman, skinned with the horror aesthetic of the Phantasm movie franchise. The player controls Reggie, navigating single-screen mausoleum levels to rescue Mike Pearson from the Tall Man.

---

## Gameplay

Each level is a single screen with 5-7 randomly generated platform tiers connected by ladders. Reggie starts at the bottom next to his parked Hemicuda. Mike is held captive at the top in a red-curtained alcove, guarded by the Tall Man who towers over the level flanked by silver columns.

Before rescuing Mike, the player must smash a golden urn in an alcove on the opposite side of the top tier. The urn holds the binding power that imprisons Mike — destroying it breaks the spell and frees him. The player moves left/right, climbs ladders up and down, jumps, and fires a shotgun to destroy enemies. Portal columns on two different platforms allow instant teleportation between them.

## Enemies

Enemies are introduced progressively:

- Level 1: Dwarf Servants — hooded figures with red eyes that emerge from barrel stacks and walk toward the player. One shot to destroy. 50 points.
- Level 2: Sentinel Spheres — fly in sweeping curved paths across the screen, spikes facing their direction of travel. Level 3+ adds slight player tracking. One shot to destroy. 100 points.
- Level 3: Gravers — slow zombie-like figures in brown clothes and gas masks carrying shovels. Patrol back and forth across tiers in alternating directions. Three shots to destroy. 150 points.
- Level 4: Hearse — drives across a random platform at high speed. Cannot be destroyed. Avoid it.
- Level 5: Crematorium — no enemies on first visit. Touching furnaces is fatal.
- The Tall Man — stands at the top of each level. Cannot be destroyed. Touching him is fatal.

After level 5, the cycle repeats with Sentinel Spheres always present alongside the level's primary enemy. Spawn rates increase each cycle.

## Controls

**Desktop:**
- Arrow keys: Move left/right, climb up/down
- Z: Jump
- X: Fire shotgun
- R: Restart
- Q: Quit to title

**Mobile:**
- D-pad: Movement and climbing
- JUMP button: Jump
- FIRE button: Shotgun

## Scoring

| Action | Points |
|---|---|
| Destroy sphere | 100 |
| Destroy dwarf | 50 |
| Destroy graver | 150 |
| Smash urn | 200 |
| Rescue Mike | 1000 |

Extra life every 10,000 points. Game starts with 3 lives.

## Difficulty Progression

- Level 1: Dwarves only, clear paths
- Level 2: Spheres only, curved flight paths
- Level 3: Gravers only, patrol and jump
- Level 4: Hearse only, avoid at all costs
- Level 5: Crematorium, no enemies on first visit
- Level 6+: Cycle repeats, spheres always present, faster spawn cycles

## Level Design

Each level features:
- 5-7 randomly generated platform tiers spanning the full canvas
- Ladders connecting each tier (never overlapping vertically)
- Two barrel stacks (dwarf spawn points) on different tiers
- Two portal column pairs on different tiers for teleportation
- Golden urn in a red-curtained alcove (must smash to free Mike)
- Mike in a red-curtained alcove on the opposite side of the top tier
- The Tall Man towering over the top level, flanked by silver columns
- Parked Hemicuda at the bottom-left as a background element
- Mausoleum crypt wall background behind the top tier

---

## Technical Details

### Architecture

Single-file HTML5 Canvas game with no external dependencies. All game logic, rendering, audio, and input handling in one `index.html`.

### Asset System

```javascript
const A = {
    boxArtImage: 'assets/box-art.png',
    reggieLeft: 'assets/reggie-left.png',
    reggieRight: 'assets/reggie-right.png',
    reggieClimb: 'assets/reggie-climb.png',
    mikeImage: 'assets/mike.png',
    tallManImage: 'assets/tallman.png',
    tallManFallImage: 'assets/tall-man-fall.png',
    sphereImage: 'assets/sphere.png',
    dwarfImage: 'assets/dwarf1.png',
    dwarfImage2: 'assets/dwarf2.png',
    graverImage: 'assets/graver1.png',
    graverImage2: 'assets/graver2.png',
    hearseImage: 'assets/hearse.png',
    hemicudaImage: 'assets/hemicuda.png',
    columnImage: 'assets/column.png',
    shotgunBlast: 'assets/shotgun.mp3',
    sphereDestroy: 'assets/sphere-destroy.mp3',
    dwarfDestroy: 'assets/dwarf-destroy.mp3',
    graverDestroy: 'assets/graver-destroy.mp3',
    playerDeath: 'assets/death.mp3',
    gameoverSound: 'assets/gameover.mp3',
    rescueSound: 'assets/rescue.mp3',
    levelSound: 'assets/level.mp3',
    hearseSound: 'assets/hearse.mp3',
    dwarfSpawn: 'assets/dwarf-spawn.mp3',
    sphereSpawn: 'assets/sphere-spawn.mp3',
    graverSpawn: 'assets/graver-spawn.mp3',
    gameoverSound: 'assets/gameover.mp3',
    teleportSound: 'assets/teleport.mp3',
    jumpSound: 'assets/jump.mp3',
    tallManFallSound: 'assets/tallman-fall.mp3',
    tallManBurnSound: 'assets/tallman-burn.mp3',
    leverSound: 'assets/lever.mp3',
    backgroundMusic: 'assets/music.mp3',
};
```

### Image Specs

| Asset | Dimensions | Format | Notes |
|---|---|---|---|
| Box Art | Any | PNG/JPG | Splash screen, object-fit cover |
| Reggie Left | 32 × 40 px | PNG w/ transparency | Facing left |
| Reggie Right | 32 × 40 px | PNG w/ transparency | Facing right |
| Reggie Climb | 32 × 40 px | PNG w/ transparency | Climbing ladder |
| Mike | 24 × 36 px | PNG w/ transparency | Captive in alcove |
| Tall Man | 40 × 70 px | PNG w/ transparency | Towering over top level |
| Sphere | 24 × 24 px | PNG w/ transparency | Silver sentinel sphere |
| Dwarf | 20 × 28 px | PNG w/ transparency | Hooded servant |
| Graver | 24 × 54 px | PNG w/ transparency | Gas mask zombie with shovel (2 frames) |
| Hearse | 70 × 24 px | PNG w/ transparency | Black hearse |
| Hemicuda | 100 × 40 px | PNG w/ transparency | Parked muscle car |
| Column | 16 × 50 px | PNG w/ transparency | Silver column |

### Sound Specs

| Asset | Duration | Format | Notes |
|---|---|---|---|
| shotgun | 0.3–0.5 sec | MP3 | Shotgun blast |
| sphere-destroy | 0.2–0.4 sec | MP3 | Sphere destroyed |
| dwarf-destroy | 0.2–0.3 sec | MP3 | Dwarf destroyed |
| graver-destroy | 0.3–0.5 sec | MP3 | Graver destroyed |
| death | 0.3–0.5 sec | MP3 | Player death with blood splash |
| gameover | 1.0–2.0 sec | MP3 | Game over |
| rescue | 0.5–1.0 sec | MP3 | Mike rescued / urn collected |
| level | 0.5–1.0 sec | MP3 | Level complete |
| hearse | 0.5–1.0 sec | MP3 | Hearse drives across |
| dwarf-spawn | 0.2–0.4 sec | MP3 | Dwarf appears from barrels |
| sphere-spawn | 0.2–0.4 sec | MP3 | Sphere enters screen |
| graver-spawn | 0.3–0.5 sec | MP3 | Graver walks on from edge |
| gameover | 1.0–2.0 sec | MP3 | Game over |
| teleport | 0.2–0.4 sec | MP3 | Portal teleport |
| jump | 0.1–0.3 sec | MP3 | Reggie jumps |
| tallman-fall | 0.5–1.0 sec | MP3 | Tall Man falling |
| tallman-burn | 0.5–1.0 sec | MP3 | Tall Man hits furnace |
| lever | 0.2–0.4 sec | MP3 | Lever pulled in crematorium |
| music | 30–120 sec | MP3 | Background music, loops |

### File Structure

```
phantasm/
  index.html
  story.html
  README.md
  assets/
    box-art.png
    reggie-left.png
    reggie-right.png
    reggie-climb.png
    mike.png
    tallman.png
    tall-man-fall.png
    sphere.png
    dwarf1.png
    dwarf2.png
    graver1.png
    graver2.png
    hearse.png
    hemicuda.png
    column.png
    shotgun.mp3
    sphere-destroy.mp3
    dwarf-destroy.mp3
    graver-destroy.mp3
    death.mp3
    gameover.mp3
    rescue.mp3
    level.mp3
    hearse.mp3
    dwarf-spawn.mp3
    sphere-spawn.mp3
    graver-spawn.mp3
    gameover.mp3
    teleport.mp3
    jump.mp3
    tallman-fall.mp3
    tallman-burn.mp3
    lever.mp3
    music.mp3
```

---

## Credits

Concept, design, art direction, and audio: [Andrew Doss](https://www.andrewdoss.com/)

Game engine and code: Built with Kiro AI-assisted development

Based on characters and concepts from the Phantasm film franchise.

Hosted on GitHub Pages
