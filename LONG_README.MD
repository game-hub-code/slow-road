# Slow Roads (My Version): The Presenter's Guide

**Reader:** you, presenting this project to judges.
**Goal:** explain it, demo it, and answer questions.
**Read order:** Parts 1 to 3, then Part 12, then practice Part 13 out loud.

**How sure is each fact?** A fact with no tag comes straight from the project files. Two tags mark weaker facts:

- `[INFERRED]` = worked out from clues in the code. Probably right, not proven.
- `[UNKNOWN]` = not found in the files.

**Not tested:** everything here comes from reading the files. The game was never opened in a browser while writing this. Run it yourself before you present.

---

## Part 1. The 30-second pitch

> "Slow Roads is a driving game that runs in a web browser. The road never ends, and the game builds hills, trees, and weather as you drive. I started from the Slow Roads game by Anslo and made my own version. I added a car color picker, a glowing boost icon, and a cleaner start, and I edited the logo on the car."

Memorize three sentences:

1. **What it is:** an endless, relaxing driving game in the browser.
2. **What is special:** the world is made by math while you drive. Nobody drew it by hand.
3. **What I did:** I changed and improved it. The color picker is the big one.

---

## Part 2. What is mine and what is not

Judges will ask who made it. This table gives you a safe, true answer.

| Part | Whose is it? |
|---|---|
| The game engine, the endless world, the physics, the sounds, the 3D models, the art | **Anslo**, the creator of Slow Roads (slowroads.io, anslo.dev). The project folder began as a saved copy of the files that slowroads.io sends to a browser. |
| The car color picker (solid and gradient) | **Mine** |
| The glowing boost lightning bolt | **Mine** |
| Skipping the start screen | **Mine** |
| Hiding the donate buttons and one menu icon | **Mine** |
| The edited logo on the car's paint image | **Mine** |
| The visitor counter | **Mine** (a small script from an outside service) |
| This project folder and its 42 saved versions | **Mine** |

**Say:** "This is my version of Slow Roads. The original game is by Anslo. The changes are mine."

**Why this matters:**

- In its FAQ, the original creator answers "Will you make it open source?" with "Probably not anytime soon."
- The project folder has no license file, so `[UNKNOWN]` whether copying is allowed.
- If you say you built the whole game, anyone can check slowroads.io and find the same game. Saying "my version, built on Anslo's game" cannot be proven wrong, and it still shows real work.
- If you ever want to share or sell it, ask Anslo for permission first.

---

## Part 3. What the game is, in plain words

You drive a car along a road through hills. The road never ends. There are no enemies, no timer, and no lives. The creator calls it "endless driving zen", which means calm driving.

You can change:

- **Season:** spring, summer, autumn, winter.
- **Weather and time:** sunrise, clear, rain, sunset, night. Winter also has snow.
- **Place:** green hills, or the planets Mars, Venus, and the Moon.
- **Car:** Roadster (sports car), Coach (bus), Lambo, Supercar.
- **Road style:** easy, normal, hard, wide, straight.
- **Camera:** behind the car (near or far), first person, or on the bonnet.

There is also **autodrive**, where the game steers for you.

### Controls

| Key | What it does |
|---|---|
| W or Up arrow | Speed up |
| S or Down arrow | Brake, then reverse |
| A / D or Left / Right arrow | Steer |
| Space | Handbrake |
| Left Shift (hold) | Boost |
| F | Autodrive on or off |
| R | Put the car back on the road |
| C | Change camera |
| L or H | Headlights on or off |
| M | Mute |
| P | Pause |
| Q and E | Previous and next weather `[INFERRED]` |

The mouse can steer too. The game does not work on phones because it needs a keyboard.

---

## Part 4. Words you need

