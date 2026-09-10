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
