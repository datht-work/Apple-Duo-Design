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
