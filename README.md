# Night City Runner

A browser-based 3D neon driving and police-pursuit prototype, presented in two independently generated implementations: **DeepSeek** and **ChatGPT**. Both use Three.js and keep the game implementation in a single HTML file per version.

## Play and inspect

- **DeepSeek version (original):** open [`index.html`](./index.html)
- **ChatGPT version:** open [`chatgpt/index.html`](./chatgpt/index.html)

The ChatGPT version is stored in its own directory so it does not overwrite the original DeepSeek source. Both versions load Three.js from a CDN and therefore need an internet connection.

## What is in the game?

Both versions aim to deliver a neon-soaked, cyberpunk-inspired driving experience with police pursuit, escape and interception objectives, keyboard controls, a HUD, procedural city scenery, and synthesized game audio. Their implementations differ in visual style, AI, and gameplay systems.

## Implementation comparison

| Area | DeepSeek version (`index.html`) | ChatGPT version (`chatgpt/index.html`) |
| --- | --- | --- |
| Visual direction | Stylized/toon-shaded city, outlined vehicle geometry, high-contrast cyan/magenta/yellow palette | More realistic-looking PBR/physical materials, rainy neon atmosphere, screen-space visual effects, detailed car surfaces and lighting |
| City rendering | Procedurally generated tile-based city with cached building textures and instanced traffic | Procedural city chunks, generated textures, road/path helpers and chunk updates around the player |
| Pursuit AI | Wanted-level escalation with police reinforcements, roadblocks and helicopter/spike-strip systems | Police pathfinding around obstacles, a dedicated AI getaway target in Pursuit mode, and collision-driven interception |
| Game systems | Wanted stars, escape timer/cooldown, EMP, item/repair logic, score and near-miss tracking | Escape and Pursuit modes, target-health system, EMP and smoke abilities, repair locations, combo/score, and best-score persistence |
| Vehicle customization | Three selectable color schemes and three camera views | Distinct player/interceptor/target vehicle presentation and multiple camera views |
| Source organization | About 3,350 source lines, formatted across many readable lines | A compact, heavily minified/generated source file; much larger on disk because substantial image/texture data is embedded |
| External dependencies | Three.js 0.169.0 and add-ons from UNPKG | Three.js 0.169.0 and add-ons from jsDelivr |

This comparison describes features visible in the source, not a claim that every feature has passed hands-on gameplay testing. Rendering quality and performance depend on browser, GPU, display resolution, and network access.

## Overall assessment

**For the requested balance of visual realism and an engaging playable prototype, the ChatGPT version has a slight edge in presentation and the focused interception loop.** Its use of physical materials, rain/atmospheric effects, a separate AI getaway target, target health, smoke, and repair locations gives it a stronger realistic-racing direction and a more explicit objective in Pursuit mode.

**The DeepSeek version is the stronger source-code handoff and has the broader visible police-escalation fantasy.** Its readable multi-line source is easier to inspect and maintain, and its wanted-level progression, police reinforcements, roadblocks, helicopter and spike-strip concepts create a more varied pursuit sandbox. It also has three explicit vehicle color schemes.

| Evaluation dimension | Edge | Reason |
| --- | --- | --- |
| Realistic visual direction | ChatGPT | Physical materials and rain/neon presentation better match a realism-oriented brief |
| Readability and maintainability | DeepSeek | The source is formatted across thousands of readable lines rather than being heavily minified |
| Police escalation systems | DeepSeek | More explicit wanted-level response variety is implemented in the source |
| Dedicated interception target | ChatGPT | Pursuit mode has a separate AI suspect with its own health and movement |
| Easy source review | DeepSeek | Smaller, more readable source makes inspection and future edits easier |
| Overall for a visual-first demo | ChatGPT, narrowly | Stronger material/atmosphere direction and a clear target-interception loop; this is a source-based judgment, not a measured benchmark |

**Verdict:** ChatGPT wins narrowly for the requested visual direction and focused Pursuit-mode gameplay; DeepSeek wins on source readability and breadth of police-escalation mechanics. Neither should be treated as a finished, fully verified game without browser testing and further balancing.

## Run locally

Use a modern browser with WebGL and ES module/import-map support. Python 3 can serve the repository from its root:

```bash
git clone https://github.com/bookid284-art/night-city-runner.git
cd night-city-runner
python3 -m http.server 8000 --bind 127.0.0.1
```

Then open:

- DeepSeek: <http://localhost:8000/>
- ChatGPT: <http://localhost:8000/chatgpt/>

Press `Ctrl+C` to stop the server. No npm install, build step, backend, or API key is required. Opening through a local HTTP server is recommended instead of using a `file://` URL.

## Controls

| Key | Action |
| --- | --- |
| `W` / Up | Accelerate |
| `S` / Down | Brake / reverse |
| `A` / Left, `D` / Right | Steer |
| `Space` | Handbrake / drift |
| `Shift` | Nitro boost |
| `Q` | EMP |
| `E` | Use item / repair (implementation-dependent) |
| `F` | Smoke (ChatGPT version) |
| `C` | Change camera |
| `R` | Reset / restart (implementation-dependent) |
| `P` / `Esc` | Pause (implementation-dependent) |
| `M` | Toggle sound |

The on-screen controls and exact key behavior can differ slightly between versions; refer to each game's in-menu instructions.

## Project files

| Path | Purpose |
| --- | --- |
| `index.html` | Original DeepSeek-generated game |
| `chatgpt/index.html` | ChatGPT-generated alternative |
| `README.md` | English setup guide and implementation comparison |
| `.gitignore` | Common local-file exclusions |

## Technical notes and limitations

- Both implementations are AI-generated prototypes; source inspection alone does not establish that every mechanic works correctly in every browser.
- Both depend on a CDN for Three.js, so they are not fully offline.
- No project license has been selected. Third-party dependencies remain subject to their respective licenses.
