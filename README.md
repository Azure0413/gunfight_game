# ARMS RACE — Browser Gun Game

A fast-paced, top-down **Gun Game** built entirely with vanilla HTML, CSS, and JavaScript. Fight against five AI-controlled opponents, progress through ten weapon tiers, and secure the final elimination with the **Golden Knife**.

> No framework, package manager, build tool, or external asset is required. Open the game in a modern browser and play.

<p align="center">
  <a href="YOUR_LIVE_DEMO_URL"><strong>Play Live Demo</strong></a>
  ·
  <a href="#controls"><strong>Controls</strong></a>
  ·
  <a href="#deployment"><strong>Deploy</strong></a>
</p>

<!-- Replace the image below with a screenshot or GIF of the game. -->
<!-- ![ARMS RACE gameplay](./assets/arms-race-preview.gif) -->

## Overview

ARMS RACE is a complete single-player browser shooter inspired by the classic Gun Game mode. Each elimination advances the player to the next weapon. The first combatant to reach the final tier and score a Golden Knife elimination wins the match.

The project was designed as a self-contained portfolio piece that demonstrates real-time game programming, AI behavior, pathfinding, collision detection, procedural audio, responsive HUD design, and state management without relying on a game engine.

## Highlights

- **6-player free-for-all:** one human player and five AI opponents
- **10 weapon tiers:** pistol, SMG, shotgun, burst rifle, assault rifle, LMG, sniper, launcher, magnum, and Golden Knife
- **Three difficulty levels:** Recruit, Regular, and Veteran
- **Advanced bot behavior:** Hunt, Combat, and Retreat states with distinct AI personalities
- **A\* pathfinding:** grid-based navigation with path smoothing and obstacle avoidance
- **Line-of-sight combat:** raycast checks, strafing, reaction delays, burst timing, and aim variation
- **Gun Game rules:** weapon upgrades, knife demotions, self-destruct penalties, and final-weapon victory
- **Complete combat feedback:** hit markers, kill feed, announcements, particles, damage indicators, shell casings, screen shake, and camera look-ahead
- **Procedural sound:** weapon effects and background music generated through the Web Audio API
- **Full match interface:** timer, health, ammo, reload progress, weapon ladder, scoreboard, pause menu, and post-match statistics
- **Zero dependencies:** everything runs from a single HTML file

## Gameplay

Every player begins with the **P-9 Pistol**. Eliminating an opponent upgrades the killer to the next weapon tier. A quick-knife elimination demotes the victim by one tier, while eliminating yourself with the Havoc Launcher also causes a demotion.

The match lasts **7 minutes**. A player wins immediately by scoring an elimination with the Golden Knife. If time expires first, the player on the highest weapon tier wins, with total eliminations used as the tie-breaker.

Additional mechanics include:

- Eliminations restore **25 HP**
- Green healing pads restore **40 HP** and respawn after a cooldown
- Players respawn without losing their current weapon tier
- Dash movement provides short bursts of mobility
- Kill streaks and multi-kills trigger special announcements

## Controls

| Input | Action |
|---|---|
| `W` `A` `S` `D` | Move |
| Mouse | Aim |
| Left Mouse Button | Fire / use Golden Knife |
| `R` | Reload |
| `F` or Right Mouse Button | Quick knife attack |
| `Shift` | Dash |
| `Tab` | Hold to view scoreboard |
| `P` or `Esc` | Pause / resume |

> The current control scheme is optimized for desktop browsers with a keyboard and mouse.

## Weapon Progression

| Tier | Weapon | Type |
|---:|---|---|
| 1 | P-9 Pistol | Semi-automatic pistol |
| 2 | Viper SMG | Automatic submachine gun |
| 3 | Jackal Shotgun | Multi-pellet shotgun |
| 4 | Trident Burst | Three-round burst rifle |
| 5 | AR-15 Rifle | Automatic assault rifle |
| 6 | M60 LMG | High-capacity machine gun |
| 7 | Longshot Sniper | High-damage precision rifle |
| 8 | Havoc Launcher | Area-of-effect rocket launcher |
| 9 | Magnum .44 | High-damage revolver |
| 10 | Golden Knife | Final melee weapon |

