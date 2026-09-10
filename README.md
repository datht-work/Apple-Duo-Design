# 📱 iPhone Duo Design Conversion — Agent Skill

> **Audience**: Product Managers & UX Designers
> **Scope**: Converting existing iOS apps to support iPhone Duo (dual-display foldable)
> **Source**: [Apple HIG — Designing for iPhone Duo](https://developer.apple.com/design/human-interface-guidelines/designing-for-iphone-duo)

---

## What Is This?

An **Apple Duo Agent Skill** that provides a structured, 4-phase workflow for
Product Managers to evaluate and plan the conversion of existing iOS apps to
support iPhone Duo.

The skill is provided as a set of Markdown files that can be easily loaded into
your AI assistant (Claude, ChatGPT, Cursor, etc.) to guide the conversion process.

---

## Quick Start

### Step 1: Prepare Input
Gather **5–8 screenshots** of your app's key screens:
- Home/landing screen
- Primary content screen (where users spend most time)
- Navigation flow (how users move between sections)
- Detail/edit screen (forms, editors, detail views)
- Settings or secondary screen

> 💡 **Tip**: Both portrait AND landscape screenshots give the best results.
> Figma exports (PNG/JPG) also work. Text descriptions are a fallback.

### Step 2: Ask the Agent
Attach your screenshots and use prompts like:

```
Evaluate this app for iPhone Duo conversion
```
```
Create a PRD for converting our app to support iPhone Duo
```
```
What user stories do we need for iPhone Duo support?
```
```
Compare our approach with Samsung Fold apps
```

### Step 3: Get Results
The agent runs a 4-phase workflow and produces:

| Phase | Output | What You Get |
|-------|--------|-------------|
| **1. Audit** | Readiness Report | 🔴🟡🟢 severity ratings per screen/component |
| **2. PRD** | Draft PRD | Ready for stakeholder review with metrics |
| **3. Stories** | User Stories | Prioritized with MoSCoW + acceptance criteria |
| **4. Roadmap** | Phasing Plan | Launch-ready → Fast-follow → Delight |

---

## Skill Contents

```
iphone-duo-design-conversion/
├── SKILL.md                     — Main workflow (4 phases)
└── references/
    ├── hig-summary.md           — Apple HIG for PMs (non-technical)
    ├── pm-checklist.md          — 30+ audit items across 6 categories
    ├── prd-template.md          — 8-section PRD with [AUTO]/[PM] markers
    ├── user-stories-catalog.md  — 17 stories + app-type selection matrix
    └── competitive-analysis.md  — iPhone Duo vs Samsung Fold vs Pixel Fold
```

### File Descriptions

| File | Size | Purpose |
|------|------|---------|
| [`SKILL.md`](./SKILL.md) | 4.7 KB | Entry point. Defines accepted inputs, 4-phase workflow, key principles |
| [`hig-summary.md`](./references/hig-summary.md) | 8.0 KB | Apple HIG translated into PM language with "PM Action" items per section |
| [`pm-checklist.md`](./references/pm-checklist.md) | 8.1 KB | Screen-by-screen audit with 6 categories, 30+ items, scoring summary |
| [`prd-template.md`](./references/prd-template.md) | 7.9 KB | Fill-in PRD: Executive Summary → Features → Metrics → Phasing → Risks |
| [`user-stories-catalog.md`](./references/user-stories-catalog.md) | 10.9 KB | 17 user stories across 7 categories with acceptance criteria + app-type matrix |
| [`competitive-analysis.md`](./references/competitive-analysis.md) | 10.7 KB | 8-dimension comparison with Samsung Z Fold & Pixel Fold |

---

## iPhone Duo — Key Facts for PMs

| Attribute | Details |
|-----------|---------|
| **Displays** | Outer (compact width, phone-like) + Inner (regular width, tablet-like) |
| **Hinge** | Center fold supporting multiple poses |
| **Biggest UX change** | Tab bars & toolbars move to **vertical side rail** |
| **Biggest opportunity** | Master-detail views expand to show both panes simultaneously |
| **Developer effort** | Low if app already uses standard SwiftUI/UIKit components |
| **Launch date** | 2026 (new Apple HIG section published September 9, 2026) |

### The #1 Thing PMs Must Understand

> **Controls move to the side.** On iPhone Duo, the tab bar and toolbar display
> as a vertical rail on the side of the screen — not at the bottom. This
> maximizes vertical space for content but fundamentally changes the navigation
> pattern. Every iOS app will be affected.

---

## Competitive Context

| Feature | iPhone Duo 🍎 | Samsung Z Fold 🤖 | Pixel Fold 🤖 |
|---------|:---:|:---:|:---:|
| Auto-adaptation | ✅ Best | ⚠️ Manual | ⚠️ Manual |
| Vertical controls | ✅ Unique | ❌ Bottom nav | ❌ Bottom nav |
| Fold-aware layout | ✅ System-managed | ⚠️ Dev-managed | ⚠️ Dev-managed |
| Multi-window | ⚠️ Split View only | ✅ Up to 3 apps | ✅ 2 apps |
| Ecosystem maturity | 🆕 New (2026) | ✅ 5th gen (2019+) | ⚠️ 2nd gen (2023+) |
| Developer effort | 🟢 Low | 🟡 Medium | 🟡 Medium |

**First-mover advantage**: Early Duo-optimized apps will stand out. Samsung's
foldable app ecosystem is crowded; Apple's is fresh territory.

---

## Conversion Strategy: 3 Phases

```
┌─────────────────────┐    ┌─────────────────────┐    ┌─────────────────────┐
│   PHASE A: LAUNCH   │───▶│  PHASE B: ENHANCE   │───▶│  PHASE C: DELIGHT   │
│                     │    │                     │    │                     │
│ Fix 🔴 Breaking     │    │ Split views         │    │ Fold-aware features │
│ Vertical controls   │    │ Arrangement views   │    │ Pose-specific UX    │
│ State persistence   │    │ Content hierarchy   │    │ Competitive parity  │
│                     │    │                     │    │                     │
│ Ship with Duo launch│    │ 1-2 sprints after   │    │ Next quarter        │
└─────────────────────┘    └─────────────────────┘    └─────────────────────┘
```

---

## 🤖 Using with Claude, ChatGPT & Other AIs

Because this skill is written in standard Markdown, you can easily use it with any GenAI tool:

### Option 1: Claude Projects / Custom GPTs (Recommended)
1. Download all files in this repository.
2. Go to **Claude Projects** or **ChatGPT Custom GPT** creation.
3. Upload all the `.md` files as **Project Knowledge** (Claude) or **Knowledge Files** (ChatGPT).
4. Copy the content of `SKILL.md` and paste it into the **Custom Instructions / System Prompt** field.
5. *How to use*: Just upload your app screenshots and type: *"Run the Phase 1 App Audit on these screenshots."*

### Option 2: The "Mega-Prompt" Approach
If you don't have access to Claude Projects or Custom GPTs, you can use the bundled `apple_duo_mega_prompt.md` file:
1. Open `apple_duo_mega_prompt.md` (this file combines all instructions, checklists, and references into one massive text block).
2. Copy the entire text.
3. Start a new chat in Claude/ChatGPT and paste the text.
4. Add your screenshots to the same message and hit Send.

---

## Essential Apple Resources

- 📖 [Designing for iPhone Duo (HIG)](https://developer.apple.com/design/human-interface-guidelines/designing-for-iphone-duo)
- 🎬 [Design for iPhone Duo (Video)](https://developer.apple.com/videos/play/tech-talks/111466)
- 🎬 [Raise the bar with iPhone Duo (Video)](https://developer.apple.com/videos/play/tech-talks/111462)
- 🎬 [Strike a pose with adaptive layouts (Video)](https://developer.apple.com/videos/play/tech-talks/111463)
- 📐 [Apple Design Resources](https://developer.apple.com/design/resources/)

---

*Skill version: 1.0 — September 2026*
*Based on Apple HIG published September 9, 2026*
