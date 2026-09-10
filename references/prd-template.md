# PRD Template: iPhone Duo App Conversion

> **Instructions**: Fill in each section based on the audit findings. Sections
> marked [AUTO] will be pre-populated by the agent from the audit checklist.
> Sections marked [PM] require PM input and decision-making.

---

## 1. Executive Summary

### 1.1 Product
- **App Name**: [PM]
- **Current Platforms**: [PM] (e.g., iPhone, iPad, Mac)
- **Current iOS Version Support**: [PM]
- **Target Duo SDK**: iOS 26+ (iPhone Duo)

### 1.2 Business Case
- **Why convert now**: [PM]
- **Target audience on Duo**: [PM]
- **Revenue impact estimate**: [PM]
- **Competitive pressure**: [AUTO — from competitive analysis]

### 1.3 Conversion Summary
- **Overall readiness score**: [AUTO — from audit]
- **Estimated effort**: [AUTO — S/M/L per phase]
- **Recommended timeline**: [AUTO — phasing recommendation]

---

## 2. User Impact Analysis

### 2.1 User Personas Affected
Identify which user personas will be most impacted by the conversion:

| Persona | Primary Use Case | Duo Impact | Priority |
|---------|-----------------|------------|----------|
| [PM] | [PM] | [AUTO] | [PM] |

### 2.2 User Journey Changes
Map how key user journeys change on Duo:

| Journey | Current Flow | Duo Flow (Closed) | Duo Flow (Open) | Change Severity |
|---------|-------------|-------------------|-----------------|-----------------|
| [AUTO] | [AUTO] | [AUTO] | [AUTO] | [AUTO] |

### 2.3 Navigation Pattern Changes
Detail how the vertical control layout affects navigation:

| Current Pattern | Duo Pattern | User Learning Curve | Risk |
|----------------|-------------|--------------------|----- |
| Bottom tab bar | Vertical side rail | Low (system-managed) | [PM] |
| Top toolbar | Vertical side rail | Medium | [PM] |
| Custom navigation | Requires redesign | High | [PM] |

### 2.4 Apple Ecosystem Synergy (Duo WOW Factor)
Identify opportunities to integrate Duo features with the broader Apple ecosystem:

| Integration | Concept | User Value | Effort |
|-------------|---------|------------|--------|
| Handoff / Continuity | Seamless transition outer ↔ inner ↔ Mac/iPad | Very High | [AUTO] |
| Dynamic Island | Outer display Live Activities | High | [PM] |
| Apple Watch | Remote control / glanceable info while Duo is in Tent mode | Medium | [PM] |

---

## 3. Feature Requirements

### 3.1 Outer Display (Closed Device)
Features that must work on the compact outer display:

| Feature | Current Status | Required Changes | Priority |
|---------|---------------|------------------|----------|
| [AUTO] | [AUTO] | [AUTO] | [PM] |

### 3.2 Inner Display (Open Device)
Features that benefit from the wider inner display:

| Feature | Enhancement Opportunity | Expected UX Improvement | Priority |
|---------|----------------------|------------------------|----------|
| [AUTO] | [AUTO] | [AUTO] | [PM] |

### 3.3 Fold-Aware Features
Features that respond to the device's fold state:

| Feature | Fold Behavior | Implementation Complexity | Priority |
|---------|--------------|--------------------------|----------|
| [AUTO] | [AUTO] | [AUTO] | [PM] |

### 3.4 Pose-Specific Features (Optional Enhancements)
Features optimized for specific device poses:

| Pose | Feature Opportunity | User Value | Effort |
|------|-------------------|------------|--------|
| Book mode | Side-by-side reading | [PM] | [AUTO] |
| Laptop mode | Content top / controls bottom | [PM] | [AUTO] |
| Tent mode | Shared viewing / presentation | [PM] | [AUTO] |

---

## 4. Technical Dependencies

### 4.1 Engineering Assessment Checklist
Share this with your engineering team for technical validation:

- [ ] Current minimum iOS target version
- [ ] Use of `NavigationSplitView` / `UISplitViewController`
- [ ] Use of Auto Layout / SwiftUI layout system
- [ ] Use of size classes (`horizontalSizeClass`, `verticalSizeClass`)
- [ ] Safe area inset handling (`safeAreaInsets`)
- [ ] State restoration implementation
- [ ] Third-party UI libraries used (list them)
- [ ] Custom drawing / Core Graphics usage
- [ ] Camera API usage
- [ ] Game engine (if applicable)

