
---

# ☀️ SOLAR DODGER | HYPER-MAX

> **AVOID THE OBSTACLES // SYNC TO THE RHYTHM**

**Solar Dodger** is a high-performance, rhythm-synced survival game built entirely in Vanilla JavaScript. It features a custom **Hybrid Audio Engine** that synchronizes gameplay events, visual pulses, and obstacle spawning to the beat of the music.

---

## 🎮 Play the Demo

### [👉 LAUNCH SYSTEM (Play Demo)](https://wall-e-code.github.io/SOLAR-DODGER-HYPER-MAX-Plus/)

---

## ✨ Features

* **3 Distinct Phases:**
* **Phase 1 (Solar):** 130 BPM. Deep red visuals. Standard dodging.
* **Phase 2 (Neon):** 150 BPM. Cyber-grid aesthetics. Moving "Neon Block" obstacles.
* **Phase 3 (The Void):** 180 BPM. High intensity. Includes "Seeker" enemies that track the player.


* **Hybrid Audio Engine:**
* Uses the **Web Audio API** to analyze time and schedule events with high precision.
* Falls back to a procedural **Synth Mode** (generating audio waves in real-time) if MP3 assets are missing.


* **Dynamic Visuals:**
* Smooth CSS Variable transitions for phase coloring.
* 60FPS Canvas rendering with particle systems and screen shake.
* UI "Glitch" effects and sci-fi HUD.


* **Cross-Platform:**
* Desktop: Keyboard controls.
* Mobile: Touch zones or Swipe gestures (Lock-to-Landscape supported).



---

## 🕹️ Controls

The game supports multiple control schemes which can be toggled in the settings menu.

| Platform | Control Style | Action |
| --- | --- | --- |
| **PC / Desktop** | **Keyboard** | `A` / `D` or `Left Arrow` / `Right Arrow` to strafe. |
| **Mobile** | **Tap Mode** | Tap the **Left** or **Right** side of the screen. |
| **Mobile** | **Swipe Mode** | Swipe anywhere on screen to move lanes. |

---

## 🛠️ Technical Architecture

This project demonstrates advanced front-end techniques without external game engines.

### 1. The Game Loop & State

The game utilizes `requestAnimationFrame` for a smooth render loop. Logic is separated into `update()` (physics/state) and `draw()` (canvas rendering).

* **Lane Logic:** A 5-lane grid system with "Lane Reservation" logic to ensure it is mathematically impossible to spawn an unwinnable wall of obstacles.
* **Collision:** AABB (Axis-Aligned Bounding Box) collision detection with "Invincibility Frames" after damage.

### 2. Audio-First Scheduling

Instead of using `setInterval` (which drift), the game uses the **Web Audio API `currentTime**` as the master clock.

* **Lookahead Scheduler:** A recursive function queues notes and game events slightly into the future to ensure perfect timing, even if the main thread lags.
* **BPM Sync:** Obstacles spawn exactly on the beat (Quarter notes, Eighth notes) depending on the active Phase.

### 3. CSS & Performance

* **Paint Flashing:** Minimized by using CSS Transforms for UI animations.
* **Variables:** CSS Custom Properties (`--active-color`, `--p1-bg`) control the entire theme, allowing the JS to switch the game's "Phase" by simply toggling a class on the `<body>`.

---

## 📂 Project Structure

```text
/
├── index.html       # DOM structure, HUD, and Audio Elements
├── style.css        # CSS3, Animations, Sci-fi UI styling
├── script.js        # Game Engine, Audio Context, Logic
├── README.md        # Documentation
└── audio/           # (Optional) Place .mp3 files here
    ├── phase1_solar_130.mp3
    ├── phase2_neon_150.mp3
    └── phase3_void_180.mp3

```

> **Note:** If you do not provide the audio files in the `/audio` folder, the game automatically switches to **Synth Mode**, procedurally generating a soundtrack using Oscillators.

---

## 🚀 Local Installation

1. **Clone the repository:**
```bash
git clone https://github.com/WaLL-E-code/SOLAR-DODGER-HYPER-MAX-Plus.git
cd SOLAR-DODGER-HYPER-MAX-Plus

```


2. **Run a local server:**
Because the game uses the `AudioContext`, modern browsers may block audio functionality if you simply double-click `index.html` (due to CORS policies). Use a local server:
* **VS Code:** Install "Live Server" extension -> Right Click `index.html` -> "Open with Live Server".

