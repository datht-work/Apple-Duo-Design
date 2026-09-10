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

### Phase 1: App Audit
1. Ask the user for app screenshots or Figma exports (see Accepted Inputs above)
2. Analyze each screen against the [PM Checklist](./references/pm-checklist.md)
3. Read the [HIG Summary](./references/hig-summary.md) for iPhone Duo requirements
4. Identify impacted areas and classify by severity:
   - 🔴 **Breaking** — Will not function correctly on Duo (e.g., fixed layouts, hardcoded widths)
   - 🟡 **Suboptimal** — Works but misses Duo capabilities (e.g., no split view expansion)
   - 🟢 **Compatible** — Already adapts well (e.g., uses standard system components)
5. Output: **Audit Report** with severity ratings per screen/component

### Phase 2: PRD Generation
1. Use the [PRD Template](./references/prd-template.md) as the base
2. Fill in findings from Phase 1
3. Include competitive context from [Competitive Analysis](./references/competitive-analysis.md)
4. Recommend which features to adapt vs. which to redesign
5. Recommend "Wow Factor" features that leverage Duo capabilities for App Store featuring potential.
6. Define success metrics and KPIs
7. Output: **Draft PRD** ready for stakeholder review

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
5. Output: **Phasing Roadmap** with timeline recommendations

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

## Reference Documents

| Document | Purpose |
|----------|---------|
| [HIG Summary](./references/hig-summary.md) | Apple HIG for iPhone Duo, organized for PM consumption |
| [PM Checklist](./references/pm-checklist.md) | Screen-by-screen audit checklist |
| [PRD Template](./references/prd-template.md) | Ready-to-fill PRD for conversion projects |
| [User Stories Catalog](./references/user-stories-catalog.md) | Pre-built user stories with acceptance criteria |
| [Competitive Analysis](./references/competitive-analysis.md) | Comparison with Samsung Fold & Pixel Fold ecosystems |


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