### 4.2 Third-Party Dependencies
Identify third-party libraries that may need updates:

| Library | Current Version | Duo Support Status | Action Required |
|---------|----------------|-------------------|-----------------|
| [PM/Eng] | [PM/Eng] | [PM/Eng] | [PM/Eng] |

### 4.3 Design Dependencies
Identify design assets and systems that need updates:

- [ ] Design system supports vertical control layout
- [ ] Icon set includes SF Symbols or can replace text labels
- [ ] Breakpoint system covers Duo display sizes
- [ ] Figma/Sketch components adapted for split view
- [ ] Motion/animation specs reviewed for resize transitions

---

## 5. Success Metrics & KPIs

### 5.1 Quality Metrics (Must-Have)
| Metric | Target | Measurement |
|--------|--------|-------------|
| No layout breakage on Duo | 0 visual bugs | QA testing on device/simulator |
| State persistence on open/close | 100% state retained | Automated test suite |
| All features accessible in all poses | 100% feature parity | Feature audit matrix |

### 5.2 Experience Metrics (Should-Have)
| Metric | Target | Measurement |
|--------|--------|-------------|
| Split view adoption (inner display) | [PM]% of sessions | Analytics event tracking |
| Time-to-task improvement on inner display | [PM]% reduction | A/B comparison |
| User satisfaction (Duo-specific) | [PM] NPS delta | Post-update survey |

### 5.3 Business Metrics (Nice-to-Have)
| Metric | Target | Measurement |
|--------|--------|-------------|
| App Store rating post-update | Maintain ≥ [PM] | App Store Connect |
| Duo user retention (D7/D30) | ≥ overall retention | Analytics cohort |
| Feature adoption on Duo | [PM]% engagement | Analytics events |

---

## 6. Timeline & Phasing

### Phase A: Launch-Ready (Ship with Duo)
**Goal**: App works correctly on Duo without visual bugs

| Deliverable | Effort | Owner | Dependencies |
|-------------|--------|-------|-------------|
| Fix all 🔴 Breaking issues | [AUTO] | Eng | None |
| Verify vertical control layout | [AUTO] | Eng + Design | Design icons |
| State persistence through open/close | [AUTO] | Eng | None |
| QA pass on Duo simulator | S | QA | Simulator availability |

**Timeline**: [PM] weeks before Duo launch

### Phase B: Fast-Follow (1–2 Sprints Post-Launch)
**Goal**: Take advantage of Duo's dual-display capabilities

| Deliverable | Effort | Owner | Dependencies |
|-------------|--------|-------|-------------|
| Split view for master-detail flows | [AUTO] | Eng | Design specs |
| Arrangement views for secondary content | [AUTO] | Eng + Design | Design specs |
| Enhanced content hierarchy on inner display | [AUTO] | Design + Eng | Content audit |

**Timeline**: [PM] sprints after Duo launch

### Phase C: Delight (Next Quarter)
**Goal**: Leverage Duo-unique capabilities for differentiation

| Deliverable | Effort | Owner | Dependencies |
|-------------|--------|-------|-------------|
| Fold-aware features | [AUTO] | Eng | API documentation |
| Pose-specific optimizations | [AUTO] | Eng + Design | User research |
| Competitive feature parity | [AUTO] | PM + Design | Competitive analysis |

**Timeline**: [PM] quarter

---

## 7. Risks & Mitigations

| Risk | Likelihood | Impact | Mitigation |
|------|-----------|--------|------------|
| Duo launch timeline changes | Medium | High | Decouple Phase A from specific date |
| Third-party library doesn't support Duo | Medium | High | Identify alternatives early; test in beta |
| Design resources bottleneck | High | Medium | Prioritize icon-first redesign; reuse system components |
| User confusion with vertical controls | Medium | Medium | Follow system defaults; don't customize control placement |
| Performance on dual displays | Low | High | Profile on Duo simulator early and often |

---

## 8. Stakeholder Sign-off

| Stakeholder | Role | Status | Date |
|------------|------|--------|------|
| [PM] | Product Manager | ☐ Approved | |
| [PM] | Engineering Lead | ☐ Approved | |
| [PM] | Design Lead | ☐ Approved | |
| [PM] | QA Lead | ☐ Approved | |
| [PM] | Business/GM | ☐ Approved | |

---

## Appendix

### A. Audit Report
[Link to or embed the full audit checklist results]

### B. Competitive Analysis
[Link to competitive analysis reference document]

### C. User Stories
[Link to prioritized user stories document]
