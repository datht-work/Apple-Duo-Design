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
