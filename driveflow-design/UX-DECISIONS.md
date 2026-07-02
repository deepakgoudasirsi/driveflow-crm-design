# DriveFlow — UX Design Decisions

**Product:** DriveFlow Lead Management CRM  
**Platform:** Desktop (1440 × 900px)  
**Design language:** HubSpot (CRM density) + Linear (precision & speed) + Attio (relationship-centric detail)

---

## 1. Design System Foundations

### 1.1 8pt Spacing Grid
Every margin, padding, and gap uses multiples of 4/8px: **4, 8, 16, 24, 32, 40, 48**. This creates optical consistency across screens and maps directly to Figma Auto Layout gap/padding values.

**Why:** Sales reps scan hundreds of rows daily. Misaligned spacing creates cognitive friction. An 8pt system is industry-standard (Material, Apple HIG) and scales cleanly from compact table cells to generous dashboard KPI cards.

### 1.2 Typography — Inter
- **H1 (page titles):** 24px / 700 / −2% tracking  
- **H2 (section headers):** 14px / 600  
- **Body:** 13px / 400–500  
- **Meta/captions:** 11–12px / muted color  

**Why:** Inter is optimized for UI legibility at small sizes. Linear and Attio both use geometric sans-serifs; Inter delivers similar clarity without licensing concerns. Tabular numerals on revenue/score columns prevent layout shift when sorting.

### 1.3 Color — Primary #2563EB
Blue signals trust and action without the aggression of pure red CTAs. Used sparingly: primary buttons, active nav, selected rows, funnel bars.

**Semantic palette:**
| Token | Use |
|-------|-----|
| `#2563EB` | Primary actions, qualified stage |
| `#059669` | Won, positive deltas, high scores |
| `#D97706` | Contacted, warnings, medium scores |
| `#DC2626` | Low scores, destructive actions |
| `#64748B` | Secondary text — never pure gray on white |

**Why:** HubSpot uses orange; we differentiate with blue for a fresher, DeltaX-adjacent SaaS feel while keeping semantic colors intuitive.

### 1.4 Cards & Shadows
- **Radius:** 12px on cards (Linear-style softness)  
- **Shadow:** `0 1px 3px rgba(15,23,42,0.06), 0 4px 12px rgba(15,23,42,0.04)`  

**Why:** Flat UI feels dated for CRM dashboards. Soft shadows create depth hierarchy without skeuomorphism. Rounded corners reduce visual harshness during long work sessions.

---

## 2. Global Shell (All 4 Screens)

### 2.1 Persistent Sidebar (240px)
**Decision:** Fixed left nav with grouped sections — Overview, Leads, Workspace.

**Why:**
- **HubSpot pattern:** CRM users live in one tool 6+ hours/day; persistent wayfinding beats hamburger menus.
- **Linear pattern:** Icon + label nav with subtle active state (blue tint background, not heavy fill).
- **240px width:** Fits labels without truncation; collapsible in v2 for power users.

### 2.2 Top Bar with ⌘K Search
**Decision:** Global search spanning leads, companies, deals with keyboard shortcut hint.

**Why:** Attio's command palette philosophy — reps shouldn't click 3 times to find "Priya Sharma." Search is the fastest path for high-volume lead workflows.

### 2.3 "Add Lead" Primary CTA (Top Right)
**Decision:** Single prominent primary button, always visible.

**Why:** F-pattern scanning puts top-right as the natural action zone. One primary CTA avoids decision paralysis (vs. multiple colored buttons).

---

## 3. Screen 1 — Lead Listing

### 3.1 Information Architecture
**Columns:** Lead (avatar + name + title), Company, Stage, Score, Owner, Source, Last activity, Value.

**Why each column:**
| Column | Rationale |
|--------|-----------|
| Lead + avatar | Human recognition faster than text alone (Attio people-first) |
| Stage badge | Pipeline status at a glance — color-coded, scannable |
| Score (41–95) | Prioritization signal — reps triage by score before opening records |
| Owner | Manager view — who owns follow-up accountability |
| Source | Marketing attribution — which channels produce quality leads |
| Last activity | Staleness indicator — "Stale 7d+" filter addresses this pain |
| Value (₹) | Revenue-weighted sorting for enterprise Indian market context |

### 3.2 Filter Architecture (Two Layers)
1. **Quick chips:** All leads · My leads · Hot · Stale 7d+  
2. **Structured dropdowns:** Status · Owner · Source  

**Why:** Chips handle 80% of daily filters in one click (Linear speed). Dropdowns handle edge cases without cluttering the default view.

### 3.3 Bulk Selection Toolbar
**Decision:** Blue highlight bar appears when rows are selected — Assign owner · Change stage · Delete.

**Why:** HubSpot's bulk actions are critical for sales ops. Contextual toolbar (not always visible) reduces noise but surfaces power when needed.

### 3.4 Row Interaction
- Hover: subtle gray background  
- Selected: primary light blue wash  
- Click name → Lead Details  

**Why:** Table remains the densest view for 200+ leads. Kanban is for pipeline; listing is for search/sort/bulk.

### 3.5 Realistic Data Choices
Indian market context (₹ Lakhs), B2B SaaS titles (VP Marketing, Head of Ops), mixed sources (Website, LinkedIn, Referral, Event) — demonstrates product thinking for DeltaX's ad-tech / B2B audience.

---

## 4. Screen 2 — Lead Details

### 4.1 Layout — 70/30 Split
**Left (main):** Activity timeline + Deal information  
**Right (sidebar):** Properties · Tasks · AI insight  

**Why:** Attio's record page pattern — relationship history is the hero, metadata is secondary. Sales reps spend 80% of time on "what happened?" not "what's the industry field?"

