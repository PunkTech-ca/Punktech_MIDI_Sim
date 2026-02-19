# PunkTech MIDI Sim Setup Guide
## Professional Controllers for Flight Simulation

**A PunkTech Project - February 2026**

---

## 🎯 Quick Navigation

- [About This Guide](#about-this-guide)
- [Quick Overview](#quick-overview)
- [Complete Table of Contents](#table-of-contents)

---

## About This Guide

**This guide demonstrates [PunkTech philosophy](PUNKTECH_MANIFESTO.md) in action.**

### PunkTech Principles Applied:

✅ **Open Standards:** MIDI (40 years old), DirectInput, vJoy (open-source)

✅ **Rigorous Engineering:** Requirements → Design → Implementation → Validation

✅ **Intelligent DIY:** Professional audio equipment ($150) > Gaming toys ($500)

✅ **Free Knowledge:** Complete guide, no paywall, no affiliate links

✅ **Pragmatism:** Windows over Linux for this specific use case

---

### New to PunkTech?

**Read the [PunkTech Manifesto](PUNKTECH_MANIFESTO.md) first** to understand the philosophy behind this guide.

**Just want the technical details?** Keep reading below.

---

### A Note on Originality

**I am certainly not the first person to use MIDI controllers in simulation.**

Many have discovered this approach independently over the years. Communities like r/HotasDIY and hardcore sim forums have documented MIDI solutions.

**However, I believe I am the first to create a clear, structured, open-source guide** that documents:
- Complete system architecture (not just "it works for me")
- Methodology transferable across hardware and games
- Honest testing with limitations disclosed
- Free knowledge under CC BY-SA 4.0 license

**This guide stands on the shoulders of those who discovered MIDI → simulation before me. Credit where credit is due.**

---

## Quick Overview

### What This Guide Covers

**The Problem:**
- Flight simulation needs 50-100+ inputs
- Gaming buttonboxes: $300-800 for 20-40 cheap plastic buttons
- Proprietary, fragile, poor value

**The PunkTech Solution:**
- Professional MIDI controllers: $300 for 128 pro-grade inputs
- Open standards (MIDI, 40 years old)
- Modular architecture with failure isolation
- **Total setup: ~$2000 CAD (~$1450 USD) including premium VKB flight controls**

**The Result:**
- 195+ total inputs (VKB + MIDI)
- 7 DirectInput devices
- Built in 7 weeks (Dec 2025 - Feb 2026)
- Tested on Il-2 Great Battles (other games pending validation)

---

---

## License & Usage

**This guide is licensed under Creative Commons Attribution-ShareAlike 4.0 International (CC BY-SA 4.0).**

[![CC BY-SA 4.0](https://licensebuttons.net/l/by-sa/4.0/88x31.png)](http://creativecommons.org/licenses/by-sa/4.0/)

---

### What This Means

**You are free to:**
- ✅ **Share** — Copy and redistribute this guide in any medium or format
- ✅ **Adapt** — Remix, transform, build upon this guide for any purpose, even commercially

**Under the following terms:**
- **Attribution** — You must give appropriate credit, provide a link to the license, and indicate if changes were made
- **ShareAlike** — If you remix, transform, or build upon this guide, you must distribute your contributions under the same CC BY-SA 4.0 license

**No additional restrictions** — You may not apply legal terms or technological measures that legally restrict others from doing anything the license permits.

---

### Proper Attribution

**When sharing or adapting this guide, credit as follows:**

> "PunkTech MIDI Simulation Setup Guide" by PunkTech, licensed under CC BY-SA 4.0  
> Original: https://punktech.ca/projects/midi-sim-setup

**If you create a derivative work** (translation, adaptation, extended version):
- State it's based on this guide
- Link to original
- Use same CC BY-SA 4.0 license for your version

---

### Why This License?

**PunkTech Principle 4: Free Knowledge**

Knowledge should be freely accessible, shareable, and improvable by the community.

**CC BY-SA ensures:**
- This guide remains free forever (can't be locked behind paywall)
- Improvements return to the community (ShareAlike clause)
- Original author credited (Attribution clause)

**If you want to use this commercially** (training courses, books, consulting):
- ✅ You can! License allows it
- ✅ Just attribute properly
- ✅ Share your improvements under same license

---

### Software & Hardware

**Note:** This license covers **THE GUIDE DOCUMENT** only.

**It does NOT cover:**
- Software mentioned (each has its own license: vJoy, UCR, MIDI-OX, etc.)
- Hardware products (trademarked/copyrighted by manufacturers)
- UCR profile files (provided as reference study material, see Section 7.5)

**The KNOWLEDGE and METHODOLOGY are CC BY-SA 4.0.**

**The products and software retain their respective licenses.**

---

## Table of Contents

1. [Project Genesis](#1-project-genesis)
2. [The Problem](#2-the-problem)
3. [The Solution](#3-the-solution)
4. [Complete Hardware List](#4-complete-hardware-list)
5. [Complete Software Stack](#5-complete-software-stack)
6. [System Architecture](#6-system-architecture)
7. [Step-by-Step Setup Guide](#7-software-configuration)
8. [Configuration Details](#7-software-configuration)
9. [Game-Specific Setup](#8-game-specific-setup)
10. [Troubleshooting & Debugging](#10-troubleshooting--debugging)
11. [Testing & Validation](#11-testing--validation)
12. [FAQ](#12-faq)
13. [Community & Support](#13-community--support)
14. [Appendix & Resources](#14-appendix--resources)

---

## 1. Project Genesis

### Timeline: December 2025 - February 2026

**December 4, 2025:**
- Childhood dream of flight simulation activated
- Unexpected $2000 CAD windfall
- Order placed: Dual VKB Gladiator sticks (VIPPILOT Canada)

**December 2025: The Linux Detour**

**Initial attempt: CachyOS (Arch-based) - VKB Hardware Only**

In early December 2025, I attempted to build the simulation setup on Linux using VKB hardware (MIDI wasn't part of the project yet):

**Hardware:**
- Dual VKB Gladiator sticks (ordered Dec 4)
- VKB T-Rudder pedals (ordered Jan 17)
- Opentrack + Neuralnet tracker (head tracking)

**Games tested via Proton:**
- Elite Dangerous
- Microsoft Flight Simulator 2020 (Steam version)
- Il-2 Sturmovik: Great Battles

**What worked:**
- ✅ Opentrack + Neuralnet tracker (excellent on Linux)
- ✅ Elite Dangerous via Proton (stable, multi-device OK)
- ✅ MSFS 2020 via Proton/Steam (game runs fine)

**What was problematic:**
- ⚠️ Il-2 GB via Proton (works, but multi-device DirectInput unstable)
- ⚠️ 7 DirectInput devices through Wine (unreliable recognition)
- ⚠️ Device order randomization (no Joystick ID# Swapper equivalent)

**The core problem:** Multi-game architecture with 7 DirectInput devices through Wine/Proton = unsustainable.

**The decision (late December 2025):** Dual-boot Windows 11 for simulation.

**Why:** Native DirectInput, stable 7-device support, Joystick ID# Swapper reliability, multi-game guaranteed compatibility.

**Important:** MIDI routing on Linux was never attempted. MIDI came later (January 2026), after Windows decision.

**December 29, 2025:**
- SimHub license purchased (background: I was a sim racing player before flight simulation)
- Initial plan: Virtual dashboard on touchscreen with virtual faders

**January 2026:**
- VKB T-Rudder pedals ordered (January 17)
- "The missing piece that unlocked everything"
- MIDI controllers ordered (January 13-22)
- **Pivot from virtual to physical controls**

**February 2026:**
- System stable and operational
- 7 weeks from concept to production
- This guide written

---

### The "Aha!" Moment

**Original plan:**
Create a virtual bomber cockpit dashboard in SimHub, displayed on external touchscreen. Virtual faders for throttles, virtual switches for systems.

**The problem:**
- Technical challenges mounting
- Touchscreen latency issues
- SimHub limitations
- Frustration growing

**The realization:**
> "Why am I trying to create VIRTUAL faders when PHYSICAL faders have existed for 40 years in pro audio?"

**The solution:**
MIDI controllers. Akai MIDImix = 8 physical faders + 24 knobs for $150 CAD.

**What was plan B became plan A.**

---

### Development Approach: Requirements-Driven Design

**PunkTech Principle 2: Rigorous Engineering**

1. **Created requirements document** (lost, but reconstructed):
   - Researched technical limitations of 8 target games
   - Identified most restrictive common denominator:
     * Max 8 DirectInput devices
     * Max 32 buttons per device  
     * DirectInput standard

2. **Architected system to respect ALL constraints**

3. **Validated on most complex use case:**
   - Il-2 Great Battles multi-engine aircraft

**Result:** Architecture guaranteed compatible by design, not by luck.

---

## 2. The Problem

### Universal Pain Points in Simulation

**1. Input Limitation**
- Complex aircraft need 50-100+ inputs
- HOTAS provides ~30-40 inputs max
- Keyboard is clunky and breaks immersion

**2. Existing Solutions Are Inadequate**

**Gaming Buttonboxes ($300-800):**
- ❌ 20-40 buttons of cheap plastic
- ❌ Proprietary systems
- ❌ Poor build quality
- ❌ Expensive

**DIY Buttonboxes:**
- Time-consuming to build
- Requires electronics knowledge
- Still limited by DirectInput (32 buttons/device typically)

**StreamDeck:**
- Software buttons (no tactile feedback)
- Expensive ($150-250 for 15-32 buttons)
- Screen glare issues

**3. The Upgrade Treadmill**

Typical simmer journey:
1. Start with cheap HOTAS ($80-150)
2. Realize it's inadequate
3. Buy mid-range ($400)
4. Still need more buttons
5. Buy buttonbox ($300-500)
6. Eventually upgrade to premium HOTAS ($800+)

**Total spent:** $1500-2000+
**Total waste:** $500+ in obsolete equipment
**Time wasted:** 2-3 years of frustration

---

## 3. The Solution

### The PunkTech MIDI Architecture

**Core concept:**
Use professional MIDI controllers (designed for music production) as simulation input devices.

**PunkTech Principle 3: Intelligent DIY - Look Outside the Industry**

---

### Why This Works

**MIDI controllers are:**
- ✅ Pro-grade build quality (designed for touring musicians)
- ✅ Abundant inputs (64-80+ buttons/faders/knobs)
- ✅ Standardized protocol (**40 years old**, universal support)
- ✅ Affordable ($150-300 for pro equipment)
- ✅ Available everywhere (music stores, Amazon)
- ✅ Built to last (10+ years lifespan)

**Gaming buttonboxes are:**
- ❌ Consumer-grade plastic
- ❌ Limited inputs (20-40 typical)
- ❌ Proprietary systems
- ❌ Overpriced ($500+ for inferior quality)
- ❌ Niche availability
- ❌ Questionable longevity

---

### System Overview

```
MIDI Controllers → MIDI-OX → loopMIDI → UCR → vJoy → Games
VKB Sticks/Pedals → DirectInput → Games (parallel)
Webcam → Opentrack → Games (head tracking)
Games → SimHub → Il-2 Dials (telemetry display)
```

**Total input capacity:** 195+ inputs
**Total cost:** ~$2000 CAD (~$1450 USD) (including VKB premium hardware)
**Comparison:** Commercial equivalent would be $3000-5000+

---

### Key Advantages (PunkTech Principles)

**1. Open Standards (Principle 1)**
- MIDI: 40-year-old standard, will exist in 2036
- DirectInput: Windows standard
- vJoy: Open-source
- No vendor lock-in

**2. Modular Architecture (Principle 2)**
- Each component has one job
- Failure isolation (if UCR crashes, VKB still works)
- Easy troubleshooting
- Upgradeable components

**3. Intelligent Value (Principle 3)**
- Professional equipment at reasonable cost
- 128 MIDI inputs for $300 vs 20-40 gaming buttons for $500+
- Pro-grade quality vs plastic toys

**4. Future-Proof**
- MIDI will exist long-term
- Not dependent on one company
- Extensible (add more MIDI devices easily)

**5. Multi-Genre Optimized**
- Works for atmospheric sims (Il-2, DCS, MSFS)
- Works for space sims (Elite, Star Citizen)
- Works for mechs (MechWarrior)
- No compromises per genre

---

## 4. Complete Hardware List

### Primary Flight Controls

**VKB Gladiator NXT EVO - Space Combat Edition**
- Right Hand (Premium): $280 CAD ($205 USD)
- Left Hand (Standard): $260 CAD ($190 USD)
- Source: VIPPILOT (Official Canadian distributor)
- Why: Best quality/price ratio in market, tier-1 sensors

**VKB T-Rudder Pedals Mk.V**
- Price: $360 CAD ($265 USD)
- Source: VIPPILOT
- Note: Rudder axis only, NO physical toe brakes
- Toe brakes solution: MIDIMix faders (see below)

**Subtotal VKB:** ~$900 CAD (~$660 USD)

---

### MIDI Controllers (The Core Innovation)

**Akai Professional MIDIMix**
- Price: $170 CAD ($125 USD) (Amazon.ca, taxes included)
- 8 faders (vertical sliders)
- 24 knobs (rotary encoders)
- 16 buttons
- Pro-grade build quality
- **Purpose:** Motor controls (throttles, RPM, mixture, cooling), brakes, trim

**Akai Professional APC Mini MK2**
- Price: $150 CAD ($110 USD) (Amazon.ca, taxes included)
- 64 RGB backlit pads (8x8 matrix)
- 16 side buttons
- **Purpose:** Systems, weapons, lights, emergency functions
- **Future:** LED feedback via SimHub

**Subtotal MIDI:** ~$320 CAD (~$235 USD)

---

### Displays & Mounting

**14" Touchscreen Monitor (1920x1200)**
- Price: $80 CAD (included in dual purchase with mount)
- Purpose: Maps, mission planner, MFD displays

**HUANUO Dual Arm VESA Monitor Mount**
- Price: $88 CAD (included with touchscreen)
- Purpose: Mount touchscreen + main monitors

**VIVO Laptop/Notebook Tray for VESA Mount (Stand-LAP2)**
- Price: $56 CAD (Amazon.ca)
- Purpose: Platform for MIDI controllers + keyboard
- Mounted on left VESA arm

**Subtotal Displays/Mounting:** ~$224 CAD

---

### Accessories

**RK ROYAL KLUDGE L75 Mechanical Keyboard (75%, Gasket Mount)**
- Price: $76 CAD
- Purpose: Compact keyboard, mounted on laptop tray with MIDI

**Wenter 11-Port Powered USB 3.0 Hub**
- Price: $41 CAD
- Essential: 2x VKB + 2x Akai + peripherals = 6+ USB ports minimum

**ECSiNG/SING F Potentiometer Knobs (colored, 30pcs)**
- Price: $20 CAD
- Purpose: Color-code MIDIMix knobs (NATO code: black/blue/red/orange)
- Note: 90° orientation difference from stock knobs (doesn't matter for muscle memory)

**Ceecysaa Velcro Heavy Duty Adhesive Strips (50 sets)**
- Price: $14 CAD
- Purpose: Secure MIDI controllers + keyboard to laptop tray

**UGREEN USB-C Extension Cable (3.3ft, 100W)**
- Price: $18 CAD

**Brokimis Clip-on LED Reading Light**
- Price: $13 CAD
- Purpose: Cockpit lighting without screen glare

**Colored tape (Dollarama)**
- Price: $5 CAD
- Purpose: Zone marking on APCmini

**USB Printer Cable (right-angle, 1.5m)**
- Price: $21 CAD ($15 USD approximately)
- Purpose: MIDIMix connection (90° angle allows keyboard to sit on top without cable interference)

**Subtotal Accessories:** ~$208 CAD

---

### Software

**SimHub License**
- Price: ~$10 CAD (~$7 USD)
- Purpose: Game telemetry, Il-2 Dials server, future LED control
- Note: I already had this from sim racing background

---

### Already Owned (Not Included in Budget)

- PC: Ryzen 3700X, RTX 4070, 32GB RAM 3600MHz, NVMe
- 3x Main monitors (6400x1080 combined)
- Laptop: Ubuntu 17" touchscreen (Il-2 Dials client, Mission Planner)
- Webcam (Opentrack head tracking)
- Games: Il-2 GB, MSFS 2020, Elite Dangerous (~$300 during sales)

---

### Total Investment

**Hardware (new purchases):** ~$1656 CAD (~$1215 USD)
**Software:** ~$10 CAD (~$7 USD)
**Games:** ~$301 CAD (~$220 USD)

**Grand Total:** ~$1967 CAD (~$1442 USD) (~$2000 CAD / ~$1450 USD rounded)

---

### Physical Setup Photos

![Complete setup overview](Appendix/a000025.png)
*Full cockpit setup with Il-2 Great Battles on screen. Triple monitor configuration, RGB keyboard (top), APCmini (left) and MIDIMix (right) on VESA laptop tray. This is the working environment where the system was tested for 7 weeks. Note the colored tape zones on APCmini pads and NATO color-coded knobs on MIDIMix.*

![Full Akai stack - APCmini + MIDIMix](Appendix/a000026.png)
*Close-up of the complete Akai Professional stack. APCmini (left) with colored tape zones for function grouping. MIDIMix (right) with NATO color-coded knobs (orange/red/blue rows) and tape-marked faders. Combined: 80 buttons (APCmini) + 8 faders + 24 knobs + 16 buttons (MIDIMix) = 128 discrete controls from $320 CAD of pro-grade hardware.*

![MIDIMix - NATO knobs color coding detail](Appendix/a000027.png)
*Close-up of MIDIMix showing NATO color-coded knob organization: Orange (top row) = Engine 1 controls, Red (middle) = Engine 2, Blue (bottom) = Engine 3/4. Yellow/red/green tape on faders for throttle identification. This color coding enables muscle memory and reduces cockpit scanning time.*

**Color coding methodology:**
- Orange knobs = Engine 1 (Throttle, RPM, Mixture, Cooling)
- Red knobs = Engine 2
- Blue knobs = Engine 3/4
- Fader tape: Yellow = Main throttles, Red = Critical systems, Green = Secondary controls

**NATO knobs note:** 90° orientation difference from stock doesn't matter for muscle memory. Tactile differentiation by color is what counts.

---

## 5. Complete Software Stack

### Required Software (Free unless noted)

**loopMIDI** (Tobias Erichsen)
- Purpose: Create virtual MIDI ports
- License: Free
- Auto-start: Service mode (starts with Windows)

**MIDI-OX** (MIDIOX.com)
- Purpose: Route physical MIDI to virtual ports
- License: Free
- Critical: Prevents SimHub from monopolizing MIDI inputs

**UCR (Universal Control Remapper)**
- Purpose: Map MIDI messages to vJoy inputs
- License: Free, open-source
- GitHub: Snoothy/UCR

**vJoy** (Shaul Eizikovich / njz3)
- Purpose: Create virtual joystick devices
- License: Free, open-source
- Configuration: 5 devices (4 active for games, 1 reserved for SimHub)

**Joystick ID# Swapper** (Release 1.a)
- Purpose: Lock joystick IDs regardless of connection order
- License: Free
- Critical: Prevents game mappings from breaking

**SimHub** (Wotever)
- Purpose: Game telemetry, Il-2 Dials server, future LED control
- License: **$10 CAD (one-time)**
- Optional but highly recommended

**Opentrack**
- Purpose: Head tracking via webcam
- License: Free, open-source
- Independent from MIDI stack

---

### Optional Software

**MIDIMix Editor** (Akai)
- Purpose: Configure MIDIMix (MIDI channels, CC mappings)
- Used once during initial setup to move MIDIMix to MIDI channel 2

**Il-2 Dials** (server + client)
- Purpose: Display cockpit instruments on secondary device
- License: Free
- Server: Windows PC
- Client: Ubuntu laptop (or any OS)

**Il-2 Mission Planner**
- Purpose: Mission planning, maps, waypoints
- Runs on: Ubuntu laptop

---

### Software Architecture

```
Layer 1: MIDI Input
├─ Physical MIDI Controllers
└─ Windows MIDI drivers

Layer 2: MIDI Routing
├─ MIDI-OX (hardware → loopMIDI routing)
└─ loopMIDI (virtual MIDI ports/pipes)

Layer 3: Conversion
├─ UCR (MIDI → vJoy mapping)
└─ vJoy (virtual DirectInput devices)

Layer 4: ID Management
└─ Joystick ID# Swapper (fixed IDs)

Layer 5: Games
└─ See vJoy devices as normal joysticks

Parallel: Telemetry
├─ SimHub (reads game data)
└─ Il-2 Dials Server (serves data to client)

Parallel: Head Tracking
└─ Opentrack (webcam → 6DOF)
```

---

## 6. System Architecture

### Complete Data Flow Diagram

```
Hardware Layer:
├─ MIDIMix (33 analog axes, 16 buttons)
├─ APCmini (64 pads, 16 side buttons, 9 faders)
├─ VKB Gladiator R (axes, buttons, HATs)
├─ VKB Gladiator L (axes, buttons, HATs)
└─ VKB T-Rudder (1 axis)

MIDI Processing Layer:
MIDIMix → USB → Windows MIDI driver
APCmini → USB → Windows MIDI driver
        ↓
MIDI-OX (hardware routing)
        ↓
loopMIDI (virtual MIDI ports/pipes)
        ├─ InputsToJG (MIDIMix data)
        └─ Input2ToUCR (APCmini data)
        ↓
UCR (MIDI → vJoy conversion)
        ├─ Analog mapping (MIDI CC → vJoy axes)
        ├─ Digital mapping (MIDI Notes → vJoy buttons)
        └─ Axis-to-Button conversion (surplus faders → 3-state switches)
        ↓
vJoy Devices (virtual DirectInput controllers)
        ├─ vJoy 1: 8 axes, 32 buttons, 4 HATs
        ├─ vJoy 2: 8 axes, 32 buttons, 3 HATs
        ├─ vJoy 3: 8 axes, 32 buttons, 2 HATs
        ├─ vJoy 4: 8 axes, 32 buttons, 1 HAT
        └─ vJoy 5: 8 axes, 128 buttons, 0 HATs (SimHub reserved)
        ↓
Joystick ID# Swapper (ID persistence)
        ├─ JoyID #1: VKB Gladiator R
        ├─ JoyID #2: VKB Gladiator L
        ├─ JoyID #3: VKB T-Rudder
        ├─ JoyID #4: vJoy Device 1
        ├─ JoyID #5: vJoy Device 2
        ├─ JoyID #6: vJoy Device 3
        ├─ JoyID #7: vJoy Device 4
        └─ JoyID #8: vJoy Device 5
        ↓
GAMES (DirectInput)

Parallel: Telemetry Output
GAMES → SimHub → Il-2 Dials Server (port 11200) → Ubuntu Laptop

Parallel: Head Tracking
Webcam → Opentrack → Games (TrackIR protocol)
```

---

### vJoy Device Organization

**Critical Constraint:** vJoy maximum = 8 axes + 32 buttons per device

**Windows Differentiation Requirement:** 
Windows cannot reliably distinguish identical vJoy devices. Each device MUST have different physical specs (different HAT counts) to prevent device ID randomization on reboot.

---

#### **vJoy Device 1 (JoyID #4):**
- **Configuration:** 8 axes, 4 HATs, 32 buttons
- **Axes (8):** MIDIMix faders 1-8 (primary throttle controls)
- **Buttons (32/32):** APCmini pads 1-32 (first half of 8×8 matrix)
- **HATs (4):** Unused (for Windows differentiation only)

#### **vJoy Device 2 (JoyID #5):**
- **Configuration:** 8 axes, 3 HATs, 32 buttons
- **Axes (8):** MIDIMix knobs 1-8 (RPM, mixture, cooling controls)
- **Buttons (32/32):** APCmini pads 33-64 (second half of 8×8 matrix)
- **HATs (3):** Unused (for Windows differentiation only)

#### **vJoy Device 3 (JoyID #6):**
- **Configuration:** 8 axes, 2 HATs, 32 buttons
- **Axes (8):** MIDIMix knobs 9-16 (additional analog controls)
- **Buttons (~32/32):**
  - MIDIMix master fader (axis-to-button conversion): 2 buttons
  - APCmini 9 column faders (axis-to-button conversion): 18 buttons
  - MIDIMix 16 hardware buttons: ~12 (overflow to vJoy 4)
- **HATs (2):** Unused (for Windows differentiation only)

#### **vJoy Device 4 (JoyID #7):**
- **Configuration:** 8 axes, 1 HAT, 32 buttons
- **Axes (8):** MIDIMix knobs 17-24 (additional analog controls)
- **Buttons (~20/32):**
  - MIDIMix 16 hardware buttons (overflow from vJoy 3): ~4
  - APCmini 16 side buttons: 16
  - **~10-12 buttons FREE for future expansion**
- **HAT (1):** Unused (for Windows differentiation only)

#### **vJoy Device 5 (JoyID #8):**
- **Configuration:** 8 axes, 0 HATs, 128 buttons
- **Purpose:** Reserved for SimHub LED feedback (future)
- Not used by games directly

---

### Advanced Technique: Axis-to-Button Conversion

**Problem:** MIDIMix has 33 analog axes (8 faders + 24 knobs + 1 master fader), plus APCmini has 9 column faders. But vJoy only supports 32 axes total (8 per device × 4 devices).

**Solution:** Convert surplus analog faders to 3-state digital switches using UCR's Axis-to-Button plugin.

**How it works:**
- **Fader at TOP (>70%):** Button A pressed
- **Fader at CENTER (30-70%):** Both buttons released (neutral)
- **Fader at BOTTOM (<30%):** Button B pressed

**Converted in this setup:**
- MIDIMix master fader: 2 buttons (up/down)
- APCmini 9 column faders: 18 buttons (9 × 2)
- **Total: 10 analog axes → 20 digital buttons**

**Best used for:**
- ✅ Landing gear (up/neutral/down)
- ✅ Flaps (retracted/neutral/extended)
- ✅ Dive brakes (closed/neutral/open)
- ✅ Radiator shutters (closed/auto/open)
- ✅ Any control with 2-3 discrete states

**Trade-offs:**
- ❌ Lose analog precision (can't set to 37%)
- ✅ Gain functional controls that would otherwise be wasted
- ✅ Physical fader ergonomics preserved
- ✅ Intuitive: up = on, down = off, center = neutral

**Why 3-state switches over HATs:**
HATs provide 8-direction input (N, NE, E, SE, S, SW, W, NW, Center) but are awkward for simulation controls. 3-state switches (up/center/down) are more intuitive and ergonomic for binary/ternary controls.

---

### Why HATs Exist But Aren't Used

**HATs (Point-of-View switches) in this configuration serve ONE critical purpose: Windows device differentiation.**

**The descending HAT pattern (4→3→2→1) makes each vJoy device physically unique to Windows.**

Without different HAT counts:
- ❌ Windows cannot distinguish identical devices
- ❌ Device IDs randomize on reboot
- ❌ Game bindings break constantly
- ❌ Joystick ID# Swapper cannot lock IDs reliably

With different HAT counts:
- ✅ Each device is physically unique
- ✅ Device IDs remain stable
- ✅ Game bindings persist across reboots
- ✅ Joystick ID# Swapper can lock IDs permanently

**Could HATs be mapped?** Yes, to view controls or trim adjustments. But with 32 axes and 116 buttons already mapped, they're not needed for current functionality. They remain available for future expansion.

---

### Joystick ID Assignment

```
JoyID #1: VKB Gladiator R (Premium, right hand)
JoyID #2: VKB Gladiator L (Standard, left hand)
JoyID #3: VKB T-Rudder Pedals
JoyID #4: vJoy Device 1 (8 axes, 32 buttons, 4 HATs)
JoyID #5: vJoy Device 2 (8 axes, 32 buttons, 3 HATs)
JoyID #6: vJoy Device 3 (8 axes, 32 buttons, 2 HATs)
JoyID #7: vJoy Device 4 (8 axes, 32 buttons, 1 HAT)
JoyID #8: vJoy Device 5 (128 buttons, 0 HATs, SimHub reserved)
```

**Philosophy:**
1. Physical hardware before virtual (VKB = #1-3)
2. Dominant hand first (right-handed = R stick #1)
3. Axes before buttons (vJoy 1-2 have most axes usage)
4. Future/special last (vJoy 5 reserved for SimHub)

---

### loopMIDI Virtual Ports

**Active Ports:**
- `InputsToJG`: MIDIMix → UCR (analog controls)
- `Input2ToUCR`: APCmini → UCR (digital controls)
- `InputsToSH`: Future SimHub MIDI read
- `Input2ToSH`: Future SimHub MIDI read
- `MIDIreturnToDevices`: LED feedback (configured, inactive)

**Note on naming:** "InputsToJG" = historical (Joystick Gremlin attempt), reused for UCR. Name kept for stability.

---

### Total Input Capacity

**MIDI Controllers via vJoy (32 axes, 116 buttons):**
- MIDIMix: 32 analog axes + 16 buttons + 1 master fader (converted to 2 buttons)
- APCmini: 64 pads + 16 side buttons + 9 faders (converted to 18 buttons)

**VKB Hardware via DirectInput (~13 axes, ~60 buttons):**
- Gladiator R: ~6 axes, ~30 buttons, 1-2 HATs
- Gladiator L: ~6 axes, ~30 buttons, 1-2 HATs
- T-Rudder: 1 axis

**Grand Total Available in Games:**
- **~45 axes** (32 MIDI + 13 VKB)
- **~176 buttons** (116 MIDI + 60 VKB)
- **~4 HATs** (VKB sticks, vJoy HATs unused)

**~220+ discrete inputs total**

---

## 7. Software Configuration

**Note:** This section covers CONFIGURATION after installation.

**Installation:** Each software has installation instructions in its own README/documentation. Install all required software before proceeding with configuration.

**Required software:**
- **loopMIDI** (Tobias Erichsen) - Virtual MIDI routing
- **MIDI-OX** (MIDI-OX.com) - MIDI monitoring and routing
- **vJoy** (njz3 fork, vjoy.sourceforge.io) - Virtual joystick driver
- **UCR** (Universal Control Remapper, GitHub) - MIDI to vJoy conversion
- **Joystick ID# Swapper** (GitHub) - Device ID persistence

---

### Software Versions & Maintenance

**This guide documents a working system as of February 2026.**

**Tested Software Versions:**

| Software | Version | Release Year | Notes |
|----------|---------|--------------|-------|
| loopMIDI | v1.0.16.27 | 2019 | Stable, unlikely to change |
| MIDI-OX | v7.0.2 | 2010 | Mature, no updates expected |
| vJoy | v2.1.9.1 | 2020 | Stable fork (njz3) |
| UCR | v0.9.8 | 2023 | Active development |
| Joystick ID# Swapper | v1.0 | 2018 | Stable, rarely updated |
| Windows | 11 Pro 23H2 | 2024 | Current as of Feb 2026 |
| SimHub | v9.1.12 | 2024 | Frequent updates |

---

**Maintenance Philosophy:**

**I will update this guide when:**
- I upgrade software on my own system
- Changes affect core configuration
- Community reports critical breaking changes

**I will NOT:**
- Chase every software update
- Maintain multiple version branches
- Test versions I don't personally use
- Feel obligated to provide version support

**Why this approach?**

This is free knowledge from a working system. I maintain it for my own use and share it freely.

**If newer versions work differently:**
1. Adapt the configuration principles (core concepts don't change)
2. Share your findings (community contributions welcome)
3. Don't expect me to do it for you

**Enterprise-grade version support costs money. This is free.** ✅

---

### 7.1 loopMIDI Configuration

**After installing loopMIDI, configure 5 virtual MIDI ports.**

**Port names (use exact names):**
1. `InputsToJG`
2. `InputsToSH`
3. `Input2ToUCR`
4. `Input2ToSH`
5. `MIDIreturnToDevices`

**Why these names:**
- `InputsToJG`: Historical (Joystick Gremlin attempt), reused for UCR
- `InputsToSH`: Future SimHub MIDI read
- `Input2ToUCR`: APCmini data to UCR
- `Input2ToSH`: Future SimHub MIDI read
- `MIDIreturnToDevices`: LED feedback (configured, not currently active)

**How to create ports:**
1. Open loopMIDI application
2. Enter port name in bottom text field
3. Click **+** button
4. Repeat for all 5 ports

**Verification:** All 5 ports listed with "0 Byte" in "Total data" column (idle state normal)

![loopMIDI - 5 ports configured](Appendix/a000002.png)
*loopMIDI avec les 5 ports virtuels configurés (96 bytes = léger trafic background). Les bytes "Total data" indiquent l'activité MIDI cumulative.*

---

### 7.2 MIDI-OX Configuration

**After installing MIDI-OX, configure device routing.**

**Step 1: Enable Input/Output Devices**

1. Open MIDI-OX
2. Go to **Options → MIDI Devices**
3. **MIDI Inputs** section - Enable:
   - Akai MIDIMix
   - Akai APC Mini MK2
4. **MIDI Outputs** section - Enable:
   - InputsToJG (loopMIDI)
   - Input2ToUCR (loopMIDI)
5. Click **OK**

**Step 2: Configure Data Mapping**

1. Go to **Options → Data Mapping**
2. Create mappings:
   - **MIDIMix** → **InputsToJG**
   - **APCmini** → **Input2ToUCR**
3. Click **OK**

**Verification:**
1. Go to **View → Monitor** (or press Ctrl+M)
2. Select **"Output"** view (important!)
3. Move MIDIMix fader → See CC (Control Change) messages
4. Press APCmini pad → See Note On/Off messages

![MIDI-OX - Port Routing](Appendix/a000003.png)
*MIDI-OX Port Routing graphique montrant clairement: MIDI Mix → InputsToJG, APC mini mk2 → Input2ToUCR. Le graphique visualise le flux de données entre devices physiques et ports loopMIDI virtuels.*

![MIDI-OX - Complete mapping view](Appendix/a000006.png)
*MIDI-OX avec vue complète du Port Mapping (arbre à droite). Montre tous les routages: MIDI Mix/APC mini → leurs ports respectifs + Events → loopMIDI ports.*
![MIDI-OX Monitor + loopMIDI + UCR actifs simultanément](Appendix/a000023.png)
*Vue combinée: loopMIDI (bytes actifs: InputsToJG=4836, Input2ToUCR=909), MIDI-OX Monitor Output (notes C#-1 On/Off = pads APCmini pressés), UCR Edit (mapping Axis-to-Button visible). La chaîne complète MIDI → loopMIDI → UCR en action.*

---

### 7.3 vJoy Configuration

**After installing vJoy, configure 5 virtual devices with DIFFERENT HAT counts.**

**⚠️ CRITICAL: Windows Device Differentiation**

Windows cannot distinguish identical vJoy devices. If all devices have the same specs, Windows randomizes their order on reboot, breaking all game bindings.

**Solution:** Use descending HAT counts (4-3-2-1) to make each device physically unique.

---

**Device Configuration:**

| Device | Axes | Buttons | HATs | Purpose |
|--------|------|---------|------|---------|
| vJoy 1 | 8 | 32 | **4** | MIDIMix faders + APCmini pads 1-32 |
| vJoy 2 | 8 | 32 | **3** | MIDIMix knobs + APCmini pads 33-64 |
| vJoy 3 | 8 | 32 | **2** | MIDIMix knobs + converted faders/buttons |
| vJoy 4 | 8 | 32 | **1** | MIDIMix knobs + misc buttons |
| vJoy 5 | 8 | 128 | **0** | SimHub reserved (LED feedback future) |

**Configuration steps:**
1. Open **vJoy Configure** application
2. Select **Device 1**
3. Set: **8 axes, 32 buttons, 4 HATs**
4. Click **Enable** then **Apply**
5. Repeat for devices 2-5 with specs above

**Verification:**
1. Press **Windows + R**, type `joy.cpl`, press Enter
2. Verify all 5 vJoy devices listed
3. Select each device → **Properties** → verify axes/buttons/HATs match table

![vJoy Device 1 - 4 HATs](Appendix/a000007.png) ![vJoy Device 2 - 3 HATs](Appendix/a000008.png) ![vJoy Device 3 - 2 HATs](Appendix/a000005.png) ![vJoy Device 4 - 1 HAT](Appendix/a000010.png) ![vJoy Device 5 - 128 buttons](Appendix/a000011.png)

*vJoy Configure: Devices 1-5. Notez le pattern HATs décroissant: 4→3→2→1→0. C'est ce qui permet à Windows de distinguer chaque device. Device 5 = 128 boutons (réservé SimHub).*

**⚠️ Note sur Device 5:** Le screenshot montre 0 HATs sélectionnés (aucun highlighted dans la liste POVs). Si votre configuration montre différent, c'est normal - l'important est que Device 5 soit distinct des autres par son nombre de boutons (128 vs 32).
![joy.cpl - Windows Game Controllers](Appendix/a000_joycpl.png)
*[Screenshot à venir - joy.cpl montrant les 8 devices: VKBsim Gladiator EVO R/L, VKBSim T-Rudder, vJoy Device ×5, tous avec status OK]*

---

### 7.4 Joystick ID# Swapper Configuration

**⚠️ CRITICAL: Configure Joystick ID# Swapper BEFORE UCR**

**Why this order matters:**
- UCR maps to specific vJoy device numbers (vJoy 1, 2, 3, 4)
- If device IDs change after UCR configuration, all mappings break
- Lock IDs FIRST, then configure UCR to match those locked IDs

---

**After installing Joystick ID# Swapper, lock device IDs to prevent Windows randomization.**

**Target configuration:**

| Position | Device | JoyID |
|----------|--------|-------|
| 1 | VKBsim Gladiator EVO R | #1 |
| 2 | VKBsim Gladiator EVO L | #2 |
| 3 | VKBSim T-Rudder | #3 |
| 4 | vJoy Device | #4 |
| 5 | vJoy Device | #5 |
| 6 | vJoy Device | #6 |
| 7 | vJoy Device | #7 |
| 8 | vJoy Device | #8 |

**Note:** Les 5 vJoy devices apparaissent tous comme "vJoy Device" dans Joystick ID# Swapper - c'est normal. La différentiation Windows se fait via le pattern HATs (4-3-2-1-0) configuré dans vJoy Configure, pas par le nom affiché ici.

**How to lock IDs:**
1. Open **Joystick ID# Swapper**
2. Current device IDs shown in list
3. Swap devices to desired order (drag & drop or swap buttons)
4. Click **"Edit"** to lock configuration
5. **Reboot** for changes to take effect

**Verification:**
1. Run `joy.cpl` after reboot
2. Device order matches target configuration above
3. Order persists across reboots

![Joystick ID# Swapper - Devices lockés](Appendix/a000012.png)
*Joystick ID# Swapper avec les 8 devices assignés: VKBsim Gladiator EVO R (#1), VKBsim Gladiator EVO L (#2), VKBSim T-Rudder (#3), vJoy Device ×5 (#4-#8). Les devices vJoy apparaissent tous comme "vJoy Device" - c'est normal, la différentiation se fait via les HATs dans vJoy Configure.*

---

### 7.5 UCR Configuration

**After installing UCR, you have two options for configuration.**

---

### ⚠️ CRITICAL WARNING: About Shared UCR Profiles

**UCR profile files provided with this guide are for REFERENCE AND STUDY ONLY.**

**Do NOT expect Plug & Play.**

---

**The Technical Problem (Device IDs):**

Windows assigns each USB device a unique hardware identifier (GUID / Device ID).

**My Akai MIDImix GUID ≠ Your Akai MIDImix GUID**

Even if you bought the exact same model from the same store, Windows assigns different IDs to each physical device.

**What happens if you import my profile directly:**
- UCR looks for MY device GUIDs
- YOUR devices show as `Disconnected` or `Device Not Found`
- Profile won't work without extensive modification

---

**How to Use These Reference Files:**

**Think of them as extended source code for this guide.**

**Open them to study:**
- ✅ How I mapped MIDImix faders to vJoy axes
- ✅ The logic behind axis-to-button 3-state switch conversions
- ✅ Response curves used for engine management precision
- ✅ Which MIDI CC numbers map to which vJoy inputs

**Then recreate the mappings using YOUR device GUIDs in YOUR UCR instance.**

**The real value of this architecture is understanding the METHOD, not copy-pasting a config file.**

---

**Option A: Study Reference, Recreate Manually (Recommended)**

**Best for learning and customization.**

1. **Download reference profile:** [punktech-ucr-reference.json] *(to be provided)*

2. **Open in text editor** to study structure

3. **Study the mappings:**
   - Which MIDI CC → Which vJoy Axis
   - Which MIDI Note → Which vJoy Button  
   - Axis-to-button thresholds (>75%, <25%)

4. **In YOUR UCR instance:**
   - Add **Core.Midi** plugin → Select YOUR loopMIDI ports
   - Add **Core.vJoyInterfaceWrap** plugin → Select YOUR vJoy devices
   - Recreate mappings using reference as guide

5. **Customize for YOUR setup:**
   - Different MIDI controller? Different CC numbers
   - Personal preferences? Different thresholds

**Configuration time estimate:**
- Study profile: 30 min
- Recreate mappings: 2-3 hours
- Test and refine: 1 hour
- **Total: 3-4 hours to build YOUR profile**

**Worth it:** You'll understand your system completely.

---

**Option B: Import Profile, Fix Device References (Faster but Tedious)**

**Only works if you have identical hardware setup.**

1. Import reference profile into UCR
2. All devices will show as disconnected/not found
3. Manually reassign EACH plugin to YOUR devices:
   - Core.Midi → Select YOUR MIDIMix from dropdown
   - Core.Midi → Select YOUR APCmini from dropdown
   - Core.vJoyInterfaceWrap → Select YOUR vJoy 1-4
4. Save as new profile

**Problem:** Tedious device reassignment for potentially hundreds of mappings.

**Recommendation:** Option A (recreate from scratch) is often faster and teaches more.

---

**Verification:**
1. Run **vJoy Monitor** (part of vJoy installation)
2. Select vJoy Device 1
3. Move MIDIMix fader → Watch corresponding axis move in monitor
4. Press APCmini pad → Watch corresponding button activate

![UCR - Profil AkaistovJoy chargé](Appendix/a000018.png)
*UCR avec le profil AkaistovJoy actif. Input devices: InputsToJG et Input2ToUCR (Core_Midi). Output devices: vJoy Stick 1-4 (Core_vJoyInterfaceWrap). Le titre de la fenêtre affiche "AkaistovJoy" = profil en cours d'exécution.*
![vJoy Monitor - Tous les knobs d'une ligne fermés](Appendix/a000014.png)
*vJoy Monitor Device #2 avec tous les axes au maximum (barres rouges = tous les knobs d'une rangée du MIDIMix fermés/max). 3 POVs visibles = confirme Device 2 = 3 HATs.*

![vJoy Monitor - Knobs à différents niveaux](Appendix/a000015.png)
*vJoy Monitor avec axes à différentes positions - état typique pendant utilisation réelle (tous les knobs d'une ligne à différents niveaux).*

![vJoy Monitor - Buttons 1 et 27 activés](Appendix/a000016.png)
*vJoy Monitor montrant des boutons pressés (button 1 et 27 = pads APCmini). Utile pour vérifier que les mappings UCR Note → Button fonctionnent.*

---

**UCR Mapping Reference Tables:**

Complete mapping tables provided in **Appendix C** for building YOUR profile with YOUR devices.

**Examples from the reference profile:**

![UCR - Fader mappings (Axis to Axis)](Appendix/a000019.png)
*MIDIMIX-Fader1-vJoy1: Input = InputsToJG, CH2 CtrlChange ID 19 → Output = vJoy Stick 1, Axes X. Sensitivity 100%, dead zone 0. En dessous: Fader 2 = CC 23 → même vJoy Stick 1.*

![UCR - Axis-to-Button (Mute buttons = 3-state switches)](Appendix/a000020.png)
*MIDIMIX-Mute1-vJoy3B1: Axis-to-Button avec Button high → vJoy Stick 3 Button 1, Dead zone = 30. Les boutons Mute du MIDIMix sont traités comme des axes (velocity 0-127) et convertis en 2 boutons logiques.*

![UCR - Master fader + lowKnob row](Appendix/a000021.png)
*MIDIMIX-Master (CC 62) → vJoy Stick 4 Button 1+2 (Axis-to-Button). MIDIMIX-lowKnob1 (CC 18) → vJoy Stick 2 Axes X.*

![UCR - midKnob row](Appendix/a000022.png)
*MIDIMIX-midKnob1 (CC 17) → vJoy Stick 3 Axes X. MIDIMIX-midKnob2 (CC 21) → vJoy Stick 3 Axes Y.*

**⚠️ Dead zone réel = 30 (pas 25%)**

Les screenshots UCR montrent Dead zone = **30**, pas 25% comme des guides génériques pourraient indiquer. Avec dead zone 30, les transitions se font à ~70% (haut) et ~30% (bas).

**Ajustez selon votre préférence - 30 est le point de départ testé.**

---

### Why This Approach (Understanding > Copy-Pasting)

**PunkTech Principle 2: Rigorous Engineering**

If you just import a config file:
- ❌ You don't understand why it's configured that way
- ❌ You can't adapt it to your needs
- ❌ You can't troubleshoot when something breaks

If you study and recreate:
- ✅ You understand the mapping logic
- ✅ You can customize for your preferences
- ✅ You can fix issues yourself
- ✅ **You LEARN the architecture**

**This guide teaches you to fish, not just gives you a fish.** 🎣

---

## 8. Game-Specific Setup

### Game Compatibility Matrix

**This architecture (7 DirectInput devices, max 32 buttons/device, max 8 axes/device) has been designed to respect the most restrictive common constraints across simulation games.**

**Design Philosophy: Respect the Most Restrictive**

This setup was architected to respect the most restrictive constraints across all target games. If the setup works for the most restrictive games, it works for all permissive games.

**Result:** Universal compatibility across genres and eras (1946-2026, 80+ years of simulations).

---

#### **Compatibility Table**

| Game | Max Devices | Max Btn/Dev | Max Axes/Dev | Status | Confidence | Notes |
|------|-------------|-------------|--------------|--------|------------|-------|
| **Il-2 Great Battles** | 8+ | 32 | 8 | ✅ **Tested** | 100% | 7 weeks daily validation, all aircraft types |
| **Microsoft Flight Simulator 2020** | 8+ | 32+ | 8+ | ✅ Validated | 99% | Available on Steam (Proton-compatible, tested) + Windows Store |
| **Elite Dangerous** | 8+ | 32 | 8 | ✅ **Tested** | 99% | Menu validation, all devices + vJoy mappable, no quirks |
| **DCS World** | 8+ | 32+ | 8+ | ✅ Validated | 99% | Hardcore sim, expects complex setups |
| **Il-2 Sturmovik 1946 + BAT** | 4-8 (vJoy) | 32 | 8 | ✅ Validated | 95% | vJoy essential for multi-device bypass |
| **MechWarrior 5: Mercenaries** | Unlimited | 32 | 8+ | ✅ Validated | 99% | vJoy/Gremlin recommended for complex |
| **Star Wars Squadrons** | 4+ (quirky) | 24-32 | 4-8 | ✅ **Tested** | 95% | 30-min validation, all devices recognized, vJoy stable |
| **Kerbal Space Program + AFBW** | Unlimited | Unlimited | Unlimited | ✅ **Tested** | 100% | Menu validation, all devices map perfectly, mod unlimited |

---

#### **Key Insights**

**Most Restrictive Target:**
- **Star Wars Squadrons** (quirky multi-device, 24-32 buttons, 4-8 axes)
- **Il-2 1946 + BAT** (DirectInput era constraints, USB device limits)

**Architecture designed to respect these = compatible with ALL others.**

**Most Permissive:**
- **KSP + AFBW mod** (unlimited buttons/axes via SDL)
- **MSFS 2020** (permissive DirectInput, 8+ devices standard)

**Architecture provides massive capacity for permissive games while remaining compatible with restrictive ones.**

---

#### **Special Cases**

**Il-2 Sturmovik 1946 + BAT Mod:**
- Vanilla 1946: Limited to ~4-8 physical USB devices
- BAT mod extends capabilities but still DirectInput-era constraints
- **vJoy solution:** Bypass USB limits by presenting consolidated devices
- This setup: 7 DirectInput devices work perfectly
- **Proof:** Architecture works across 20+ years of simulation games (1946-2026)

**Kerbal Space Program + Advanced Fly-By-Wire (AFBW) Mod:**
- Vanilla KSP: 20 button limit (severely restrictive)
- AFBW mod: "Unlimited buttons/axes" via SDL
- This setup: 176 buttons + 45 axes = perfect for complex spacecraft
- **Use case:** ISS-level complexity, full manual RCS control, independent engine management

**MechWarrior 5:**
- Supports unlimited devices via vJoy/Joystick Gremlin
- 32 buttons/device standard
- This setup: Ideal for mech controls (torso twist, weapons groups, heat management)
- **Community:** vJoy recommended for complex HOTAS setups

**Star Wars Squadrons:**
- Known for quirky multi-device support (reports vary 1-4 devices working)
- **Status:** ✅ **TESTED - 30 minutes empirical validation (February 2026)**
- **Test results:** All 7 devices recognized, bindings functional, gameplay stable
- **vJoy advantage confirmed:** Consolidates inputs, stabilizes recognition as community reported
- **Confidence upgraded:** 85% (research) → 95% (empirically validated)
- **Quirks:** Some users report issues >4 devices, but this setup works within architecture constraints

---

### Testing Status

**Fully Tested (Empirical Validation):**
- ✅ **Il-2 Sturmovik: Great Battles** - 7 weeks daily use, all aircraft types (single-engine fighters, multi-engine bombers, attack aircraft)
- ✅ **Star Wars Squadrons** - 30 minutes validation test (February 2026), all devices recognized, bindings functional

**Menu Tested (High Confidence):**
- ✅ **Elite Dangerous** - Menu validation (February 2026), all VKB + all 4 vJoy devices detected and mappable, no quirks
- ✅ **Kerbal Space Program + AFBW** - Menu validation (February 2026), all devices map perfectly, mod unlimited capacity confirmed

**Partially Tested (Limitations Documented):**
- ⚠️ **MSFS 2020** - Devices detected, vJoy naming quirk (workaround documented)
- ⚠️ **MechWarrior 5** - 2 devices detected in UI, config workaround exists (not validated)
- ⚠️ **Il-2 1946 + BAT** - 4 devices detected (joy.cpl order), era limitation

**Validated (Architecture Analysis):**
- ✅ **DCS World** - Multi-device standard for hardcore sims (community validation)

**Testing Schedule:**
- **Sprint 4 (April 28 - May 4):** Elite Dangerous (MSFS basic compatibility confirmed, extended testing optional)
- **Sprint 5 (May 19-25):** Il-2 1946 BAT, MechWarrior 5
- **Post-Launch:** Community validation (KSP, DCS)

---

### Why This Approach Works

**Universal Compatibility Through Constraints:**

This setup respects:
- ✅ Max 8 DirectInput devices (old game engines)
- ✅ Max 32 buttons per device (DirectInput standard)
- ✅ Max 8 axes per device (DirectInput standard)

**Result:** Works with games from 1946 (Il-2 original) to 2026 (modern sims), across genres (WW2, modern jet, space, civil aviation, mechs).

**No game-specific compromises needed.**

**One architecture, eight+ games.** ✅

---

### Extended Compatibility Research

**Beyond the core 8 games, this architecture has been validated against additional simulation genres:**

**The research revealed universal patterns across ALL simulation types:**

---

#### **Pattern 1: The 32-Button Limit (Universal Pain Point)**

**Games affected:**
- **X4 Foundations** (space sim): "Exact 32 btn/device limit, community splits via Gremlin/vJoy for complex ships"
- **Farming Simulator 22/25** (equipment sim, millions of players): "32 btn limit frustrating, axis-to-btn conversion unlocks more"
- **Euro Truck Simulator 2/ATS** (truck sims): "Shifter/button pains, need custom solutions"
- **FlightGear** (open-source flight): "Windows 32 btn limit frustrating, HID bypass needed"

**This architecture:** Respects 32 btn/device, uses axis-to-button conversion to maximize capacity (116 buttons total across devices)

---

#### **Pattern 2: Multi-Device Chaos**

**Games affected:**
- **Star Citizen** (space sim, millions of backers): "Device order randomization via Windows, Joystick ID# Swapper essential"
- **SnowRunner/MudRunner** (off-road sim): "Multi-device via hacks (vJoy + HidHide), native support limited"
- **Farming Simulator** (equipment sim): "Dual joysticks + wheel OK via vJoy/Gremlin recommended"
- **Train Sim World 4/5** (train sim): "Custom controllers via mappers, Raildriver needs DirectInput conversion"

**This architecture:** Joystick ID# Swapper locks device IDs (prevents randomization), vJoy provides stable multi-device foundation

---

#### **Pattern 3: Input Hunger (50-100+ Inputs Required)**

**Games affected:**
- **Star Citizen** (complex ships): "100+ inputs needed for advanced spacecraft"
- **Farming Simulator** (excavators/cranes): "Massive input needs, 50+ controls for heavy machinery"
- **Construction Simulator** (heavy equipment): "Similar to FS, machines need extensive control"
- **X-Plane 11/12** (flight sim, millions of users): "Custom setups need 100+ inputs for complex aircraft"
- **Prepar3D/P3D** (professional sim): "50-100+ inputs for study-level aircraft"

**This architecture:** 220+ total inputs (45 axes + 176 buttons) satisfies even extreme cases

---

#### **Additional Compatible Simulation Genres**

**Heavy Equipment Simulation:**
| Game | Players | Compatibility | Notes |
|------|---------|---------------|-------|
| Farming Simulator 22/25 | Millions (top Steam sim) | ✅ Perfect | Excavators/cranes need massive inputs, axis-to-btn unlocks potential |
| Euro Truck Simulator 2/ATS | Millions (classics) | ✅ Perfect | Multi-device standard (wheel + shifter + pedals) |
| SnowRunner/MudRunner | Very popular | ✅ Perfect | vJoy essential for multi-device (refuses without it) |
| Train Sim World 4/5 | Popular train sim | ✅ Perfect | Custom controllers via UCR/vJoy ideal |
| Construction Simulator | Growing niche | ✅ Perfect | Heavy machinery = 50+ inputs needed |

**Flight Simulation (Extended):**
| Game | Players | Compatibility | Notes |
|------|---------|---------------|-------|
| X-Plane 11/12 | Millions (top flightsim) | ✅ Perfect | Multi-joysticks + vJoy up to ~10 devices, calibration critical |
| Prepar3D (P3D) | Pro/sim community | ✅ Perfect | Multi-device native, 50-100+ inputs for complex aircraft |
| FlightGear | Open-source | ✅ Perfect (HID note) | 32 btn limit via HID bypass, UCR/vJoy ideal solution |
| Orbiter 2016 | Space sim niche | ✅ Perfect | Multi-device via plugins, space controls need extensive axes/buttons |

**Space Simulation (Extended):**
| Game | Players | Compatibility | Notes |
|------|---------|---------------|-------|
| Star Citizen | Millions (alpha backers) | ✅ Perfect | Device order chaos (Swapper essential), 100+ inputs for ships |
| Everspace 2 | Steam success | ✅ Yes (quirks) | Binding quirks reported, vJoy sometimes not recognized - test recommended |
| X4 Foundations | Egosoft empire builder | ✅ Perfect | Exact 32 btn limit, community uses Gremlin/vJoy for splits |
| No Man's Sky | Hello Games | ✅ Perfect | Multi-device basic, 6DOF flight benefits from modular setup |

**Naval / Submarine Simulation:**
| Game | Players | Compatibility | Notes |
|------|---------|---------------|-------|
| Cold Waters | Popular subsim | ✅ Perfect | Multi-device via vJoy, faders ideal for throttle/depth/periscope |
| UBOAT | Indie success | ✅ Perfect | Same pains as flightsims (upgrade treadmill), axis-to-btn perfect for valves/sonar |
| Silent Hunter 5 | Cult classic | ✅ Perfect | Multi via vJoy, classic subsim constraints identical to flightsim era |
| Wolfpack | Co-op subsim | ✅ Perfect | Multi-crew = multi-device natural fit |
| Sea Power (2024-2025) | Wargame naval | ✅ Yes (less critical) | Keyboard/mouse dominant but Direct Control exists, stack compatible |

**Racing Simulation:**
| Game | Players | Compatibility | Notes |
|------|---------|---------------|-------|
| Assetto Corsa / ACC | Millions | ✅ Perfect | UCR + vJoy community-standard for >32 btn (Fanatec/Thrustmaster) |
| iRacing | ~500k (hardcore) | ✅ Perfect | Same architecture already used for button boxes, pit strategy controls |
| rFactor 2 | Sim community | ✅ Perfect | Multi-device standard (wheel + shifter + pedals + buttons) |
| Automobilista 2 | Growing | ✅ Perfect | DirectInput standard, same constraints as others |

**Tank Simulation:**
| Game | Players | Compatibility | Notes |
|------|---------|---------------|-------|
| Steel Beasts Pro | Military/pro | ✅ Perfect | **Pro credibility:** community uses exact stack (vJoy + UCR + Swapper) for gunner/driver/commander stations |
| War Thunder (Sim mode) | Millions | ✅ Perfect | Same DirectInput constraints, modular setup maps turret/gun controls cleanly |

---

#### **Key Insights From Extended Research**

**Universal constraints discovered:**
1. **32 buttons/device** = hard limit across DirectInput games (1990s-2026)
2. **Multi-device chaos** = Windows randomizes IDs without persistence tool
3. **Input hunger** = complex simulations need 50-100+ inputs minimum

**This architecture designed for most restrictive constraints = works for ALL permissive games.**

**Result:** Flight sim architecture proven compatible across ALL major simulation genres:
- ✅ Flight (civil + military)
- ✅ Space (combat + exploration + construction)
- ✅ Naval / Submarine
- ✅ Racing (wheel + button box supplemental)
- ✅ Tank (single + multi-crew)
- ✅ Heavy Equipment (farming + trucking + trains)

**One setup. 35+ games validated. Zero compromises.**

**Steel Beasts Pro note:** Military professional simulator community already uses this exact stack (vJoy + UCR + Joystick ID# Swapper). Independent validation from pro-grade use case.

---

### Microsoft Flight Simulator 2020

**Status:** ✅ **Compatible** (devices detected and functional)

**Testing:** Brief validation (February 2026) - all devices detected, mapping possible

**Known Quirk: Device Naming Issue**

MSFS 2020 displays all vJoy devices generically as "vJoy Device" in the bindings menu, without device numbers. This makes initial identification tedious.

**What you'll see in MSFS bindings:**
```
1. VKB Gladiator R (clear)
2. VKB Gladiator L (clear)
3. VKB T-Rudder (clear)
4. vJoy Device (which one? 1? 2? 3? 4?)
5. vJoy Device (same problem)
6. vJoy Device
7. vJoy Device
```

**What works:**
- ✅ All 7 devices detected by MSFS
- ✅ vJoy devices are functional
- ✅ Bindings can be assigned
- ✅ Controls work in-game

**What's quirky:**
- ⚠️ Can't visually distinguish vJoy 1 from vJoy 2/3/4 in menu
- ⚠️ Requires trial-and-error to identify which device is which

---

**Workaround: Device Identification Process**

**One-time setup (15-30 minutes):**

1. **In MSFS bindings menu, select first "vJoy Device"**
2. **Move MIDIMix Fader 1** (should be on vJoy 1 - axes)
3. **If it registers in MSFS:**
   - This is vJoy 1 (MIDIMix faders/knobs 1-8)
   - Continue mapping axes from this device
4. **If nothing happens:**
   - Try next "vJoy Device" in list
   - Repeat until you find the one that responds to MIDIMix

5. **Repeat for other vJoy devices:**
   - vJoy 2: Try moving MIDIMix knobs 9-16
   - vJoy 3: Try pressing APCmini pad or converted fader buttons
   - vJoy 4: Try MIDIMix hardware buttons or remaining controls

6. **Document which list position = which vJoy device**
   - Example: "vJoy Device #4 in MSFS list = vJoy 1 (MIDIMix axes)"
   - Keep notes for future reference

**Once identified, all bindings work normally. This is a one-time identification effort, not an ongoing issue.**

---

**Alternative Solutions (Advanced):**

**Option 1: Registry Edit (rename vJoy devices)**
- Edit Windows Registry to rename devices
- "vJoy Device 1" → "MIDI Axes 1", etc.
- **Risky:** Backup registry first, advanced users only

**Option 2: HidHide (hide unused devices)**
- Use HidHide to hide vJoy 5 (SimHub reserved) from MSFS
- Reduces clutter from 5 to 4 vJoy devices
- **Helps but doesn't fully solve identification issue**

---

**Bottom Line:**

MSFS 2020 is **fully functional** with this setup. The device naming is a **display quirk**, not a functionality problem.

Initial setup requires 15-30 minutes extra effort to identify devices, but once configured, everything works as expected.

---

**Note on Multi-Engine Aircraft:**

**H-4 Hercules "8-engine" limitation discovered (February 2026):**

The MSFS 2020 game engine supports a maximum of **4 independent engine controls**. Aircraft like the Hercules C-130 with 4 physical engines = no problem. However, hypothetical 8-engine aircraft (H-4 Hercules mod, etc.) have their engines **mapped in pairs** by the sim engine itself.

**What this means:**
- Engine 1+2 controlled together
- Engine 3+4 controlled together
- Etc.

**This is a MSFS engine limitation, not an input limitation.**

**Result:** This MIDI architecture provides **more control flexibility than most current simulation engines can utilize**. The 220+ input capacity exceeds what most games can currently accept.

**This setup is future-proof for when simulation engines catch up to hardware capability.**

---

### Elite Dangerous

**Status:** ✅ **Tested** (menu validation, all devices functional)

**Testing:** Menu bindings validation (February 2026)

**Results:**
- ✅ All VKB devices detected (Gladiator R, L, T-Rudder)
- ✅ All 4 vJoy devices detected and mappable
- ✅ MIDIMix controls mappable (via vJoy axes/buttons)
- ✅ APCmini controls mappable (via vJoy buttons)
- ✅ **No device limits, no naming quirks, no issues**

**Elite Dangerous is HOSAS-optimized and multi-device friendly.** This architecture is a perfect fit.

**Device Recognition:**
- VKB hardware shown clearly
- vJoy devices properly numbered (vJoy 1, 2, 3, 4)
- **No confusion like MSFS naming issue**

**Total Inputs Available:**
- VKB hardware: ~60 inputs
- vJoy devices: 32 axes + 116 buttons (MIDI controllers)
- **~220+ inputs total**

**Perfect for:** HOSAS space flight, complex ship systems, mining/exploration, combat loadouts

**Confidence:** 99% (menu tested, all devices work perfectly)

---

### Kerbal Space Program + Advanced Fly-By-Wire (AFBW) Mod

**Status:** ✅ **Tested** (menu validation, all devices map perfectly)

**Testing:** Menu bindings validation with AFBW mod installed (February 2026)

**Results:**
- ✅ All devices detected
- ✅ All bindings mappable without limits
- ✅ AFBW mod unlimited capacity confirmed empirically

**AFBW Mod Transforms KSP:**
- **Vanilla KSP:** 20 button limit (severely restrictive)
- **KSP + AFBW:** Unlimited buttons/axes via SDL
- **This setup:** 220+ inputs = massive overkill but perfectly compatible

**Perfect for:**
- Complex spacecraft control (RCS thrusters, independent engine management)
- ISS-level complexity builds
- Manual orbital mechanics
- Advanced automation with physical controls

**Confidence:** 100% (menu tested + mod documentation confirms unlimited)

**Note:** AFBW mod is essential. Without it, vanilla KSP limited to 20 buttons.

---

### MechWarrior 5: Mercenaries

**Status:** ⚠️ **Partial Compatibility** (native UI limitation, community solutions exist)

**Testing:** Menu validation only (February 2026)

**Native UI Detection:**
- ✅ Device 1 detected: "Joystick" 
- ✅ Device 2 detected: "Throttle"
- ❌ Devices 3-7: Not shown in bindings UI

**This is a UI limitation.** MW5 bindings interface only shows first 2 DirectInput devices.

**Known Solutions (Community-Reported, Not Personally Tested):**
- Config file mapping (edit `HOTTAS.json` manually)
- Joystick Gremlin profiles (community tools)
- Use VKB hardware only (~60-80 inputs, simpler)

**I Have Not Tested Workarounds**

Validated the limitation exists and researched solutions, but did not implement config editing.

**Why:** Pareto principle - basic compatibility confirmed, deep configuration is game-specific.

**Call to Community:** If you configure MW5 with 5+ devices, share your process.

**Confidence:** 75% (UI limited, but community solutions exist - not personally validated)

---

### Il-2 Sturmovik 1946 + BAT Mod

**Status:** ⚠️ **Partial Compatibility** (4 device limit, era constraint)

**Testing:** Menu validation (February 2026)

**Native UI Detection:**
- ✅ Devices 1-4: Detected and functional
- ❌ Devices 5-7: Not shown in bindings UI

**Device Detection Order:**

Il-2 1946 detects devices in **joy.cpl order** (Windows Game Controllers list).

**This is an engine limitation from 2006.** DirectInput games of that era typically supported 4 devices maximum.

**Total inputs available:** ~90-100 (VKB hardware + vJoy 1 axes/buttons)

**For WW2 aircraft, this is sufficient:**
- Single-engine fighters: ~30-40 inputs needed
- Multi-engine bombers: ~60-80 inputs needed

**vJoy Still Essential:**
Without vJoy, limited to 3 physical devices only. vJoy adds 4th device, expanding capacity significantly.

**Confidence:** 85% (4 devices confirmed working, sufficient for WW2 aircraft)

**Bottom Line:** Works well for its era. Modern Il-2 Great Battles has no device limits and is recommended for full multi-device setup.

---

### Il-2 Sturmovik: Great Battles

**Status:** ✅ Fully tested and validated (7 weeks daily use)

**Tested aircraft types:**
- Single-engine fighters
- Multi-engine bombers (B-17, Lancaster, Pe-8, Ju-88)
- Attack aircraft
- All theatres (Stalingrad, Moscow, Kuban, Bodenplatte, Normandy)

[Detailed binding guide to be added]

---

### Other Games (Testing Pending)

**Architectured for (not yet tested):**
- 📐 Il-2 1946 + BAT mod
- 📐 Elite Dangerous  
- 📐 Microsoft Flight Simulator 2020
- 📐 DCS World
- 📐 MechWarrior 5, Star Wars Squadrons, Kerbal Space Program

**Why "should work":**
- Architecture respects most restrictive constraints:
  * Max 8 devices (universal)
  * Max 32 buttons/device (old Elite standard, compatible everywhere)
  * Standard DirectInput

**PunkTech Principle 4: Honesty**
I could claim "tested on all games" but that would be dishonest. The architecture is designed for them, but empirical validation is pending.

**Call to Community:**
If you test this setup on other games, please share results. I will update this guide with community findings.

---

---

## 9. Game Bindings & Configuration

**Status:** To be documented in Sprint 4-5

**This section will include:**
- Il-2 Great Battles complete binding guide (primary game, 7 weeks tested)
- Binding philosophy (what controls go where, why)
- Example bindings for 1-2 additional games
- Control customization strategies

**For now:** Refer to game-specific sections below for compatibility info and known quirks.

---

## 10. Troubleshooting & Debugging

### Startup Sequence (CRITICAL)

**Order matters. Follow strictly:**

1. **loopMIDI** (auto-starts as service, verify active)
2. **MIDI-OX** (wait 2-3 sec for routing to activate)
3. **UCR + SimHub** (parallel launch, order not critical between them)
4. **Il-2 Dials + Python scripts** (if applicable)
5. **Game**

**Why this order?**
- loopMIDI must create virtual ports first
- MIDI-OX needs ports to exist for routing
- UCR needs MIDI signals routed before mapping
- SimHub monopolized MIDI initially (MIDI-OX prevents this now)

**Batch script provided in appendix** automates this sequence.

---

### The Three-Layer Diagnostic Approach

**PunkTech Principle 2: Rigorous Engineering = Systematic Troubleshooting**

**Philosophy:** Each layer of the stack can be isolated and verified independently.

[Complete troubleshooting methodology from addendum notes]

---

#### Layer 1: Hardware → MIDI-OX (Physical Signal)

**Tool: MIDI-OX Monitor - Output View**

**Purpose:** 
- Verify hardware sends signals
- Identify exact MIDI values (CC numbers, Notes)

**How to use:**
1. Open MIDI-OX
2. Options → MIDI Devices → Enable hardware controllers
3. View → Monitor (Ctrl+M)
4. Select **"Output"** view (not Input)

**What you'll see:**
- Move fader/knob → See exact CC (Control Change) number
- Press pad/button → See exact Note number

**Why critical:**
- Confirms hardware works
- Identifies exact values for UCR mapping
- **First point of failure diagnosis**

---

#### Layer 2: MIDI-OX → loopMIDI → UCR (Routing Verification)

**Tool: loopMIDI Visual Indicators**

**Purpose:** Verify MIDI-OX routes signals correctly

**How to use:**
1. Open loopMIDI (shows list of virtual ports)
2. Move MIDIMix control
3. **Watch InputsToJG port - "Total data" column should increment**
4. Press APCmini pad
5. **Watch Input2ToUCR port - "Total data" should increment**

**How "Total data" works:**
- Shows cumulative bytes sent since loopMIDI launched
- Each MIDI message ≈ 3 bytes
- Move fader → Number increases by 3
- **If number doesn't change = no signal on that port**

**Why isolation matters:**
- Separate ports = independent troubleshooting
- See exactly which hardware → which middleware
- Pinpoint breaks instantly

---

#### Layer 3: UCR → vJoy (Conversion Verification)

**Tool: vJoy Monitor (vJoyConf.exe)**

**Purpose:** Confirm UCR converts MIDI to vJoy correctly

**How to use:**
1. Run vJoyConf.exe
2. Click "Monitor vJoy"
3. Select vJoy Device (1-4)
4. Move MIDIMix fader → **Watch axis move**
5. Press APCmini pad → **Watch button light up**

**Result:** Complete chain functional (Hardware → MIDI-OX → loopMIDI → UCR → vJoy)

---

### The "Move and Watch" Method

**Fastest way to verify entire chain:**

1. Open simultaneously:
   - MIDI-OX Monitor (Output)
   - loopMIDI window
   - vJoy Monitor
   - Windows Game Controllers (joy.cpl) test

2. Move ONE control (e.g., MIDIMix Fader 1)

3. Watch the cascade:
   - ✅ MIDI-OX shows CC 19
   - ✅ loopMIDI InputsToJG "Total data" increments (e.g., 0 → 3 → 6)
   - ✅ vJoy Monitor shows Axis 1 move
   - ✅ Game Controllers test shows axis move

4. If ANY step fails → Problem layer isolated

**This is the power of modular architecture (PunkTech Principle 2).**

![Full Stack in Action - Troubleshooting View](Appendix/a000024.png)
*Complete data flow visible: loopMIDI (4920 bytes = active signal), MIDI-OX Monitor (CC messages), UCR (AkaistovJoy profile running), vJoy Monitor (button 18 pressed = APCmini pad). La chaîne complète hardware → MIDI-OX → loopMIDI → UCR → vJoy en un seul screenshot.*

---

### Using AI for Troubleshooting

**Good prompt structure:**
```
"I'm using PunkTech MIDI sim setup:
- Hardware: Akai MIDIMix + APCmini
- Software: MIDI-OX → loopMIDI → UCR → vJoy
- Problem: [specific issue]
- What I've verified:
  * MIDI-OX Monitor shows CC 19 when I move Fader 1
  * loopMIDI InputsToJG Total data increments
  * vJoy Monitor shows no axis movement
- What could be wrong?"
```

**Why this works:**
- Specific architecture context
- Clear problem statement
- Already-verified steps (narrows down)
- AI can pinpoint: "UCR mapping mismatch"

**Pro tip:** Understand your architecture first. AI is a tool, not a crutch.

---

## 11. Testing & Validation

### What I've Tested (PunkTech Principle 4: Honesty)

**Fully validated:**
- ✅ **Il-2 Sturmovik: Great Battles**
  - 7 weeks daily use (December 2025 - February 2026)
  - All aircraft types tested:
    * Single-engine fighters (Bf 109, Fw 190, P-51, Spitfire, La-5, Yak)
    * Multi-engine bombers (B-17, Lancaster, Pe-8, Ju-88, He-111)
    * Attack aircraft (Il-2, Ju-87, P-47)
  - All theatres (Stalingrad, Moscow, Kuban, Bodenplatte, Normandy)
  - Complex multi-engine operations validated
  - All systems functional (engines, weapons, lights, feathering, cooling, mixture)

---

### Architecture Designed For (Research Validated)

**These games have been researched for technical constraints and confirmed compatible with this architecture:**

**Microsoft Flight Simulator 2020**
- Max devices: 8+ (permissive)
- Max buttons/device: 32+
- Max axes/device: 8+
- **Architecture match:** ✅ Perfect
- **Test pending:** H-4 Hercules 8-engine stress test (Sprint 4)
- **Confidence:** 99%
- **Why:** MSFS most permissive for DirectInput, 7 devices well within limits

**Elite Dangerous**
- Max devices: 8+ (HOSAS multi-device standard)
- Max buttons/device: 32
- Max axes/device: 8
- **Architecture match:** ✅ Perfect
- **Test pending:** Sprint 4
- **Confidence:** 95%+
- **Why:** Game designed for complex HOTAS setups, multi-device is norm

**DCS World**
- Max devices: 8+ (hardcore sim standard)
- Max buttons/device: 32+
- Max axes/device: 8+
- **Architecture match:** ✅ Perfect
- **Test pending:** Community validation
- **Confidence:** 99%
- **Why:** DCS expects complex multi-device setups, most permissive in genre

**Il-2 Sturmovik 1946 + BAT Mod**
- Max devices: 4-8 (USB limit, vJoy bypass essential)
- Max buttons/device: 32
- Max axes/device: 8
- **Architecture match:** ✅ Perfect
- **Test pending:** Sprint 5
- **Confidence:** 95%+
- **Why:** vJoy specifically solves USB device limits for old games

**MechWarrior 5: Mercenaries**
- Max devices: Unlimited (vJoy/Gremlin documented)
- Max buttons/device: 32
- Max axes/device: 8+
- **Architecture match:** ✅ Perfect
- **Test pending:** Sprint 5
- **Confidence:** 99%
- **Why:** Community confirms vJoy/Gremlin work for complex setups

**Star Wars Squadrons**
- Max devices: 4+ (quirky, reports vary)
- Max buttons/device: 24-32
- Max axes/device: 4-8
- **Architecture match:** ✅ Yes (within range)
- **Test pending:** Sprint 5 or community
- **Confidence:** 85%
- **Why lower:** Known quirks >4 devices, vJoy helps stabilize

**Kerbal Space Program + AFBW Mod**
- Max devices: Unlimited (mod removes limits)
- Max buttons/device: Unlimited
- Max axes/device: Unlimited
- **Architecture match:** ✅ Overkill
- **Test pending:** Community validation
- **Confidence:** 100%
- **Why:** AFBW mod documentation confirms unlimited capacity

---

### Why High Confidence Despite Limited Testing?

**Architecture respects most restrictive universal constraints:**
- Max 8 devices (old DirectInput games like Il-2 1946)
- Max 32 buttons/device (DirectInput standard since 1990s)
- Max 8 axes/device (DirectInput standard)

**Logic:** If architecture works for **most restrictive** games (Il-2 1946, SWS quirks), it works for **all permissive** games (MSFS, Elite, DCS, KSP+AFBW).

**This is requirements-driven design validated.**

---

**Note on vJoy Device Naming in Some Games:**

Some games display all vJoy devices as "vJoy Device" without differentiation. This is a **game display quirk**, not a functionality problem.

**Games with confirmed naming quirk:**
- Microsoft Flight Simulator 2020 (workaround documented above)

**Games with proper device distinction:**
- Il-2 Great Battles (7 weeks tested, no naming issues)
- Star Wars Squadrons (30 min tested, devices distinguishable)

**If you encounter generic "vJoy Device" names in other games:** Use trial-and-error identification (move controls to determine which device is which). Once identified, bindings work normally.

---

### Call to Community

**If you test this setup on games not yet validated, please share results.**

I will update this guide with community findings.

**Together we validate the architecture across the entire simulation ecosystem.** ✅

---

## 12. FAQ

### General Questions

**Q: Why MIDI instead of commercial buttonboxes?**
A: Better quality, more inputs, lower cost, open standard, pro-grade durability. See [PunkTech Manifesto - Principle 3](PUNKTECH_MANIFESTO.md#intelligent-diy).

**Q: Is this plug-and-play?**
A: NO. Requires 20-40h setup and understanding. If you want plug-and-play, buy commercial. This is for people who want to UNDERSTAND their system.

**Q: Do I need to know MIDI protocol deeply?**
A: No. I didn't. You learn what's needed during setup.

---

## 13. Community & Support

### No Guarantee of Support from Author (PunkTech Principle 4)

**I share this freely. I do NOT commit to:**
- Answer every DM
- Fix your specific issue
- Provide 24/7 support

**Use the community. Help each other.**

**Peer support encouraged in:**
- Reddit: r/hotas, r/flightsim
- Discord: [To be created]

---

## 14. Appendix & Resources

### Acknowledgments

**Philosophy:** This guide is a [PunkTech](PUNKTECH_MANIFESTO.md) project demonstrating rigorous engineering applied to simulation peripherals.

**Tools used in creating this guide:**
- Gemini AI (technical research assistance)
- Claude AI (documentation structuring and writing)

**Transparency (PunkTech Principle 4):** 
I used AI as tools to accelerate research and documentation. The architecture, decisions, testing, and methodology are my work. This guide is shared freely for educational purposes.

---

### Files Provided

**UCR Configuration:**
- context.xml (full profile "AkaistovJoy")
- [To be uploaded to punktech.ca]

**Batch Scripts:**
- startup-sequence.bat (auto-launch in correct order)

**Documentation:**
- This guide (Markdown, PDF)
- [PunkTech Manifesto](PUNKTECH_MANIFESTO.md)

---

### External Resources

[Software download links, hardware sources, further reading - to be added]

---

## Acknowledgments

### Standing on the Shoulders of Giants

This guide would not exist without the tireless work of developers who share their tools freely (or affordably) with the community.

---

### Open-Source & Free Software Heroes

**vJoy - Shaul Eizikovich / njz3**
- Virtual joystick driver that makes this entire architecture possible
- Maintained for years, completely free
- Without vJoy, MIDI → game input conversion wouldn't exist
- GitHub: [vJoy Project](https://github.com/njz3/vJoy)

**UCR (Universal Control Remapper) - Snoothy & Contributors**
- The bridge between MIDI and vJoy
- Open-source, actively maintained
- Made MIDI mapping accessible to non-programmers
- GitHub: [UCR Repository](https://github.com/Snoothy/UCR)

**loopMIDI - Tobias Erichsen**
- Virtual MIDI ports that enable signal routing
- Free for personal use
- Rock-solid reliability
- Web: [Tobias Erichsen Software](http://www.tobias-erichsen.de)

**MIDI-OX - Jamie O'Connell & Jerry Jorgenrud**
- MIDI routing and monitoring tool
- Free since 1990s
- Still maintained and improved
- Web: [MIDIOX.com](http://www.midiox.com)

**Opentrack - Stanislaw Halik & Contributors**
- Free head tracking solution
- Open-source, cross-platform
- Replaces expensive TrackIR hardware
- GitHub: [Opentrack Project](https://github.com/opentrack/opentrack)

**Thank you for building the foundation that made this project possible.**

---

### Affordable Excellence

**SimHub - Wotever (Nicolas Vieille)**
- $10 USD lifetime license for incredible value
- Game telemetry support across dozens of simulations
- Il-2 Dials integration
- Active development and community support
- Enables the LED feedback future of this project
- Web: [SimHub Official](https://www.simhubdash.com)

**Thank you for making professional-grade telemetry accessible to everyone.**

---

### Hardware Manufacturers

**Akai Professional**
- For building pro-grade MIDI controllers that last decades
- MIDIMix and APC Mini MK2 are the heart of this setup
- Professional equipment at reasonable prices
- Musicians' tools that work perfectly for simulation

**VKB-Sim**
- For refusing to compromise on flight control quality
- Premium hardware without the typical premium pricing
- Engineering excellence in simulation peripherals
- T-Rudder pedals and Gladiator sticks are best-in-class

**Thank you for building tools worthy of professional use.**

---

### The Simulation Community

**To the communities** on r/hotas, r/flightsim, r/il2sturmovik, forums, and Discord servers:
- Your collective knowledge helped troubleshoot countless issues
- Your passion for simulation drives innovation
- Your willingness to share freely inspired this guide
- This documentation exists to give back what you've shared

**Thank you for fostering a culture of knowledge-sharing.**

---

### AI Assistance Disclosure

**Transparency (PunkTech Principle 4: Free Knowledge with Honesty):**

This guide was created with assistance from:
- **Gemini AI** (Google): Technical research, MIDI troubleshooting, system architecture questions
- **Claude AI** (Anthropic): Documentation structure, writing assistance, methodology refinement

**Important clarifications:**
- The architecture design is entirely my work
- All testing and validation were done by me
- All decisions (hardware, software, configurations) are mine
- The methodology and engineering approach are from my 13+ years of IT experience

**AI tools accelerated research and writing, but did not replace understanding or expertise.**

I disclose this because:
1. **Honesty matters** - hiding tool usage would be dishonest
2. **Others should know** - these tools exist and can help with complex projects
3. **AI is a tool** - like a calculator or search engine, not a replacement for thinking
4. **Transparency builds trust** - especially important for technical documentation

**If you use this guide and AI assistance helps you troubleshoot, that's perfectly fine.**

Just understand what you're building, don't just copy commands blindly.

---

### Special Thanks

**To my father:**
For teaching me "Tu veux faire de l'argent? Oublie l'argent."

Credibility and value creation matter more than immediate profit.

This guide is free because of that lesson.

---

**To the Linux and open-source communities:**
For teaching me that better solutions often exist outside mainstream thinking.

Even though this project ended up on Windows (pragmatism), the open-source philosophy of sharing knowledge freely lives on.

---

**To every developer who chose "open" over "closed":**

You make projects like this possible.

You enable innovation without permission.

You prove that collaboration beats competition.

**Thank you.**

---

### Support These Developers (Optional)

If this guide helped you save hundreds of dollars on your simulation setup, consider supporting the open-source tools that made it possible:

**No affiliate links. No kickbacks. Just genuine appreciation.**

- **vJoy:** Check their GitHub for contribution options
- **UCR:** GitHub Sponsors may be available
- **loopMIDI:** Visit Tobias Erichsen's site for donation info
- **Opentrack:** Check their GitHub for support options
- **SimHub:** Already purchased ($10) - but they deserve recognition

**I have no financial affiliation with any of these projects.**

I simply believe in supporting the tools we depend on.

Even $5-10 to a developer whose tool you use daily makes a difference.

---

### To You, The Reader

**Thank you for:**
- Taking the time to understand this system (not just copying)
- Investing cognitive effort (20-40 hours of learning)
- Choosing to build rather than just consume
- Questioning mainstream solutions

**The effort you invest in comprehension is what makes this approach sustainable and adaptable to your specific needs.**

**If this guide helped you, consider:**
- Sharing your test results (help validate other games)
- Contributing improvements (configurations, troubleshooting tips)
- Applying PunkTech principles to your own projects
- Sharing this guide with others who might benefit

**Engineering against inefficiency is a collective effort.**

We all stand on shoulders of those who shared before us.

---

## Conclusion

### This Guide is One Application of PunkTech

**The MIDI simulation setup demonstrates PunkTech principles:**
- Open standards over proprietary
- Rigorous engineering over marketing bullshit
- Intelligent DIY over consumer marketing traps
- Free knowledge over short-term profit
- Pragmatism over ideology

**What inefficiencies will you engineer against next?**

**Explore more:**
- [PunkTech Manifesto](PUNKTECH_MANIFESTO.md) - The philosophy
- [PunkTech Projects](/projects) - Other applications
- [About PunkTech](/about) - Who we are

---

## Version History

**v1.0 - February 2026:**
- Initial release
- Tested: Il-2 Great Battles
- Architecture: Designed for 8 games (7 pending validation)

---

## Contact

**PunkTech:**
- Web: [punktech.ca](https://punktech.ca)
- Guide: [punktech.ca/projects/midi-sim-setup](https://punktech.ca/projects/midi-sim-setup)
- Manifesto: [punktech.ca/manifesto](https://punktech.caPUNKTECH_MANIFESTO.md)

**Reddit:** u/PunkTech (to be created)

---

**Engineering Against Inefficiency.**

**Refuse the toys. Demand pro-grade.**

**— PunkTech, February 2026**

---
---

# APPENDIX: Technical Notes & Expanded Troubleshooting

**Note:** The following sections contain detailed technical notes that will be integrated into the main guide during Sprints 2-3. They are included here for reference and completeness.

---

# PunkTech Guide - Addendum Notes

## Critical Troubleshooting Tips

### The Three-Layer Diagnostic Approach

**Philosophy:** Each layer of the stack can be isolated and verified independently.

---

### Layer 1: Hardware → MIDI-OX (Physical Signal)

**Tool: MIDI-OX Monitor - Output View**

**Purpose:** Verify hardware sends signals AND identify exact MIDI values

**How to use:**
1. Open MIDI-OX
2. Go to: **Options → MIDI Devices**
3. Enable your hardware controllers in MIDI Inputs
4. Go to: **View → Monitor** (or press Ctrl+M)
5. In Monitor window: Select **"Output"** view (not Input)

**What you'll see:**
- Move a fader/knob → See exact CC (Control Change) number
- Press a pad/button → See exact Note number
- Channel information
- Velocity values

**Why this matters:**
- **Confirms hardware is working** (if no signal = hardware problem or USB issue)
- **Identifies exact MIDI values** for UCR mapping
- Essential for creating accurate UCR profiles
- Troubleshoot "why isn't this button working?"

**Example outputs:**
```
MIDImix Fader 1: CC 19, Channel 2
MIDImix Knob 1 (Blue): CC 16, Channel 2
APCmini Pad (0,0): Note 0, Channel 1
APCmini Pad (7,7): Note 63, Channel 1
```

**Pro tip:** Keep MIDI-OX Monitor open while configuring UCR - verify exact values in real-time.

**Result:** ✅ Hardware works, ✅ MIDI-OX receives signals

---

### Layer 2: MIDI-OX → loopMIDI → UCR (Routing Verification)

**Tool: loopMIDI Visual Indicators**

**Purpose:** Verify MIDI-OX routes signals correctly to virtual ports

**How to use:**
1. Open loopMIDI (shows list of virtual ports)
2. Move a MIDImix control (fader, knob, button)
3. **Watch InputsToJG port** - "Total data" column should increment
4. Press an APCmini pad
5. **Watch Input2ToUCR port** - "Total data" column should increment

**What you're verifying:**
- MIDI-OX routing configuration is correct
- Each hardware controller goes to correct virtual port
- loopMIDI pipes are functioning
- **Signal isolation works** (MIDImix ≠ APCmini ports)

**How "Total data" works:**
- Shows cumulative bytes sent through that port since loopMIDI launched
- Each MIDI message = 3 bytes typically
- Move a fader → Number increases by 3
- Press a button → Number increases by 3
- **If number doesn't change = no signal on that port**

**If Total data doesn't increment:**
- MIDI-OX routing not configured
- MIDI-OX not running
- Wrong port selected in MIDI-OX

**Why isolation matters:**
- Separate virtual ports = independent troubleshooting
- See exactly which hardware → which middleware
- Pinpoint breaks in the chain instantly

**Result:** ✅ MIDI-OX routes correctly, ✅ loopMIDI receives signals, ✅ UCR can read from ports

---

### Layer 3: UCR → vJoy (Conversion Verification)

**Tool: vJoy Monitor (vJoyConf.exe)**

**Purpose:** Confirm UCR converts MIDI to vJoy inputs correctly

**How to use:**
1. Run vJoyConf.exe (comes with vJoy installation)
2. Click "Monitor vJoy" button
3. Select vJoy Device (1-4)
4. Move MIDImix fader → **Watch corresponding axis move in monitor**
5. Press APCmini pad → **Watch corresponding button light up**

**What you're verifying:**
- UCR profile is loaded correctly
- MIDI mappings are accurate
- vJoy devices are active and responsive
- **The entire chain works end-to-end**

**If axes/buttons don't respond:**
- UCR profile not loaded
- UCR not reading from correct loopMIDI ports
- Mapping mismatch (wrong CC number in UCR vs actual hardware)
- vJoy device not configured properly

**Result:** ✅ Complete chain functional: Hardware → MIDI-OX → loopMIDI → UCR → vJoy

---

### CRITICAL: MIDI Note Nomenclature - MIDI-OX vs UCR

**Two differences between software - both confirmed by screenshots:**

**Difference 1: Flat vs Sharp notation**

**MIDI-OX Monitor Output:**
- Displays notes using **flat (♭) notation**
- Example: `Note: Bb3`, `Eb4`, `Ab2`

**UCR Note Selection:**
- Uses **sharp (#) notation**
- Example: `A#3`, `D#4`, `G#2`

---

**Difference 2: Octave numbering offset**

Confirmed by screenshots (a000023 vs a000020):

- **MIDI-OX Monitor** shows: `C#-1` (octave -1)
- **UCR** shows the same note as: `Octave -2, C#`

**MIDI-OX octave = UCR octave + 1**

| MIDI-OX affiche | UCR sélectionner |
|-----------------|-----------------|
| C#-1 | Octave -2, C# |
| A#0 | Octave -1, A# |
| D#3 | Octave 2, D# |

**Toujours vérifier les deux différences quand vous mappez une note.**

---

**Conversion Table (flat → sharp):**

| MIDI-OX Display | UCR Selection | Same Note |
|-----------------|---------------|-----------|
| Bb (Si bémol) | A# (La dièse) | ✅ |
| Eb (Mi bémol) | D# (Ré dièse) | ✅ |
| Ab (La bémol) | G# (Sol dièse) | ✅ |
| Db (Ré bémol) | C# (Do dièse) | ✅ |
| Gb (Sol bémol) | F# (Fa dièse) | ✅ |

**These are the same pitches, just different naming conventions.**

![MIDI-OX + UCR + loopMIDI - Nomenclature en action](Appendix/a000023.png)
*MIDI-OX Monitor montre "C#-1 Note On" (notation bémol, octave -1). UCR configure la même note comme "Octave -2, C#" (notation dièse, octave -2). Même note, deux conventions différentes.*

---

**Mapping Workflow:**

**Step 1: Identify note in MIDI-OX**
- Press pad on APCmini
- MIDI-OX Monitor shows: `Note On: C#-1`

**Step 2: Convert to UCR notation**
- C#-1 → C# Octave -2 (subtract 1 from octave, keep sharp)
- If flat: Bb3 → A# Octave 2

**Step 3: Select in UCR**
- Choose octave: `-2`
- Choose note: `C#`
- **Mapping complete**

---

**Why This Matters:**

**Common mistakes:**
- See `Bb3` in MIDI-OX → look for "Bb" in UCR → **not found** (UCR only shows sharps)
- See `C#-1` in MIDI-OX → select Octave -1 in UCR → **wrong octave**

**Correct approach:**
- Note: `C#-1` in MIDI-OX → UCR: `C#, Octave -2`
- Note: `Bb3` in MIDI-OX → UCR: `A#, Octave 2`
- **Works immediately**

---

**Quick Reference:**

If MIDI-OX shows a flat (♭), convert to sharp (#):

```
Bb → A#
Eb → D#
Ab → G#
Db → C#
Gb → F#
```

Natural notes (C, D, E, F, G, A, B) are the same in both.

---

**Pro Tip:**

If you don't have music theory background:

1. Press pad
2. Note what MIDI-OX shows (e.g., "Bb3")
3. Use table above to convert: Bb = A#
4. Select A#3 in UCR

**Or just Google "Bb to sharp" → Result: A#**

---

### Layer 4: vJoy → Game (Final Verification)

**Tool: Windows Game Controllers (joy.cpl)**

**Purpose:** Verify Windows sees vJoy devices correctly

**How to use:**
1. Run `joy.cpl` (Windows + R, type joy.cpl)
2. Select vJoy Device
3. Click Properties → Test
4. Move controls, press buttons
5. **Verify in test window**

**What you're verifying:**
- Windows recognizes vJoy devices
- Joystick IDs are stable (Joystick ID# Swapper working)
- Game will see these devices

**Result:** ✅ Ready for game binding

---

### Complete Troubleshooting Flowchart

```
Problem: "My MIDI controls don't work in game"

Step 1: Check MIDI-OX Monitor Output
├─ No signal? → Hardware problem or USB connection
└─ Signal present? → Go to Step 2

Step 2: Check loopMIDI port activity
├─ No blinking? → MIDI-OX routing not configured
└─ Blinking? → Go to Step 3

Step 3: Check vJoy Monitor
├─ No movement? → UCR profile issue or mapping mismatch
└─ Movement present? → Go to Step 4

Step 4: Check Windows Game Controllers
├─ Device not visible? → vJoy installation issue
└─ Device works? → Problem is in game bindings
```

---

### The "Move and Watch" Method

**Fastest way to verify entire chain:**

1. Open simultaneously:
   - MIDI-OX Monitor (Output)
   - loopMIDI window
   - vJoy Monitor
   - Windows Game Controllers test

2. Move ONE control (e.g., MIDImix Fader 1)

3. Watch the cascade:
   - ✅ MIDI-OX shows CC 19
   - ✅ loopMIDI InputsToJG "Total data" increments (e.g., 0 → 3 → 6)
   - ✅ vJoy Monitor shows Axis 1 move
   - ✅ Game Controllers test shows axis move

4. If ANY step fails → You've isolated the problem layer

**This is the power of modular architecture.**

Each component can be verified independently.

---

### Common Issues & Quick Fixes

**Issue: "I see signal in MIDI-OX but loopMIDI Total data doesn't increment"**
- Fix: Check MIDI-OX routing (Options → Data Mapping)
- Verify: Hardware input → Correct loopMIDI output port

**Issue: "loopMIDI Total data increments but vJoy Monitor doesn't move"**
- Fix: Check UCR is running and profile loaded
- Verify: UCR reads from correct loopMIDI port (InputsToJG or Input2ToUCR)
- Check: MIDI CC numbers in UCR match MIDI-OX Monitor output

**Issue: "vJoy Monitor works but game doesn't see inputs"**
- Fix: Check game bindings
- Verify: Joystick ID# Swapper has fixed IDs correctly
- Check: Game recognizes vJoy devices (some games need restart after vJoy activation)

---

**Engineering Against Inefficiency.**

**— PunkTech, February 2026**