| Word | Meaning | Say it like this |
|---|---|---|
| **Browser** | The program for websites (Chrome, Edge). | "The game runs inside Chrome." |
| **HTML** | The file that says what is on a web page. | "It is the front door of the project." |
| **JavaScript** | The language browsers run. | "All the game rules are JavaScript." |
| **CSS** | Rules for how a page looks: colors, fonts. | "CSS is the paint." |
| **3D model** | A shape made of thousands of tiny triangles. | "The car is a 3D model." |
| **Texture** | A picture wrapped around a 3D shape like wrapping paper. | "The logo lives in the car's texture." |
| **Procedural generation** | The computer builds the world with rules and math. | "The hills are made by math." |
| **Seed** | A starting number. Same seed, same world. | "Type the same seed to get the same road." |
| **Heightmap** | A grid of numbers saying how tall the ground is. | "Big number is a mountain." |
| **LOD (level of detail)** | Far things are simple, near things are detailed. | "Like a painting: fine brush up close." |
| **Shader** | A tiny program on the graphics card that picks each pixel's color. | "My color picker is a shader." |
| **WebGL** | The browser feature for 3D graphics. | "It lets the browser draw 3D." |
| **Library** | Code other people wrote that you reuse. | "The 3D engine is a library." |
| **Minified** | Code squeezed small and hard to read. | "The big files are minified." |
| **Analytics** | Counting how people use a site. | "The site counts visitors." |
| **localStorage** | A small notebook the browser keeps for each site. | "The game saves settings there." |
| **Commit** | A saved snapshot of the project with a note. | "My project has 42 snapshots." |

---

## Part 5. Tools used

| Tool | Job | Proof |
|---|---|---|
| **three.js** | 3D engine: draws the world, car, sky, lights. | Named in the library file. |
| **React 17.0.2** | Builds menus and screens. | Version found in the library file. |
| **webpack build** | The packing tool that made the two big JS files. | The name `webpackJsonpapp` appears in both. File names look like a Create React App build `[INFERRED]`. |
| **alea** | Seeded random numbers. | `alea.min.js`. |
| **socket.io** | Lets the page talk to a server live, for analytics. | `[INFERRED]` from the `.on` and `.emit` calls. |
| **Web Audio (via three.js)** | Plays sounds, some louder when close. | Code and sound files. |
| **Fonts Jura, ShareTech** | Menu text style. | Two `.ttf` files. |
| **A local web server** | Lets you run the game on your computer. | See Part 10. |

No game engine app (Unity, Unreal, Godot) was used. It is plain JavaScript.

---

## Part 6. Every file explained (for a 10-year-old)

**Big picture:** think of the project as a **toy car set in a box**.

- `index.html` is the **box lid with the instructions**. It says what goes where and starts everything.
- The big JavaScript file is the **brain**. It knows all the rules.
- The library file is the **toolbox** someone else made. The brain borrows tools from it.
- The CSS file is the **paint and stickers**.
- The `media` folder is the **parts bin**: pictures, sounds, and 3D shapes.

```
slow-road/
├── index.html             the box lid (and where MY edits live)
├── alea.min.js            the dice
├── manifest.json          the "install me" card
├── favicon_circle.svg     the tiny tab icon
├── null.html              an empty leftover page
├── README.md              this guide
└── static/
    ├── css/main.a473f648.chunk.css      the paint
    ├── js/2.f5fa8177.chunk.js           the toolbox
    ├── js/main.e7a33c55.chunk.js        the brain (the game)
    └── media/                           the parts bin (163 files)
```

Total: 172 files, about 27 MB.

### `index.html` (20 KB): the box lid. This is where MY work is.

**Like:** the front door of a house. Everyone enters here.
**What it does, in order:**
1. Gives the page its name ("slow roads") and one-line description ("endless driving zen in your browser").
2. Loads the dice (`alea.min.js`), the paint (CSS), the toolbox, and the brain.
3. After the game appears, runs my small scripts that change things: the color picker, the boost bolt, hiding the donate buttons, skipping the start screen.
4. Runs the visitor counter script.

**If a judge asks:** "This is where I made my changes. Everything else is the original game."

### `static/js/main.e7a33c55.chunk.js` (1 MB, 22,429 lines): the brain

**Like:** the game's brain and rulebook in one.
**What is inside:**

| Section | Kid explanation |
|---|---|
| Input | Listens to your keys and mouse. |
| Game clock | Ticks about 60 times a second: check keys, move car, draw the picture. Like frames in a flipbook. It never lets one tick last longer than 0.1 second. |
| Audio | Loads and plays sounds. Fades in at the start. Goes quiet when paused. |
| Car | Remembers speed, steering, headlights, tilt. |
| Terrain maker | Makes the hills from the seed. |
| Road maker | Draws a road through the hills. |
| Scenery placers | Plant trees, rocks, grass, and walls. |
| Sky and weather | Colors and looks for each time of day, plus rain, snow, fog. |
| Vehicle controller | The driving rules: speed, grip, braking, boost, autodrive. |
| Cameras | The four ways to look at the car. |
| Menus | The start screen, settings, controls panel, FAQ text. |
| Analytics | Sends usage info to the creator's server. |
| Records | Tracks four records. |

