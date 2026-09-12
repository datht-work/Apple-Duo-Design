---
name: iphone-duo-design-conversion
description: >-
  Guides Product Managers through assessing and planning the conversion of
  existing iOS apps to support iPhone Duo (dual-display foldable). Use when the
  user asks to evaluate, audit, plan, or create a PRD for adapting an app to
  iPhone Duo. Accepts app screenshots or Figma exports as input to analyze
  current layouts and generate actionable conversion plans with user stories,
  checklists, and phasing recommendations.
---

# iPhone Duo Design Conversion for Product Managers

## Purpose

This skill helps Product Managers systematically convert existing iOS apps to
support iPhone Duo. It provides a structured workflow from audit through
delivery, with all outputs framed for PM/UX decision-making — not
implementation.

## Accepted Inputs

The agent MUST ask for one or more of the following inputs before proceeding:

### Primary: App Screenshots (Recommended)
- Screenshots of the current app's key screens (Home, Detail, Navigation, Settings)
- Screenshots should cover **portrait** and **landscape** orientations
- The agent will analyze layout patterns, navigation structure, content hierarchy
- Minimum 3 screens, ideal 5–8 screens for comprehensive audit

### Secondary: Figma Exports
- Exported PNG/JPG frames from Figma designs
- If user provides a Figma link, ask them to export key frames as images
- The agent CANNOT access Figma files directly — always request exported images

### Tertiary: Text Description
- If no visuals available, accept a detailed text description of the app
- Must include: navigation pattern (tab bar, sidebar), key screens, content types
- This produces a less precise audit but still actionable

## Workflow: 4 Phases

### Phase 0: App Category Detection (Automatic)
Before starting the audit, identify the app's category and load the relevant
audit profile from [App Category Guide](./references/app-category-guide.md):
- Social/Feed, Messaging, Productivity, E-Commerce, Video/Streaming,
  Maps/Navigation, Health/Fitness, Finance/Banking
- Use the category's "Top 3 Duo Concerns" to prioritize audit focus
- If user has already completed an earlier phase, skip to the requested phase

### Phase 1: App Audit
1. Ask the user for app screenshots or Figma exports (see Accepted Inputs above)
2. Identify the app category and load the matching profile from [App Category Guide](./references/app-category-guide.md)
3. Analyze each screen against the [PM Checklist](./references/pm-checklist.md)
4. Read the [HIG Summary](./references/hig-summary.md) for iPhone Duo requirements
5. Classify findings by severity using the rules in [Audit Report Template](./references/audit-report-template.md):
   - 🔴 **Breaking** — Will not function correctly on Duo (e.g., fixed layouts, odd-column grids, text-only tab bars)
   - 🟡 **Suboptimal** — Works but misses Duo capabilities (e.g., no split view, no max-width on content)
   - 🟢 **Compatible** — Already adapts well (e.g., uses standard system components)
6. Reference [Visual Patterns](./references/visual-patterns.md) to show Before → After layout diagrams
7. Output: **Audit Report** following the format in [Audit Report Template](./references/audit-report-template.md)

### Phase 2: PRD Generation
1. Use the [PRD Template](./references/prd-template.md) as the base
2. Fill in findings from Phase 1
3. Include competitive context from [Competitive Analysis](./references/competitive-analysis.md)
4. Recommend which features to adapt vs. which to redesign
5. Recommend "Wow Factor" features that leverage Duo capabilities for App Store featuring potential
6. Include Apple Ecosystem Synergy opportunities (Continuity, Dynamic Island, Tent Mode)
7. Define success metrics and KPIs
8. Output: **Draft PRD** ready for stakeholder review

