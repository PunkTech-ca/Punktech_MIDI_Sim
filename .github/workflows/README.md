# PunkTech MIDI Simulation Setup Guide

**Professional-grade MIDI controllers for flight/space simulation**

[![License: CC BY-SA 4.0](https://img.shields.io/badge/License-CC%20BY--SA%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-sa/4.0/)
![Status](https://img.shields.io/badge/status-pre--launch-yellow)
![Version](https://img.shields.io/badge/version-0.9-blue)

---

## The Problem

Gaming buttonboxes are expensive toys disguised as tools:
- $500 for 20 plastic buttons
- Proprietary ecosystems
- Limited inputs for complex aircraft
- Marketing premiums on "gaming" branding

**There's a better way.**

---

## The Solution

**Use professional MIDI controllers designed for musicians.**

**Why this works:**
- Pro-grade build quality (musicians tour with this gear)
- Massive input capacity (80+ buttons, 32+ axes per controller)
- Open standard (MIDI protocol, 40 years proven)
- Lower cost ($150-300 vs $500-2000)
- Modular and expandable

**Architecture:**
- MIDI Controllers → MIDI-OX → UCR → vJoy → Games
- 7 DirectInput devices (VKB hardware + 4 vJoy virtual)
- 220+ total inputs (45 axes + 176 buttons)
- Multi-game compatibility (one setup, all games)

---

## What This Guide Provides

**Complete documentation:**
- ✅ System architecture (data flow, device organization, constraints)
- ✅ Hardware recommendations (tested combinations)
- ✅ Software configuration (step-by-step, not just "install")
- ✅ Game compatibility (8 games tested/validated)
- ✅ Troubleshooting methodology (3-layer diagnostic approach)
- ✅ Philosophy & methodology (understanding > copy-pasting)

**15,000+ words. ~90 minute read for newcomers.**

**Not a quick tutorial. A comprehensive reference.**

---

## Status & Timeline

**Current Version:** 0.9 (Pre-Launch)  
**Expected Launch:** June 2, 2026  
**Project Start:** December 4, 2025

**Development Progress:**

| Component | Status | Sprint |
|-----------|--------|--------|
| Core documentation | ✅ 95% Complete | Done |
| Architecture design | ✅ 100% Complete | Done |
| Game compatibility | ✅ 8 games validated | Done |
| Software screenshots | ⏳ Pending | Sprint 1 (Feb 27) |
| UCR profile export | ⏳ Pending | Sprint 1 |
| Mapping tables | ⏳ Pending | Sprint 2-3 |
| Game bindings | ⏳ Pending | Sprint 4 |
| Physical photos | ⏳ Pending | Sprint 4 |

---

## Quick Links

- **[📖 Complete Guide](docs/midi-sim-setup-guide.md)** - Full documentation
- **[🎯 PunkTech Manifesto](docs/punktech-manifesto.md)** - Philosophy & principles
- **[🎮 Game Compatibility](docs/midi-sim-setup-guide.md#game-specific)** - 8 games validated
- **[🔧 UCR Profiles](ucr-profiles/)** - Reference configs (⚠️ read warnings!) *(coming Sprint 1)*
- **[📊 Mapping Tables](appendix/mapping-tables.md)** - MIDI → vJoy reference *(coming Sprint 2)*

---

## Key Stats

**Hardware Tested:**
- Akai MIDImix (33 axes via MIDI)
- Akai APC Mini MK2 (80 buttons via MIDI)
- VKB Gladiator R/L + T-Rudder (60 inputs DirectInput)

**Games Validated:**
- ✅ **Tested (empirical):** Il-2 Great Battles (7 weeks), Star Wars Squadrons, Elite Dangerous, Kerbal Space Program + AFBW
- ⚠️ **Tested (partial):** MSFS 2020, MechWarrior 5, Il-2 1946 + BAT
- 📐 **Validated (research):** DCS World

**Architecture:**
- 7 DirectInput devices (max compatibility)
- 32 axes, 116 MIDI buttons, 60+ VKB inputs
- 220+ total discrete inputs
- Respects most restrictive game constraints (universal compatibility)

**Investment Required:**
- Time: 30-60 hours (setup + learning)
- Money: $300-2,000 depending on scope
- Cognitive: Understanding systems, not just following steps

---

## Who This Is For

### ✅ You Should Read This If:

- You need to understand **WHY**, not just HOW
- You're frustrated with overpriced gaming buttonboxes
- You enjoy systems thinking and deep documentation
- You have 30-60 hours to invest in mastery
- You fly complex aircraft (multi-engine bombers, spacecraft, heavy equipment)
- You want one setup that works across multiple games
- "Reading manuals for fun" describes you

### ❌ You Should Skip This If:

- You want plug-and-play solutions (buy a buttonbox)
- You prefer video tutorials over text
- "TL;DR" is your default response
- You don't want to understand the underlying architecture
- 15,000 words feels too long (it is, intentionally)

### 🧠 Honest Assessment:

**This is a neuroatypique-to-neuroatypique guide.**

Depth over brevity. Understanding over convenience. Methodology over products.

If you've ever spent 6 hours researching a $20 purchase, this guide is for you.

---

## Philosophy (PunkTech Principles)

**1. Open Standards Over Proprietary Lock-in**
- MIDI = 40-year open standard vs proprietary gaming ecosystems

**2. Rigorous Engineering Over Marketing Bullshit**
- Requirements-driven design, not feature-chasing
- Tested empirically, documented honestly

**3. Intelligent DIY Over Consumer Marketing Traps**
- Question mainstream inefficiency
- Look outside the industry (music stores, not gaming stores)

**4. Free Knowledge Over Short-term Profit**
- CC BY-SA 4.0 licensed (shareable, improvable, free forever)
- No affiliate links, no paywalls, no hidden incentives

**5. Pragmatism Over Ideology**
- Use the right tool for the job (Windows for this use case, despite preference for Linux)
- Document reality, not ideals

**See [full manifesto](docs/punktech-manifesto.md) for details.**

---

## Example: Why MIDI?

**Typical gaming buttonbox:**
- Virpil Control Panel: $500 USD, 20 buttons, plastic
- "Gaming" branding premium
- Proprietary connector

**Professional MIDI alternative:**
- Akai APC Mini MK2: $150 CAD, 80 buttons, metal + rubber
- Musicians tour with this gear (proven durability)
- Open MIDI standard (works with anything)

**Same functionality. 1/3 the price. Better quality.**

**This pattern repeats across the entire setup.**

---

## Architecture Overview
```
Hardware Layer:
├─ Akai MIDImix (8 faders, 24 knobs, 16 buttons)
├─ Akai APC Mini MK2 (64 pads, 9 faders, 7 buttons)
├─ VKB Gladiator R (stick)
├─ VKB Gladiator L (stick/throttle)
└─ VKB T-Rudder (pedals)
    ↓
MIDI Routing:
├─ MIDI-OX (hardware → loopMIDI routing)
├─ loopMIDI (5 virtual MIDI ports)
└─ UCR (MIDI → vJoy conversion)
    ↓
Virtual Device Layer:
├─ vJoy 1-4 (MIDI inputs, 32 axes + 116 buttons)
├─ Joystick ID# Swapper (persistent device IDs)
└─ VKB devices (native DirectInput)
    ↓
Game Layer:
└─ 7 DirectInput devices recognized by all games
```

**Key Innovation:** Axis-to-button conversion (10 analog faders → 20 digital buttons for 3-state switches like landing gear)

**Why It Works:** Designed for most restrictive game constraints, works universally.

---

## Sample Results

**Il-2 Sturmovik: Great Battles (7 weeks daily testing):**
- Complete engine management (8 faders for 4 engines × 2 parameters)
- All systems accessible (landing gear, flaps, radiators, mixture, prop pitch, weapons)
- Multi-crew bombers fully functional (gunner positions, bombardier controls)

**Elite Dangerous (menu tested, 99% confidence):**
- HOSAS-optimized (dual VKB sticks + MIDI for systems)
- 220+ inputs for complex ship management
- Power distribution, shield controls, mining, exploration all mappable

**Kerbal Space Program + AFBW (menu tested, 100% confidence):**
- Unlimited input capacity (mod removes vanilla 20-button limit)
- Perfect for ISS-level spacecraft complexity
- Manual RCS control, independent engine management

---

## Installation vs Configuration

**Important distinction:**

**This guide does NOT teach software installation.**
- Each tool has its own README (loopMIDI, MIDI-OX, vJoy, UCR)
- You can install software yourself

**This guide teaches CONFIGURATION for this architecture.**
- How to set up loopMIDI's 5 ports (and why 5)
- How to configure vJoy with different HAT counts (and why that matters)
- How to map MIDI CC/Notes to vJoy axes/buttons
- How to troubleshoot when things don't work

**Understanding > following steps.**

---

## Testing Transparency

**What I've personally tested:**
- ✅ Il-2 Great Battles: 7 weeks daily use, all aircraft types
- ✅ Star Wars Squadrons: 30 min gameplay validation
- ✅ Elite Dangerous: Menu bindings validation
- ✅ KSP + AFBW: Menu bindings validation
- ⚠️ MSFS 2020: Device detection (vJoy naming quirk documented)
- ⚠️ MechWarrior 5: Menu validation (2-device UI limit found)
- ⚠️ Il-2 1946 + BAT: Menu validation (4-device era limit confirmed)

**What I haven't tested but researched:**
- 📐 DCS World (community validation, architecture compatible)
- 📐 20+ additional games (Farming Simulator, Euro Truck, X-Plane, etc.)

**PunkTech Principle 4: Honesty**

I document what I know, admit what I don't, and encourage community validation.

---

## Known Limitations

**Honest about constraints:**
- ⚠️ Windows-only (vJoy, UCR are Windows tools)
- ⚠️ 30-60 hours investment required (not plug-and-play)
- ⚠️ Some games have quirks (MSFS naming, MW5 UI limits - documented)
- ⚠️ UCR profiles device-specific (can't just copy-paste, must recreate)
- ⚠️ Maintenance responsibility (I update when I upgrade, not on-demand)

**See guide for complete limitations and workarounds.**

---

## Community Contributions

**Wanted:**
- 🎮 Game-specific bindings (DCS, racing sims, tank sims, etc.)
- 🎛️ Alternative hardware configs (Behringer, Novation, other MIDI controllers)
- 🌍 Translations (Spanish, French, German, etc.)
- 🔧 Software version updates (test newer versions, document changes)
- 🐛 Bug reports & corrections

**How to contribute:**
- Fork repository
- Make changes
- Submit pull request
- Or open issue with findings

**See [CONTRIBUTING.md](.github/CONTRIBUTING.md) for guidelines.** *(coming soon)*

---

## License

This work is licensed under [Creative Commons Attribution-ShareAlike 4.0 International (CC BY-SA 4.0)](https://creativecommons.org/licenses/by-sa/4.0/).

**You are free to:**
- ✅ Share — copy and redistribute in any medium or format
- ✅ Adapt — remix, transform, build upon for any purpose, even commercially

**Under these terms:**
- **Attribution** — Credit "PunkTech MIDI Simulation Setup Guide", link to this repo
- **ShareAlike** — Distribute your contributions under the same CC BY-SA 4.0 license

**No additional restrictions** — You may not apply legal/technical measures that restrict others.

**See [guide license section](docs/midi-sim-setup-guide.md#license--usage) for full details.**

---

## Support & Questions

**No guarantee of support from author (PunkTech Principle 4).**

I share this freely. I do NOT commit to:
- Answering every question
- Fixing your specific issue  
- Updating for every software version
- Providing "enterprise-grade" support

**This is free knowledge from a working system, not a commercial product.**

**For questions:**
- Check [FAQ section](docs/midi-sim-setup-guide.md#faq) first
- Open GitHub issue (searchable for future users)
- Community may help (encouraged!)

**Blunt but honest:** If you need guaranteed support, hire a consultant. This guide is free because it comes with no obligations.

---

## Roadmap

**Sprint 1 (Feb 27 - Mar 2, 2026):**
- [ ] Capture software configuration screenshots
- [ ] Export UCR reference profile
- [ ] Organize image assets

**Sprint 2-3 (Mar-Apr 2026):**
- [ ] Complete software configuration writing
- [ ] Create MIDI mapping tables (Appendix C)
- [ ] Integration & polish

**Sprint 4 (Apr 28 - May 4, 2026):**
- [ ] Physical setup photos
- [ ] Il-2 Great Battles complete bindings
- [ ] Optional: Additional game examples

**Sprint 5-6 (May-Jun 2026):**
- [ ] Final review & polish
- [ ] punktech.ca website setup
- [ ] Launch preparation

**Launch: June 2, 2026** 🎂

---

## Author

**PunkTech** — Engineering against inefficiency

- **Website:** https://punktech.ca *(coming June 2026)*
- **Project Start:** December 4, 2025 (VKB order date)
- **Guide Writing:** January - May 2026
- **Principles:** Open standards, rigorous engineering, free knowledge

**Background:**
- Simulation enthusiast (flight, space, equipment)
- Systems thinker (engineering mindset applied to daily life)
- Former sim racing player (background in SimHub, virtual dashboards)
- Advocate for zététique (critical thinking, evidence-based reasoning)

**Other Projects:**
- E-bike mobility analysis *(future)*
- PunkTrouble labor dispute documentation *(future)*
- PunkTech methodology applications across domains

---

## Acknowledgments

**This guide wouldn't exist without:**

**Communities:**
- r/hotas, r/flightsim, r/il2sturmovik (inspiration & validation)
- VKB, Virpil user communities (hardware knowledge)
- UCR, vJoy developers (tools that make this possible)

**Open Source:**
- UCR (Evilc, Universal Control Remapper)
- vJoy (njz3 fork, Shaul Eizikovich original)
- loopMIDI (Tobias Erichsen)
- MIDI-OX (Jamie O'Connell)

**Philosophy:**
- My father: "Tu veux faire de l'argent? Oublie l'argent." (Focus on value, money follows)
- Zététique movement: Critical thinking, reject bullshit, demand evidence

**Personal:**
- 7 weeks of Il-2 Great Battles testing
- Countless hours debugging MIDI routing
- Failed Linux attempt (learned what NOT to do)
- Community questions that shaped documentation

**See [full acknowledgments](docs/midi-sim-setup-guide.md#acknowledgments) in guide.**

---

## Project Stats

**Lines of documentation:** 15,000+ words  
**Development time:** 6 months (Dec 2025 - Jun 2026)  
**Testing investment:** 100+ hours  
**Games researched:** 28+ (8 core + 20 extended)  
**Coffee consumed:** Immeasurable ☕  

---

## Final Notes

**This is not a product. This is knowledge.**

Free to use. Free to share. Free to improve.

**If it helps you:** Share it forward. Contribute back. Build something amazing.

**If it doesn't help you:** That's OK. Not everything is for everyone.

**Welcome to PunkTech.** 🎯

---

**Questions? → [Open an issue](https://github.com/PunkTech-ca/Punktech_MIDI_Sim/issues)**  
**Want to contribute? → [See contributing guidelines](.github/CONTRIBUTING.md)** *(coming soon)*  
**Ready to build? → [Read the complete guide](docs/midi-sim-setup-guide.md)**

**Let's engineer against inefficiency. Together.** ✨