### 4.2 Hero Header
**Decision:** Large avatar, name, stage badge, score, contact row (email · phone · LinkedIn), action buttons (Log call · Send email · Schedule meeting).

**Why:**
- **Actions at top:** Reduces scroll-to-act friction (common HubSpot complaint).
- **Schedule meeting as primary:** Highest-intent conversion action for qualified leads.
- **Breadcrumb:** Leads → Priya Sharma — clear escape hatch.

### 4.3 Activity Timeline
**Decision:** Chronological feed with typed icons (email, call, note, web visit) and filter tabs.

**Why:** Reps reconstruct deal context from timeline. Icon typing enables scan-by-modality. "Opened 2×" on email shows engagement — actionable signal.

### 4.4 Right Rail — AI Insight Card
**Decision:** Gradient card suggesting follow-up based on email opens.

**Why:** Modern CRM differentiation (HubSpot AI, Attio intelligence). Shows product thinking beyond static CRUD — proactive nudges increase conversion. Placed in sidebar so it assists without blocking core content.

### 4.5 Tasks Widget
**Decision:** Checkbox tasks with due dates; overdue in amber.

**Why:** CRM without task completion is a contact database. Inline tasks keep reps in-record vs. switching to Asana.

---

## 5. Screen 3 — Lead Management (Kanban)

### 5.1 Column Structure
**Stages:** New → Contacted → Qualified → Proposal → Won  
**Column header shows:** Stage dot · Count · Total ₹ value  

**Why:**
- **5 columns fit 1440px** without horizontal scroll overload (260px each).
- **Value in header:** Managers assess pipeline health per stage, not just card count.
- **Color dots:** Stage identity without reading text (Linear status dots).

### 5.2 Card Design
Each card: Score · Name · Company · Deal value · Tags · Owner avatar · Last updated.

**Why:**
- **Score on card:** Prioritize within column without opening detail.
- **"Hot lead" / "Follow-up due" tags:** Exception-based attention — only noisy when action needed.
- **Drag affordance:** Marcus Johnson card shows blue focus ring — communicates interactivity.

### 5.3 View Toggle (List / Board)
**Decision:** Board active; List links back to Screen 1 mental model.

**Why:** Same data, two mental models — table for analysis, board for movement. Toggle prevents duplicate nav items.

### 5.4 "+ Add lead" per Column
**Decision:** Dashed button at column bottom.

**Why:** Reduces friction — add directly to "New" without modal stage picker. Matches Trello/Linear column add patterns.

---

## 6. Screen 4 — Dashboard

### 6.1 KPI Row (4 Cards)
| Metric | Why it matters |
|--------|----------------|
| Total leads (248, ↑12.4%) | Volume health |
| Qualified rate (34.2%) | Funnel quality, not just quantity |
| Pipeline value (₹1.42 Cr) | Revenue forecast |
| Avg. deal cycle (18 days) | Efficiency trend |

**Why 4 KPIs:** Miller's Law — 4±1 chunks. More KPIs dilute focus. Each maps to a different stakeholder question (marketing, sales, finance, ops).

### 6.2 Lead Funnel Chart (Full Width)
**Decision:** Horizontal bar funnel with stage labels, counts, and conversion %.

**Why:** Funnel is the #1 CRM dashboard chart. Horizontal layout reads left-to-right as progression. Gradient blue → green on Won stage shows success terminus.

### 6.3 Leads by Source (Donut)
**Decision:** Donut with center total + legend.

**Why:** Marketing needs channel mix at a glance. Donut preserves part-to-whole relationship better than bar for 4–5 categories.

### 6.4 Weekly Activity (Grouped Bar)
**Decision:** Calls (blue) · Emails (light blue) · Meetings (green) by weekday.

**Why:** Activity metrics expose rep behavior patterns — e.g., email-heavy Wed vs. meeting-heavy Fri. Managers spot coaching opportunities.

### 6.5 Top Performers + Recent Activity
**Decision:** Two compact widgets below charts.

**Why:** Dashboard serves both managers (leaderboard) and reps (what happened recently). Keeps dashboard actionable, not just analytical.

---

## 7. Interaction Patterns Summary

| Pattern | Screens | Inspiration |
|---------|---------|-------------|
| Command search (⌘K) | All | Linear |
| Bulk select + contextual toolbar | Listing | HubSpot |
| Record timeline | Details | Attio |
| AI nudge card | Details | HubSpot AI |
| Drag-and-drop kanban | Pipeline | Trello + HubSpot |
| Funnel + source charts | Dashboard | HubSpot Reports |

---

## 8. Accessibility & Polish Notes (Figma Handoff)

- **Contrast:** All text meets WCAG AA on white/light backgrounds  
- **Focus states:** Search input has 3px primary ring (implement on all interactives in Figma prototypes)  
- **Hit targets:** Minimum 36×36px for icon buttons  
- **Empty states:** Not shown — would add "No leads match filters" with clear CTA in production  
- **Loading:** Skeleton rows for table, shimmer on KPI cards  

---

## 9. What I'd Present in a DeltaX Interview

1. **Problem framing:** "Sales reps lose 2+ hours/day context-switching between tools — DriveFlow centralizes triage (listing), depth (details), movement (kanban), and accountability (dashboard)."  
2. **Key tradeoff:** Table vs. Kanban — chose both with clear jobs-to-be-done.  
3. **Differentiation:** AI insight card + lead scoring visible everywhere — intelligence layer, not just database.  
4. **Metrics that matter:** Qualified rate over raw lead count — quality > vanity.  
5. **Next iteration:** Mobile companion for field reps, custom pipeline stages, webhook integrations.

---

*Open `index.html` in a browser to interact with all 4 screens. Use the bottom frame switcher or sidebar navigation.*
