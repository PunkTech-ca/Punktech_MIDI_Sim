# PunkTech MIDI Simulation Setup Guide

**Professional MIDI Controllers for Flight Simulation**

[![License: CC BY-SA 4.0](https://img.shields.io/badge/License-CC%20BY--SA%204.0-lightgrey.svg)](http://creativecommons.org/licenses/by-sa/4.0/)

---

## 🎯 What Is This?

A complete, open-source guide for using **professional audio MIDI controllers** (Akai MIDIMix, APCmini) as simulation peripherals instead of expensive gaming buttonboxes.

**The Result:**
- 220+ inputs (45 axes + 176 buttons)
- $150-300 MIDI gear vs $500-800 gaming toys
- Pro-grade durability
- Works across 35+ simulation games

---

## 📖 Documentation

**Main Guide:** [Docs/GUIDE-MIDI-SIM-SETUP.md](Docs/GUIDE-MIDI-SIM-SETUP.md)

**Philosophy:** [PUNKTECH_MANIFESTO.md](PUNKTECH_MANIFESTO.md)

**Contributing:** [CONTRIBUTING.md](CONTRIBUTING.md)

---

## 🚀 Quick Start

**Prerequisites:**
- Windows 11 (10 compatible)
- MIDI controllers (Akai MIDIMix + APCmini or similar)
- VKB/Virpil HOTAS (or any DirectInput joysticks)
- 20-40 hours setup time investment

**Software Stack:**
- loopMIDI (virtual MIDI routing)
- MIDI-OX (MIDI monitoring/routing)
- vJoy (virtual joystick driver)
- UCR (MIDI → vJoy conversion)
- Joystick ID# Swapper (device persistence)

**Read the complete guide:** [Docs/GUIDE-MIDI-SIM-SETUP.md](Docs/GUIDE-MIDI-SIM-SETUP.md)

---

## ✅ Game Compatibility

**Fully Tested (Empirical Validation):**
- ✅ Il-2 Sturmovik: Great Battles (7 weeks daily use)
- ✅ Star Wars Squadrons (30 min gameplay)
- ✅ Elite Dangerous (menu validation, all devices work)
- ✅ Kerbal Space Program + AFBW (menu validation)

**Validated (Architecture Analysis):**
- ✅ DCS World
- ✅ Microsoft Flight Simulator 2020
- ⚠️ MechWarrior 5 (2 devices UI, config workaround exists)
- ⚠️ Il-2 Sturmovik 1946 + BAT (4 devices, era limitation)

**Extended Compatibility (35+ games researched):**
- Flight sims: X-Plane 11/12, Prepar3D, FlightGear
- Space sims: Star Citizen, X4 Foundations, No Man's Sky
- Naval sims: Cold Waters, UBOAT, Silent Hunter 5
- Equipment sims: Farming Simulator 22/25, Euro Truck 2/ATS
- Racing sims: Assetto Corsa, iRacing, rFactor 2
- Tank sims: Steel Beasts Pro, War Thunder

See [full compatibility matrix](Docs/GUIDE-MIDI-SIM-SETUP.md#game-compatibility-matrix) in guide.

---

## 💡 Why MIDI Controllers?

**vs Gaming Buttonboxes:**
| Feature | Gaming Buttonbox | MIDI Controller |
|---------|------------------|-----------------|
| Price | $500-800 | $150-300 |
| Inputs | 20-40 | 80-116 |
| Durability | Cheap plastic | Pro-grade plastic\metal |
| Expandability | Proprietary ecosystem | Open standard (40 years old) |
| Resale value | Low (niche market) | High (music production use) |

**Professional audio gear = better quality, lower cost, higher versatility.**

---

## 🎓 PunkTech Philosophy

This guide demonstrates [PunkTech principles](PUNKTECH_MANIFESTO.md):

1. **Open Standards** - MIDI (1983), DirectInput, vJoy (open-source)
2. **Rigorous Engineering** - Requirements → Design → Implementation → Validation
3. **Intelligent DIY** - Question mainstream, seek optimal solutions
4. **Free Knowledge** - CC BY-SA 4.0, no paywall, no affiliate links
5. **Pragmatism** - Windows over Linux for this specific use case

Read the [full manifesto](PUNKTECH_MANIFESTO.md) for context.

---

## 🤝 Contributing

Community contributions welcome! See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

**How to contribute:**
- Test on additional games and report results
- Document game-specific bindings
- Translate guide to other languages
- Share UCR profiles (with device mapping notes)
- Submit bug reports or corrections

---

## 📜 License

This guide is licensed under [Creative Commons Attribution-ShareAlike 4.0 International (CC BY-SA 4.0)](LICENSE.md).

**You are free to:**
- ✅ Share and redistribute
- ✅ Adapt and build upon
- ✅ Use commercially

**Under these terms:**
- Attribution required
- Share derivatives under same license

---

## 🌐 Links

- **Guide:** https://github.com/PunkTech-ca/Punktech_MIDI_Sim/blob/main/Docs/GUIDE-MIDI-SIM-SETUP.md
- **Website:** https://punktech.ca (coming June 2026)
- **Reddit:** u/PunkTech-ca
- **Issues:** https://github.com/PunkTech-ca/Punktech_MIDI_Sim/issues

---

## ⚠️ Important Notes

### Not the First, But the Most Complete

**I am not the first person to use MIDI controllers in simulation.** Many have discovered this independently over the years.

**However, I believe I am the first to create a clear, structured, open-source guide** documenting:
- Complete system architecture (not just "it works for me")
- Methodology transferable across hardware and games
- Honest testing with limitations disclosed
- Free knowledge under CC BY-SA 4.0

This guide stands on the shoulders of those who came before. Credit where credit is due.

### Software Versions

This guide documents a working system as of **February 2026**.

**Tested versions:**
- loopMIDI v1.0.16.27
- MIDI-OX v7.0.2
- vJoy v2.1.9.1
- UCR v0.9.8
- Windows 11 Pro 23H2

I will update when I upgrade my own system. **I do NOT commit to testing every new version.** See guide for maintenance philosophy.

### Setup Complexity

⚠️ **This is NOT plug-and-play.**

**Investment required:**
- 20-40 hours (depending on technical background)
- Understanding of system architecture
- Troubleshooting skills
- Willingness to learn

**If you want "click and go":** Buy a commercial buttonbox. This guide is not for you.

**If you want to understand and master:** Welcome. The effort is worth it.

---

## 📊 Project Status

**Current Version:** 1.0 (Pre-Launch)

**Launch Date:** June 2, 2026

**Status:** Documentation complete, final polish in progress

---

## 🙏 Acknowledgments

**This project would not exist without:**

- The MIDI specification authors (1983)
- vJoy developers (Shaul Eizikovich, njz3)
- UCR developers (Evilc)
- The simulation community who discovered MIDI → sim before me
- Everyone who reported issues, tested, and contributed

Thank you.

---

**Built with care in Sherbrooke, Québec 🇨🇦**

**PunkTech - February 2026**
