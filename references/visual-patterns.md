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
