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
