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