**One line in this file is mine:** `window._carState = z;` at line 796. It shares the car's data so my boost icon can read it.

### `static/js/2.f5fa8177.chunk.js` (650 KB): the toolbox

**Like:** a borrowed toolbox.
It holds React (menus) and three.js (3D). Squeezed small on purpose, so it is very hard to read. Nobody on this project wrote it.

### `static/css/main.a473f648.chunk.css` (27 KB): the paint

**Like:** the paint and stickers for the menus.
Sets the fonts, the menu boxes, the speed display, and the buttons.

### `alea.min.js` (1 KB): the dice

**Like:** dice that always roll the same way if you start from the same spot.
Give it a seed, and it produces the same "random" numbers every time. That is why the same seed makes the same world.

### `manifest.json`: the "install me" card

**Like:** a name tag.
It says the app is called "Slow Roads", should open full screen, and uses the circle icon.

### `favicon_circle.svg`: the tab icon

**Like:** the tiny picture on the browser tab.

### `null.html`: an empty leftover page

**Like:** an empty envelope. It holds one line, "No Content: https://slowroads.io/null". You can ignore it.

### `static/media/` (163 files): the parts bin

| Kind | How many | Like... |
|---|---|---|
| `.jpg` | 47 | Wallpaper for the ground: grass, gravel, rock, sand, snow, and the surfaces of Mars, Venus, and the Moon. |
| `.png` | 49 | Cut-out stickers: trees, bushes, clouds, road pieces, barriers, the start logo. |
| `.svg` | 33 | Crisp little icons for menus, weather, seasons, and vehicles. They stay sharp at any size. |
| `.mp3` | 16 | Long sounds: engine, tires, braking, scraping, wind, nature. |
| `.wav` | 4 | Short beeps: autodrive on and off, a bump, the achievement chime. |
| `.obj` | 12 | 3D shapes: car, bus, motorbike, wheels, signs, wall pieces, Mars rocks. |
| `.ttf` | 2 | Fonts: Jura and ShareTech. |

**The most important media file for you:** `roadster-07b_map.17a06a45.jpg`. It is the car's "paint job", a flat picture that wraps around the 3D car. I edited it three times to add and adjust the logo.

**Known gaps:** the code asks for 6 files that are not in the folder: `Dosis.3e75d17d.ttf`, `clouds_01.4a7d98a7.png`, `controls_mouse_buttons.1f93e888.svg`, `debug_body.193b9327.obj`, `debug_wheel.291c4dc1.obj`, `no_mobile_1.959d982f.svg`. The page also points to a missing `./img.jpg`. Whether anything visible breaks is `[UNKNOWN]`.

---

## Part 7. How the game works inside

### 7.1 The world is made by math

Picture a **giant invisible grid of numbers** over the ground. Each number says how high the land is. That grid is the **heightmap**. The game builds it in layers: big rough shapes first, then smaller bumps on top, like adding detail to clay.

Normal difficulty uses 3 layers and a height scale of 160. Harder settings use 4 layers. A smoothing curve rounds the bumps so the hills roll.

### 7.2 The seed

A computer cannot pick truly random numbers. It follows a recipe that starts from a **seed**. Same seed, same hills. In the menu you can type a **generation seed** and press **apply changes**. The game remembers your seed in the browser's notebook.

### 7.3 The road

After the land, the game traces a **midline** (the center of the road) through it. Simple rules keep it drivable: not too steep, not too sharp. **Road complexity** changes the rules: easy, normal, hard, wide, straight. Road width in normal mode is 3 units.

### 7.4 Only build what you can see

An endless world cannot all exist at once. So the game:

- builds detailed tiles near the road,
- builds rough big tiles far away,
- deletes tiles behind you.

That is **level of detail**. **Fog** hides the far edge. There are 5 view-distance levels (from 200 up to 6,000 units) and 5 detail levels. **Render scale** (0.5, 0.75, 1.0, 1.5) draws fewer or more pixels. If the game stays under 45 frames per second, it says "Low FPS? Try lowering the quality settings".

### 7.5 Loading steps

| Step | Share | Job |
|---|---|---|
| topography | 25% | Make the hill heights |
| scene | 10% | Set up sky, light, weather |
| farGrid | 35% | Build far land |
| nearGrid | 28% | Build close land and scenery |
| finalise | 2% | Last checks |

### 7.6 Seasons, weather, places

