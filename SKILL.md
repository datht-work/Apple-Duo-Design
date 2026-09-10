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
