# Marooned on Mars: Session Summary

NASA Space Apps Challenge 2026 entry (event 14-15 Nov 2026), challenge "Interplanetary Survival Guide: Martian Map".

## How the project evolved
1. **Brainstorm.** Started with hackathon ideas applicable to NASA. The favourite was a Google-Maps-style explorer built from Mars photos, so "Interplanetary Survival Guide: Martian Map" was chosen as the challenge.
2. **Game pivot.** The idea became **Marooned on Mars**, a single-file Three.js (r128) 3D survival game in the browser, with a greenhouse, a broken ship, gravity zones, thought bubbles above the astronaut and a Google-Maps-style list of landmarks you can teleport to.
3. **Hosting.** Deployed as a Claude artifact and on Cloudflare Workers. The repo is `asteya01/nsac-mars`.

## Main features
- **NASA terrain.** Ground built from a real Mars Trek `.obj` export, converted to a 398x398 height grid. Heights are stretched 2x, and the SHA-256 and `verify_nasa_dem.py` let anyone check the grid. The area outside the grid is procedural.
- **Real constants.** Gravity 3.71 m/s2, 610 Pa pressure, a Mars Sol Date clock for Jezero crater, and a NASA data drawer (live clock, facts, photos).
- **Vehicles and bases.** Real Curiosity and Perseverance GLB models, a drivable rover, a flyable aircraft (ARES-C), an enterable habitat with a radio and suit charger, and a greenhouse.
- **Radiation.** A solar-flare system with a buried radiation shelter and a particle-storm HUD.
- **Astronaut.** A rounded, detailed suit, an animated suit-up cutscene, a flashlight, first-person view with hand and view bobbing, a gait with foot planting, and emotes.
- **UI and tools.** A mission-ops style interface, a settings menu with rebindable controls, and a photo mode that hides all UI for presentation screenshots.

## Latest changes (this session)
- **Jump rewrite.** Mars-appropriate jump height and variable jump height (release early to jump lower). It adds a jump buffer, a short cooldown, landing absorption and airborne poses.
- **Standing-jump sink.** The foot-planting correction was pushing the body up to 20 cm into the sand after landing. The downward correction is now capped at 4 cm.
- **Arms after jumping.** Arms and legs now return to normal when standing still after a jump. Before, they stayed out until you moved.
- **Legs during jumps.** Legs keep the pose they had at take-off, with only 25% of the air pose mixed in.
- **Footprints.** Each print is now a small patch whose every vertex is sampled from the ground mesh, so it lies in the slope instead of floating over it. The texture is a dark hollow with a lifted rim, and it dims at night.
- **Solar flares.** The first flare comes after 9 minutes (was 2.5) and later ones every 20-30 minutes (was 5-7).

## Honest notes
- The terrain scale is assumed at 1 unit = 1 m, and the 2x height exaggeration is a game choice.
- Temperature, radiation inside shelters, and oxygen and battery use are modelled and tuned for play.
- All testing was by script (headless Chromium with a software renderer), not on a real GPU.
- Multiplayer was tried in a separate version but is not part of this build.
- An ankle-tilt foot animation was tried and removed at the user's request.

## Files
`index.html` (the game), `nasa_dem.js`, `curiosity_data.js`, `perseverance_data.js`, `nasa_photos.js`, `README.md`.
