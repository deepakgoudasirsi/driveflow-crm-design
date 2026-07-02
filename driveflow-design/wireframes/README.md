# DriveFlow — Lo-Fi Wireframes

Early layout exploration for the HSR Motors lead management CRM (1440px desktop).

## Screen 1 — Lead Listing

```
┌──────────┬────────────────────────────────────────────────────────┐
│ Sidebar  │  Search · Filters · Export · Add Lead                  │
│          ├────────────────────────────────────────────────────────┤
│ Dashboard│  Lead Listing · 248 active leads                       │
│ Listing* │  [Status] [Source] [Owner] [Score] filter chips        │
│ Pipeline │  ┌──────────────────────────────────────────────────┐  │
│          │  │ □  Name      Source   Score  Status   Owner     │  │
│          │  │ □  Priya S.  Facebook  92    New      Ananya    │  │
│          │  │ □  Rahul M.  Website   78    Contacted Vikram   │  │
│          │  └──────────────────────────────────────────────────┘  │
└──────────┴────────────────────────────────────────────────────────┘
```

**Goal:** Triage leads at scale — filter, sort, bulk assign, spot high scores.

## Screen 2 — Lead Details

```
┌──────────┬────────────────────────────────────────────────────────┐
│ Sidebar  │  ← Back · Priya Sharma · Score 92 · Call · Email       │
│          ├─────────────────────────────┬──────────────────────────┤
│          │  Activity Timeline          │  Deal Info               │
│          │  · Call logged              │  Model: Creta SX(O)        │
│          │  · Email opened             │  Budget: ₹18–20L         │
│          │  · Note added               │  Timeline: 2 weeks       │
│          │                             │  Tasks                   │
│          │  Notes & Tasks tabs         │  AI Follow-up Insight     │
└──────────┴─────────────────────────────┴──────────────────────────┘
```

**Goal:** Full context before every call — timeline, deal info, next actions.

## Screen 3 — Lead Management (Kanban)

```
┌──────────┬────────────────────────────────────────────────────────┐
│ Sidebar  │  Pipeline · ₹2.4Cr total value · Filter by owner       │
│          ├────────┬────────┬──────────┬──────────┬─────────────────┤
│          │  New   │Contact │ Qualified│ Proposal │     Won         │
│          │  12    │   8    │    6     │    4     │      3          │
│          │ ┌────┐ │ ┌────┐ │  ┌────┐  │  ┌────┐  │   ┌────┐        │
│          │ │card│ │ │card│ │  │card│  │  │card│  │   │card│        │
│          │ └────┘ │ └────┘ │  └────┘  │  └────┘  │   └────┘        │
└──────────┴────────┴────────┴──────────┴──────────┴─────────────────┘
```

**Goal:** Visual pipeline — drag deals across stages, see stage values.

## Screen 4 — Dashboard

```
┌──────────┬────────────────────────────────────────────────────────┐
│ Sidebar  │  Dashboard · This week vs last week                    │
│          │  [Leads] [Conversion] [Revenue] [Avg Response] KPIs    │
│          ├─────────────────────────────┬──────────────────────────┤
│          │  Conversion Funnel          │  Lead Source Mix         │
│          │  ████████ New               │      (donut chart)       │
│          │  ██████ Contacted           │                          │
│          │  ████ Qualified             │  Weekly Activity Bars    │
│          │                             │  Top Performers Table    │
└──────────┴─────────────────────────────┴──────────────────────────┘
```

**Goal:** Business manager view — funnel health, source ROI, team performance.

---

These wireframes informed the high-fidelity prototype in `index.html`.
