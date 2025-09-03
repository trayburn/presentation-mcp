# Asteroids — Bake-Off Edition  
### PyGame single-level demo for Claude Code CLI vs Cursor

---

## 1 Goal  
Create a compact, showcase-quality Asteroids clone in **Python 3.12 + PyGame 2.x** that each CLI tool can generate end-to-end from this single prompt.

---

## 2 Gameplay at a Glance  

| Element | Spec |
|---------|------|
| **Opening screen** | Large ASCII-art title **“Asteroids”**, subtitle **“Built by Improving”**, and flashing text **“Press Enter”**. |
| **Single level** | Large, medium, and small asteroids enter from any side and float in a direct line until destroyed or they reach the other side. |
| **Player ship** | Ship is a simple small triangle. Starts in middle. Up arrow fires jets. The longer it is pressed, the faster the ship moves. Down arrow slows ship. The longer it is pressed, the faster it slows. Turn with ← / → arrows. Fire dots with space bar. |
| **Asteroids** | Asteroids are randomly shaped combinations of small squares and small triangles but hollow inside. Classic Asteroids physics. Dots fired from ship destroy small asteroids, break up medium asteroids into 2 small asteroids and large asteroids into 2 medium asteroids. Asteroids increase in count every 10 seconds starting with 4.  |
| **Win state** | When 30 total asteroids are destroyed entirely, show sprite-based fireworks and flashing overlay **“CONGRATS IMPROVER”** for ~5 s, then return to title. |
| **Lose state** | If an asteroid hits the player ship, ship explodes. |

---

## 3 Functional Requirements  

1. **Title Screen**  
   - Render ASCII banner using the following ASCII-art:
```
            _____ _______ ______ _____   ____ _____ _____   _____ 
     /\    / ____|__   __|  ____|  __ \ / __ \_   _|  __ \ / ____|
    /  \  | (___    | |  | |__  | |__) | |  | || | | |  | | (___  
   / /\ \  \___ \   | |  |  __| |  _  /| |  | || | | |  | |\___ \ 
  / ____ \ ____) |  | |  | |____| | \ \| |__| || |_| |__| |____) |
 /_/    \_\_____/   |_|  |______|_|  \_\\____/_____|_____/|_____/

```
   - Subtitle and flashing **“Press Enter”** underneath.  
   - `<Enter>` or `<Space>` starts the game.  

2. **Screen Dimensions**  
   - `SCREEN_WIDTH  = 1024`, `SCREEN_HEIGHT = 800`.  

3. **Ship Details and Mechanics**  
   - Ship speed = 0-10 px/frame. Starts at stationary in center of screen pointing up.
   - Top of triangle from starting position is the front of the ship for the entire game regardless of direction.
   - Ship increases speed by 1 on each up arrow. Decreases speed by 1 on each down arrow.
   - Ship speed = 0-10 px/frame. Starts at 0.  
   - Ship turns 1 degree on each left or right arrow in the direction of the arrow.   
   - Space bar fires a '.' from the front of the ship.

4. **Asteroid Layout Generator**  
   - Asteroid starting side, position, and direction varies. 
   - Large asteroid is `16 px x 16 px.  
   - Medium asteroid is `8 px x 8 px.  
   - Small asteroid is `4 px x 4 px.  
   - Speed of asteroids is 2 px/frame initially and each new asteroid travels 2 px/frame faster. 


5. **Fireworks Celebration**  
   - Load 4‑8 tiny PNG sprite sheets **or** draw procedural bursts.  
   - Overlay bold, flashing **“CONGRATS IMPROVER”** (400 ms on / 400 ms off).

6. **Game States & Loop**  
   - States: `TITLE`, `PLAYING`, `VICTORY`.  
   - `<Esc>` quits; `<F1>` toggles fullscreen; `<Ctrl+L>` clears level.

---

## 4 Non-Functional Requirements  

```
Asteroids/
├── main.py
├── assets/
│   └── fireworks/*.png
└── README.md
```

* ≤ 2000 LOC total; clarity over brevity.  
* Classes: `Game`, `Ship`, `LargeAsteroid`, `MediumAsteroid`, `SmallAsteroid`, `FireworksManager`.  
* No external deps beyond PyGame + stdlib.

---

## 5 Acceptance Criteria  

- `python main.py` shows title in < 2 s.
- Enter fades title and spawns level in < 1 s.
- Level clear triggers fireworks & message for ≈ 5 s.
- No uncaught exceptions during a 3‑min play-test.
- Runs on Windows 10/11 & macOS 14 (ARM/Intel).
- As a cheat code for demo purposes, Ctrl+L (for Windows) or Cmd+L (for MacOS) will complete the level.

---

## 6 Stretch Goals (skip if time‑boxed)

- Simple bounce SFX (wav/ogg).  
- Ship jet glows on hit.  
- `config.json` for easy tuning.

---

## 7 Hand‑Off Instructions  

> **Generate all source files** exactly as described above.  
> If assets are missing, create placeholder PNGs via code.  
> Output each file’s contents (or provide a ZIP link) so the project runs out‑of‑the‑box.
