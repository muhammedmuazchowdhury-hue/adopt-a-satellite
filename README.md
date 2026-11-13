
# Adopt a Satellite: Relic Map

**A privacy-first, offline space-education app for children.** It tells the stories of robotic spacecraft that humans left behind on the Moon, on Mars, and in deep space, and it runs in a browser with no server, no account, and no internet connection.

Built by **Team Tiny Sparks** for the **NASA Space Apps Challenge 2026**, theme: *"Abandoned but not forgotten."*

> **Disclaimer:** Adopt a Satellite is an independent educational project. It is not an official NASA product.
>
> **Status:** Functional prototype, ready for local judging. A school pilot is planned. Works 100% offline.
>
> **Live:** https://adoptasatellite.vercel.app/
> **Submission:** a single self-contained HTML file (all code, styles, and images included).
> **Coming soon:** Earth-Orbit Tracker
>
> Some Mars records still show "pending" labels, and a Bangla translation review is still needed. See [Known issues](#known-issues).

---

## Contents

- [What it is](#what-it-is)
- [Features](#features)
- [Quick start](#quick-start)
- [Repository layout](#repository-layout)
- [Data sources (NASA and others)](#data-sources-nasa-and-others)
- [Tech stack](#tech-stack)
- [Build and test](#build-and-test)
- [Accessibility](#accessibility)
- [Language support](#language-support)
- [Offline use and low-connectivity schools](#offline-use-and-low-connectivity-schools)
- [Privacy and child safety](#privacy-and-child-safety)
- [Child-Given Reviews](#child-given-reviews)
- [Roadmap](#roadmap)
- [Known issues](#known-issues)
- [Contributing](#contributing)
- [AI usage and transparency](#ai-usage--transparency)
- [Licence and attribution](#licence-and-attribution)

---

## What it is

Each abandoned machine is treated as a **relic** with a story. Children learn what the machine did, where it is now, how long it worked, and why it still matters.

The whole app is **one HTML file of about 500 KB**. It needs no installation and no network to run. The only feature that needs the internet is opening optional NASA source links.

## Features

The app has five sections and a home screen. A language switch sits at the top.

| Section | What it does |
|---|---|
| **Home** | Introduces the app and shows a "Relic of the day", chosen by calendar date so every device shows the same relic that day. |
| **Relic Map** | Nineteen records across three worlds: Moon (7), Mars (8), deep space (4). Each has a photo, a child-friendly story, a timeline, coordinates where reliable, source links, and an "Adopt this relic" button. |
| **Rescue / Remember** | A re-entry angle game, a curator-style nameplate writing activity, and a "My Opinion" box. |
| **Signal Lab** | Five levels that teach Morse code. Input can be sound, a flash lamp, vibration, or a telegraph key. |
| **Time Capsule** | Text notes, a simple drawing canvas, short voice notes (stored on the device), PNG postcards, and JSON backup export and import with rollback on failure. |
| **Passport** | Twelve badges, a rank that rises with badges, and bronze, silver, and gold certificates. Motivation, not testing. |

### The nineteen relics

- **Moon (7):** Lunar Orbiter 1, Surveyor 3, Apollo 11 Tranquility Base, Apollo 15 Lunar Roving Vehicle, Apollo 16 ALSEP, Apollo 17 ALSEP, Lunokhod 1
- **Mars (8):** Viking 1, Viking 2, Mars Pathfinder with Sojourner, Spirit, Opportunity, Phoenix, InSight, Ingenuity
- **Deep space (4):** Pioneer 10, Pioneer 11, Cassini, Galileo

---

## Quick start

**Use the app:** open `index.html` (or the built `Adopt_a_Satellite_*.html`) in Chrome, Edge, Firefox, or Safari. Nothing to install.

**Rebuild the single file from source:**

```bash
python3 tools/embed_images.py Adopt_a_Satellite_Relic_Map_bn_images.html ./images
```

Images must be named by relic ID, for example `lo1.webp`, `a11.webp`, `a15.webp`, `v1.webp`, `gal.webp`. Missing images are reported, not silently skipped.

**No Python?** Open `tools/embed_tool.html` in a browser. Choose the app file and the 19 WebP images, then download the built file. Everything runs locally.

## Repository layout

```
.
├── README.md
├── LICENSE                                 # Apache 2.0 full text (to be added)
├── index.html                              # the app (single file, images embedded)
├── tools/
│   ├── embed_images.py                     # embeds WebP images into the app as base64
│   └── embed_tool.html                     # browser-only version of the same step
├── docs/
│   └── Project_Detail_Adopt_a_Satellite.md # full project detail
└── tests/
    └── (Playwright checks; see Build and test)
```

> The layout above is the target. The current working files may use different names.

---

## Data sources (NASA and others)

This project relies heavily on NASA data. Every relic record carries its own source list inside the app, so a teacher can check any claim.

### Coordinates and landing-site data

| Source | Used for |
|---|---|
| NASA NSSDCA, Apollo landing-site coordinates (`lunar_sites.html`) | Apollo 11, 15 (LRRR and Lunar Module), 16, and 17 coordinates. Checked against this table. |
| NASA NSSDCA, lunar artifact impacts (`lunar_artifact_impacts.html`) | Lunar Orbiter 1 and other lunar artifact positions. Two NASA values differ slightly; the app shows both. |
| NASA NSSDCA, Surveyor (`surveyor.html`) | Surveyor 3 landing details and coordinates. |
| NASA NSSDCA, Apollo 16 and 17 pages (`apollo16info.html`, `apollo17info.html`) | ALSEP and mission background. |
| NASA Science, Apollo 12 and Surveyor 3 resource | Story context for Surveyor 3 and the Apollo 12 visit. |
| NASA JPL Photojournal, PIA03901 and related | Viking 1 and Viking 2 landing-site references. |
| NASA MOLA, Viking 1 page (`science.gsfc.nasa.gov/attic/mola/viking1.html`) | Viking 1 landing site and dates. |

### Mission and timeline data

| Source | Used for |
|---|---|
| NASA NSSDCA, Pioneer 10 and 11 (`pioneer10-11.html`) | Pioneer 10 and 11 mission facts and dates. |
| NASA Science, Pioneer 10 "sends last signal" | Pioneer 10 final contact. |
| NASA Science and NASA history news, Pioneer 11 | Pioneer 11 launch context (launched 1973). |
| NASA Science, Viking 1 and Viking mission pages | Viking mission facts. |
| NASA Science, Mars Pathfinder mission page | Pathfinder landing and end-of-mission dates. |
| NASA Science, Sojourner terrain resource | Sojourner context. |
| NASA Science, last commands to Opportunity | Opportunity's final contact and mission end. |
| JPL news, Spirit contact attempts concluded | Spirit's end of contact. |
| JPL news, Opportunity mission comes to an end | Opportunity's end of mission. |
| NASA Science, InSight mission page and NASA news on InSight retirement | InSight dates and mission end. |
| NASA news release, Ingenuity mission ends | Ingenuity's end of flights. |
| NASA history, Phoenix launch (launched 2007) | Phoenix launch date and context. |
| JPL, Phoenix mission page | Phoenix mission facts. |
| NASA Science, Cassini Grand Finale overview and NASA news release on Cassini's end | Cassini's final orbits and atmospheric entry. |
| JPL, Galileo mission page and NASA Science, Galileo probe | Galileo probe entry into Jupiter's atmosphere. |
| NASA mission page, Apollo 15 | Apollo 15 mission facts. |
| NASA mission page, Lunar Orbiter 1 | Lunar Orbiter 1 mission and impact context. |
| NASA Apollo Lunar Surface Journal, Apollo 11 overview (`alsj/a11/a11ov.html`) | Apollo 11 mission details. |

### Photos

| Relic | Photo source (as recorded for the project) |
|---|---|
| Lunar Orbiter 1 | NASA NSSDCA, "Lunar Orbiter 1 Earthrise" |
| Apollo 11 | LROC (Lunar Reconnaissance Orbiter Camera) gallery |
| Apollo 16 and 17 ALSEP | NASA Images (images.nasa.gov) |
| Apollo 15 Lunar Roving Vehicle | LROC gallery |
| Surveyor 3 | LROC images |
| Lunokhod 1 | LROC |
| Viking 1 and Viking 2 | JPL Photojournal |
| Spirit, Phoenix, Opportunity, Ingenuity, Sojourner, InSight | NASA Science and JPL image resources |
| Pioneer 10 and 11 | NASA NSSDCA |
| Cassini and Galileo | NASA Science |

> **Before publication:** confirm the reuse terms for each photo. Most NASA media is public domain, but some items carry credit lines or third-party rights. Record the exact licence for each image in `docs/`.

### Other standards and references

| Source | Used for |
|---|---|
| ITU-R M.1677-1, International Morse code | Morse timings and character set in Signal Lab |
| NASA technical reports (ntrs.nasa.gov, solarsystem.nasa.gov monograph) | Background on deep-space communication and mission engineering |
| NASA, *Beyond Earth: A Chronicle of Deep Space Exploration* | Historical context for the deep-space records |

### How the sources are kept honest

- Where two NASA sources disagree, the app shows both values and states which one the marker uses.
- The Apollo 15 marker is labelled as the **laser reflector (LRRR)** position, not the rover's parking place.
- Where a relic's position is not reliable, the app shows a note instead of a map marker.

---

## Tech stack

| Layer | Technology |
|---|---|
| App | Plain HTML5, CSS3 (variables, light and dark themes), and vanilla JavaScript. No framework, no bundler. |
| Audio | Web Audio API (`AudioContext`) for Morse tones |
| Drawing and postcards | Canvas 2D API, `toDataURL` for PNG export |
| Haptics | Vibration API, on phones that support it |
| Voice notes | `MediaRecorder` API, stored in **IndexedDB** |
| Progress and settings | `localStorage` |
| Backup and import | `Blob`, `FileReader`, `URL.createObjectURL`, JSON |
| Images | WebP, embedded as base64 data URIs inside the HTML |
| Typography | Hind Siliguri and other Bangla font names in the CSS stack. Fonts are not bundled; the device's installed fonts are used. |
| Build tools | Python 3 standard library (`base64`, `json`, `os`) for `embed_images.py`; a browser version in `embed_tool.html` |
| Testing | Node.js `node --check` for syntax; Python Playwright (headless Chromium) for click-through tests |
| Version control | Git and GitHub |

**Deliberately not used:** no backend, no database server, no analytics, no advertising SDKs, no CDN libraries, no external fonts. This keeps the app private and offline.

---

## Build and test

### Build the single file

```bash
python3 tools/embed_images.py <app-template.html> <folder-with-webp> [output.html]
```

The template must contain `const IMG={};`. The script writes one JSON object of base64 WebP images into it.

### Check syntax

```bash
node --check script.js
```

Extract the `<script>` block first, or use the test scripts below.

### Click-through test (Playwright, headless Chromium)

The test opens the built file, switches between English and Bangla, visits all nineteen records on each of the three worlds, and reports:

- any page errors
- any "pending" label visible on a record
- the number of images shown

Last recorded result: all 19 records open in both languages, 19 of 19 images show, and no page errors. Five Mars records still show "pending" labels (see [Known issues](#known-issues)).

---

## Accessibility

Built in, most without any setting:

- **Keyboard:** the main controls can be reached with Tab, with a visible focus outline.
- **Screen readers:** labelled buttons and cards, with `aria-label` and `role` attributes. Live regions announce results in the re-entry game.
- **Reduced motion:** animation follows the operating system's "reduce motion" setting.
- **Dark mode:** follows the device's light or dark setting.
- **Large touch targets:** interactive buttons are at least 44 px tall.
- **Safe-area padding:** content is not cut off on phones with notches.

**Not yet built:**

- In-app text-size control (currently relies on browser zoom)
- High-contrast option
- Dyslexia-friendly font option
- Read-aloud of stories
- Visual equivalent for sound-only Signal Lab parts beyond the flash mode
- Some icons and animations rely on colour or motion alone

**Planned accessibility panel:** text size, high contrast, dyslexia-friendly font, read-aloud, reduce motion, and a simple mode. It will be tested with screen-reader and keyboard-only users before release.

---

## Language support

- A **"বাংলা"** button switches the whole interface and all story text between Bangla and English. The choice is saved on the device.
- Numbers and dates appear with Bangla digits in Bangla mode (for example, 1969 becomes ১৯৬৯).
- Forty-three additional text items were translated for the newer relics, including place names, event names, and coordinate notes.

**Known gaps:**

- The NASA source-link titles stay in English, since they are page titles.
- The Bangla text was written for this project and needs review by a native speaker and a science teacher.
- Terms such as "relic", "probe", and "lander" need a consistent glossary.

---

## Offline use and low-connectivity schools

The app was built for hill and remote villages where internet is slow or absent.

- **One file.** Photos are embedded, so no separate files are fetched.
- **No network calls.** The code contains no `fetch` or `XMLHttpRequest` calls.
- **No external fonts or scripts.** Bangla text uses fonts already on the device.
- **Local data.** Progress, notes, and badges live in `localStorage` on the device. Voice notes live in IndexedDB.
- **Only NASA links need the internet.** The rest works fully offline.

**Getting the file to a school:** USB drive or memory card, Bluetooth file transfer, mobile messaging (even a slow connection is enough once), or a local school network share.

**Keeping content current:** publish each release as a new file with a version number. Progress does not sync between devices. Teachers can move progress with the Time Capsule backup file.

**Planned for schools without devices:** printable relic cards with a QR code to the NASA page, a printed Morse card, and a printable passport template.

---

## Privacy and child safety

- **No accounts.** Children enter only a nickname, which can be made up.
- **No tracking.** No analytics, advertising, or third-party trackers.
- **No community features.** Children cannot message each other or anyone else through the app.
- **Local data only.** Everything a child creates stays on the device unless a teacher exports a backup.
- **Honest framing.** The app repeatedly says it is a story and that nothing sent from it reaches a real spacecraft.

Teachers should still supervise shared devices and handle backups, which can contain private notes and voice recordings. Clearing the browser's site data for the app removes all stored data.

---

## Child-Given Reviews

We tested the app with **five children aged 6 to 12**. Their words are below, in the language they used (Bangla) with an English version beside each.

> **A note for the judges.** The quotes were lightly edited for clarity and translated into English so they are easy to read. The meaning and the feelings are the same as what the children said.
>
> **Child privacy.** We do not show photos, names, or any identifying details of the children. This follows the same rule as the app itself: children are never asked for personal information.
>
> **Consent.** Permission was obtained from the legal guardians of all five children.

### 1. The child who loved the Morse vibration
*Tested: Signal Lab (vibration mode)*

**বাংলা:** "যখন ফোনটা কম্পন করলো, আমার মনে হলো মহাকাশ থেকে কেউ আমাকে গোপন কোনো মেসেজ পাঠাচ্ছে! আমি চোখ বন্ধ করে কম্পন শুনেই বুঝে ফেলেছি।"

**English:** "When the phone vibrated, it felt like space was sending me a secret message! I closed my eyes and understood the code just by feeling it."

### 2. The child who played Rescue / Remember
*Tested: Rescue / Remember*

**বাংলা:** "আমি জানতাম না মঙ্গলে এত রোবট আটকে আছে! আমি প্রথমে একটা রোবটকে ফিরিয়ে আনতে চেয়েছিলাম, কিন্তু পরে ভাবলাম ওটা ওখানে একা থাকবে, তাই আমি ওর গল্পটা মনে রাখার সিদ্ধান্ত নিলাম।"

**English:** "I didn't know so many robots were stuck on Mars! I wanted to bring one back, but then I felt sad thinking about leaving it alone. So, I decided to remember its story instead."

### 3. The child who used the Bangla toggle and the Time Capsule
*Tested: Bangla / English toggle and Time Capsule*

**বাংলা:** "আমি স্পিরিট রোভারের জন্য বাংলায় একটা চিঠি লিখেছি! নিজের ভাষায় মহাকাশের গল্প পড়তে এবং লিখতে খুব মজা লাগছে। আগে মনে হতো এগুলো শুধু ইংরেজিতে পড়তে হয়।"

**English:** "I wrote a message in Bengali for the Spirit rover! It's so fun to read about space in my own language. I used to think I could only read these in English."

### 4. The child who adopted a relic
*Tested: Relic Map and "Adopt this relic"*

**বাংলা:** "আমি অ্যাপোলো ১১-কে অ্যাডপ্ট করেছি। এখন মনে হয় ওটা আমার নিজের পাওয়া কোনো কিছু! স্কুলে বন্ধুদের বলবো, আমার নিজের একটা স্পেস মেশিন আছে।"

**English:** "I adopted Apollo 11. It feels like it's mine now! I'm going to tell my friends at school that I have my own space machine."

### 5. The child whose idea of space changed
*Tested: the whole app*

**বাংলা:** "আমি ভাবতাম শুধু রকেট ওড়ানোই মহাকাশ। এখন জানলাম পুরোনো মেশিনগুলোর গল্পও কত সুন্দর। আমি বড় হয়ে স্পেস ইঞ্জিনিয়ার হতে চাই, যাতে আমি এমন রোবট বানাতে পারি যেটা কখনো নষ্ট হবে না!"

**English:** "I used to think space was just about launching rockets. Now I know the stories of old machines are so cool. I want to be a space engineer when I grow up so I can build robots that never stop working!"

### What the children's words tell us

| Feature | What a child said | What it suggests |
|---|---|---|
| Signal Lab, vibration | Understood Morse "just by feeling it" with eyes closed | Touch can carry the message, which matters for children who cannot rely on sight or sound |
| Rescue / Remember | Chose to remember a robot's story instead of bringing it back | The activity builds empathy and the idea of remembrance, our project theme |
| Bangla toggle and Time Capsule | Wrote a Bangla message to the Spirit rover | Reading and writing in their own language makes space feel within reach |
| Adopt this relic | "It feels like it's mine now" | Ownership makes children want to share the story with friends |
| Whole app | Space is not only rockets, and old machines have stories | The app changes how children see space, and one child now wants to be a space engineer |

### How far this feedback goes

This was an informal test with five children, not a controlled study. The quotes show how these children felt. They do not measure learning outcomes, and five children cannot represent all learners. A larger school pilot is part of our roadmap, and we plan to include children with different abilities and in different regions.

---

## Roadmap

**Immediate next steps (after judging)**

1. Fix the five Mars records that still show "pending" labels.
2. Verify dates and coordinates for the newer records against the NASA pages.
3. Get the Bangla text reviewed by a native speaker.
4. Write a short teacher guide in Bangla and English.
5. Test on Android phones and tablets.
6. Record a two-minute demo that runs with the internet off.

**Future goals (2031–2036 vision, plans and not commitments)**

1. Build the accessibility panel (text size, contrast, dyslexia font, read-aloud, simple mode).
2. Add Bangla and English read-aloud.
3. Produce printable relic cards, Morse cards, and passport templates.
4. Run a school pilot in a rural or hill area.
5. Add an Earth-Orbit Tracker and more relics, including ISS retirement and Artemis-era equipment.
6. Split the code into modules and add automated tests for storage, import, and audio.

**Coming soon (in development, not in the current file)**

- **Earth-Orbit Tracker:** an orbit tracker for satellites around Earth.

---

## Known issues

- **Five Mars records** (Spirit, Phoenix, Opportunity, Ingenuity, Pathfinder) still show "pending" labels for coordinate verification or source links.
- **Some dates and coordinates** for newer records (Pathfinder, InSight, Cassini, Galileo, Pioneer 11, Lunokhod 1, and some Mars rovers) have not been checked line by line against current NASA pages.
- **Bangla translations** have not been reviewed by a native speaker.
- **Limited testing so far:** the app has been tried informally with five children (see [Child-Given Reviews](#child-given-reviews)). Broader testing on low-end Android devices and a classroom pilot are still to do.
- **Code structure:** the script is in large blocks, and there are no automated unit tests for storage, import, or audio.
- **Bangla text** uses a mapping step, so new English text needs a matching Bangla entry added by hand.

---

## Contributing

Contributions are welcome, especially:

- checking dates and coordinates against NASA sources
- native-speaker review of Bangla text
- accessibility testing with screen readers and keyboard-only use
- testing on low-end devices and in schools

**Please:** cite a NASA source for every new fact, add the source to the relic record, and run the click-through test before opening a pull request.

**Please don't:** add analytics, external scripts, accounts, or any feature that sends children's data off the device.

---

## AI usage and transparency

AI tools were used as assistants. The team made all design, data, and storytelling decisions and checked the final work.

**Tools used**
- **Claude (Anthropic) and ChatGPT (OpenAI):** code suggestions (CSS animation ideas, Canvas drawing logic, debugging JavaScript event listeners), first drafts of this README and the project summary, and first-draft Bangla translations of some newer text. The team reviewed all of it.
- **ElevenLabs (Antoni voice):** generated the voiceover from a script written by the team.

**Human work**
- The team wrote the voiceover script, chose the pacing, and directed the tone.
- The team designed the single-file architecture, the offline storage (localStorage and IndexedDB), and the user interface.
- All NASA data, coordinates, dates, and the 19 relic records were researched and entered by the team.
- The 2035 vision and the child feedback summary were written and reviewed by the team.

**Image assets**
- No AI tools were used for images. All 19 relic images are NASA images (NSSDCA, JPL, and LROC), compressed to WebP by the team.

**Pending:** the Bangla translations still need review by a native speaker (see [Known issues](#known-issues)).

---

## Licence and attribution

- **Code:** Apache License 2.0. This matches NASA's default for Space Apps submissions if no OSI licence is chosen, and it is an OSI-approved licence. A `LICENSE` file with the full text must be added to the repository.
- **NASA material:** facts, dates, coordinates, and photos come from NASA and other public sources, as listed in [Data sources](#data-sources-nasa-and-others). Each NASA image's reuse terms should be confirmed and recorded before publication.
- **Team:** Team Tiny Sparks, NASA Space Apps Challenge 2026.

Thanks to the NASA teams behind the mission archives, the NSSDCA landing-site tables, the JPL Photojournal, the Lunar Reconnaissance Orbiter Camera, and the Apollo Lunar Surface Journal, whose public records made every relic story possible.
```

