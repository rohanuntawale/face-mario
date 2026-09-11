# 🎮 Face Mario

A small Mario-style platformer in **one file** (`index.html`) — no build tools, no dependencies.
The player character is **your own image**.

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
| Run | Shift or X | B button |
| Restart level | R | — |

## What's in the game

- 200-tile side-scrolling level with pits, pipes, stairs and a flagpole
- Coins and `?` blocks (head-butt them for coins)
- Goombas you can stomp (bounce higher if you hold jump)
- Lives, score, squash-and-stretch animation, parallax clouds & hills
- Touch controls on phones

## Open-source Mario-like games worth studying

If you want to go further than one file, these are real, actively maintained open-source projects:

| Project | What it is |
|---|---|
| **[walkwaterfall/mario](https://github.com/walkwaterfall/mario)** | Classic Mario clone in vanilla JS |
| **[justinapple/mario-game](https://github.com/justinapple/mario-game)** | Browser Mario with levels & sounds |
| **[ElliotKB/mariojs](https://github.com/ElliotKB/mariojs)** | Vanilla JS platformer |
| **[SuperTux](https://www.supertux.org/)** | Full native C++ Mario-like game (huge codebase) |
| **[Secret Maryo Chronicles](https://github.com/SecretMaryo/SecretMaryo-Chronicles)** | Another full C++ Mario-like |

⚠️ Note: Nintendo's actual Mario art, sounds and level designs are copyrighted — that's why
these projects use original assets, and why putting **your own face** in this game is the
perfectly safe (and more fun) option.

## Make it yours

**Your face:** drop `face.png` (or `.jpg` / `.webp` / `.gif`) next to `index.html` — a square
crop with a plain background looks best. `face.svg` is just the placeholder smiley; overwrite
or ignore it. If no image file is found, the game uses a built-in smiley.

**The level:** open `index.html` and find `buildGrid()` — the whole level is a handful of
readable calls:

```js
ground(0, 17); ground(21, 54);      // floor segments; gaps between = deadly pits
pipe(30, 14);                        // pipe at column 30, 2 tiles tall
plat(66, 69, 13);                    // floating platform
row(62, 12, '?B?B');                 // bricks & ?-blocks (bump from below)
coins(17, 21, 13);                   // coin arcs over pits
[12, 26, 40].forEach(goomba);        // enemy spawn columns
stair(222, 8); flag(236);            // final staircase + flagpole
```

Move things around, add sections, make it yours. Game feel lives in the constants near the
top (`GRAV`, `JUMP_V`, `RUN_MAX`…).

## Want more?

Ask your AI assistant to add: more levels, power-ups (mushroom = bigger head!), sound effects,
a two-player mode, or a level editor.
