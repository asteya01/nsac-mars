# Marooned on Mars

A 3D Mars survival game built for the NASA International Space Apps Challenge 2026. You are stranded in Jezero crater: harvest tomatoes, call Earth from the base radio, shelter from a solar flare, run the Curiosity instruments, drive the rover and fly the ARES-C aircraft.

Single-page game (Three.js r128), no build step.

## Run it
Serve the folder with any static server and open `index.html`:

    python3 -m http.server 8000

Then visit http://localhost:8000. It also deploys as-is to Cloudflare Pages, GitHub Pages or Netlify.

## Controls
W A S D move, Shift sprint, Space jump, E interact, G flashlight, V first person, M places, I NASA data, P photo mode (hides all UI; PNG saving works when served over http), J trigger a solar flare (demo).
Rover: W A S D, Space handbrake, Shift boost, E exit. Aircraft: Shift thrust, S/W pitch, A/D bank, Space cut thrust or brake, E exit.

## NASA data
- `nasa_dem.js`: terrain from a NASA Mars Trek elevation export (about 400 m of Jezero). The land beyond that tile is generated procedurally.
- `perseverance_data.js`, `curiosity_data.js`: rover reference data.
- `nasa_photos.js`: NASA imagery used in the in-game NASA panel.
- Curiosity is built from NASA's official 3D model. The ARES-C aircraft is fictional, inspired by NASA's ARES Mars-airplane concept.
