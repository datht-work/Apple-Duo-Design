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
