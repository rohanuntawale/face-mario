# 🎮 Face Mario

A small Mario-style platformer in **one file** (`index.html`) — no build tools, no dependencies.
The player character is **your own image**. 6 themed levels, title screen, pause menu,
synthesized sound effects and a saved high score.

## Put your face in the game

1. Take any picture of yourself (a square-ish photo with a plain background works best).
2. Name it **`face.png`** and drop it next to `index.html`.
   - Also accepted: `face.svg`, `face.jpg`, `face.jpeg`, `face.gif`, `face.webp`
   - A cute built-in smiley is used until you add your own file.
3. Open `index.html` in a browser. That's it — that's you jumping on goombas.

> Tip: a photo with a transparent background looks best. You can remove the background
> for free at remove.bg, or ask your AI assistant to do it.

## Controls

| Action | Keys | Touch |
|---|---|---|
| Move | ← → or A D | ◀ ▶ buttons |
| Jump (hold = higher) | Space / ↑ / W / Z | A button |
| Run | Shift | B button |
| Shoot fireball (when powered) | X or F | 🔥 button |
| Pause | P or Esc | on-screen buttons |
| Sound on/off | M | on-screen buttons |
| Menus / confirm | Enter or click the buttons | tap the buttons |
| Restart level | R | — |

## What's in the game

- **6 themed levels** (each 252 tiles wide): Green Hills, Sunset Coast, Starry Night, The Underground (cave ceilings!), Frostbite Peaks (falling snow), The Keep — ending in a **boss fight** instead of a flagpole
- **Full game flow**: title screen → level intro banners → play → level clear → ending screen, with pause, game over and continue
- **Countdown timer per level** (300s on the early levels, 260s on the tough ones) — a red flashing ⏱ and a warning jingle when you're under 60 seconds. Time runs out = you lose a life. Reach the flagpole and every remaining second converts into bonus score with the classic ticking drain!
- Coins and `?` blocks (head-butt them for coins)
- **Power-ups: 🍄 mushroom makes your face GROW (small → big), 🔥 fire flower lets you throw bouncing fireballs (max 2 on screen). Get hit while powered and you shrink instead of dying, with a moment of invincibility — but die and you lose your power-up!**
- Goombas you can stomp (bounce higher if you hold jump) — or roast with fireballs
- **Bob-ombs** that patrol with wind-up keys on their heads: touch or stomp one and the fuse lights — run! Fireballs light them too, and a lit bomb's blast chains every other bomb nearby. Blast radius hurts you, so kick the fuse and get clear (or stomp, which bounces you to safety)
- **Secret brick vaults** (cracked bricks) — only a big head-bump or a fireball can smash them, and every one hides a coin stash. Small Mario just thuds off them. One vault per level, so there's always a secret you can't open on your first life
- **Armored bomb-vaults** (riveted steel walls) — in the later levels, sealed coin chambers that nothing else can open: fireballs bounce off, head-bumps just thud. Every chamber has a bob-omb parked by its door — kick it, stand clear, and let the blast blow the wall open. Bigger stash, bigger boom
- **🤴 BOSS: The Warden** — a hulking King Bob-omb with a crown guards the end of The Keep. Fireballs and stomps **clank off him** — the only thing that hurts him is explosions. Two stationary bomb depots flank his arena: bait the hopping Warden close to a depot, light one bomb, and the whole depot dominoes into him (3 damage per depot). He hops at you with landing shockwaves, and at 2 HP he **enrages**. Two clean chains beat him for a +15 bonus and a victory screen before the ending
- Synthesized retro sound effects (WebAudio, no files) — jump, coins, stomps, death jingles, victory fanfare; mute with M
- **Save file** (localStorage): best score, per-level best times, and which levels you've cleared — shown on the title screen, level intros, the clear banner and the ending. Beat a best time and the banner announces it!
- Countdown timer per level — time runs out = you lose a life; leftover time converts into bonus score at the flag
- Flagpole slide, fireworks, squash-and-stretch animation, parallax backdrops
- Touch controls on phones

## Open-source Mario-like games worth studying

If you want to go further than one file, these are real, actively maintained open-source projects:

| Project | What it is |
|---|---|
| **[SuperTux](https://www.supertux.org/)** | Full native C++ Mario-like game (huge codebase) |
| **[Secret Maryo Chronicles](https://github.com/SecretMaryo/SecretMaryo-Chronicles)** | Another full C++ Mario-like |

⚠️ Note: Nintendo's actual Mario art, sounds and level designs are copyrighted — that's why
these projects use original assets, and why putting **your own face** in this game is the
perfectly safe (and more fun) option.

## Make it yours

**Your face:** drop `face.png` (or `.jpg` / `.webp` / `.gif`) next to `index.html` — a square
crop with a plain background looks best. `face.svg` is just the placeholder smiley; overwrite
or ignore it. If no image file is found, the game uses a built-in smiley.

**The levels:** open `index.html` and find the `LEVELS` array — each level is a `makeLevel(name, palette, builder, time)`
with a handful of readable calls (the last argument is the time limit in seconds):

```js
ground(0, 17); ground(21, 54);      // floor segments; gaps between = deadly pits
pipe(30, 14);                        // pipe at column 30, 2 tiles tall
plat(66, 69, 13);                    // floating platform
row(62, 12, '?B?B');                 // bricks & ?-blocks (bump from below)
coins(17, 21, 13);                   // coin arcs over pits
put(63, 11, 'M');                    // mushroom pickup ('W' = fire flower)
bomb(100); bomb(106);                // bob-omb nest — light one, watch the chain
vault(182, 185);                     // secret brick vault: fireball a side wall or smash the roof
[12, 26, 40].forEach(goomba);        // enemy spawn columns
stair(222, 8); flag(236);            // final staircase + flagpole
```

Move things around, add sections, make it yours. Game feel lives in the constants near the
top (`GRAV`, `JUMP_V`, `RUN_MAX`…).

## Want more?

Ask your AI assistant to add: more levels, a two-player mode, a level editor, or a world map.
