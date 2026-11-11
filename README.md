# AstraForge: Space Mission Design Simulator

NASA Space Apps Challenge 2026: *Space Mission Design Game*

A browser game where players design, launch and fly a complete space mission. Pick a destination, choose real spacecraft and rockets from 10 nations (or future and space-based launch systems), engineer 65 parameters, launch from the pad, and fly the mission in true-scale 3D. Every mission ends with a scored report.

## How to run

**Option 1: local server (required for 3D).** The 3D engine loads as ES modules, which browsers block when a page is opened straight from disk. Planet textures, the star catalogue and the NASA models are included; three.js and astronomy-engine come from the jsDelivr CDN, so an internet connection is needed.

```bash
cd astraforge
python3 -m http.server 8000
# open http://localhost:8000
```

**Option 2: publish online for judges.** Upload the folder to GitHub and enable GitHub Pages, or drag the folder onto Netlify Drop. No build step is needed. See `SUBMISSION.md` for the Space Apps portal steps and form text.

## What's inside

| Feature | Where |
|---|---|
| Commander login, editable profile, rank, 13 badges, mission log | `08-profile.js` |
| 5 levels, 19 destinations, briefing and objectives | `02-data.js`, `07-ui.js` |
| Hangar: 52 spacecraft, 33 launch systems in 3 groups (ground, space-based, future) | `02-data.js`, `07-ui.js` |
| Engineering bay: 65 parameters, live GO/NO-GO poll | `04-physics.js`, `07-ui.js` |
| Engineering study: a full page for every parameter with physics, variables, real-world values and a live sensitivity chart | `05-study-data.js`, `09-study.js` |
| Future tech lab: 22 technologies, roadmap, propulsion map, animated diagrams, use in mission | `03-future-data.js`, `11-futurelab.js` |
| CAD import: STL, OBJ, GLB/GLTF, PLY. Measures size, volume, mass and centre of gravity, checks fairing fit, and flies your model | `10-cad.js` |
| 3D: textured planets, Earth shader with terrain relief, ocean glint, cloud shadows and city lights, ray-marched atmospheric scattering (Earth and Mars), physical sky, image-based lighting, MSAA, bloom, Milky Way, particles | `12-engine3d.js` |
| Next-generation renderer: three.js r186 **WebGPURenderer**. It uses WebGPU where the browser has it (Chrome, Edge, Safari 26, Firefox 141+ on Windows) and falls back to WebGL 2 automatically. Every custom effect (Earth surface, clouds, ray-marched atmosphere, volumetric engine plumes, GPU-animated smoke, star field) is written in TSL, the three.js shading language, which compiles to WGSL or GLSL | `12-gpu.js`, `index.html` |
| Cinematic post-processing graph (TSL): HDR pass with 4× MSAA, mipmap bloom, anamorphic lens ghosts, vignette, AgX filmic tone mapping and film grain | `12-gpu.js` |
| Adaptive quality: Low / Medium / High tiers picked from the graphics back end and device, plus a frame-time governor that lowers or raises render resolution to hold the frame rate. The top-bar badge shows the back end, tier and live fps; click it to change the tier | `12-gpu.js` |
| Live home page: Earth right now from 420 km above Sriharikota (real day/night, Sun, Moon, sky) | `12-engine3d.js` |
| Space Atlas: the real Solar System at any date with time warp, true or cinematic scale, focus on any body, distances, light delay, rise/set times, Moon phases, eclipses, planets visible tonight, launch windows | `17-atlas.js` |
| Real launch-site geography: each of 17 sites is built from real coastlines, lakes, rivers and towns (Natural Earth 1:10M) and real ground colour (NASA Blue Marble), turned to the launch azimuth; site-specific pads (Sriharikota mobile service tower on rails, LC-39A crew arm, Baikonur flame pit with Soyuz support petals, Kourou mobile gantry) | `00-sites.js`, `15-site.js` |
| Realistic launch site: reflective animated ocean (three.js WaterMesh with a planar reflector), Preetham sky with drifting procedural cumulus, welded truss tower and service arms, lightning masts with wires, tank farm, buildings, 7,000+ instanced trees and shrubs, sunlit cumulus | `15-site.js` |
| Real sky: Tycho-2 Milky Way sky map and Hipparcos stars (19,054 to mag 7.2, true colours), rotated to the real sky at the launch site and time | `00-sky.js`, `12-engine3d.js` |
| Real ephemeris (astronomy-engine): Sun and Moon over the pad (day, dusk or night launches with pad flood lights), Earth's rotation, real Moon in orbit views, real planet positions during cruise, next Hohmann launch window | `12-astro.js` |
| Spacecraft architecture: 54 craft built at real size (MLI blankets, cell-level solar arrays with sun tracking, dishes, reflectors, star trackers, thrusters, instruments, landers and rovers); official NASA 3D models for Hubble, JWST, Juno, Landsat, Perseverance, Voyager, Parker and Rosetta | `13-spacecraft.js`, `models/` |
| Launch physics and data: ray-marched propellant-specific plumes (kerosene, solid, hydrogen, hypergolic, methane) with Mach diamonds; GPU-lit smoke, deluge steam and exhaust column; 2-D gravity-turn ascent (thrust, mass flow, drag, Max-Q throttling); published event timelines for 25 rockets | `14-vehicles.js`, `15-flight.js` |
| Launch vehicles: dimension-accurate 3D models of 27 rockets (stage diameters and lengths, boosters, engine layouts, fairings, grid fins, legs, abort towers), painted liveries with name and flag, glowing nozzles and layered plumes | `13-vehicles.js` |
| 3D vehicle inspector in the hangar: orbit, exploded view, see-through fairing, engine firing, 1.8 m human for scale, height ruler, section table | `13-vehicles.js` |
| Flight: ground-level launch, true-scale orbits, transfers, landings | `14-flight.js` |

