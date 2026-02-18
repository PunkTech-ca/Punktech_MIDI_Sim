# Contributing to PunkTech MIDI Simulation Setup Guide

**Thank you for considering contributing to this project!**

This guide benefits from community testing, feedback, and improvements. Here's how you can help.

---

## 🎯 Ways to Contribute

### 1. **Game Testing & Validation**

**Most valuable contribution:** Test this setup with games not yet validated.

**What we need:**
- Game title and version
- Testing depth (menu only vs gameplay hours)
- Device limits discovered (if any)
- Quirks or workarounds needed
- Confidence level (%)

**How to report:**
- Open an [issue](https://github.com/PunkTech-ca/Punktech_MIDI_Sim/issues) with tag `game-testing`
- Use template: "Game Testing: [Game Name]"
- Include screenshots if relevant

**Priority games:**
- Racing sims (iRacing, Assetto Corsa Competizione, rFactor 2)
- Naval sims (Sea Power, Silent Hunter series)
- Tank sims (Steel Beasts, Gunner HEAT PC)
- Any simulation not in current compatibility matrix

---

### 2. **Game-Specific Bindings Documentation**

**Share your complete bindings for a specific game.**

**What to include:**
- Game title
- Complete mapping table (CC/Note → vJoy axis/button → game function)
- Screenshots of in-game bindings (optional but helpful)
- Notes on what works well / what doesn't

**How to contribute:**
- Fork repo
- Add file: `Docs/Game-Bindings/[GameName]-bindings.md`
- Submit pull request

---

### 3. **UCR Profile Sharing**

**⚠️ IMPORTANT:** UCR profiles use device-specific GUIDs and won't work plug-and-play.

**Don't submit:** Raw .json profiles expecting others to import directly

**Do submit:** 
- Documented methodology (which CC → which axis, conversion logic)
- Mapping tables in markdown
- Screenshots showing UCR configuration
- Explanation of your design choices

**File location:** `Docs/UCR-Profiles/[YourName]-profile.md`

---

### 4. **Translation**

**Translate the guide to other languages.**

**Languages needed:**
- French (Français) — High priority
- Spanish (Español)
- German (Deutsch)
- Russian (Русский)
- Chinese (中文)

**How to translate:**
- Fork repo
- Create: `Docs/Translations/GUIDE-[LANGUAGE-CODE].md`
- Translate main guide maintaining structure
- Submit pull request

**Translation guidelines:**
- Keep technical terms in English (loopMIDI, vJoy, UCR, etc.)
- Translate explanations and methodology
- Maintain screenshot references (screenshots stay in English)
- Add note at top: "Translated by [Your Name], [Date]"

---

### 5. **Bug Reports & Corrections**

**Found an error? Let us know.**

**Examples:**
- Incorrect software version listed
- Broken link
- Typo or unclear explanation
- Screenshot doesn't match description
- Technical inaccuracy

**How to report:**
- Open an [issue](https://github.com/PunkTech-ca/Punktech_MIDI_Sim/issues) with tag `bug`
- Be specific about location (section number, line if possible)
- Suggest correction if you have one

---

### 6. **Improvements & Enhancements**

**Suggest improvements to the guide.**

**Examples:**
- Additional troubleshooting scenarios
- Better explanation of a concept
- New diagram or visual aid
- Alternative software/hardware options
- Optimization tips

**How to suggest:**
- Open an [issue](https://github.com/PunkTech-ca/Punktech_MIDI_Sim/issues) with tag `enhancement`
- Explain the improvement and why it helps
- If possible, provide draft text or example

---

## 📝 Contribution Process

### Small Changes (typos, links, minor corrections):

1. Fork the repository
2. Make your changes
3. Submit a pull request
4. Describe what you changed and why

**These will be reviewed and merged quickly.**

---

### Large Changes (new sections, major rewrites):

1. **Open an issue first** to discuss the change
2. Wait for feedback/approval
3. Fork the repository
4. Make your changes
5. Submit a pull request referencing the issue

**This avoids wasted effort if the change doesn't align with project goals.**

---

## ✅ Contribution Guidelines

### Content Quality

**All contributions must:**
- ✅ Be accurate (test before submitting)
- ✅ Be clear and well-written
- ✅ Follow existing formatting/style
- ✅ Include sources/references if claiming facts
- ✅ Respect the CC BY-SA 4.0 license

**Avoid:**
- ❌ Speculation or guesses presented as fact
- ❌ Marketing language or affiliate links
- ❌ Proprietary/closed solutions when open alternatives exist
- ❌ Plagiarism or copyright violation

---

### Technical Accuracy

**If documenting technical details:**
- Test thoroughly before submitting
- Note limitations or edge cases
- Specify software versions
- Include screenshots/evidence when possible

**If uncertain:** Say so. "Untested but likely..." is better than claiming certainty.

---

### Tone & Philosophy

**Match the PunkTech tone:**
- Honest about limitations
- Rigorous in methodology
- Respectful to readers
- Critical of marketing BS, not people
- Empowering, not condescending

**See [PunkTech Manifesto](PUNKTECH_MANIFESTO.md) for philosophy.**

---

## 🚫 What We Don't Accept

**The following will be rejected:**

1. **Affiliate links or monetization**
   - No Amazon affiliate links
   - No referral codes
   - No paid promotions

2. **Proprietary solutions without justification**
   - Open-source preferred
   - Proprietary OK if no open alternative exists
   - Must explain why proprietary is necessary

3. **Unattributed content**
   - Don't copy-paste from other guides without attribution
   - Respect copyright
   - Use your own words

4. **Low-effort submissions**
   - "It works" without details
   - No testing or validation
   - Vague or unclear explanations

5. **AI-generated content without review**
   - AI tools OK for drafting
   - Human must review, edit, and verify
   - Technical accuracy required

---

## 🔒 Licensing

**By contributing, you agree:**

- Your contribution will be licensed under [CC BY-SA 4.0](LICENSE.md)
- You have the right to submit the contribution
- You understand the contribution may be modified or rejected

**Attribution:**
- Contributors listed in guide credits
- GitHub commit history preserved
- Major contributors acknowledged in README

---

## 🛠️ Technical Setup for Contributors

### 1. Fork & Clone

```bash
git clone https://github.com/[YourUsername]/Punktech_MIDI_Sim.git
cd Punktech_MIDI_Sim
```

### 2. Create Branch

```bash
git checkout -b feature/your-contribution-name
```

### 3. Make Changes

Edit files in `Docs/` directory.

**File structure:**
```
Punktech_MIDI_Sim/
├── README.md
├── LICENSE.md
├── CONTRIBUTING.md
├── PUNKTECH_MANIFESTO.md
└── Docs/
    ├── GUIDE-MIDI-SIM-SETUP.md (main guide)
    ├── Appendix/ (screenshots)
    ├── Game-Bindings/ (community bindings)
    ├── UCR-Profiles/ (community profiles)
    └── Translations/ (translated guides)
```

### 4. Test Links

Verify all internal links work:
- Use relative paths: `[text](Docs/FILE.md)` not absolute URLs
- Check screenshots render: `![alt](Appendix/image.png)`

### 5. Commit & Push

```bash
git add .
git commit -m "Brief description of changes"
git push origin feature/your-contribution-name
```

### 6. Submit Pull Request

- Go to GitHub
- Click "New Pull Request"
- Describe your changes
- Reference any related issues

---

## 📞 Questions?

**Not sure if your contribution fits?**

Open an [issue](https://github.com/PunkTech-ca/Punktech_MIDI_Sim/issues) with tag `question` and ask.

**We're friendly and happy to help.**

---

## 🏆 Recognition

**Contributors will be:**
- Listed in guide credits
- Acknowledged in README
- Appreciated immensely

**Top contributors may be invited to:**
- Co-maintain the project
- Review pull requests
- Shape future direction

---

## 💚 Thank You

**Every contribution helps:**
- Improves guide quality
- Expands game coverage
- Helps future users
- Strengthens the community

**Your effort is valued and appreciated.**

---

**Built with community in Montréal, Québec 🇨🇦**

**PunkTech - February 2026**