- 4 seasons: spring, summer (default), autumn, winter.
- 5 to 6 looks per season. Summer: sunrise, clear, rain, sunset, night. Autumn adds twilight. Winter adds snow, winterSunrise, winterSunset.
- Off-world: Mars, Venus, Moon, each with its own ground pictures and sounds. The Moon has one look.

### 7.7 The car

The physics are simple on purpose. It is a set of numbers, not a full simulation.

| Car | Accel | Top speed | Mass | Note |
|---|---|---|---|---|
| Roadster | 9 | 45 | 700 | Default |
| Coach (bus) | 6 | 32 | 1400 | Slow and heavy |
| Lambo | 40 | 500 | 1400 | Same 3D model as Roadster |
| Supercar | 1500 | 50,000 | 1400 | Same model, extreme speed |

Units are probably meters per second `[INFERRED]`, because the game converts with 2.23694 (mph) and 3.6 (km/h). A Bike, Rover, and Debug car exist in the code but are switched off. Whether the Bike shows in the menu is `[UNKNOWN]`.

Every tick, the car:
1. Reads your keys.
2. Turns the left and right front wheels by slightly different angles, like a real car in a corner.
3. Finds the ground under each wheel and tilts.
4. Applies grip: road 0.99, roadside 0.95, grass 0.9 (Mars values).
5. Plays engine and tire sounds.
6. Checks for a wall bump.

Trees and signs have no collision on purpose. The creator says it keeps the game calm and saves computer work. Cruise control starts at 90 mph or 150 km/h.

### 7.8 Cameras, sound, saved data

- **Cameras:** Near Chase, Far Chase, First Person, Bonnet. The camera lags a little for a soft feel.
- **Sound:** separate files for engine, tires, wind, ambience. Some sounds get louder when close.
- **Saved data:** seed, season, weather, quality, camera, units, cruise control, distance.
- **Records:** Fastest Any Mile, Fastest First Five Miles, Furthest Single Journey, Furthest On-Road.
- **Achievement:** "The Edge" with the text "What did you expect?" What triggers it is `[UNKNOWN]`.

If the game crashes, it saves your distance and shows an error screen.

---

## Part 8. What I changed

All edits are in `index.html`, plus one line in the game file and three edits to the car's paint image.

| # | My change | How it works |
|---|---|---|
| 1 | **Car color picker** | A bucket icon in the top-left menu. Hover it to open a panel with **Solid** (one color) and **Gradient** (two colors blended top to bottom). |
| 2 | **Skip the start screen** | A script looks for the "begin" button every 200 ms and clicks it. A second script does the same every 50 ms, then hides the start box and blocks the Escape key from bringing it back. Gives up after 15 seconds. |
| 3 | **Hide donate items** | Scripts hide the "donate" link, its message, and the heart/coffee icon. |
| 4 | **Hide the last bottom-right icon** | Removes the button that reopens the start screen. |
| 5 | **Boost bolt** | A lightning bolt next to the speed number that glows while boosting. It checks the car's `hasBoost` value 60 times a second. |
| 6 | **Visitor counter** | A script from `t.whop.tw` that records page visits. |
| 7 | **Car logo** | Three edits to `roadster-07b_map...jpg`. |

### How the color picker works

Explain it in five steps:

1. **Catch the scene.** three.js can announce each 3D object it makes to a "devtools hook". My page sets up that hook early and saves the scene in `window._carScene`.
2. **Find the car parts.** When you pick a color, the code checks every object. It keeps only parts whose names start with `z_` (car body), `fwheel_` or `bwheel_` (wheels), `bus-02_body` (bus), or `m2_body` (motorbike). Road, trees, and sky have no matching name, so they stay unchanged.
3. **Add a tiny program.** Each kept part gets a **shader**. It measures the part's lowest and highest point, then works out where each pixel sits between them.
4. **Paint by height.** Solid gives every pixel your color. Gradient blends the bottom color into the top color. Doing this on the graphics card keeps it smooth. An older try used an image and looked banded, as the code comment says.
5. **Protect windows and trim.** The player car has a paint image. The shader only repaints pixels brighter than 0.745, so dark windows and trim stay dark.

Eleven test commits over two days (Sept 18 to 19) show how much trial and error it took: "STEP 1", "TEST 2 to TEST 9", and "Diagnostic Test 1 and 2".

### Timeline

