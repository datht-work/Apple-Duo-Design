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