### Phase 3: User Stories
1. Reference the [User Stories Catalog](./references/user-stories-catalog.md)
2. Select applicable stories based on app type and audit findings
3. Customize acceptance criteria for the specific app
4. Prioritize using MoSCoW framework (Must/Should/Could/Won't)
5. Output: **Prioritized User Stories** with acceptance criteria

### Phase 4: Phasing & Roadmap
1. Group user stories into delivery phases:
   - **Phase A (Launch-ready)**: Breaking issues + quick wins → Ship with Duo launch
   - **Phase B (Fast-follow)**: Split view, arrangement views → 1–2 sprints post-launch
   - **Phase C (Delight)**: Fold-aware features, pose-specific UX → Next quarter
2. Prioritize based on Effort vs. Impact (Business Value vs. Technical Cost)
3. Estimate PM-level effort (S/M/L) per story
4. Identify dependencies and risks
5. Include [Engineering Handoff](./references/engineering-handoff.md) checklist for Dev team
6. Reference [QA Testing Guide](./references/qa-testing-guide.md) for test planning
7. Output: **Phasing Roadmap** with timeline recommendations

## Key Principles

1. **User-first conversion strategy**: Every recommendation must justify its
   impact on end-user experience, not just technical compliance
2. **PM/UX decision framing**: Present options with trade-offs, not prescriptive
   technical solutions
3. **Progressive enhancement**: The app should work on Duo out of the box;
   Duo-specific features are enhancements, not requirements
4. **Apple-native focus**: This skill is exclusively for iPhone Duo. Competitive
   references are for context only — all recommendations follow Apple HIG
5. **Strategic Go-To-Market Focus**: Emphasize how being a Day 1 iPhone Duo app
   can drive user acquisition and App Store featuring. Factor Apple Ecosystem
   synergy (Continuity, Apple Watch) into the PRD.
6. **Output language**: Match the user's input language. If user writes in
   Vietnamese, output in Vietnamese. If English, output in English.

## Reference Documents

| Document | Purpose |
|----------|---------|
| [HIG Summary](./references/hig-summary.md) | Apple HIG for iPhone Duo, organized for PM consumption |
| [PM Checklist](./references/pm-checklist.md) | Screen-by-screen audit checklist |
| [PRD Template](./references/prd-template.md) | Ready-to-fill PRD for conversion projects |
| [User Stories Catalog](./references/user-stories-catalog.md) | Pre-built user stories with acceptance criteria |
| [Competitive Analysis](./references/competitive-analysis.md) | Comparison with Samsung Fold, Pixel Fold & iPad |
| [App Category Guide](./references/app-category-guide.md) | Pre-built audit profiles per app vertical |
| [Visual Patterns](./references/visual-patterns.md) | Before → After layout transformation diagrams |
| [Audit Report Template](./references/audit-report-template.md) | Standardized output format with severity rules |
| [Engineering Handoff](./references/engineering-handoff.md) | PM→Dev technical translation with code examples |
| [QA Testing Guide](./references/qa-testing-guide.md) | Structured test matrix for foldable device testing |


# Apple HIG Summary: iPhone Duo — PM Edition

> Source: [Apple HIG — Designing for iPhone Duo](https://developer.apple.com/design/human-interface-guidelines/designing-for-iphone-duo)
> Last updated: September 9, 2026

## What is iPhone Duo?

iPhone Duo is Apple's first foldable iPhone with **two displays** connected by a
**center hinge**. It opens and closes like a book, supporting multiple ways to
hold and position the device.

### Key Hardware Facts for PMs

| Attribute | Details |
|-----------|---------|
| **Displays** | Outer display (compact width) + Inner display (regular width) |
| **Hinge** | Center fold; partially open creates a "laptop" or "tent" pose |
| **Cameras** | Outer: always visible, corner-mounted; Inner: behind-display, hidden until active |
| **Form factors** | Closed (phone), Open flat (tablet-like), Partially folded (book/laptop), Standing |
| **Dynamic Island** | Present on outer display, expands from front-facing camera |

---

## 1. Device Anatomy (What PMs Need to Know)

### Two Displays, One Continuous Experience
- **Outer display**: Used when device is closed. Compact layout, similar to
  current iPhone. Toolbar and tab bars sit on the **side** (not bottom).
- **Inner display**: Used when device is open. Wider layout can show additional
  content hierarchy (e.g., Mail shows inbox list + email body side-by-side).
- **Transition must be seamless**: State, scroll position, and context MUST
  persist when user opens/closes the device.

### Device Poses
People use iPhone Duo in multiple poses:
1. **Closed** — Single outer display, held like a regular phone
2. **Open flat** — Both panels visible, tablet-like experience
3. **Partially folded (book)** — Held like an open book, content on both panels
4. **Partially folded (laptop)** — Bottom panel as "keyboard area", top as
   "screen"
5. **Standing (tent)** — Device stands on edges, content visible from either
   side

**PM Implication**: You do NOT need to design a custom layout for each pose.
Use adaptive layouts (size classes) and the existing UI will adjust. Focus on
identifying where your app *should* show more content when extra space is
available.

### Outer Display Strategy (Don't Forget the "Closed" Phone!)
Most PM attention goes to the exciting inner display, but the **outer display
is where users spend the majority of their time**. Key considerations:

1. **It's a compact-width iPhone** — Think iPhone SE form factor. Your app
   must work well in this constrained space.
2. **Quick-action workflows matter most** — Users open the outer display for
   fast tasks: reply to a message, check a notification, glance at a status.
   Optimize for speed, not depth.
3. **Dynamic Island is present** — The outer display has a Dynamic Island
   expanding from the front-facing camera. Plan Live Activities here.
4. **Vertical side rail is active** — Even on the compact outer display,
   controls sit on the side, not the bottom. This is the most visible
   change users will notice.
5. **Transition to inner must be seamless** — When the user opens the device:
   - Scroll position MUST be preserved
   - Form input MUST be retained
   - Media playback MUST continue without interruption
   - Navigation state MUST persist (no "going back to home")
6. **Design for one-handed use** — The outer display is held like a phone.
   Keep primary actions within thumb reach on the side rail.

**PM Action**: For each screen in your app, answer: "If the user only has 3
seconds on the outer display, what's the ONE thing they need to see or do?"
Prioritize that content.

---

## 2. Best Practices (Translated for PM/UX)

### 2.1 Build to Resize
- **What it means**: Your app must handle many different screen sizes gracefully
- **PM action**: Audit all screens for fixed-width elements, hardcoded pixel
  values, or assumptions about screen size
- **Risk if ignored**: App will look broken or waste space on inner display

### 2.2 Consistent Experience Across Displays
- **What it means**: Same features available on both outer and inner displays
- **PM action**: Map every feature to verify it's accessible in both compact and
  regular width. Identify features that benefit from additional space.
- **Example**: Mail shows a list OR email when closed → shows BOTH side-by-side
  when open. The sidebar/master list becomes visible, not a new feature.

### 2.3 Same Functionality Across Poses
- **What it means**: Controls may rearrange but all actions remain available
- **PM action**: Verify no action is "lost" when controls overflow or move
- **Risk if ignored**: Users discover features in one pose but can't find them
  in another → support tickets, churn

### 2.4 Vertical Control Layout
- **What it means**: Toolbars and tab bars move to the SIDE of the screen
  (vertical strip) instead of bottom/top
- **PM action**: Review all bottom navigation, toolbars, FABs. They will move
  to a vertical rail on the side.
  - Symbols/icons work well; text labels may truncate
  - Overflow menus become critical for managing many actions
- **UX implication**: Navigation patterns fundamentally change. This is the
  #1 area most apps will need to address.

### 2.5 Games & Immersive Apps
- **What it means**: Games should be playable in every pose
- **PM action**: Lock orientation if needed, fill the screen, prefer aspect
  ratio changes over letterboxing/pillarboxing
- **Key**: Maintain consistent text and control sizes across display sizes

---

## 3. Dynamic Layouts (What Changes)

### 3.1 Reserved Regions
Three areas of the screen are "reserved" and your content must avoid them:

| Region | When Active | PM Impact |
|--------|------------|-----------|
| **Outer camera** | Always on outer display | Controls arrange around it automatically; no action needed unless custom camera UI |
| **Inner camera** | Only when camera is active | UI shifts aside; verify camera-dependent features still work |
| **Fold region** | When device is partially open | Center of inner display excluded; content splits around the fold |

### 3.2 Split Views (Biggest Opportunity)
- Apps with master-detail patterns (lists → detail) automatically expand on
  inner display to show both panes
- **PM action**: Identify all navigation flows that follow list→detail pattern.
  These are prime candidates for split view expansion.
- **SwiftUI**: `NavigationSplitView` — **Ask your engineers if they use this**
- **UIKit**: `UISplitViewController` — same question

### 3.3 Arrangement Views (New Pattern)
A new layout container with primary + secondary views:
- **Split arrangement**: Divides area horizontally (landscape) or vertically
  (portrait)
- **Overlay arrangement**: Layers primary over secondary; side-by-side when
  partially folded
- **PM action**: Identify screens where showing a secondary view alongside the
  primary would improve UX (e.g., map + list, video + comments, document +
  reference)

### 3.4 Adapting to the Fold
When partially open, the fold creates a physical divider:
- **Grids** should use even column counts so content isn't bisected
- **Flexible containers** (like split views) naturally adapt
- **Alerts, sheets, menus** automatically move to avoid the fold

---

## 4. Vertical Controls Deep Dive

This is the most impactful change for most apps. On iPhone Duo, toolbar items
and tab bar items display **vertically along the side** of the screen.

### What Moves to the Side
- Dynamic Island & status bar
- Toolbar (previously top/bottom)
- Tab bar (previously bottom)
- Navigation controls (back, close, done)

### Placement Order (Top to Bottom)
1. Navigation actions (Back, Close)
2. Prominent actions (Done, Save)
3. Action groups
4. Remaining items
5. (Overflow for items that don't fit)

### PM/UX Decision Points
- **Prioritize which controls stay visible**: Not all will fit in the vertical
  rail. Use `ToolbarItemVisibilityPriority` to rank.
- **Preserve key actions**: Compose, New Note, Add — these should never overflow
- **Minimize text buttons**: Icons/symbols work better in vertical bars
- **Group related items**: Reduce visual clutter

### Bar Compression
When space is very tight, the system compresses either the toolbar or tab bar:
- **Navigation-focused apps** (e.g., Settings): Keep tab bar, compress toolbar
  to overflow
- **Task-focused apps** (e.g., Notes editor): Keep toolbar, minimize tab bar

---

## 5. Resources

### Apple Design Resources
- [Designing for iOS](https://developer.apple.com/design/human-interface-guidelines/designing-for-ios)
- [Layout Guide](https://developer.apple.com/design/human-interface-guidelines/layout)

### Apple Videos (Essential Viewing for PMs)
1. [Design for iPhone Duo](https://developer.apple.com/videos/play/tech-talks/111466) — Overview
2. [Raise the bar with iPhone Duo](https://developer.apple.com/videos/play/tech-talks/111462) — Vertical controls deep dive
3. [Strike a pose with adaptive layouts on iPhone Duo](https://developer.apple.com/videos/play/tech-talks/111463) — Layout patterns

### Key Technical APIs (For Engineering Handoff)
- `NavigationSplitView` / `UISplitViewController` — Split view
- `ArrangementView` — New Duo-specific layout
- `safeAreaInsets` — Safe area handling
- `ToolbarItemVisibilityPriority` / `UIBarButtonItemVisibilityPriority` — Control prioritization
- `ToolbarOverflowMenu` / `additionalOverflowItems` — Overflow management


# iPhone Duo Conversion — PM Audit Checklist

Use this checklist to systematically evaluate each screen of your existing iOS
app for iPhone Duo readiness. For each item, classify the finding as:

- 🔴 **Breaking** — Will malfunction or look broken on Duo
- 🟡 **Suboptimal** — Functional but misses Duo opportunities
- 🟢 **Compatible** — Works well, no changes needed

---

## How to Use This Checklist

### Input Required
Provide the agent with screenshots or Figma exports of your app's key screens.
At minimum, include:
1. **Home/landing screen** (first thing users see)
2. **Primary content screen** (where users spend most time)
3. **Navigation flow** (how users move between sections)
4. **Detail/edit screen** (forms, editors, detail views)
5. **Settings or secondary screen** (less-used but still important)

### Process
For each screen provided:
1. Run through every category below
2. Mark each item with a severity rating
3. Note specific elements that need attention
4. Summarize the overall readiness score

---

## Category 1: Layout & Responsiveness

### 1.1 Fixed Widths & Heights
- [ ] Does any UI element use hardcoded pixel widths?
- [ ] Are there fixed-height containers that don't scale?
- [ ] Do images or media have fixed aspect ratios that don't adapt?
- [ ] Are there custom drawing routines that assume a specific screen size?

**Why it matters**: iPhone Duo inner display is significantly wider than the
outer display. Fixed dimensions will cause content to look cramped on the inner
display or leave empty gaps.

### 1.2 Size Class Support
- [ ] Does the app respond to compact vs. regular width size classes?
- [ ] Does layout change meaningfully between compact and regular width?
- [ ] Is there a landscape layout? (indicates some adaptive design exists)

**Why it matters**: Size classes are the primary mechanism for adapting to Duo's
two displays. Apps without size class support need the most work.

### 1.3 Safe Area Handling
- [ ] Does content respect safe area insets?
- [ ] Are there elements positioned at absolute screen edges?
- [ ] Do custom views handle the Dynamic Island region?

**Why it matters**: Duo introduces new safe areas — the fold region and vertical
control rail — that will clip content if safe areas are not respected.

### 1.4 Scroll & Content Flow
- [ ] Does scrollable content fill available width dynamically?
- [ ] Do collection views/grids adjust column count based on width?
- [ ] Are there horizontal scrolling areas that assume fixed width?

**Why it matters**: Grids need even column counts to avoid content being
bisected by the fold.

---

## Category 2: Navigation & Controls

### 2.1 Tab Bar
- [ ] Does the app use a standard UITabBarController / TabView?
- [ ] How many tab items are there? (5+ will overflow in vertical mode)
- [ ] Do tab items have text labels? (text truncates in vertical bars)
- [ ] Are tab items using SF Symbols or custom icons?

**Impact**: Tab bars move to a **vertical rail** on the side. Text-heavy tab
bars will need icon-first redesign.

### 2.2 Toolbar
- [ ] Does the app use a standard toolbar?
- [ ] How many toolbar items per screen? (count them)
- [ ] Are there text-only toolbar buttons?
- [ ] Is there a "compose" or "new" action? (must stay visible)

**Impact**: Toolbars also move to the vertical rail. Items are prioritized
top-to-bottom; overflow items go into a system menu.

### 2.3 Navigation Bar
- [ ] Standard back button or custom?
- [ ] Large title style or inline?
- [ ] Custom navigation bar height or appearance?

**Impact**: Navigation controls move to the side rail. Custom navigation bars
may conflict with the system's vertical layout.

### 2.4 Floating Action Buttons (FABs)
- [ ] Are there FABs or floating controls?
- [ ] Are they positioned bottom-right (standard) or custom position?
- [ ] Do they overlap with where the side rail will appear?

**Impact**: FABs positioned at screen edges may conflict with vertical control
placement.

### 2.5 Bottom Sheets & Modals
- [ ] Does the app use bottom sheets?
- [ ] Are there modal presentations?
- [ ] Do sheets/modals use fixed heights?

**Impact**: Sheets and modals automatically adapt for fold avoidance, but
fixed-height sheets may behave unexpectedly.

---

## Category 3: Content Hierarchy

### 3.1 Master-Detail Patterns
- [ ] Does the app have list → detail navigation? (e.g., inbox → email)
- [ ] How many levels of hierarchy exist?
- [ ] Would showing two levels simultaneously benefit the user?

**Opportunity**: This is the #1 enhancement for Duo. Split views show both
panes on the inner display. Identify all master-detail flows.

### 3.2 Content Density
- [ ] Is the current layout sparse (lots of whitespace)?
- [ ] Would additional content panels improve the experience?
- [ ] Are there "hidden" content sections (tabs within tabs)?

**Opportunity**: Inner display's extra width can surface content that's
currently behind navigation taps.

### 3.3 Sidebar / Drawer Navigation
- [ ] Does the app use a hamburger menu or drawer?
- [ ] Is there a sidebar that appears in landscape on iPad?

**Opportunity**: Drawers/sidebars can become persistent columns on the inner
display, improving discoverability.

---

## Category 4: Media & Camera

### 4.1 Camera Integration
- [ ] Does the app access the camera?
- [ ] Does it use the front-facing camera?
- [ ] Is there a custom camera UI?

**Impact**: The inner camera is behind the display and only appears when active.
Custom camera UIs need to handle the reserved region.

### 4.2 Photo/Video Display
- [ ] How are images displayed? (full-width, grid, carousel)
- [ ] Is there a photo viewer/gallery?
- [ ] Video player orientation handling?

**Impact**: Media viewers should adapt to the wider inner display. Consider
showing photo metadata or editing tools in a secondary panel.

### 4.3 AR Features
- [ ] Does the app use ARKit?
- [ ] Any camera-dependent overlays?

**Impact**: AR experiences need to handle the fold and camera switching.

---

## Category 5: State & Continuity

### 5.1 State Persistence
- [ ] Does the app save state when backgrounded?
- [ ] Is scroll position restored on return?
- [ ] Do forms retain input when the app resizes?

**Impact**: Opening/closing Duo triggers a resize event. State MUST persist
through this transition or users lose context.

### 5.2 Animation & Transitions
- [ ] Are there view transition animations?
- [ ] Do animations assume a specific screen size?
- [ ] Are there custom interactive gestures?

**Impact**: Animations tied to fixed dimensions may glitch during open/close
transitions.

### 5.3 Orientation Handling
- [ ] Does the app lock to portrait?
- [ ] Does it support landscape?
- [ ] Are there orientation-specific layouts?

**Impact**: Duo's inner display can be used in both orientations. Portrait-
locked apps miss the landscape inner display opportunity.

---

## Category 6: Games & Immersive Content

### 6.1 Game Layout
- [ ] Does the game use the full screen?
- [ ] Are controls positioned relative to screen edges?
- [ ] Does it support multiple aspect ratios?

**Impact**: Games should fill the screen without letterboxing. Controls should
scale with display size.

### 6.2 Text & UI Scaling
- [ ] Is text size consistent across different screen sizes?
- [ ] Do HUD elements scale appropriately?
- [ ] Are touch targets sized for finger interaction?

**Impact**: Duo's inner display is larger; controls that were sized for a phone
screen may feel too small.

---

## Scoring Summary

After completing the checklist, summarize:

| Category | 🔴 Breaking | 🟡 Suboptimal | 🟢 Compatible | Overall |
|----------|-------------|---------------|---------------|---------|
| Layout & Responsiveness | | | | |
| Navigation & Controls | | | | |
| Content Hierarchy | | | | |
| Media & Camera | | | | |
| State & Continuity | | | | |
| Games & Immersive | | | | |
| **Total** | | | | |

### Readiness Rating
- **Duo-Ready** (0 🔴, ≤2 🟡): Ship as-is, enhance later
- **Needs Work** (1–3 🔴 or 3+ 🟡): Fix breaking issues before launch
- **Major Rework** (4+ 🔴): Significant redesign required


# PRD Template: iPhone Duo App Conversion

> **Instructions**: Fill in each section based on the audit findings. Sections
> marked [AUTO] will be pre-populated by the agent from the audit checklist.
> Sections marked [PM] require PM input and decision-making.

---

## 1. Executive Summary

### 1.1 Product
- **App Name**: [PM]
- **Current Platforms**: [PM] (e.g., iPhone, iPad, Mac)
- **Current iOS Version Support**: [PM]
- **Target Duo SDK**: iOS 26+ (iPhone Duo)

### 1.2 Business Case
- **Why convert now**: [PM]
- **Target audience on Duo**: [PM]
- **Revenue impact estimate**: [PM]
- **Competitive pressure**: [AUTO — from competitive analysis]

### 1.3 Conversion Summary
- **Overall readiness score**: [AUTO — from audit]
- **Estimated effort**: [AUTO — S/M/L per phase]
- **Recommended timeline**: [AUTO — phasing recommendation]

---

## 2. User Impact Analysis

### 2.1 User Personas Affected
Identify which user personas will be most impacted by the conversion:

| Persona | Primary Use Case | Duo Impact | Priority |
|---------|-----------------|------------|----------|
| [PM] | [PM] | [AUTO] | [PM] |

### 2.2 User Journey Changes
Map how key user journeys change on Duo:

| Journey | Current Flow | Duo Flow (Closed) | Duo Flow (Open) | Change Severity |
|---------|-------------|-------------------|-----------------|-----------------|
| [AUTO] | [AUTO] | [AUTO] | [AUTO] | [AUTO] |

### 2.3 Navigation Pattern Changes
Detail how the vertical control layout affects navigation:

| Current Pattern | Duo Pattern | User Learning Curve | Risk |
|----------------|-------------|--------------------|----- |
| Bottom tab bar | Vertical side rail | Low (system-managed) | [PM] |
| Top toolbar | Vertical side rail | Medium | [PM] |
| Custom navigation | Requires redesign | High | [PM] |

### 2.4 Apple Ecosystem Synergy (Duo WOW Factor)
Identify opportunities to integrate Duo features with the broader Apple ecosystem:

| Integration | Concept | User Value | Effort |
|-------------|---------|------------|--------|
| Handoff / Continuity | Seamless transition outer ↔ inner ↔ Mac/iPad | Very High | [AUTO] |
| Dynamic Island | Outer display Live Activities | High | [PM] |
| Apple Watch | Remote control / glanceable info while Duo is in Tent mode | Medium | [PM] |

---

## 3. Feature Requirements

### 3.1 Outer Display (Closed Device)
Features that must work on the compact outer display:

| Feature | Current Status | Required Changes | Priority |
|---------|---------------|------------------|----------|
| [AUTO] | [AUTO] | [AUTO] | [PM] |

### 3.2 Inner Display (Open Device)
Features that benefit from the wider inner display:

| Feature | Enhancement Opportunity | Expected UX Improvement | Priority |
|---------|----------------------|------------------------|----------|
| [AUTO] | [AUTO] | [AUTO] | [PM] |

### 3.3 Fold-Aware Features
Features that respond to the device's fold state:

| Feature | Fold Behavior | Implementation Complexity | Priority |
|---------|--------------|--------------------------|----------|
| [AUTO] | [AUTO] | [AUTO] | [PM] |

### 3.4 Pose-Specific Features (Optional Enhancements)
Features optimized for specific device poses:

| Pose | Feature Opportunity | User Value | Effort |
|------|-------------------|------------|--------|
| Book mode | Side-by-side reading | [PM] | [AUTO] |
| Laptop mode | Content top / controls bottom | [PM] | [AUTO] |
| Tent mode | Shared viewing / presentation | [PM] | [AUTO] |

---

## 4. Technical Dependencies

### 4.1 Engineering Assessment Checklist
Share this with your engineering team for technical validation:

- [ ] Current minimum iOS target version
- [ ] Use of `NavigationSplitView` / `UISplitViewController`
- [ ] Use of Auto Layout / SwiftUI layout system
- [ ] Use of size classes (`horizontalSizeClass`, `verticalSizeClass`)
- [ ] Safe area inset handling (`safeAreaInsets`)
- [ ] State restoration implementation
- [ ] Third-party UI libraries used (list them)
- [ ] Custom drawing / Core Graphics usage
- [ ] Camera API usage
- [ ] Game engine (if applicable)

### 4.2 Third-Party Dependencies
Identify third-party libraries that may need updates:

| Library | Current Version | Duo Support Status | Action Required |
|---------|----------------|-------------------|-----------------|
| [PM/Eng] | [PM/Eng] | [PM/Eng] | [PM/Eng] |

### 4.3 Design Dependencies
Identify design assets and systems that need updates:

- [ ] Design system supports vertical control layout
- [ ] Icon set includes SF Symbols or can replace text labels
- [ ] Breakpoint system covers Duo display sizes
- [ ] Figma/Sketch components adapted for split view
- [ ] Motion/animation specs reviewed for resize transitions

---

## 5. Success Metrics & KPIs

### 5.1 Quality Metrics (Must-Have)
| Metric | Target | Measurement |
|--------|--------|-------------|
| No layout breakage on Duo | 0 visual bugs | QA testing on device/simulator |
| State persistence on open/close | 100% state retained | Automated test suite |
| All features accessible in all poses | 100% feature parity | Feature audit matrix |

### 5.2 Experience Metrics (Should-Have)
| Metric | Target | Measurement |
|--------|--------|-------------|
| Split view adoption (inner display) | [PM]% of sessions | Analytics event tracking |
| Time-to-task improvement on inner display | [PM]% reduction | A/B comparison |
| User satisfaction (Duo-specific) | [PM] NPS delta | Post-update survey |

### 5.3 Business Metrics (Nice-to-Have)
| Metric | Target | Measurement |
|--------|--------|-------------|
| App Store rating post-update | Maintain ≥ [PM] | App Store Connect |
| Duo user retention (D7/D30) | ≥ overall retention | Analytics cohort |
| Feature adoption on Duo | [PM]% engagement | Analytics events |

---

## 6. Timeline & Phasing

### Phase A: Launch-Ready (Ship with Duo)
**Goal**: App works correctly on Duo without visual bugs

| Deliverable | Effort | Owner | Dependencies |
|-------------|--------|-------|-------------|
| Fix all 🔴 Breaking issues | [AUTO] | Eng | None |
| Verify vertical control layout | [AUTO] | Eng + Design | Design icons |
| State persistence through open/close | [AUTO] | Eng | None |
| QA pass on Duo simulator | S | QA | Simulator availability |

**Timeline**: [PM] weeks before Duo launch

### Phase B: Fast-Follow (1–2 Sprints Post-Launch)
**Goal**: Take advantage of Duo's dual-display capabilities

| Deliverable | Effort | Owner | Dependencies |
|-------------|--------|-------|-------------|
| Split view for master-detail flows | [AUTO] | Eng | Design specs |
| Arrangement views for secondary content | [AUTO] | Eng + Design | Design specs |
| Enhanced content hierarchy on inner display | [AUTO] | Design + Eng | Content audit |

**Timeline**: [PM] sprints after Duo launch

### Phase C: Delight (Next Quarter)
**Goal**: Leverage Duo-unique capabilities for differentiation

| Deliverable | Effort | Owner | Dependencies |
|-------------|--------|-------|-------------|
| Fold-aware features | [AUTO] | Eng | API documentation |
| Pose-specific optimizations | [AUTO] | Eng + Design | User research |
| Competitive feature parity | [AUTO] | PM + Design | Competitive analysis |

**Timeline**: [PM] quarter

---

## 7. Risks & Mitigations

| Risk | Likelihood | Impact | Mitigation |
|------|-----------|--------|------------|
| Duo launch timeline changes | Medium | High | Decouple Phase A from specific date |
| Third-party library doesn't support Duo | Medium | High | Identify alternatives early; test in beta |
| Design resources bottleneck | High | Medium | Prioritize icon-first redesign; reuse system components |
| User confusion with vertical controls | Medium | Medium | Follow system defaults; don't customize control placement |
| Performance on dual displays | Low | High | Profile on Duo simulator early and often |

---

## 8. Stakeholder Sign-off

| Stakeholder | Role | Status | Date |
|------------|------|--------|------|
| [PM] | Product Manager | ☐ Approved | |
| [PM] | Engineering Lead | ☐ Approved | |
| [PM] | Design Lead | ☐ Approved | |
| [PM] | QA Lead | ☐ Approved | |
| [PM] | Business/GM | ☐ Approved | |

---

## Appendix

### A. Audit Report
[Link to or embed the full audit checklist results]

### B. Competitive Analysis
[Link to competitive analysis reference document]

### C. User Stories
[Link to prioritized user stories document]


# iPhone Duo — User Stories Catalog

Pre-built user stories organized by feature area. Select applicable stories
based on your app's audit findings. Each story includes acceptance criteria
and a MoSCoW priority recommendation.

---

## How to Use This Catalog

1. Review each category and select stories relevant to your app
2. Customize the `[App-specific]` placeholders
3. Adjust MoSCoW priority based on your app's audit severity
4. Add acceptance criteria specific to your content/features

### MoSCoW Legend
- **Must** — Required for Duo launch (blocks release if missing)
- **Should** — Expected in first Duo-optimized release
- **Could** — Nice-to-have enhancement
- **Won't** — Explicitly out of scope for this cycle

---

## Category 1: Layout Adaptation

### US-1.1: Responsive Layout on Both Displays
**As a** user,
**I want** the app to display properly on both the outer and inner displays,
**so that** I can use it comfortably whether the device is open or closed.

**Priority**: Must

**Acceptance Criteria**:
- [ ] No content clipping, overlapping, or horizontal scrolling on outer display
- [ ] No excessive whitespace or undersized content on inner display
- [ ] Layout adjusts smoothly when opening/closing the device (no jumps or flashes)
- [ ] All text remains readable at all display sizes
- [ ] Touch targets meet minimum 44pt requirement on both displays

### US-1.2: Adaptive Grid Layout
**As a** user viewing [App-specific: grid content, e.g., photo gallery, product grid],
**I want** the grid to show more columns on the inner display,
**so that** I can browse more content at once when the device is open.

**Priority**: Should

**Acceptance Criteria**:
- [ ] Grid shows [2] columns on outer display (compact width)
- [ ] Grid shows [4+] columns on inner display (regular width)
- [ ] Column count is always EVEN when device is partially folded (avoids fold bisecting content)
- [ ] Grid transition animates smoothly during open/close
- [ ] Item sizes remain proportional and touch-friendly

### US-1.3: Fold-Aware Content Positioning
**As a** user holding the device partially open,
**I want** content to avoid the center fold area,
**so that** nothing important is hidden by the hinge.

**Priority**: Should

**Acceptance Criteria**:
- [ ] No text, buttons, or interactive elements positioned across the fold region
- [ ] Content reflows to distribute evenly on both sides of the fold
- [ ] Images/media that would span the fold are repositioned or resized
- [ ] The fold region is handled via safe area insets (not hardcoded)

---

## Category 2: Navigation & Vertical Controls

### US-2.1: Vertical Tab Bar Adaptation
**As a** user,
**I want** the tab bar to display as a vertical rail on the side,
**so that** I have maximum vertical space for content.

**Priority**: Must

**Acceptance Criteria**:
- [ ] Tab bar appears on the side (not bottom) on outer display
- [ ] Tab bar appears on the side in landscape on inner display
- [ ] Tab bar appears at the bottom in portrait on inner display
- [ ] All tab items are accessible (visible or via overflow)
- [ ] Active tab state is clearly indicated in vertical orientation
- [ ] Tab icons are clear without text labels (or labels fit in vertical bar)

### US-2.2: Toolbar Vertical Layout
**As a** user,
**I want** toolbar actions to be accessible in the vertical side rail,
**so that** I can perform all actions regardless of device pose.

**Priority**: Must

**Acceptance Criteria**:
- [ ] Primary actions (e.g., Compose, Save, Share) are always visible in the rail
- [ ] Secondary actions overflow into system overflow menu
- [ ] Overflow menu is discoverable and accessible
- [ ] Toolbar items use symbols/icons (not text-only buttons)
- [ ] Item order is consistent: navigation → prominent actions → groups → remaining

### US-2.3: Control Proximity to Content
**As a** user working with [App-specific: split view content],
**I want** controls to appear near the content they affect,
**so that** I don't have to reach across the screen.

**Priority**: Should

**Acceptance Criteria**:
- [ ] List-specific controls stay near the list pane (not the detail pane)
- [ ] Detail-specific controls stay near the detail pane
- [ ] Controls don't jump between panes when the layout changes
- [ ] Control grouping is logical and consistent across poses

---

## Category 3: Split View & Content Hierarchy

### US-3.1: Split View for Master-Detail
**As a** user with the device open,
**I want** to see [App-specific: list and detail, e.g., inbox and email body]
side by side,
**so that** I can browse and read without navigating back and forth.

**Priority**: Should

**Acceptance Criteria**:
- [ ] List pane visible alongside detail pane on inner display
- [ ] List collapses to single-pane on outer display
- [ ] Selected item in list highlights and updates detail pane
- [ ] Scroll position in list is preserved when switching between displays
- [ ] Navigation state is consistent (opening device doesn't lose context)

### US-3.2: Arrangement View — Split
**As a** user viewing [App-specific: map + list, video + comments],
**I want** to see both views simultaneously when the device is open,
**so that** I can reference both pieces of information at once.

**Priority**: Could

**Acceptance Criteria**:
- [ ] Primary view occupies one side, secondary view occupies the other
- [ ] Split direction matches device orientation (horizontal when wider, vertical when taller)
- [ ] Both views are independently scrollable
- [ ] Collapsing (closing device) shows only the primary view
- [ ] State in both views is preserved during open/close transitions

### US-3.3: Arrangement View — Overlay
**As a** user viewing [App-specific: content with floating panel, e.g., reading
with notes, photo with editing tools],
**I want** the overlay panel to sit side-by-side when the device is partially folded,
**so that** I have unobstructed access to both content and tools.

**Priority**: Could

**Acceptance Criteria**:
- [ ] Overlay layers on top of primary when device is flat/closed
- [ ] Overlay moves to side-by-side when device is partially folded
- [ ] Transition between overlay and side-by-side is smooth
- [ ] Both views remain interactive in side-by-side mode
- [ ] Closing the overlay returns to single primary view

---

## Category 4: State & Continuity

### US-4.1: Seamless Display Transition
**As a** user,
**I want** my current state to be preserved when I open or close the device,
**so that** I don't lose my place or have to re-navigate.

**Priority**: Must

**Acceptance Criteria**:
- [ ] Scroll position is preserved
- [ ] Selected item/tab remains selected
- [ ] Form input is not lost
- [ ] Media playback continues without interruption
- [ ] Modal/sheet state is preserved (or gracefully dismissed)
- [ ] No loading spinners or data re-fetch on display change

### US-4.2: Consistent Feature Access
**As a** user,
**I want** all features to be available regardless of how I hold the device,
**so that** I never discover a feature I can't access in my current pose.

**Priority**: Must

**Acceptance Criteria**:
- [ ] Every action available on inner display is also available on outer display
- [ ] Every action available in portrait is also available in landscape
- [ ] Controls that overflow are accessible via overflow menu
- [ ] No features are hidden behind pose-specific gestures

---

## Category 5: Camera & Media

### US-5.1: Camera Region Handling
**As a** user using [App-specific: camera feature],
**I want** the UI to properly handle the camera cutout regions,
**so that** no controls or content are obscured.

**Priority**: Must (if app uses camera)

**Acceptance Criteria**:
- [ ] Outer camera region is avoided for interactive elements
- [ ] Inner camera region activates only when camera is in use
- [ ] UI shifts to accommodate inner camera without jarring layout change
- [ ] Camera viewfinder fills appropriate display area based on device pose

### US-5.2: Enhanced Media Viewing
**As a** user viewing [App-specific: photos, videos, documents],
**I want** media to take advantage of the larger inner display,
**so that** I can see more detail and context.

**Priority**: Should

**Acceptance Criteria**:
- [ ] Media expands to fill inner display width
- [ ] Metadata/info panel can appear alongside media on inner display
- [ ] Zooming/panning behavior adapts to display size
- [ ] Media transitions smoothly between display sizes

---

## Category 6: Games & Immersive

### US-6.1: Full-Screen Game Adaptation
**As a** gamer,
**I want** the game to fill the entire screen on any display,
**so that** I get an immersive experience without black bars.

**Priority**: Must (if app is a game)

**Acceptance Criteria**:
- [ ] Game fills outer display without letterboxing
- [ ] Game fills inner display without letterboxing
- [ ] Controls scale appropriately for each display size
- [ ] Text remains readable on both displays
- [ ] Performance is consistent across both displays
- [ ] Touch input regions adapt to display size

### US-6.2: Pose-Aware Game Controls
**As a** gamer using the device in laptop/tent pose,
**I want** game controls to adapt to the fold position,
**so that** I can use the bottom panel for controls and top panel for the game view.

**Priority**: Could

**Acceptance Criteria**:
- [ ] Controls relocate to bottom panel when in laptop pose
- [ ] Game view fills top panel
- [ ] Transition between poses is smooth (no game interruption)
- [ ] Player can configure control placement preferences

---

## Category 7: Accessibility

### US-7.1: Accessible Vertical Controls
**As a** user with accessibility needs,
**I want** the vertical control rail to work with VoiceOver and assistive technologies,
**so that** I can navigate the app on Duo.

**Priority**: Must

**Acceptance Criteria**:
- [ ] All vertical rail items have descriptive accessibility labels
- [ ] VoiceOver reading order follows the visual top-to-bottom order
- [ ] Focus follows the correct sequence through vertical controls
- [ ] Dynamic Type settings are respected in the vertical rail
- [ ] Switch Control and other input methods work with vertical layout

---

## Quick Reference: Story Selection by App Type

| App Type | Must Stories | Should Stories | Could Stories |
|----------|-------------|---------------|---------------|
| **Social/Messaging** | 1.1, 2.1, 2.2, 4.1, 4.2, 7.1 | 3.1, 5.2, 1.2 | 3.2, 3.3 |
| **Productivity** | 1.1, 2.1, 2.2, 4.1, 4.2, 7.1 | 3.1, 3.2, 2.3 | 3.3, 6.2 |
| **E-Commerce** | 1.1, 1.2, 2.1, 4.1, 4.2, 7.1 | 3.1, 5.2, 2.2 | 1.3, 3.2 |
| **Media/Entertainment** | 1.1, 2.1, 4.1, 5.2, 7.1 | 3.2, 3.3, 1.3 | 6.2 |
| **Games** | 1.1, 6.1, 4.1, 7.1 | 6.2, 1.3 | 3.2 |
| **Camera/Photo** | 1.1, 5.1, 5.2, 4.1, 7.1 | 3.2, 2.1 | 1.3, 3.3 |
| **Maps/Navigation** | 1.1, 2.1, 4.1, 7.1 | 3.2, 1.3, 5.2 | 3.3, 2.3 |
| **Reading/News** | 1.1, 2.1, 4.1, 7.1 | 3.1, 1.3, 5.2 | 3.3 |


# Competitive Analysis: Foldable Device Ecosystems

This document compares the iPhone Duo design approach with Samsung Galaxy Fold
and Google Pixel Fold to provide PMs with competitive context. While this skill
is **exclusively focused on iPhone Duo and Apple HIG**, understanding competitor
approaches helps PMs make informed decisions about feature prioritization and
differentiation.

---

## Executive Comparison

| Dimension | iPhone Duo | Samsung Galaxy Z Fold | Google Pixel Fold |
|-----------|-----------|----------------------|-------------------|
| **Form Factor** | Book-style dual display | Book-style with cover display | Book-style with cover display |
| **Inner Display** | Seamless dual-panel | Single large foldable | Single large foldable |
| **Outer Display** | Full compact phone | Narrow cover screen (Fold 5: wider) | Wide cover screen |
| **Hinge** | Center fold, multi-pose | Center fold, Flex Mode | Center fold, tabletop mode |
| **OS Approach** | Size classes + automatic adaptation | Multi-window, App Continuity | Multi-window, tabletop mode |
| **Developer Effort** | Low (if using standard components) | Medium (explicit fold-aware APIs) | Medium (explicit fold-aware APIs) |
| **Design Philosophy** | Progressive enhancement | Feature maximalism | Clean integration |

---

## 1. Layout & Adaptation Philosophy

### iPhone Duo (Apple)
- **Philosophy**: "You're still designing for iPhone" — adaptive layouts scale
  naturally
- **Mechanism**: Size classes (compact/regular) + safe area insets handle most
  adaptation automatically
- **Developer effort**: Minimal if app already uses Auto Layout / SwiftUI
- **PM takeaway**: Lowest effort for compliant apps; biggest risk for apps with
  fixed layouts

### Samsung Galaxy Z Fold (Samsung/Android)
- **Philosophy**: Multi-window power user experience
- **Mechanism**: Explicit fold-aware APIs, `Jetpack WindowManager`, Activity
  embedding for dual-pane
- **Developer effort**: Moderate; requires explicit opt-in to fold-aware features
- **Unique features**:
  - **Flex Mode**: Bottom half as touchpad/controller when partially folded
  - **Multi-window**: Run two separate apps simultaneously
  - **App Continuity**: State handoff between cover and inner screen
  - **Taskbar**: Persistent bottom taskbar for quick app switching
- **PM takeaway**: Samsung has the most mature foldable ecosystem with features
  Apple is now introducing. Users migrating from Samsung expect these.

### Google Pixel Fold (Google/Android)
- **Philosophy**: Clean, simple fold-aware experience
- **Mechanism**: Same `Jetpack WindowManager` APIs, but with a focus on
  canonical layouts
- **Developer effort**: Similar to Samsung, uses shared Android APIs
- **Unique features**:
  - **Tabletop mode**: Content top, controls bottom when half-folded
  - **Canonical layouts**: Google-defined reference layouts for foldables
  - **Rear camera selfie**: Use high-quality rear camera with outer display as
    viewfinder
- **PM takeaway**: Google's approach is closest to Apple's in philosophy —
  clean, standard, less feature-heavy than Samsung

---

## 2. Navigation Pattern Comparison

| Pattern | iPhone Duo | Samsung Z Fold | Pixel Fold |
|---------|-----------|----------------|------------|
| **Tab bar** | Moves to vertical side rail | Stays at bottom (Android convention) | Stays at bottom |
| **Toolbar** | Moves to vertical side rail | Stays at top (Android convention) | Stays at top |
| **Navigation rail** | System-managed vertical rail | Material 3 NavigationRail (optional) | Material 3 NavigationRail (optional) |
| **Back navigation** | Side rail placement | System back button/gesture | System back button/gesture |
| **Split view** | NavigationSplitView (system) | Activity embedding / SlidingPaneLayout | Same as Samsung |
| **Multi-window** | Split View multitasking | Free-form multi-window | Same as Samsung |

### Key Differences for PMs

> **iPhone Duo's vertical control rail is unique**. Samsung and Pixel both keep
> navigation at the bottom of the screen (Android convention). Apple moves
> controls to the side to maximize vertical content space. This is the most
> significant UX difference between the platforms.

**Implication**: If your app is cross-platform, the Duo version will have a
fundamentally different navigation paradigm than the Android foldable version.
This requires separate UX thinking, not just responsive scaling.

---

## 3. Fold Awareness Comparison

| Feature | iPhone Duo | Samsung Z Fold | Pixel Fold |
|---------|-----------|----------------|------------|
| **Fold detection** | Safe area insets | WindowManager FoldingFeature | WindowManager FoldingFeature |
| **Content avoidance** | Automatic via reserved regions | Manual — developer checks fold bounds | Manual — developer checks fold bounds |
| **Flex/Laptop mode** | Supported via arrangement views | Flex Mode — explicit API | Tabletop mode — explicit API |
| **Tent mode** | Supported as a pose | Supported but no dedicated API | Not emphasized |
| **Fold animation** | System-managed transitions | Developer-managed | Developer-managed |

### Key Differences for PMs

> **Apple automates more**. On Samsung and Pixel, developers explicitly check
> for fold state and adjust. On iPhone Duo, the system handles most of this
> through safe areas and arrangement views. This means:
> - Less engineering effort for Apple conversion
> - But also less granular control for custom fold experiences
> - Samsung's Flex Mode has years of user expectation (camera preview on top,
>   controls on bottom)

---

## 4. Multitasking Comparison

| Feature | iPhone Duo | Samsung Z Fold | Pixel Fold |
|---------|-----------|----------------|------------|
| **Split screen** | Split View (2 apps) | Multi-window (up to 3 apps) | Multi-window (2 apps) |
| **Floating window** | No | Yes (pop-up view) | No (removed in Pixel 9) |
| **Drag & drop** | Between apps in Split View | Between apps and windows | Between apps in split |
| **App pairs** | Not explicitly supported | Edge Panel app pairs | Not supported |

### Key Differences for PMs

> Samsung's multitasking is significantly more complex. iPhone Duo simplifies to
> standard Split View, which means your app shares the screen with one other
> app. Design for half-screen scenarios.

---

## 5. Camera & Media Comparison

| Feature | iPhone Duo | Samsung Z Fold | Pixel Fold |
|---------|-----------|----------------|------------|
| **Cover screen camera** | Always visible, corner-mounted | Cover screen camera | Cover screen camera |
| **Inner camera** | Behind-display, hidden until active | Under-display or pinhole | Pinhole |
| **Rear selfie** | Not mentioned in HIG | Supported (use main camera + cover preview) | Supported (signature feature) |
| **Camera reserved region** | Dynamic — inner cam appears only when active | Fixed pinhole | Fixed pinhole |

### Key Differences for PMs

> iPhone Duo's behind-display inner camera is unique — it only creates a
> reserved region when the camera is active. This is cleaner than Samsung/Pixel's
> permanent camera cutout on the inner display.

---

## 6. App Ecosystem Maturity

| Metric | iPhone Duo | Samsung Z Fold | Pixel Fold |
|--------|-----------|----------------|------------|
| **Market presence** | New (2026) | 5th generation (since 2019) | 2nd generation (since 2023) |
| **Optimized apps** | Growing (iOS ecosystem adapts fast) | ~1000+ optimized (Samsung claims) | Limited (relies on Android adaptive) |
| **Developer tools** | SwiftUI/UIKit (mature) | Jetpack WindowManager (mature) | Same as Samsung |
| **Design guidelines** | New HIG section (Sept 2026) | Established fold UX guidelines | Material Design foldable guidance |
| **User expectations** | Unestablished (new device) | High (5 years of foldable use) | Moderate |

### PM Implications

1. **First-mover advantage on iOS**: Early Duo-optimized apps will stand out in
   the App Store. Samsung's ecosystem is crowded; Apple's is fresh.
2. **Lower user expectations**: Duo users won't have preconceived foldable
   expectations (unlike Samsung users). You have room to define the experience.
3. **BUT Samsung users who switch will expect**: Flex Mode-like features,
   multi-window, app continuity. Plan for this feedback.

---

## 7. Differentiation Opportunities

### What iPhone Duo Does Better (Leverage These)
1. **Automatic adaptation**: Standard SwiftUI/UIKit apps resize gracefully with
   minimal code changes
2. **Vertical control rail**: More content space than Android's bottom-bar
   approach
3. **Behind-display camera**: Cleaner inner display without permanent cutout
4. **System-level fold handling**: Less developer effort for fold-aware layouts
5. **Apple ecosystem integration**: Continuity with Mac, iPad, Apple Watch

### What Competitors Do Better (Address These)
1. **Samsung Flex Mode**: Years of established UX for half-folded use → Consider
   arrangement views for similar experiences
2. **Samsung multi-window**: Power users expect to run multiple apps → Your
   app should handle Split View gracefully
3. **Pixel rear selfie**: Popular camera feature → Not available on Duo but
   inner camera quality may compensate
4. **Samsung app pairs**: Quick launch of two apps together → Not an Apple
   feature; focus on single-app excellence

---

## 8. Cross-Platform Conversion Strategy

If your app exists on both iOS and Android, consider this approach:

### Shared Decisions
- Content hierarchy (what to show side-by-side) is the same across platforms
- Information architecture changes apply equally
- User research on foldable usage patterns applies to both

### Platform-Specific Decisions
| Decision | iPhone Duo | Android Foldable |
|----------|-----------|-----------------|
| Navigation pattern | Vertical rail (Apple mandate) | Bottom nav + optional NavRail |
| Fold-aware layout | Arrangement views, safe areas | WindowManager FoldingFeature |
| Split view API | NavigationSplitView | Activity embedding |
| Multitasking | Split View only | Multi-window, pop-up |
| Design system | Apple HIG + SF Symbols | Material Design 3 |

### PM Recommendations
1. **Do the content strategy once**: Decide which content pairs well for split
   view on both platforms simultaneously
2. **Design navigation separately**: The vertical rail on Duo is fundamentally
   different from Android navigation patterns
3. **Test on real devices**: Foldable UX cannot be fully validated on simulators;
   budget for device acquisition
4. **Sequence wisely**: If your Android app already supports foldables, you have
   a content blueprint. If not, starting with iPhone Duo (less effort due to
   system automation) may be more efficient.

---

## 9. iPad vs. iPhone Duo Inner Display

Many stakeholders will ask: "Isn't the Duo inner display just a small iPad?"
Here's the comparison:

| Dimension | iPad (10th gen) | iPhone Duo (Inner) |
|-----------|----------------|-------------------|
| **Display size** | 10.9" | ~7.5" (estimated) |
| **Width class** | Regular (always) | Regular (open) / Compact (closed) |
| **Multitasking** | Slide Over, Split View, Stage Manager | Split View only |
| **Navigation** | Standard bottom tab or sidebar | Vertical side rail (unique to Duo) |
| **Keyboard** | Full-size floating or docked | Standard + Laptop mode (fold split) |
| **Use context** | Desk, couch, dedicated usage | On-the-go, pocketable, quick glances |

### Key Differences for PMs
1. **iPad is always "open"** — users expect full-featured layouts at all times.
   Duo requires TWO layout strategies (compact outer + regular inner).
2. **iPad sidebar ≠ Duo side rail** — iPad sidebar is a content navigation
   pattern. Duo's side rail is a system-level control surface.
3. **iPad apps that already use `NavigationSplitView` are 80% Duo-ready** —
   This is the strongest indicator of conversion readiness.
4. **Don't ship the iPad layout on Duo** — The inner display is smaller than
   iPad. Layouts designed for 10.9" will feel cramped at ~7.5". Adjust
   spacing, font sizes, and content density.

---

## 10. Best-in-Class Foldable App Case Studies

Real-world examples of apps that handle foldable devices well on Android,
offering lessons for iPhone Duo conversion.

### 10.1 Microsoft Outlook (Samsung Fold)
**What they did right:**
- Email list + reading pane split view on inner display
- Compose window in laptop mode (content top, keyboard bottom)
- Calendar view expands to show week view on inner display
- Seamless state transition between cover and inner display

**Lesson for Duo**: Email/productivity apps should prioritize Split View above
all other features. It's the single biggest UX win.

### 10.2 YouTube (Samsung Fold / Pixel Fold)
**What they did right:**
- Video plays at native aspect ratio (no stretching)
- Flex Mode: video on top half, controls + comments on bottom half
- Landscape inner display shows video + related videos side-by-side
- PiP continues when folding the device

**Lesson for Duo**: Video apps should map Flex Mode → Laptop Mode directly.
Use ArrangementView for the video + comments split.

### 10.3 Google Maps (Pixel Fold)
**What they did right:**
- Map expands to fill inner display
- Search results appear as a persistent side panel (not a bottom sheet)
- Turn-by-turn navigation adapts to wider display
- Tabletop mode shows map on top, directions on bottom

**Lesson for Duo**: Map apps gain the most from Split View (map + list).
Bottom sheets should be reviewed — they may interact poorly with the fold.

### 10.4 Samsung Notes (Samsung Fold)
**What they did right:**
- Note list + editor split view on inner display
- Drawing canvas expands to full inner display
- Flex Mode: canvas on top, tool palette on bottom
- Multi-window: Notes + Browser side-by-side for research

**Lesson for Duo**: Note/document apps should use `NavigationSplitView` for
list + editor, and ArrangementView for canvas + tools.

### 10.5 Spotify (Samsung Fold)
**What they did right:**
- Now Playing expands to show lyrics + album art on inner display
- Queue management visible alongside player controls
- Flex Mode: album art on top, controls on bottom
- Cover display shows compact Now Playing widget

**Lesson for Duo**: Music apps should use Arrangement View (album art + lyrics)
and optimize outer display for glanceable Now Playing.


# App Category Guide: iPhone Duo Conversion Profiles

Pre-built audit profiles organized by app vertical. Use this guide to quickly
identify the most impactful Duo conversion areas for a specific type of app,
rather than scanning a generic checklist.

---

## How to Use This Guide

1. Identify your app's primary category from the list below
2. Read the "Top Duo Concerns" — these are the areas most likely to have 🔴
   Breaking issues for this category
3. Review the "Primary Wow Factor" — this is the single biggest UX opportunity
   on Duo for this category
4. Use the "Audit Focus" checklist to prioritize which PM Checklist items to
   evaluate first

---

## 1. Social Media / Feed Apps
*Examples: Facebook, X (Twitter), Instagram, Threads, LinkedIn*

### Top 3 Duo Concerns
| # | Concern | Why It Breaks |
|---|---------|---------------|
| 1 | **Feed posts stretch to full width** | On the wide inner display, a single-column feed with full-width images becomes comically oversized. Text lines become unreadably long. |
| 2 | **Vertical video (Reels/Shorts) gets pillarboxed** | 9:16 content on a near-square inner display creates huge black bars on both sides. |
| 3 | **Tab bar text truncation** | Social apps often have 5+ tabs with text labels (Home, Search, Reels, Shop, Profile). All will truncate in the vertical side rail. |

### Primary Wow Factor
**2-Column Masonry Feed + Arrangement View for Video**
- Feed: Switch from single-column to 2-column card layout (like Pinterest/iPad) on the inner display. Users see 2× more content per scroll.
- Video: Use Arrangement View to show video on one side and comments/reactions on the other. No more UI overlaying the creator's content.

### Audit Focus (Priority Order)
1. ☐ Measure post/card max-width behavior on wide screens
2. ☐ Identify all vertical video (9:16) playback surfaces
3. ☐ Count tab bar items and check for text labels
4. ☐ Check Stories tray horizontal scroll behavior
5. ☐ Evaluate comment/reply sheet behavior on wide display

### Duo Layout Recommendation
```
┌─────────────────────────────────────────────┐
│  INNER DISPLAY (Open)                       │
│                                             │
│  ┌─────────────┐  ┌─────────────┐           │
│  │  Post Card  │  │  Post Card  │  ← 2-col  │
│  │  (image +   │  │  (image +   │    feed   │
│  │   text)     │  │   text)     │           │
│  ├─────────────┤  ├─────────────┤           │
│  │  Post Card  │  │  Post Card  │           │
│  └─────────────┘  └─────────────┘           │
└─────────────────────────────────────────────┘

┌──────────────────────────────────────────────┐
│  REELS MODE (Arrangement View)               │
│                                              │
│  ┌──────────────────┐ ┌───────────────────┐  │
│  │                  │ │  Comments          │  │
│  │   9:16 Video     │ │  ─────────────    │  │
│  │   (native size)  │ │  Like · Reply     │  │
│  │                  │ │  ─────────────    │  │
│  │                  │ │  Related Reels    │  │
│  └──────────────────┘ └───────────────────┘  │
└──────────────────────────────────────────────┘
```

---

## 2. Messaging / Chat Apps
*Examples: WhatsApp, Telegram, Signal, iMessage, Slack, Discord*

### Top 3 Duo Concerns
| # | Concern | Why It Breaks |
|---|---------|---------------|
| 1 | **Chat bubbles stretch too wide** | On the inner display, chat bubbles without max-width become hard to read (line lengths exceed comfortable reading width of ~60-75 characters). |
| 2 | **Push navigation loses context** | Current flow: tap chat → full screen thread → tap back → return to list. On Duo, this wastes half the screen. |
| 3 | **Keyboard + fold interaction** | In laptop mode, the fold sits between the chat thread and keyboard. Input bar positioning must respect the fold region. |

### Primary Wow Factor
**Split View: Chat List + Active Thread**
The #1 most natural Split View candidate. Left pane shows conversation list, right pane shows the active thread. Users can switch between chats without ever navigating "back." This is the killer use case for foldable messaging.

### Audit Focus (Priority Order)
1. ☐ Check if app uses `NavigationSplitView` / `UISplitViewController`
2. ☐ Measure chat bubble max-width constraints
3. ☐ Test keyboard behavior with custom input bars
4. ☐ Evaluate group chat / channel list hierarchy depth
5. ☐ Check media message (photo/video/voice) layout on wide display

### Duo Layout Recommendation
```
┌──────────────────────────────────────────────┐
│  INNER DISPLAY (Split View)                  │
│                                              │
│  ┌──────────────┐ ┌──────────────────────┐   │
│  │ Chat List    │ │ Active Thread        │   │
│  │              │ │                      │   │
│  │ ● John  2m  │ │  Hey, are you free?  │   │
│  │ ► Sarah 5m  │ │         Sure! 👍     │   │
│  │   Mike  1h  │ │  Great, see you at   │   │
│  │   Team  3h  │ │  the cafe at 3pm     │   │
│  │              │ │                      │   │
│  │              │ │ [Message input bar]  │   │
│  └──────────────┘ └──────────────────────┘   │
└──────────────────────────────────────────────┘
```

---

## 3. Productivity / Document Apps
*Examples: Notes, Google Docs, Notion, Todoist, Things 3*

### Top 3 Duo Concerns
| # | Concern | Why It Breaks |
|---|---------|---------------|
| 1 | **No sidebar on compact width** | Many productivity apps hide the sidebar/file browser behind a hamburger menu. This is a missed opportunity on the inner display. |
| 2 | **Editor toolbar overflow** | Rich text editors often have 10+ toolbar items (Bold, Italic, List, Image, etc.). These will aggressively overflow in the vertical rail. |
| 3 | **Form/input state loss on resize** | Opening/closing the device while editing a form or document must not lose unsaved input. |

### Primary Wow Factor
**Laptop Mode: Document Preview + Full Keyboard**
When the device is partially folded at ~90°, the top half shows the document in reading/preview mode, and the bottom half becomes a full-width typing surface with rich formatting toolbar. This mimics a real laptop experience for content creation.

### Audit Focus (Priority Order)
1. ☐ Check sidebar/drawer pattern (hamburger vs persistent)
2. ☐ Count editor toolbar items and identify priority actions
3. ☐ Test state restoration for in-progress edits
4. ☐ Evaluate document/note list → editor navigation pattern
5. ☐ Check if app supports iPad multitasking (strong indicator of Duo readiness)

### Duo Layout Recommendation
```
┌──────────────────────────────────────────────┐
│  LAPTOP MODE (Partially Folded ~90°)         │
│                                              │
│  ┌──────────────────────────────────────┐    │
│  │  Document Preview                    │    │
│  │  ─────────────────────────────       │    │
│  │  Your text appears here in a         │    │
│  │  beautiful reading layout...         │    │
│  ├──────────── FOLD ────────────────┤    │
│  │  [B] [I] [U] [Link] [List] [📎]     │    │
│  │  ┌──────────────────────────────┐    │    │
│  │  │  Full-width keyboard area    │    │    │
│  │  └──────────────────────────────┘    │    │
│  └──────────────────────────────────────┘    │
└──────────────────────────────────────────────┘
```

---

## 4. E-Commerce / Shopping Apps
*Examples: Amazon, Shopee, Lazada, Zalora, Temu*

### Top 3 Duo Concerns
| # | Concern | Why It Breaks |
|---|---------|---------------|
| 1 | **Product grid odd columns** | Most e-commerce apps use 2-column grids. On the wider inner display, they may jump to 3 columns — which gets bisected by the fold when partially open. |
| 2 | **Product detail page wastes space** | Product images that stack vertically above description text will leave huge gaps on the wide inner display. |
| 3 | **Checkout flow on wide display** | Forms and payment flows designed for narrow screens may look awkward when stretched. |

### Primary Wow Factor
**Product Image + Details Side-by-Side**
On the inner display, show the product image gallery on the left and the product details (price, reviews, Add to Cart) on the right. Users can swipe through photos while reading reviews simultaneously — no more scrolling up and down.

### Audit Focus (Priority Order)
1. ☐ Check product grid column count behavior on wide screens
2. ☐ Evaluate product detail page layout (stacked vs. side-by-side)
3. ☐ Test checkout form on wide display (max-width, centering)
4. ☐ Check image carousel/gallery behavior
5. ☐ Evaluate search results page grid layout

### Duo Layout Recommendation
```
┌──────────────────────────────────────────────┐
│  PRODUCT DETAIL (Split View)                 │
│                                              │
│  ┌──────────────────┐ ┌──────────────────┐   │
│  │                  │ │ Product Name     │   │
│  │   [Product       │ │ ⭐⭐⭐⭐½ (2.3k)  │   │
│  │    Image         │ │                  │   │
│  │    Gallery]      │ │ $49.99  $79.99   │   │
│  │                  │ │                  │   │
│  │  ● ● ● ○ ○      │ │ [Add to Cart]    │   │
│  │                  │ │ [Buy Now]        │   │
│  └──────────────────┘ └──────────────────┘   │
└──────────────────────────────────────────────┘
```

---

## 5. Video / Streaming Apps
*Examples: YouTube, Netflix, TikTok, Disney+, Twitch*

### Top 3 Duo Concerns
| # | Concern | Why It Breaks |
|---|---------|---------------|
| 1 | **Aspect ratio mismatch** | 16:9 landscape videos get letterboxed vertically. 9:16 vertical videos get pillarboxed horizontally. Neither fills the inner display well. |
| 2 | **Full-screen player assumptions** | Many video players assume they own the entire screen. On Duo, they need to coexist with other UI. |
| 3 | **Player controls overlap fold** | Play/pause, scrubber, and volume controls centered at the bottom may land on the fold region when partially open. |

### Primary Wow Factor
**Tent Mode: Hands-Free Viewing**
Place the device in tent mode on a table. The outer display plays the video while the inner display shows playback controls or is turned off to save battery. Perfect for watching while cooking, eating, or working out.

### Audit Focus (Priority Order)
1. ☐ Check all video aspect ratios supported (16:9, 9:16, 1:1, 4:3)
2. ☐ Test player controls in partially folded state
3. ☐ Evaluate PiP (Picture-in-Picture) support
4. ☐ Check if video + metadata (comments, description) can split
5. ☐ Test background audio/video behavior on fold

---

## 6. Maps / Navigation Apps
*Examples: Google Maps, Apple Maps, Waze, Grab, Uber*

### Top 3 Duo Concerns
| # | Concern | Why It Breaks |
|---|---------|---------------|
| 1 | **Map renders at wrong density** | Map tiles rendered for a phone-size viewport may appear too zoomed-in on the wider inner display. |
| 2 | **Bottom sheet overlap with fold** | Map apps heavily rely on bottom sheets for place details. These may interact poorly with the fold region. |
| 3 | **Turn-by-turn navigation on fold** | Navigation mode typically uses the full screen. The fold could bisect the map or directions. |

### Primary Wow Factor
**Map + List/Details Split View**
Left side: Full interactive map. Right side: Search results list, place details, or turn-by-turn directions. Users can browse the list while seeing all pins on the map simultaneously.

### Audit Focus (Priority Order)
1. ☐ Check MapKit / Google Maps SDK viewport behavior on wide screens
2. ☐ Evaluate bottom sheet heights and fold interaction
3. ☐ Test search results overlay on wider display
4. ☐ Check turn-by-turn navigation in all poses
5. ☐ Evaluate ride-sharing pickup/dropoff UI on wide display

---

## 7. Health / Fitness Apps
*Examples: Apple Health, Strava, MyFitnessPal, Nike Run Club*

### Top 3 Duo Concerns
| # | Concern | Why It Breaks |
|---|---------|---------------|
| 1 | **Dashboard widget grid** | Health apps use dense grids of metric cards. Odd column counts will be bisected by the fold. |
| 2 | **Chart readability** | Charts designed for compact width may become overly stretched on the inner display. |
| 3 | **Active workout mode** | During exercise, users may prefer the outer display for glanceable metrics. State must sync. |

### Primary Wow Factor
**Workout Split: Live Metrics + Route Map**
During an active workout, show real-time stats (pace, heart rate, distance) on one side and the live route map on the other. No more tapping between screens while running.

---

## 8. Finance / Banking Apps
*Examples: Banking apps, PayPal, Robinhood, Wise*

### Top 3 Duo Concerns
| # | Concern | Why It Breaks |
|---|---------|---------------|
| 1 | **Biometric auth on fold/unfold** | Apps that require Face ID on every screen transition may trigger unnecessary re-authentication when opening/closing the device. |
| 2 | **Sensitive data on wide display** | Account balances and transaction details stretched across the full inner display are more visible to people nearby. |
| 3 | **Transaction list → detail pattern** | This is a classic master-detail but banking apps rarely implement Split View due to security concerns. |

### Primary Wow Factor
**Account Overview + Transaction Detail Split**
Left: Account summary with balances. Right: Transaction detail or spending analytics chart. Secure by design — both panes require the same auth level.

---

## Quick Reference Matrix

| Category | #1 Breaking Risk | #1 Wow Factor | Effort |
|----------|-----------------|---------------|--------|
| Social/Feed | Feed post width | 2-column Masonry | Large |
| Messaging | Chat bubble width | Chat List + Thread Split | Medium |
| Productivity | Toolbar overflow | Laptop Mode Compose | Medium |
| E-Commerce | Grid odd columns | Product Image + Details | Medium |
| Video/Streaming | Aspect ratio | Tent Mode Viewing | Large |
| Maps | Bottom sheet + fold | Map + List Split | Medium |
| Health/Fitness | Dashboard grid | Workout Stats + Map | Medium |
| Finance | Biometric re-auth | Account + Transactions | Small |


# iPhone Duo Visual Patterns: Before → After

Reference diagrams showing how common UI patterns transform on iPhone Duo.
Use these to communicate layout changes to stakeholders, designers, and
engineers.

---

## Pattern 1: Bottom Tab Bar → Vertical Side Rail

The most universal change. Affects virtually every app.

### Before (Standard iPhone)
```
┌─────────────────────────────┐
│  ← Title              ⋯    │  ← Navigation Bar (top)
│─────────────────────────────│
│                             │
│                             │
│        Content Area         │
│                             │
│                             │
│                             │
│─────────────────────────────│
│  🏠    🔍    ➕    🔔    👤  │  ← Tab Bar (bottom)
└─────────────────────────────┘
```

### After (iPhone Duo — Outer Display)
```
┌───┬──────────────────────┐
│ ← │                      │
│───│                      │
│ 🏠│                      │
│ 🔍│     Content Area     │
│ ➕│                      │
│ 🔔│                      │
│ 👤│                      │
│   │                      │
└───┴──────────────────────┘
  ↑
  Vertical Side Rail
  (icons only, no text)
```

### Key Change
- Tab bar items move from horizontal bottom strip to vertical side rail
- Text labels drop off — **icons must be self-explanatory**
- Items ordered top-to-bottom by priority
- 5+ items may overflow into a system "⋯" menu

---

## Pattern 2: Push Navigation → Split View

Applies to any app with list → detail flow (Mail, Chat, Settings, E-Commerce).

### Before (Standard iPhone)
```
Screen 1 (List)              Screen 2 (Detail)
┌─────────────────┐          ┌─────────────────┐
│  ← Inbox        │  tap →   │  ← Back         │
│─────────────────│          │─────────────────│
│ ● John    2m    │ ──────►  │ From: John      │
│   Sarah   5m    │          │ Subject: Hey    │
│   Mike    1h    │          │                 │
│   Team    3h    │          │ Hi, are you     │
│                 │          │ free tomorrow?  │
└─────────────────┘          └─────────────────┘
  (user must tap               (user must tap
   "Back" to return)            to see list)
```

### After (iPhone Duo — Inner Display, Split View)
```
┌───┬─────────────────┬──────────────────────┐
│ ← │ Inbox           │ From: John           │
│───│─────────────────│──────────────────────│
│ 📥│ ● John    2m    │ Subject: Hey         │
│ 📤│   Sarah   5m    │                      │
│ 🗑│   Mike    1h    │ Hi, are you          │
│ ⋯│   Team    3h    │ free tomorrow?       │
│   │                 │                      │
│   │                 │ [Reply] [Forward]    │
└───┴─────────────────┴──────────────────────┘
       List Pane             Detail Pane
       (always visible)      (updates on tap)
```

### Key Change
- Both list and detail visible simultaneously
- No "back" button needed — tap another list item to switch
- Side rail holds navigation + toolbar items
- On closing device → collapses back to single-pane push navigation

---

## Pattern 3: Full-Width Feed → Multi-Column Layout

Applies to social media, news, and content discovery apps.

### Before (Standard iPhone)
```
┌─────────────────────────────┐
│ ┌─────────────────────────┐ │
│ │ 👤 User Name    · 2h    │ │
│ │ ┌─────────────────────┐ │ │
│ │ │                     │ │ │
│ │ │   Full-width image  │ │ │  ← Image stretches
│ │ │   (takes entire     │ │ │     100% of screen
│ │ │    screen width)    │ │ │
│ │ │                     │ │ │
│ │ └─────────────────────┘ │ │
│ │ ❤️ 234  💬 45  ↗️ 12    │ │
│ │ Long caption text that  │ │
│ │ wraps at screen edge... │ │
│ └─────────────────────────┘ │
│ ┌─────────────────────────┐ │
│ │ 👤 Another Post         │ │
│ │ ...                     │ │
└─────────────────────────────┘
```

### After (iPhone Duo — Inner Display, 2-Column)
```
┌───┬───────────────────────────────────────┐
│ 🏠│ ┌────────────────┐ ┌────────────────┐ │
│ 🎬│ │ 👤 User  · 2h  │ │ 👤 User2 · 5h │ │
│ 👥│ │ ┌────────────┐ │ │ ┌────────────┐ │ │
│ 🔔│ │ │  Image     │ │ │ │  Image     │ │ │
│ ☰│ │ │  (half     │ │ │ │  (half     │ │ │
│   │ │ │   width)   │ │ │ │   width)   │ │ │
│   │ │ └────────────┘ │ │ └────────────┘ │ │
│   │ │ ❤️ 234 💬 45   │ │ ❤️ 89 💬 12   │ │
│   │ │ Caption text   │ │ Caption text   │ │
│   │ └────────────────┘ └────────────────┘ │
│   │ ┌────────────────┐ ┌────────────────┐ │
│   │ │ Next post...   │ │ Next post...   │ │
└───┴───────────────────────────────────────┘
```

### Key Change
- Feed switches from 1-column to 2-column card layout
- Images are constrained to card width (not full screen)
- Text wraps within card boundaries — much more readable
- Users see 2× more content per viewport
- **Fallback**: If 2-column is too complex, at minimum set `max-width: 600pt` and center the single column

---

## Pattern 4: Vertical Video (9:16) → Arrangement View

Applies to Reels, Shorts, TikTok, and any vertical video player.

### Before (Standard iPhone — Full Screen)
```
┌─────────────────────────────┐
│                             │
│                             │
│     9:16 Vertical Video     │
│     fills entire screen     │
│                             │
│                    ❤️ 21K   │  ← Buttons overlay
│                    💬 7K    │     on top of video
│                    ↗️ 12    │
│                    💬 Send  │
│                             │
│ @creator · Description...   │
│ 🎵 Original Sound           │
└─────────────────────────────┘
```

### After (iPhone Duo — Inner Display, Arrangement View)
```
┌───┬──────────────────┬─────────────────────┐
│ 🏠│                  │  Comments           │
│ 🎬│                  │  ───────────────    │
│ 👥│  9:16 Video      │  @user1: Amazing!  │
│ 🔔│  (native size,   │  @user2: 🔥🔥🔥    │
│ 👤│   NO overlays)   │  @user3: Tutorial? │
│   │                  │  ───────────────    │
│   │                  │  ❤️ 21K  ↗️ 12     │
│   │                  │  ───────────────    │
│   │                  │  Related Reels:    │
│   │                  │  [thumb] [thumb]   │
│   │  @creator        │  [thumb] [thumb]   │
└───┴──────────────────┴─────────────────────┘
       Video Pane           Interaction Pane
       (clean, no UI)       (comments, actions)
```

### Key Change
- Video plays at native 9:16 ratio without pillarbox black bars
- All interaction UI (likes, comments, share) moves to a dedicated right pane
- Users can read/write comments without the UI covering the video
- On closing device → returns to standard full-screen overlay mode

---

## Pattern 5: Laptop Mode (Partially Folded ~90°)

Applies to productivity, messaging, and content creation apps.

### Laptop Mode Layout
```
┌──────────────────────────────────────┐
│                                      │
│          CONTENT DISPLAY             │
│    (document, chat thread, video,    │
│     or camera viewfinder)            │
│                                      │
│                                      │
├════════════════ FOLD ════════════════┤
│                                      │
│          CONTROLS / INPUT            │
│    (keyboard, toolbar, media         │
│     picker, or game controls)        │
│                                      │
└──────────────────────────────────────┘
```

### Use Cases by App Type
| App Type | Top Half (Display) | Bottom Half (Controls) |
|----------|-------------------|----------------------|
| **Messaging** | Chat thread (scrollable) | Keyboard + emoji picker + attachment bar |
| **Camera** | Viewfinder preview | Shutter button + mode selector + gallery |
| **Video Call** | Remote participant video | Self-view + mute/camera/hang-up controls |
| **Document Editor** | Document preview/reading | Formatting toolbar + keyboard |
| **Music** | Album art + lyrics | Playback controls + queue |

---

## Pattern 6: Tent Mode (Standing on Edges)

Applies to video, presentation, and shared-viewing apps.

### Tent Mode Layout
```
         ┌─────────────────┐
        ╱                   ╲
       ╱   OUTER DISPLAY     ╲
      ╱    (facing viewer)    ╲
     ╱                         ╲
    ╱   Shows: video playback,  ╲
   ╱    presentation slides,     ╲
  ╱     photo slideshow,          ╲
 ╱      or event info/QR code     ╲
╱                                   ╲
─────────── table surface ───────────

Inner display faces DOWN (off / controls only)
```

### Use Cases
| Scenario | Outer Display Shows | Inner Display |
|----------|--------------------|-----------------------|
| **Cooking** | Recipe video playing | Off (saves battery) |
| **Presentation** | Slides for audience | Speaker notes (private) |
| **Gathering** | Event QR code / schedule | Admin controls |
| **Music** | Album art + now playing | Queue management |

---

## Pattern 7: Fold-Aware Grid (Even Columns)

Applies to any app with grid/collection views (photos, products, settings).

### Before (Odd Columns — BROKEN)
```
┌──────────────────────────────────────────┐
│  ┌──────┐  ┌──────┐  ┌──────┐           │
│  │ Item │  │ Item │  │ Item │  ← 3 cols │
│  └──────┘  └──────┘  └──────┘           │
│  ┌──────┐  ┌───╫──┐  ┌──────┐           │
│  │ Item │  │ It╫  │  │ Item │           │
│  └──────┘  └───╫──┘  └──────┘           │
│                ╫                         │
│           FOLD LINE                      │
│    (bisects middle column! 🔴)           │
└──────────────────────────────────────────┘
```

### After (Even Columns — CORRECT)
```
┌──────────────────────────────────────────┐
│  ┌──────┐  ┌──────┐ ║ ┌──────┐ ┌──────┐ │
│  │ Item │  │ Item │ ║ │ Item │ │ Item │ │
│  └──────┘  └──────┘ ║ └──────┘ └──────┘ │
│  ┌──────┐  ┌──────┐ ║ ┌──────┐ ┌──────┐ │
│  │ Item │  │ Item │ ║ │ Item │ │ Item │ │
│  └──────┘  └──────┘ ║ └──────┘ └──────┘ │
│                      ║                    │
│                 FOLD LINE                 │
│    (acts as natural divider ✅)           │
└──────────────────────────────────────────┘
```

### Rule
> **Always use EVEN column counts (2, 4, 6) on the inner display when the
> device is partially folded.** The fold acts as a natural gutter between
> the two halves.

---

## Quick Reference: Which Pattern Applies?

| If your app has... | Apply Pattern |
|--------------------|---------------|
| Bottom tab bar | Pattern 1 (Vertical Rail) |
| List → Detail navigation | Pattern 2 (Split View) |
| Content feed (social, news) | Pattern 3 (Multi-Column) |
| Vertical video (Reels/Shorts) | Pattern 4 (Arrangement View) |
| Text input / content creation | Pattern 5 (Laptop Mode) |
| Hands-free viewing scenarios | Pattern 6 (Tent Mode) |
| Photo/product grids | Pattern 7 (Even Columns) |


# iPhone Duo Audit Report — Output Template

Use this standardized format for all Phase 1 App Audit outputs. This ensures
consistent, comparable reports across different apps and AI tools.

---

## Template

```markdown
# iPhone Duo Conversion — Phase 1 App Audit Report

**Product**: [App Name]
**Input Analyzed**: [N] UI Screenshots ([list screen names])
**Audit Date**: [Date]
**Target Platform**: iPhone Duo (iOS 26+)

---

## 📊 Executive Summary

[1-2 paragraphs summarizing the app's overall Duo readiness.
Mention the most critical breaking issue and the biggest opportunity.]

**Overall Readiness Rating**: [Choose one]
- 🟢 **Duo-Ready** (0 🔴, ≤2 🟡): Ship as-is, enhance later
- 🟡 **Needs Work** (1–3 🔴 or 3+ 🟡): Fix breaking issues before launch
- 🔴 **Major Rework** (4+ 🔴): Significant redesign required

**Counts**: [X] 🔴 Breaking, [Y] 🟡 Suboptimal, [Z] 🟢 Compatible

---

## 📱 Screen-by-Screen Analysis

### Screen 1: [Screen Name]
*Current UI: [Brief description of the screen's current layout]*

| Element | Finding | Severity | Recommendation |
|---------|---------|----------|----------------|
| [UI Element] | [What's wrong/right] | 🔴/🟡/🟢 | [Specific fix] |
| [UI Element] | [What's wrong/right] | 🔴/🟡/🟢 | [Specific fix] |

[Repeat for each screen analyzed]

---

## 📋 Category Scoring Matrix

| Category | 🔴 Breaking | 🟡 Suboptimal | 🟢 Compatible |
|----------|-------------|---------------|---------------|
| Layout & Responsiveness | [count] | [count] | [count] |
| Navigation & Controls | [count] | [count] | [count] |
| Content Hierarchy | [count] | [count] | [count] |
| Media & Camera | [count] | [count] | [count] |
| State & Continuity | [count] | [count] | [count] |
| Games & Immersive | [count] | [count] | [count] |
| **Total** | **[X]** | **[Y]** | **[Z]** |

---

## 🚀 Top 3 "Wow Factor" Opportunities

1. **[Feature Name]**: [1-2 sentence description of the opportunity
   and why it would impress users/Apple]
2. **[Feature Name]**: [Description]
3. **[Feature Name]**: [Description]

---

## 🔧 Engineering Questions for Tech Lead

Before proceeding to Phase 2 (PRD), share these questions with your
engineering team:

1. [Specific technical question based on audit findings]
2. [Specific technical question]
3. [Specific technical question]

---

## ➡️ Recommended Next Step

[State whether to proceed to Phase 2 PRD, or if additional screenshots
are needed, or if the app needs investigation before proceeding.]
```

---

## Severity Classification Rules

Use these rules to ensure consistent severity ratings across audits:

### 🔴 Breaking (Will malfunction on Duo)
Assign 🔴 when:
- UI element uses hardcoded pixel widths that cannot adapt
- Grid uses odd column count (will be bisected by fold)
- Tab bar has 5+ items with text labels (will truncate in vertical rail)
- Custom navigation bar with hardcoded height
- Content positioned at absolute screen edges (ignores safe areas)
- Any full-screen video at non-standard aspect ratio without adaptation
- App is portrait-locked with no landscape support

### 🟡 Suboptimal (Works but misses Duo capabilities)
Assign 🟡 when:
- App uses push navigation where Split View would be better
- Content fills full width without max-width constraint on inner display
- Toolbar items could benefit from priority ordering but aren't
- Keyboard/input bar doesn't account for fold region
- No secondary content panel where one would improve UX
- Standard components used but not optimized for width

### 🟢 Compatible (Works well, no changes needed)
Assign 🟢 when:
- Uses standard system components (UITabBarController, NavigationSplitView)
- Content uses Auto Layout / SwiftUI layout with flexible constraints
- Already supports iPad multitasking (strong indicator of Duo readiness)
- Images and media use aspect-fit or responsive sizing
- State restoration is implemented for background/foreground transitions


# iPhone Duo Conversion — Engineering Handoff Guide

This document bridges the gap between PM output (PRD, Audit) and Engineering
action. Use it to translate PM findings into specific technical tasks.

---

## How to Use This Document

1. **After Phase 2 (PRD)**: PM shares the Audit Report + PRD with the
   Engineering Lead.
2. **Engineering Lead reviews this document** alongside the PRD to create
   Jira tickets / technical tasks.
3. **Each section maps to a PRD requirement** and provides the specific
   API, pattern, or code change needed.

---

## 1. Vertical Side Rail Migration

### What PM Said
> "Tab bar and toolbar need to work in vertical layout."

### What Engineering Needs to Do

#### If using SwiftUI:
```swift
// TabView automatically adapts to vertical rail on Duo.
// Ensure tab items use Label with SF Symbols:
TabView {
    HomeView()
        .tabItem {
            Label("Home", systemImage: "house.fill")
        }
    SearchView()
        .tabItem {
            Label("Search", systemImage: "magnifyingglass")
        }
}
// ✅ SF Symbols will display correctly in vertical rail
// ❌ Avoid text-only labels — they truncate
```

#### If using UIKit:
```swift
// UITabBarController handles vertical rail automatically.
// Ensure each tab uses an image:
let homeTab = UITabBarItem(
    title: "Home",
    image: UIImage(systemName: "house.fill"),
    selectedImage: UIImage(systemName: "house.fill")
)
// Title may be hidden in vertical mode — icon must be self-explanatory
```

#### Toolbar Priority (Critical):
```swift
// SwiftUI: Set visibility priority for toolbar items
.toolbar {
    ToolbarItem(placement: .primaryAction) {
        Button("Compose", systemImage: "square.and.pencil") { }
    }
    ToolbarItem(placement: .secondaryAction) {
        Button("Filter", systemImage: "line.3.horizontal.decrease") { }
    }
}
// primaryAction = always visible in rail
// secondaryAction = may overflow to ⋯ menu
```

```swift
// UIKit: Set visibility priority
let composeButton = UIBarButtonItem(/* ... */)
composeButton.visibilityPriority = .required  // Always visible
let filterButton = UIBarButtonItem(/* ... */)
filterButton.visibilityPriority = .optional   // May overflow
```

### Checklist
- [ ] Replace all text-only tab items with SF Symbol icons
- [ ] Set `visibilityPriority` for all toolbar items
- [ ] Test overflow menu accessibility
- [ ] Verify tab bar displays correctly on outer display (compact)
- [ ] Verify tab bar displays correctly on inner display (regular)

---

## 2. Split View Implementation

### What PM Said
> "Show list and detail side-by-side on the inner display."

### What Engineering Needs to Do

#### SwiftUI (Preferred):
```swift
NavigationSplitView {
    // Sidebar / List pane
    List(items) { item in
        NavigationLink(value: item) {
            ItemRow(item: item)
        }
    }
    .navigationTitle("Inbox")
} detail: {
    // Detail pane
    if let selectedItem {
        ItemDetailView(item: selectedItem)
    } else {
        Text("Select an item")
    }
}
// Automatically shows split on inner display,
// collapses to stack on outer display
```

#### UIKit:
```swift
let splitVC = UISplitViewController(style: .doubleColumn)
splitVC.setViewController(listVC, for: .primary)
splitVC.setViewController(detailVC, for: .secondary)
// Set preferred display mode:
splitVC.preferredDisplayMode = .oneBesideSecondary
```

### Checklist
- [ ] Identify all push-navigation flows that are master → detail
- [ ] Replace `NavigationStack` with `NavigationSplitView` where applicable
- [ ] Ensure detail pane has a placeholder state ("Select an item")
- [ ] Test state persistence when switching between split and stack modes
- [ ] Verify selected item highlighting in list pane

---

## 3. Arrangement Views (New Duo Pattern)

### What PM Said
> "Show video + comments side-by-side" or "Show map + list together."

### What Engineering Needs to Do

```swift
// ArrangementView is new in iOS 26 for iPhone Duo
ArrangementView(.split) {
    // Primary view (takes priority)
    VideoPlayerView()
} secondary: {
    // Secondary view
    CommentsListView()
}

// Overlay arrangement (layers when flat, side-by-side when folded):
ArrangementView(.overlay) {
    MapView()
} secondary: {
    SearchResultsList()
}
```

### Checklist
- [ ] Identify screens where a secondary view adds value
- [ ] Choose between `.split` and `.overlay` arrangement
- [ ] Ensure both views are independently scrollable
- [ ] Test behavior when closing device (secondary should hide gracefully)
- [ ] Handle state in both views during transitions

---

## 4. Grid Column Adaptation

### What PM Said
> "Photo grid must use even columns to avoid fold bisection."

### What Engineering Needs to Do

```swift
// SwiftUI: Use adaptive grid with minimum item size
LazyVGrid(columns: [
    GridItem(.adaptive(minimum: 150))  // System calculates column count
], spacing: 8) {
    ForEach(items) { item in
        ItemCell(item: item)
    }
}

// To FORCE even columns, calculate based on available width:
let columnCount = max(2, Int(availableWidth / idealItemWidth))
let evenColumnCount = columnCount % 2 == 0 ? columnCount : columnCount - 1
let columns = Array(repeating: GridItem(.flexible()), count: evenColumnCount)
```

### Checklist
- [ ] Audit all grid/collection views in the app
- [ ] Replace fixed column counts with adaptive or calculated even counts
- [ ] Test grid at all display widths (outer compact, inner regular)
- [ ] Verify grid appearance when device is partially folded
- [ ] Ensure grid items maintain proportional sizes

---

## 5. State Persistence Through Fold/Unfold

### What PM Said
> "User must not lose their place when opening/closing the device."

### What Engineering Needs to Do

Opening/closing the device triggers a **size class change** (compact ↔ regular).
This is equivalent to a device rotation. The app must handle this gracefully.

```swift
// SwiftUI: State is automatically preserved if using @State, @StateObject
// VERIFY: No state resets in .onChange(of: horizontalSizeClass)

// UIKit: Implement state restoration
override func encodeRestorableState(with coder: NSCoder) {
    super.encodeRestorableState(with: coder)
    coder.encode(scrollOffset, forKey: "scrollOffset")
    coder.encode(selectedItemID, forKey: "selectedItemID")
}

override func decodeRestorableState(with coder: NSCoder) {
    super.decodeRestorableState(with: coder)
    scrollOffset = coder.decodeFloat(forKey: "scrollOffset")
    selectedItemID = coder.decodeObject(forKey: "selectedItemID") as? String
}
```

### Critical Test Scenarios
- [ ] Open device while scrolled halfway through a list → position preserved
- [ ] Open device while typing in a form → text input retained
- [ ] Open device while playing media → playback continues uninterrupted
- [ ] Open device while a modal/sheet is presented → modal state preserved
- [ ] Close device while in split view → collapses to correct single pane

---

## 6. Safe Area & Fold Region Handling

### What PM Said
> "Content must avoid the fold area and camera regions."

### What Engineering Needs to Do

```swift
// SwiftUI: Safe areas are automatic IF using standard layouts.
// For custom views, read safe area:
GeometryReader { geometry in
    let safeArea = geometry.safeAreaInsets
    // safeArea includes fold region when partially open
    MyCustomView()
        .padding(safeArea)
}

// UIKit: Use safeAreaInsets
override func viewSafeAreaInsetsDidChange() {
    super.viewSafeAreaInsetsDidChange()
    // Relayout content to respect new safe areas
    // (fold region creates additional insets on inner display)
}
```

### Checklist
- [ ] Remove all hardcoded padding/margin values (replace with safe area)
- [ ] Verify no content draws behind the fold region
- [ ] Test with Dynamic Island on outer display
- [ ] Verify custom drawing (Core Graphics, Metal) respects safe areas

---

## 7. Simulator Testing Setup

### Running on iPhone Duo Simulator
```bash
# Open Xcode and select iPhone Duo simulator from the device list
# Or via command line:
xcrun simctl list devices | grep "iPhone Duo"
xcrun simctl boot "iPhone Duo"
```

### Key Simulator Features to Test
1. **Toggle fold state**: Use the simulator controls to open/close/partially fold
2. **Rotate**: Test all orientations in both open and closed states
3. **Multi-window**: Test your app in Split View with another app
4. **Performance**: Profile with Instruments → ensure no frame drops during
   fold/unfold animations

### Recommended Test Matrix
| Pose | Orientation | What to Check |
|------|------------|---------------|
| Closed | Portrait | Vertical rail, compact layout, touch targets |
| Closed | Landscape | Horizontal layout, rail position |
| Open Flat | Portrait | Split view, content hierarchy, grid columns |
| Open Flat | Landscape | Full width behavior, max-width constraints |
| Partially Folded | Book mode | Fold avoidance, content split, grid even columns |
| Partially Folded | Laptop mode | Top/bottom content split, keyboard behavior |

---

## API Quick Reference

| Task | SwiftUI | UIKit |
|------|---------|-------|
| Split View | `NavigationSplitView` | `UISplitViewController` |
| Arrangement View | `ArrangementView` | `UIArrangementViewController` |
| Toolbar Priority | `.toolbar { ToolbarItem(placement:) }` | `UIBarButtonItem.visibilityPriority` |
| Overflow Menu | `ToolbarOverflowMenu` | `additionalOverflowItems` |
| Tab Bar | `TabView` (auto-adapts) | `UITabBarController` (auto-adapts) |
| Safe Areas | `GeometryReader.safeAreaInsets` | `view.safeAreaInsets` |
| Size Class | `@Environment(\.horizontalSizeClass)` | `traitCollection.horizontalSizeClass` |
| Fold Detection | Safe area insets change | `viewSafeAreaInsetsDidChange()` |


# iPhone Duo — QA Testing Guide

Structured testing guide for Quality Assurance teams validating iPhone Duo
app conversions. Covers all device poses, transition scenarios, edge cases,
and regression tests.

---

## 1. Test Environment Setup

### Required Tools
- Xcode with iPhone Duo Simulator (iOS 26+)
- Physical iPhone Duo device (for final validation — simulator cannot fully
  replicate fold haptics and hinge angles)
- Screen recording enabled for bug documentation
- Accessibility Inspector for VoiceOver testing

### Pre-Test Checklist
- [ ] App builds and runs on iPhone Duo simulator
- [ ] Simulator fold controls are accessible (Debug → Simulate Fold)
- [ ] Both outer and inner displays render content
- [ ] No immediate crashes on launch

---

## 2. Pose Testing Matrix

Test the app in every device pose. For each pose, verify:
- Layout renders correctly
- All controls are accessible
- Content is readable
- Touch targets meet 44pt minimum

### 2.1 Closed (Outer Display)
| # | Test Case | Expected Result | Pass/Fail |
|---|-----------|-----------------|-----------|
| 1 | Launch app on outer display | App renders in compact width with vertical side rail | |
| 2 | Navigate through all tabs | All tabs accessible in vertical rail | |
| 3 | Scroll through content | Smooth scrolling, content fills width | |
| 4 | Open a detail screen | Standard push navigation works | |
| 5 | Interact with toolbar items | All items accessible (visible or overflow) | |
| 6 | Rotate to landscape | Layout adapts, no clipping | |

### 2.2 Open Flat (Inner Display)
| # | Test Case | Expected Result | Pass/Fail |
|---|-----------|-----------------|-----------|
| 1 | Open device from closed | Layout transitions smoothly to regular width | |
| 2 | Split View appears (if applicable) | List + Detail shown side-by-side | |
| 3 | Grid adjusts column count | Even number of columns displayed | |
| 4 | Content max-width | Text and images don't stretch to full width | |
| 5 | Tab bar position | Correct placement for current orientation | |
| 6 | Rotate to landscape | Layout adapts, split view adjusts | |

### 2.3 Partially Folded — Book Mode
| # | Test Case | Expected Result | Pass/Fail |
|---|-----------|-----------------|-----------|
| 1 | Fold device to ~120° | Content avoids fold region | |
| 2 | Grid layout | Even columns, fold acts as divider | |
| 3 | Scroll through content | No content hidden behind fold | |
| 4 | Interactive elements near fold | No buttons/links in fold zone | |
| 5 | Text readability | Text wraps away from fold | |

### 2.4 Partially Folded — Laptop Mode
| # | Test Case | Expected Result | Pass/Fail |
|---|-----------|-----------------|-----------|
| 1 | Fold device to ~90° (laptop) | Top: content, Bottom: controls | |
| 2 | Keyboard appears | Keyboard on bottom half, content on top | |
| 3 | Input bar position | Above keyboard, below fold | |
| 4 | Scroll while typing | Top content scrolls independently | |
| 5 | Dismiss keyboard | Content reclaims full inner display | |

### 2.5 Tent Mode
| # | Test Case | Expected Result | Pass/Fail |
|---|-----------|-----------------|-----------|
| 1 | Place device in tent position | Outer display shows content | |
| 2 | Media playback | Video/audio plays on outer display | |
| 3 | Controls | If applicable, controls accessible | |

---

## 3. Transition Testing (CRITICAL)

These tests verify the most common failure point: state persistence during
device open/close transitions.

### 3.1 Outer → Inner Transitions
| # | Scenario | Expected Result | Pass/Fail |
|---|----------|-----------------|-----------|
| 1 | Open while scrolled 50% down a list | Scroll position preserved exactly | |
| 2 | Open while viewing a detail screen | Detail stays visible (+ list pane appears if Split View) | |
| 3 | Open while typing in a text field | Text input preserved, cursor position maintained | |
| 4 | Open while a modal/sheet is displayed | Modal stays presented or gracefully adapts | |
| 5 | Open while playing audio | Audio continues without interruption | |
| 6 | Open while playing video | Video continues, player adapts to wider display | |
| 7 | Open while a menu/popover is shown | Menu repositions or dismisses cleanly | |
| 8 | Open while a loading spinner is active | Loading continues, no duplicate requests | |

### 3.2 Inner → Outer Transitions (Closing)
| # | Scenario | Expected Result | Pass/Fail |
|---|----------|-----------------|-----------|
| 1 | Close while in Split View | Collapses to current detail pane (or list) | |
| 2 | Close while scrolled in a grid | Grid reduces columns, scroll position approximate | |
| 3 | Close while typing | Text preserved, keyboard may re-layout | |
| 4 | Close while a sheet is half-expanded | Sheet adapts to compact width | |
| 5 | Close rapidly (quick snap shut) | No crash, no data loss | |

### 3.3 Rapid Transitions (Stress Test)
| # | Scenario | Expected Result | Pass/Fail |
|---|----------|-----------------|-----------|
| 1 | Open and close 10 times rapidly | No memory leak, no crash | |
| 2 | Open halfway, close, open fully | Correct layout at each stage | |
| 3 | Rotate while opening | Layout resolves to correct state | |

---

## 4. Navigation & Controls Testing

### 4.1 Vertical Side Rail
| # | Test Case | Expected Result | Pass/Fail |
|---|-----------|-----------------|-----------|
| 1 | All tab items visible | Icons display correctly in vertical orientation | |
| 2 | Tab overflow (5+ items) | Overflow items accessible via ⋯ menu | |
| 3 | Active tab indicator | Clear highlight on selected tab in vertical rail | |
| 4 | Toolbar items priority | High-priority items visible, low-priority overflow | |
| 5 | Overflow menu | Tapping ⋯ shows all overflowed items | |
| 6 | Long-press on tab items | Expected behavior (if applicable) | |

### 4.2 Floating Action Buttons
| # | Test Case | Expected Result | Pass/Fail |
|---|-----------|-----------------|-----------|
| 1 | FAB position on outer display | Not overlapping with side rail | |
| 2 | FAB position on inner display | Not overlapping with side rail or fold | |
| 3 | FAB tap target | Meets 44pt minimum on all displays | |

---

## 5. Accessibility Testing

### 5.1 VoiceOver
| # | Test Case | Expected Result | Pass/Fail |
|---|-----------|-----------------|-----------|
| 1 | Navigate side rail with VoiceOver | All items announced with descriptive labels | |
| 2 | Reading order in vertical rail | Top-to-bottom matches visual order | |
| 3 | Focus moves correctly after transition | Focus doesn't jump to unexpected element on open/close | |
| 4 | Overflow menu accessible | VoiceOver can open and navigate overflow items | |

### 5.2 Dynamic Type
| # | Test Case | Expected Result | Pass/Fail |
|---|-----------|-----------------|-----------|
| 1 | Large text in vertical rail | Labels scale or hide gracefully | |
| 2 | Large text in Split View | Both panes remain usable | |
| 3 | Extra large text on outer display | Content doesn't clip or overlap | |

### 5.3 Reduced Motion
| # | Test Case | Expected Result | Pass/Fail |
|---|-----------|-----------------|-----------|
| 1 | Open/close transitions with reduced motion | Instant transition, no animation | |
| 2 | Layout changes respect reduced motion | No sliding/fading, just snap | |

---

## 6. Performance Testing

| # | Metric | Target | How to Measure |
|---|--------|--------|----------------|
| 1 | Frame rate during fold/unfold | ≥ 60 FPS | Instruments → Core Animation |
| 2 | Memory usage delta (open vs closed) | < 10% increase | Instruments → Allocations |
| 3 | Layout computation time | < 16ms per frame | Instruments → Time Profiler |
| 4 | App launch time on outer display | < 2s | Instruments → App Launch |
| 5 | Split View render time | < 100ms | Custom timing + Instruments |

---

## 7. Edge Cases

| # | Edge Case | Expected Result | Pass/Fail |
|---|-----------|-----------------|-----------|
| 1 | Low Power Mode active | App still adapts layout (no degradation) | |
| 2 | Background app returns to foreground on different display | Correct layout for current display | |
| 3 | Notification received during fold transition | Alert displays correctly | |
| 4 | Screenshot taken during transition | Clean capture, no artifacts | |
| 5 | Split View with another app (multitasking) | App handles half-screen gracefully | |
| 6 | Dark Mode on one display, switching | Consistent dark mode across transition | |
| 7 | Keyboard with third-party input method | Layout still correct with non-system keyboard | |