| Date | What happened |
|---|---|
| Aug 4 | First files added |
| Aug 28 to 30 | Edits to `index.html` |
| Sept 17 | Main CSS, JS, and media added. Start screen removed. README added |
| Sept 18 | Color picker added and fixed. Donate items hidden |
| Sept 18 to 19 | The long run of color tests, then a "final" version |
| Sept 22 | Start screen hiding, boost bolt, car logo |
| Sept 24 | New roadster paint image and logo edit |
| Sept 27 | Visitor counter added |

42 saved versions in total.

---

## Part 9. Careful questions to expect

**Privacy.** The original game connects to a server at `34.250.221.219` and sends settings, vehicle choice, frame rate, play time, distance, browser type, screen size, and errors. It also asks `ipapi.co` for your country, region, and city. A setting called "analytics-disabled" can switch it off. My visitor counter is a second, separate tracker. Whether the creator's server still answers is `[UNKNOWN]`. Say: "The game has built-in analytics from the original. I added a visitor counter."

**Donate buttons.** The original creator pays to keep the site online with donations. I hid the buttons for a cleaner look. Be ready to say you know why they exist, and that the creator's link is still in the code.

**License.** The folder has no license file and the creator says the game is not open source. Present this as a learning project built on Anslo's game. Ask permission before sharing or selling it.

**The old README.** The first version of the project's own short README ends with a "Contributing" note about improving new cars and fixing an "ultra+ bug". Whether that came from another project is `[UNKNOWN]`. Do not claim those fixes were made.

---

## Part 10. How to run it for the demo

You need a small local web server. Install Node.js, then open a terminal in the project folder:

```
npm i -g http-server
http-server
```

Or use `npx serve`. Open the address it prints (for example `http://127.0.0.1:8081`) in Chrome. After you edit a file, press **Ctrl + F5**.

Without Node: run `python -m http.server 8000` in the folder (Python 3), or use the VS Code "Live Server" extension. Netlify Drop (app.netlify.com/drop) can host the folder for about an hour with no account, as long as you keep a backup.

**Demo tips**
- Turn on browser **hardware acceleration**, or it will look like a slideshow.
- If it is slow, lower view distance, detail, or render scale.
- Use a keyboard.
- Record a 2 to 3 minute backup video, plus screenshots.

### 3-minute demo script

1. Open the game. Say: "It opens straight into driving because I skipped the start screen." (10 s)
2. Drive. Show steering, boost, and the bolt glowing. (30 s)
3. Hover the bucket icon. Pick a solid color, then a gradient. (30 s)
4. Press C for camera, F for autodrive. (20 s)
5. Open settings. Change season and weather. (30 s)
6. Type a seed and press apply. Say: "Same seed, same world." (30 s)
7. Switch to Mars and the Lambo. (20 s)
8. Finish with the pitch from Part 1. (10 s)

---

## Part 11. Numbers to remember

- **Files:** 172. **Media files:** 163. **Saved versions:** 42.
- **Game code:** 22,429 lines, about 1 MB.
- **Libraries:** React 17.0.2 and three.js.
- **Game version:** 1.0.1.
- **Cars on:** 4. **Seasons:** 4. **Off-world places:** 3.
- **Road styles:** 5. **Camera styles:** 4. **Loading steps:** 5.
- **My changes:** color picker, boost bolt, hidden donate items, skipped start screen, car logo, visitor counter.

---

## Part 12. The honest part

1. **The original game is Anslo's.** My work is the set of changes in Part 8. Say so, and you are safe.
2. **Nothing here was run in a browser.** Test it yourself.
3. **The game code is minified.** A few details (like Q and E) are `[INFERRED]`.
4. **Permission is `[UNKNOWN]`.** There is no license file. Credit Anslo.
5. **Two trackers exist.** The original analytics and my visitor counter.

---

## Part 13. Judge Q&A (practice out loud)

**About the project**

**Q: What is your project?**
A: My version of Slow Roads, an endless driving game in the browser. I added a car color picker, a boost icon, and a cleaner start.

**Q: Did you make the whole game?**
A: No. The original game and its world engine are by Anslo. I built my version on top of it and made the changes.

**Q: What did you add?**
A: A color picker with solid and gradient modes, a lightning bolt that shows boost, a skipped start screen, hidden donate buttons, an edited logo on the car, and a visitor counter.

**Q: Why this game?**
A: Say your own reason. A safe one: "It shows many ideas at once: 3D graphics, math-made worlds, and driving physics in a browser."

**Q: What was the hardest part?**
A: The color picker. It took 11 test versions over two days to get a smooth gradient that leaves the windows alone.

**Q: Is it yours?**
A: The changes and this project folder are mine. The original game belongs to Anslo.