## AI System

Each bot combines a high-level finite-state machine with lower-level combat behavior.

### Behavior states

- **Hunt:** locate and navigate toward a target
- **Combat:** maintain a weapon-appropriate distance, strafe, aim, and attack
- **Retreat:** seek an available healing pad when health is low

### Navigation and combat

- Grid-based A\* pathfinding
- Greedy path smoothing for more natural movement
- Wide line-of-sight checks for traversable routes
- Obstacle-aware steering and stuck recovery
- Target prioritization based on distance, visibility, and enemy weapon tier
- Weapon-specific engagement distances
- Difficulty-dependent reaction speed, movement speed, and aim error
- Distinct bot personalities such as aggressive, accurate, evasive, flanking, and knife-focused behavior

## Technical Details

| Area | Implementation |
|---|---|
| Rendering | HTML5 Canvas 2D API |
| Game loop | `requestAnimationFrame` with delta-time updates |
| Audio | Web Audio API with procedurally generated tones and noise |
| AI | Finite-state machine, target scoring, and A\* pathfinding |
| Physics | Circle-vs-rectangle collision resolution and projectile simulation |
| Effects | Particles, decals, camera shake, hit markers, floating damage, and corpses |
| Interface | HTML/CSS HUD layered above the Canvas |
| Dependencies | None |

## Run Locally

### Option 1: Open directly

Download the project and open `gun-game.html` in a modern desktop browser.

### Option 2: Start a local server

Using Python:

```bash
python -m http.server 8000
```

Then visit:

```text
http://localhost:8000/gun-game.html
```

Using Node.js:

```bash
npx serve .
```

## Deployment

Because the project is fully static, it can be deployed for free with GitHub Pages, Vercel, Netlify, Cloudflare Pages, or any static web host.

### GitHub Pages

1. Rename `gun-game.html` to `index.html` so the game loads from the site root.
2. Push `index.html` and this `README.md` to a GitHub repository.
3. Open the repository's **Settings → Pages**.
4. Under **Build and deployment**, choose **Deploy from a branch**.
5. Select the `main` branch and the `/ (root)` folder.
6. Save the settings and add the generated URL to the **Play Live Demo** link at the top of this README.

### Vercel or Netlify

1. Rename `gun-game.html` to `index.html`.
2. Import the GitHub repository into Vercel or Netlify.
3. Leave the build command empty because no build process is needed.
4. Set the output or publish directory to the repository root.
5. Deploy and replace `YOUR_LIVE_DEMO_URL` with the production URL.

## Project Structure

```text
arms-race/
├── index.html       # Complete game, styles, UI, audio, and logic
├── README.md        # Project documentation
└── assets/          # Optional screenshots, GIFs, or social preview images
```

The uploaded source file is currently named `gun-game.html`. For production hosting, renaming it to `index.html` is recommended.

## Browser Support

The game is intended for recent versions of:

- Google Chrome
- Microsoft Edge
- Mozilla Firefox
- Safari

JavaScript and the Web Audio API must be enabled. Audio begins after the first user interaction because of browser autoplay restrictions.

## Suggested Portfolio Description

> ARMS RACE is a dependency-free browser shooter developed with HTML5 Canvas and vanilla JavaScript. It features a complete Gun Game progression system, five personality-driven AI opponents, finite-state combat behavior, A\* pathfinding, real-time projectile simulation, procedural Web Audio, and a polished responsive HUD—all contained in a single deployable HTML file.

## Future Improvements

- Mobile and gamepad controls
- Additional maps and environment hazards
- Local multiplayer or WebSocket-based online multiplayer
- Persistent settings and statistics
- More weapons, game modes, and AI personalities
- Improved accessibility options
- Automated gameplay and regression tests

## License

Choose and add a license before publishing the repository. The [MIT License](https://choosealicense.com/licenses/mit/) is a common option for portfolio projects that you want others to view, use, and modify.

---

Built as a lightweight demonstration of browser game development, AI behavior design, and interactive UI engineering.
