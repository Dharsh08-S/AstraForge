# NASA Space Apps 2026: submission kit for AstraForge

The Space Apps portal does **not** take app uploads. The project page accepts only images (JPG, PNG or GIF, up to 10 MB). You submit two **public links**:

- one to the working app or code (the "Final Project" link)
- one to a short demo (the "Project Demo" link)

Submission is open from **14 November, 09:00** to **15 November, 23:59** (local time of your Local Event). Press **"Submit for Judging"** before the deadline. Submission is final.

## 1. Put the app online (free, about 10 minutes)

**Option A: Netlify Drop (fastest)**

1. Unzip `AstraForge.zip`.
2. Open https://app.netlify.com/drop and drag the `astraforge` folder onto the page.
3. Netlify gives you a public link such as `https://astraforge-xyz.netlify.app`.
4. Claim the site with a free account so the link stays up.

**Option B: GitHub Pages (also gives you a code repository)**

1. Create a public repository, for example `astraforge`.
2. Upload the *contents* of the `astraforge` folder: `index.html` must be at the top level.
3. Go to Settings → Pages → Deploy from branch → `main` / root.
4. The link will be `https://<your-username>.github.io/astraforge/`.

Before submitting, open the link in a **private or incognito window**. It must work without logging in.

## 2. Make the demo (required)

The demo must be **either**:

- a video of **30 seconds or less** with English subtitles, **or**
- a slide deck of **7 slides or fewer**, including the title slide.

Host it publicly (YouTube unlisted, Google Drive set to "anyone with the link", and so on). Demos over these limits are not eligible for global judging.

Suggested 30-second video shots:

1. Home page: live Earth from orbit with the "LIVE" caption.
2. Briefing: choosing the destination and launch date.
3. Hangar: the 3D rocket viewer (exploded view) and the satellite viewer.
4. Engineering bay: changing a parameter and watching the GO / NO-GO poll.
5. Launch: night launch from Sriharikota with steam, plume and smoke column.
6. Orbit: satellite deploying its solar arrays.
7. Space Atlas: time-warp of the real Solar System, ending on the score report.

## 3. Form fields (draft text; edit it into your own words)

**Project name:** AstraForge: Space Mission Design Simulator

**High-level project summary (about 150 words)**

AstraForge is a browser game that teaches space mission design by letting players build and fly a complete mission. Players pick one of five destination levels (Earth orbit, Moon, Mars, the inner Solar System and deep space). They choose a real spacecraft and rocket from ten spacefaring nations, or a future concept, and engineer 65 parameters. Each parameter has a physics explanation and a live sensitivity chart. The mission then launches from the real launch site at the real date and time. A physics-based ascent, true-scale orbits and interplanetary transfers use real planet positions. Every kilogram, watt and kilobit is checked by the rocket equation, link-budget, power, thermal and radiation models, and the mission ends with a scored report. A live Space Atlas shows the real Solar System, eclipses and launch windows. It runs in any modern browser with nothing to install.

**Link to project demo:** *(your public video or slide link)*

**Link to final project:** *(your Netlify or GitHub Pages link)*

**Detailed project description:** describe what it does, how it works (the physics models listed in `README.md`), the benefits (hands-on learning of trade-offs), the intended impact (students and first-time mission designers) and the tools used: JavaScript, three.js r186 (WebGPU renderer with WebGL 2 fallback, TSL shaders), astronomy-engine, glTF-Transform.

**NASA data** (required for global awards; describe how each is used):

- **NASA 3D Resources:** official 3D models of Hubble, James Webb, Juno, Landsat 8, Perseverance, Voyager, Parker Solar Probe and Rosetta. They are shown in the spacecraft viewer and in flight.
- **NASA Blue Marble imagery:** the real ground colour around each launch site (Sriharikota, Kennedy, Baikonur, Kourou and 13 more).
- **NASA mission facts:** published masses, power, antenna sizes and orbits for the NASA spacecraft templates (Hubble, JWST, Landsat 9, GPS III, Perseverance, Juno, Europa Clipper, Parker, New Horizons, Voyager 1). Also SLS dimensions and timeline.
- **NASA Deep Space Network:** the antenna sizes and link-budget approach used in the communications model.

**Space agency partner and other data** (list everything):

- **Partner agencies:** ISRO, ESA, JAXA, CNSA, Roscosmos, KASA, UKSA, ISA and UAESA public mission and launcher data (masses, dimensions, timelines), approximate and rounded.
- **Natural Earth 1:10M vectors (public domain):** real coastlines, lakes, rivers and towns around the launch sites.
- **Hipparcos star catalogue:** via d3-celestial (BSD-3-Clause).
- **Milky Way sky map:** the Tycho-2 sky box shipped with CesiumJS (Apache-2.0), reprojected to J2000.
- **Earth day, night and cloud textures:** three.js examples (MIT).
- **Planet textures:** Solar System Scope (CC BY 4.0).
- **Libraries:** three.js r186 with WebGPURenderer and TSL (MIT), astronomy-engine (MIT, VSOP87 / ELP2000 ephemerides), glTF-Transform (MIT).

**Use of artificial intelligence (the rules require disclosure):**

> AI assistance (Anthropic Claude) was used to help write and debug the JavaScript source code, the physics models and the documentation text. All code was reviewed and tested by the team. No AI-generated images, video or audio are used in the app. Images are rendered live from the 3D scene, and the 3D models and sky images come from NASA and the open sources listed above. AI was not used to create or modify any NASA logos, flags or mission identifiers.

If you use any AI-generated image or video in your demo, the rules require a visible "AI-generated" watermark on it.

**Project submission verification:** tick "Confirm All Work is Original" and accept the Terms and Conditions.

## 4. Final checklist

- [ ] All team members are confirmed at the **same Local Event**. A solo "Stellar Orbit" team is fine.
- [ ] The app link works in a private window, on a phone and on a laptop. The top-bar badge should read "WebGPU" in Chrome or Edge; "WebGL 2" is the automatic fallback and also fine.
- [ ] The demo is 30 seconds or less (with English subtitles) or 7 slides or fewer, and is public.
- [ ] All text is in English.
- [ ] The NASA data field is filled in.
- [ ] The AI-use statement is filled in.
- [ ] "Submit for Judging" has been pressed before 23:59 on 15 November.