**About how it is built**

**Q: What language is it written in?**
A: JavaScript, with HTML for the page and CSS for the style.

**Q: Which tools does it use?**
A: three.js for 3D, React for menus, alea for seeded random numbers, and a webpack bundle to pack it.

**Q: Does it need to be installed?**
A: No. It runs in a browser. At home, you start a small local server.

**Q: Why not Unity?**
A: The creator's FAQ says plain JavaScript loads in one click, needs no install, and gives more control over speed.

**Q: Does it work on a phone?**
A: No. It needs a keyboard.

**About the world**

**Q: How does the world never end?**
A: It builds a small area around the road as you go and throws away the area behind you.

**Q: What is a seed?**
A: A starting number for the random recipe. Same seed, same world.

**Q: What is procedural generation?**
A: The computer builds things from rules and math instead of a person drawing each part.

**Q: How are the hills made?**
A: A grid of height numbers made in layers, then smoothed. Big numbers are mountains.

**Q: How is the road made?**
A: The game draws a center line through the hills with rules about steepness and sharp turns.

**Q: Why does far land look simpler?**
A: Level of detail. Far land uses fewer triangles to save computer power, and fog hides the change.

**Q: Why can I drive through trees?**
A: On purpose. The creator says it keeps the game calm and saves computing work.

**Q: How many seasons and places?**
A: Four seasons and three off-world places: Mars, Venus, and the Moon.

**About the car**

**Q: How does the car physics work?**
A: Simple numbers for speed, steering, grip, and weight. Each tick it reads your keys, steers the wheels, tilts to the ground, and plays sounds.

**Q: How many cars are there?**
A: Four are on: Roadster, Coach, Lambo, and Supercar. Three share one 3D model.

**Q: What is autodrive?**
A: A built-in driver that steers along the road. Press F.

**Q: What does boost do?**
A: Hold Shift for extra acceleration. My bolt icon glows while it is on.

**About the color picker**

**Q: How does it work?**
A: It finds the car parts in the 3D scene by name and gives each a small graphics-card program. The program picks each pixel's color by how high it is on the car.

**Q: Why not just change the image?**
A: An older try used an image and looked banded. The graphics card gives a smooth blend.

**Q: Why do the windows stay dark?**
A: The program only repaints light pixels. Dark pixels keep their color.

**Q: Does it work on other vehicles?**
A: The code covers the car, its wheels, the bus body, and the motorbike body.

**About data and rules**

**Q: Does it collect data?**
A: The original game sends usage data to the creator's server. I also added a visitor counter.

**Q: Is it legal to copy it?**
A: There is no license file and the creator says it is not open source. So I treat this as a learning project and credit Anslo. Whether permission exists is unknown, and I would ask before sharing it widely.

**Q: Why did you remove the donation button?**
A: For a cleaner look. I know donations pay for the original site, and I credit the creator.

**Q: What would you improve next?**
A: Save the chosen color, fix the six missing files, and add a switch to turn the trackers off.

**Trick questions**

**Q: What is the version number?** A: 1.0.1.
**Q: How many lines of code?** A: 22,429 in the game file. Most of it is the original.
**Q: Biggest file?** A: `main.e7a33c55.chunk.js`, about 1 MB.
**Q: Is there a score?** A: No. There are four records: fastest mile, fastest first five miles, furthest single journey, and furthest on-road.
**Q: What if I leave the road?** A: You slow down because grass has less grip. Press R to reset.

**If you do not know an answer,** say: "I am not sure about that part. What I do know is..." Then say the closest true thing. Never guess.

---

## Part 14. Fact-check table

| Claim | Tag | Source |
|---|---|---|
| Original game by Anslo, slowroads.io | Verified | Project README, start-screen text in game code |
| 42 saved versions | Verified | Version history |
| React 17.0.2 | Verified | Library file |
| three.js | Verified | Library file and game code |
| Version 1.0.1 | Verified | `const Zi = "1.0.1"` in game code |
| One line changed in the game file | Verified | Version history |
| 4 cars enabled | Verified | `enabled` flags |
| Speed units are m/s | Inferred | Conversion numbers |
| Q/E change weather | Inferred | Key list and labels |
| Create React App build | Inferred | File names |
| socket.io for analytics | Inferred | `.emit`, `.on` calls |
| "The Edge" trigger | Unknown | Not found |
| Permission to copy | Unknown | No license file |
| Game runs correctly | Untested | Not run |
