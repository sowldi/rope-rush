# ROPE RUSH

A black-and-white pixel-art tug-of-war game for the browser. One file (`index.html`) with plain HTML, CSS and JavaScript. No libraries, no server, no external files or fonts: it works offline. Just open `index.html`.

## Game modes
- **VS Computer**: you (left) against the computer (right). Difficulty: Easy / Normal / Hard. The computer picks a random character and follows the same stamina rules as you.
- **2 Player**: two people on the same keyboard/device. No online multiplayer, no server, no accounts.
- **Training**: no opponent. Practice pulls, use RESET TRAINING or BACK TO MENU.

VS Computer and 2 Player can be played as **Best of 3** (first to 2 rounds, round 3 is the FINAL ROUND) or as a single round. A drawn round is replayed in Best of 3.

## Rope and rules
Rope `0` = left side wins, `50` = center, `100` = right side wins. A round lasts 60 seconds; when time runs out, the side the rope is closer to wins (exactly 50 = draw).

## Characters
Small differences only:
| Character | Difference |
|---|---|
| Rookie | Balanced (Normal Pull 5.5, Power Pull 21, cost 8, regen 12/s) |
| Runner | Regen 14/s, Power Pull 19 |
| Strongman | Power Pull 23, regen 10/s |
| Ninja | Normal Pull costs 7 stamina, moves 5 |

## Stamina (same for everyone)
Max 100. Normal Pull costs 8 (Ninja 7), waits 0.25 s. Power Pull moves 21 (character-dependent), costs 32, waits 1.2 s. Stamina regenerates after 0.4 s without pulling. Below 25 stamina, pull strength is halved. A pull is refused if there is not enough stamina.

## Combo and comeback (human players only, not Training)
- **Combo**: Normal Pulls within 1 second build `COMBO x2, x3...` (x3 = +8%, x4+ = +15%). Power Pull resets it.
- **Comeback**: when a human player is losing badly (rope beyond 70% toward the opponent) they get `COMEBACK!`: +20% Normal Pull and +50% stamina regen, until the rope is back within 60%. The computer gets neither.

## Controls
| Mode | Normal Pull | Power Pull | Pause |
|---|---|---|---|
| VS Computer / Training | SPACE | SHIFT | P or ESC |
| 2 Player, Player 1 | A | W | P or ESC |
| 2 Player, Player 2 | L | O | P or ESC |

One key press = one pull; holding a key does not repeat. On phones use the big NORMAL PULL / POWER PULL / PAUSE buttons (in 2 Player each player has their own button column). Input works only while a round is running.

## Visual style
Black, white and gray pixel/arcade look using system monospace font, square borders, hard shadows and stepped CSS animations (idle bobbing, pull, power pull, win, lose). Power Pull shakes and flashes the arena. THEME toggles dark/light (saved).

## Other features
Sound (Web Audio beeps, toggle button, starts after your first click), pause/resume, rematch (PLAY AGAIN), MAIN MENU, responsive layout with controls fixed at the bottom.

## LocalStorage
- `ropeRushStats`: matches, match wins/losses/draws, rounds, round wins/losses, best combo. Only **VS Computer** games are recorded.
- `ropeRushTheme`: dark or light.
