<div align="center">

# CalmLayer
### A crisis mode for the internet.

[![Katy Youth Hacks 2026](https://img.shields.io/badge/Katy_Youth_Hacks-2026-0E3B34?style=for-the-badge)](https://katy-youth-hacks-2026.devpost.com/)
[![Theme](https://img.shields.io/badge/Theme-Tech_for_Humanity-7FA98F?style=for-the-badge)](#)
[![Live demo](https://img.shields.io/badge/Live_demo-github.io-E9A13B?style=for-the-badge)](https://<USERNAME>.github.io/calmlayer/)
[![License](https://img.shields.io/badge/License-MIT-1A1A1A?style=for-the-badge)](LICENSE)

[![1st Place](https://img.shields.io/badge/1st_Place-Katy_Youth_Hacks_2026-E9A13B?style=for-the-badge)](https://katy-youth-hacks-2026.devpost.com/)
*The web should adapt to people in crisis — not the other way around.*

**[→ Try the live demo](https://jasurcyb.github.io/calmlayer/)**

</div>

---

> Most technology is built for one kind of person: calm, rested, literate,
> unhurried, and safe. But the moments we need the web most are usually the
> moments we are least able to use it. CalmLayer is a prototype interface
> layer that meets a stressed person where they actually are.

---

## The problem, in one screen

Open a real benefits form on a bad day and you are greeted by:

- a wall of legalese — *"Pursuant to subsection 14(b), the undersigned hereby attests…"*
- a blinking **SESSION EXPIRING IN 04:59** countdown that punishes slow hands,
- a cookie banner, a popup ad, and a sidebar of ten links nobody asked for,
- twelve required fields, every one of them urgent, none of them plain.

The interface assumes you have time, focus, and steady hands.
The person on the other side of the screen has none of those.

The more urgent the situation, the harder the page becomes. **That is the bug CalmLayer fixes.**

## The idea

CalmLayer does **not** delete important information. It changes the *order,
language, spacing, and interaction* so a stressed person can focus on the one
thing that matters right now.

One press of **Enable Calm Mode** and the whole page exhales:

- the countdown stops and quietly reads *"Take your time. Your session is safe."*
- the ads, banners, and secondary noise disappear,
- legalese becomes plain sentences,
- twelve fields become **one answer at a time**,
- buttons grow large, readable, and unhurried,
- help is always a single tap away.

The demo proves the idea *on itself* — there is no separate mockup. You live
the problem and the solution inside the same ten seconds.

## Three tests

The same information, twice. The left column is the web as it is; the right is
the web as it could be when someone is struggling.

| # | Scenario | Normal web | Calm web |
|---|----------|------------|----------|
| **01** | Government aid form | 12 fields of legalese, red asterisks, a ticking session timer | One question at a time · *Step 1 of 4* · huge buttons · an *I need help* escape hatch on every screen |
| **02** | Medical discharge instructions | One dense clinical paragraph of jargon | Three things you can remember · a working **Read this aloud** button (Web Speech API) |
| **03** | Emergency information page | 18 competing all-caps warnings | A single next action · *Call for help* · a guided **breathing pacer** (inhale 4s · hold · exhale 6s) |

## How the dual-mode system works

The entire interface lives in two states, switched through **one attribute**
on `<body>`. Every color, font size, radius, and spacing value is a CSS custom
property that listens to that attribute — so a single press transforms the
whole page in one smooth transition instead of a reload.

```html
<body data-mode="normal">   <!-- chaotic, pressured, dense -->
<body data-mode="calm">     <!-- serene, one step, unhurried -->
```

```css
:root, body[data-mode="normal"] {
  --bg: #ffffff;  --ink: #1a1a1a;  --alarm: #c4372c;
  --body: 13px;   --radius: 4px;   --space: cramped;
}
body[data-mode="calm"] {
  --bg: #f1f5f0;  --ink: #0e3b34;  --accent: #e9a13b;
  --body: 19px;   --radius: 18px;  --space: generous;
}
```

No frameworks. No build step. No backend. One self-contained page.

## Design tokens at a glance

The contrast is the point — Normal Mode is *deliberately* hostile so the
relief of Calm Mode is felt, not just seen.

| Token | Normal | Calm |
|-------|--------|------|
| Background | harsh white `#FFFFFF` | soft mist `#F1F5F0` |
| Text | ink `#1A1A1A` | deep pine `#0E3B34` |
| Signal | alarm red `#C4372C` | warm amber `#E9A13B` |
| Body size | 12–13 px | 18–20 px |
| Corners | sharp 4 px | soft 18 px |
| Pace | blinking, urgent | slow, breathing |

Typography is a deliberate choice, not a default: **Fraunces** for display,
and **Atkinson Hyperlegible** — a typeface designed by the Braille Institute
for maximum readability — for body text.

## Accessibility — the project practices what it preaches

A tool *about* access that ignores access would be a contradiction. CalmLayer
walks its own talk:

- [x] semantic HTML and full keyboard navigation
- [x] `aria-live` announcements on every mode change
- [x] AA+ color contrast in **both** modes
- [x] large (≥ 48 px) hit targets in Calm Mode
- [x] complete `prefers-reduced-motion` support
- [x] browser-native speech synthesis for tired or low-literacy readers

## Try it

**Live (recommended):** [https://jasurcyb.github.io/calmlayer/](https://jasurcyb.github.io/calmlayer/)
Speech synthesis and all motion work best over `https://`.

**Locally:** there is nothing to install or build.

```bash
# serve the folder (don't double-click the file — speech needs http/https)
python -m http.server 8000
# then open http://localhost:8000
```

> Note: opening the file directly via `file://` can block the browser's
> speech synthesis. A local server or the live link avoids this.

## Built with

`HTML5` · `CSS3` (custom-property design system) · `Vanilla JavaScript` ·
`Web Speech API` · `IntersectionObserver` · `Google Fonts` ·
`WCAG-minded accessibility`

## What's next

- **A browser extension** that adds Calm Mode to *any* site a person is
  struggling with — not just this demo.
- **An open-source SDK** that public services, hospitals, and emergency
  platforms can embed in a few lines.
- **A design standard** for stress-aware interfaces: concrete rules for
  language, spacing, motion, and pressure signals (like countdown timers)
  that should never appear when someone is already under pressure.

## A note on scope

CalmLayer is a supportive interface prototype. It is **not** a medical device
and **not** an emergency service. In a real emergency, call local emergency
numbers.

---

<div align="center">

Built with care for **Katy Youth Hacks 2026 — Tech for Humanity**.
Set in *Atkinson Hyperlegible*, designed for readability.

*Almost everyone will need a calmer web someday — often on the worst day
they can remember. This is for that day..*

</div>
