# DriveFlow — Figma Recreation Spec

Use this guide to rebuild the prototype as native Figma frames with Auto Layout.

---

## File Setup

| Setting | Value |
|---------|-------|
| Frame size | 1440 × 900px (Desktop) |
| Grid | 8pt layout grid, 8px gutter |
| Font | Inter (Google Fonts) |
| Primary | `#2563EB` |
| Background | `#F8FAFC` |
| Surface | `#FFFFFF` |
| Border | `#E2E8F0` |
| Text primary | `#0F172A` |
| Text secondary | `#64748B` |

Create **4 frames** named:
1. `01 — Lead Listing`
2. `02 — Lead Details`
3. `03 — Pipeline Kanban`
4. `04 — Dashboard`

Build a **shared component library** page first, then instance across frames.

---

## Component Library (Auto Layout)

### Sidebar / `Nav-Sidebar`
- **Layout:** Vertical Auto Layout, gap 16, padding 16, fill height, fixed width 240
- **Children:** Brand row → Nav groups → User chip (push to bottom with `Space between` on parent)

### Nav Item / `Nav-Item`
- **Auto Layout:** Horizontal, gap 8, padding 8×8, corner radius 8
- **Variants:** Default · Hover · Active (bg `#EFF6FF`, text `#2563EB`)

### Button / `Btn`
- **Variants:** Primary · Secondary · Ghost · Small
- **Auto Layout:** Horizontal, gap 8, padding 8×16, radius 8
- **Primary fill:** `#2563EB`, text white

### Card / `Card`
- **Auto Layout:** Vertical, gap 0, padding 0, radius 12
- **Stroke:** 1px `#E2E8F0`
- **Effect:** Drop shadow — Y:4, blur:12, color `#0F172A` 4%

### Badge / `Stage-Badge`
- **Variants:** New · Contacted · Qualified · Proposal · Won
- **Auto Layout:** Horizontal, padding 3×8, radius 999

### Avatar / `Avatar`
- **Variants:** XS (22) · SM (28) · MD (32) · LG (56)
- **Corner radius:** 6 (LG: 12)

### Score / `Lead-Score`
- **Variants:** High (green) · Med (amber) · Low (red)
- **Fixed width:** 32px min

### Table Row / `Lead-Row`
- **Auto Layout:** Horizontal, fill container
- **Cell padding:** 8×16
- **Variants:** Default · Hover · Selected (bg `#EFF6FF`)

### Kanban Card / `Pipeline-Card`
- **Auto Layout:** Vertical, gap 8, padding 16, radius 8
- **Variants:** Default · Drag · Featured · Won

### KPI Card / `KPI-Stat`
- **Auto Layout:** Vertical, gap 8, padding 16, radius 12

---

## Frame 1 — Lead Listing (1440×900)

```
┌─────────────────────────────────────────────────────────┐
│ Sidebar 240px │ Topbar 64px (search + Add Lead)         │
│               ├─────────────────────────────────────────┤
│               │ Page header: "Lead Listing" + actions   │
│               │ Filter bar card                         │
│               │ Table card (flex fill)                  │
└─────────────────────────────────────────────────────────┘
```

**Auto Layout hierarchy:**
- Root frame: Horizontal, clip content
  - Sidebar (fixed 240)
  - Main column: Vertical, fill
    - Topbar: Horizontal, space-between, padding 0×24, height 64
    - Content: Vertical, gap 16, padding 24, fill

**Table:** Use Figma `Table` plugin or repeat `Lead-Row` component × 6. Header row: uppercase 11px `#94A3B8`.

---

## Frame 2 — Lead Details

```
┌─────────────────────────────────────────────────────────┐
│ Sidebar │ Breadcrumb                                    │
│         │ Detail header card (avatar + actions)         │
│         │ ┌──────────────────────┬──────────────────┐ │
│         │ │ Timeline + Deal info │ Properties       │ │
│         │ │ (fill)               │ Tasks            │ │
│         │ │                      │ AI insight       │ │
│         │ └──────────────────────┴──────────────────┘ │
└─────────────────────────────────────────────────────────┘
```

**Detail grid:** Horizontal Auto Layout, gap 16
- Main: Vertical, fill (flex 1)
- Sidebar: Vertical, fixed 320px

**Timeline items:** Horizontal Auto Layout, gap 16. Connect with 1px vertical line (absolute positioned).

---

## Frame 3 — Pipeline Kanban

```
┌─────────────────────────────────────────────────────────┐
│ Sidebar │ Page header + List/Board toggle               │
│         │ Kanban toolbar card                           │
│         │ ┌─────┬─────┬─────┬─────┬─────┐             │
│         │ │ New │Cont.│Qual.│Prop.│ Won │  ← scroll   │
│         │ │cards│cards│cards│cards│cards│             │
│         │ └─────┴─────┴─────┴─────┴─────┘             │
└─────────────────────────────────────────────────────────┘
```

**Kanban column / `Kanban-Col`:**
- Width: 260px fixed
- Vertical Auto Layout: Header → Cards (gap 8, padding 8) → Add button
- Column bg: `#F8FAFC`, radius 12

**Prototype interaction:** Drag `Pipeline-Card` between columns; on drop, update column header count.

---

## Frame 4 — Dashboard

```
┌─────────────────────────────────────────────────────────┐
│ Sidebar │ Page header + date range                    │
│         │ KPI row: 4 equal columns (gap 16)             │
│         │ Funnel chart (full width)                   │
│         │ ┌──────────────────┬──────────────────┐     │
│         │ │ Source donut     │ Weekly activity  │     │
│         │ ├──────────────────┼──────────────────┤     │
│         │ │ Top performers   │ Recent activity  │     │
│         │ └──────────────────┴──────────────────┘     │
└─────────────────────────────────────────────────────────┘
```

**KPI grid:** Horizontal Auto Layout, 4 children with `Fill container` equally.

**Dashboard grid:** 2×2 grid using Auto Layout wrap or nested horizontal rows.

---

## Prototype Connections

| From | Interaction | To |
|------|-------------|-----|
| Sidebar "Lead Listing" | Click | Frame 1 |
| Sidebar "Pipeline" | Click | Frame 3 |
| Sidebar "Dashboard" | Click | Frame 4 |
| Lead name "Priya Sharma" | Click | Frame 2 |
| Breadcrumb "Leads" | Click | Frame 1 |
| Kanban card (Priya) | Click | Frame 2 |
| View toggle "List" | Click | Frame 1 |

Use **Smart Animate** with 200ms ease-out for screen transitions.

---

## Export Checklist for Assignment Submission

- [ ] 4 frames at 1440×900
- [ ] Component library page with variants
- [ ] Auto Layout on all containers
- [ ] 8pt spacing verified with Figma layout grid
- [ ] Inter font throughout
- [ ] Primary `#2563EB` on CTAs and active states
- [ ] Realistic CRM data (not lorem ipsum)
- [ ] Prototype flow linking all 4 screens
- [ ] Optional: Cover page with product name + your name

---

## Quick Import Alternative

Open `index.html` in Chrome at 1440px width → capture each screen → paste into Figma as reference layer → trace with Auto Layout components above.

Path: `/Users/deepakgouda/Downloads/DeltaX - Product Associate Assignment/driveflow-design/index.html`
