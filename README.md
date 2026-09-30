[README.md](https://github.com/user-attachments/files/32841023/README.md)
# ROPE RUSH

A simple 2D browser tug-of-war game. You (left side) pull a rope against the computer (right side). Everything is in one file: `index.html` (HTML + CSS + JavaScript, no libraries).

## Target audience
Anyone who wants a quick arcade match in the browser, on desktop or mobile. Easy mode is good for beginners; Hard is for players who want a challenge.

## How to play
1. Choose a difficulty (Easy, Normal or Hard) on the main menu and press **START GAME**.
2. After the 3-2-1-GO countdown, pull the rope toward the left side with Normal Pull and Power Pull.
3. Every pull costs stamina, so choose when to pull, when to wait, and when to use a Power Pull.
4. Drag the rope to the left edge to win before the computer drags it to the right edge.

## Controls
| Action | Keyboard | Mobile / mouse |
| --- | --- | --- |
| Normal Pull | `SPACE` | NORMAL PULL button |
| Power Pull | `SHIFT` | POWER PULL button |
| Pause / resume | `P` or `ESC` | PAUSE button |

The buttons and keys call the same functions (`playerPull()` and `powerPull()`). Holding a key or button does not repeat the pull; each press is one pull.

## Game rules
- The rope position goes from 0 to 100 and starts at 50 (center).
- Player pulls move it toward 0, computer pulls move it toward 100.
- The match lasts 60 seconds.
- Input works only while the match is running (not during the countdown, pause or after the result).
- When the match ends, the timer, the bot and stamina regeneration stop. The result cannot change afterwards.

## Stamina mechanic
- Stamina goes from 0 to 100. Both the player and the computer start with 100.
- **Normal Pull:** moves the rope 5.5, costs 8 stamina.
- **Power Pull:** moves the rope 21, costs 32 stamina. It cannot be used without enough stamina (the white tick on the stamina bar shows the cost).
- Stamina regenerates 12 per second, but only after 0.4 seconds without pulling.
- Below 25 stamina, pulls move the rope only half as far (for both player and computer).
- After a Normal Pull you must wait 0.25 s, and after a Power Pull 1.2 s. The computer also waits 1.2 s after a Power Pull.

## Difficulty levels
- **Easy:** slow reactions, pulls rarely, almost never uses Power Pull.
- **Normal:** medium reaction speed, uses Power Pull sometimes and rests when its stamina is low.
- **Hard:** fast reactions, uses Power Pull very often and rests until it can afford it.

The computer follows the same stamina rules as the player. It has no hidden stamina or bonuses and only moves the rope by spending stamina on a pull.

## Win conditions
- Rope reaches 0: **PLAYER WINS**.
- Rope reaches 100: **COMPUTER WINS**.
- Time runs out: the side with the rope closer to its own edge wins (rope below 50 = player, above 50 = computer).
- If the rope is exactly at 50 when time runs out, the result is a **DRAW**.

## LocalStorage statistics
The browser saves these numbers under the key `ropeRushStats` and shows them on the main menu:
- total matches
- player wins
- computer wins

A draw counts only as a played match.

## Technologies used
HTML, CSS and plain JavaScript (no frameworks, no external files). Statistics use the browser `localStorage`.

## AI tools used
AI tools (Claude by Anthropic) helped write and check the code and this README.

## Known limitations
- Single player only, no sound.
- The difficulty balance was checked only with simulated players, not with many human testers, so it may need small changes.
- The timer is based on 100 ms game ticks, so it is accurate to about a tenth of a second.
- Statistics exist only in one browser and disappear if the site data is cleared.
- Characters are simple emoji, not custom artwork.

## How to run locally
1. Save the file as `index.html`.
2. Double-click it (or open it in Chrome / Edge / Firefox / Safari).
3. Press START GAME. No installation or server is needed.