## Launch modes

- **Ground launch** from 17 real launch sites. Latitude sets the free boost from Earth's rotation (465 m/s × cos i), the lowest reachable inclination, dogleg penalties and the GEO plane-change Δv. The flight starts on the pad with the sky darkening as the rocket climbs, then switches to a true-scale Earth for staging, fairing jettison and orbit insertion.
- **Space-based launch:** depart from a refuelled orbital depot in LEO, a nuclear thermal tug, a VASIMR plasma tug, or the Lunar Gateway (NRHO). Capacity comes from the rocket equation for the departure stage.
- **Future launch systems:** air-breathing spaceplane (SABRE), heavy lift with a nuclear thermal upper stage, a kinetic (centrifuge) launcher with a 10,000 g limit, and a space elevator.

## Project structure

| File | Contents |
|---|---|
| `index.html` | Page layout, screens and script order |
| `css/style.css` | All styling |
| `js/00-textures.js` | Embedded planet and sky textures (see credits) |
| `js/01-utils.js` | Helpers and constants |
| `js/02-data.js` | Levels, destinations, instruments, propulsion, launch vehicles, spacecraft, launch sites |
| `js/03-future-data.js` | Future Tech Lab content |
| `js/04-physics.js` | Physics model, launch geometry, capacity, all validation checks |
| `js/05-study-data.js` | Engineering-study text for all 65 parameters |
| `js/06-simulation.js` | Day-by-day mission simulation and scoring |
| `js/07-ui.js` … `js/11-futurelab.js` | Screens |
| `js/12-engine3d.js` | Renderer, shaders, planets, spacecraft models, particles |
| `js/00-sky.js` | Star catalogue and Milky Way map |
| `js/00-sites.js` | Real geography around the launch sites |
| `js/12-astro.js` | Ephemeris helpers (astronomy-engine) |
| `js/13-spacecraft.js` | Spacecraft architecture, NASA model loader, spacecraft inspector |
| `js/14-vehicles.js` | Launch-vehicle geometry (`VGEO`), plumes, liveries, rocket inspector |
| `js/15-site.js` | Launch-site environment |
| `js/16-flight.js` | Flight phases, ascent physics, real timelines, 3D scenes |
| `js/17-atlas.js` | Space Atlas screen |
| `js/18-boot.js` | Start-up |
| `models/*.js` | NASA 3D Resources models (glTF, meshopt-compressed), loaded on demand |

Scripts must load in numbered order.

## Adding content

**Spacecraft:** add a line to `CRAFT` in `js/02-data.js`. **Rocket:** add a line to `LV`, including `site:` (a key from `SITES`), and optionally a `VGEO` entry in `js/13-vehicles.js` with stage diameters and lengths in metres (otherwise a generic shape is built from height and fairing size). **Space-based stage:** set `kind: "space"`, `space: "leo"` or `"nrho"`, plus `Mp` (propellant, kg), `Md` (dry, kg) and `isp`. **Study text:** add or edit an entry in `STUDY` in `js/05-study-data.js`.

## Credits

- Earth, clouds, city lights and Milky Way textures: three.js examples (MIT licence).
- Moon, Mars, Jupiter, Saturn (and ring), Venus, Mercury and Sun textures: [Solar System Scope](https://www.solarsystemscope.com/textures), CC BY 4.0.
- 3D library: three.js r186 with WebGPURenderer and TSL (MIT); ephemeris: astronomy-engine 2.1 (MIT).
- Launch-site geography: Natural Earth 1:10M land, lakes, rivers and urban areas (public domain); ground colour from NASA Blue Marble (public domain, via three-globe, MIT).
- Star catalogue: Hipparcos data packaged by d3-celestial (BSD-3-Clause, Olaf Frohn). Milky Way sky map: Tycho-2 sky box from CesiumJS (Apache-2.0).
- Spacecraft models (Hubble, JWST, Juno, Landsat 8, Perseverance, Voyager, Parker Solar Probe, Rosetta): NASA 3D Resources (no copyright), compressed with glTF-Transform.
- Rocket dimensions: approximate public figures from manufacturer user guides and press kits. Liveries are simplified and carry no agency or company logos.

All vehicle and mission figures are approximate public values rounded for gameplay. They are not engineering data.
