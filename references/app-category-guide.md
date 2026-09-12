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
