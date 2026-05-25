# GanttFlow — Professional Gantt Chart & Project Management App

A fully self-contained, single-file HTML application for professional project management with dynamic Gantt charts. No server, no build tools, no dependencies to install — just open `index.html` in a browser.

---

## ✨ Features

### Project Setup
- **Company & client details** — your company info, client company info, contact details
- **Project metadata** — name, description, start/end dates, manager, team, budget, priority, color coding
- **Multiple projects** — manage several projects simultaneously from the sidebar

### Gantt Chart
- **Auto-generated timeline** — bars appear automatically when start/end dates are set
- **Color-coded by status** — Planned (gray) · In Progress (blue) · Completed (green) · Delayed (orange) · Blocked (red) · On Hold (yellow) · Cancelled (dark gray)
- **Milestone diamonds** — visual milestone markers on the timeline
- **Progress strips** — visual progress indicator inside each task bar
- **Critical path highlighting** — toggle to show the dependency chain that determines project duration
- **Today line** — always-visible vertical marker for the current date
- **Zoom controls** — Week / 2 Weeks / Month / Quarter / Year views
- **Hover tooltips** — rich details on hover without clicking
- **Scroll-to-today** — chart auto-scrolls to the current date on load

### Task & Milestone Management
- Add / edit / delete tasks and milestones
- Fields: name, description, start date, end date, assignee(s), status, priority, progress %, dependencies, notes
- **Duration auto-calculated** from start and end dates
- **Dependency auto-adjustment** — if a predecessor task end date changes, dependent tasks shift automatically (cascades)
- Quick status update from the detail panel (one click)

### Dashboard
- Overall completion percentage
- Days remaining (turns red when critical)
- Delayed / blocked task count
- In-progress task count
- **Alert banners** — blocked tasks (red), delayed tasks (orange), due-this-week warnings (yellow)
- Milestone progress tracker
- Upcoming deadlines with urgency indicators
- **Team workload bars** — visual task distribution per team member
- Activity feed — auto-logged change history

### Tasks View
- Full table of all tasks and milestones
- Search filter, status filter, priority filter
- Inline progress bars
- Click any row to open the detail panel

### Team View
- Member cards with task counts, completion stats, and active task list

### Export
| Format | Behaviour |
|--------|-----------|
| **CSV** | Downloads immediately — all tasks + milestones with all fields |
| **PDF / PNG / PPTX** | Shows branded report spec; plug in jsPDF, html2canvas, or PptxGenJS |
| **Print** | Calls `window.print()` |

### Templates
Three one-click project templates in the sidebar:
- **Software Development** — discovery → sprints → QA → launch
- **Marketing Campaign** — strategy → creative → launch → reporting
- **Construction** — permits → foundation → structure → finishing

### Other
- **Auto-save** — all changes persist to `localStorage` automatically
- **Duplicate project** — clone any project via Settings
- **Delete project** — with confirmation prompt
- **Integration toggles** — Google Calendar, Slack, Outlook, Trello (UI stubs for wiring up)
- **Import CSV** — guidance dialog (wire up a FileReader + parser to activate)
- **Mobile-responsive** — sidebar collapses, grid reflows at narrow widths

---

## 🚀 Deploy on GitHub Pages (free, 60 seconds)

1. **Fork or create a repo** on [github.com](https://github.com)
2. **Upload `index.html`** to the root of the repo (drag-and-drop in the GitHub UI)
3. Go to **Settings → Pages**
4. Under *Source*, select **Deploy from a branch** → `main` → `/ (root)` → **Save**
5. After ~30 seconds your site is live at:

```
https://<your-username>.github.io/<repo-name>/
```

> **Example:** if your GitHub username is `jdoe` and your repo is `ganttflow`, the URL is  
> `https://jdoe.github.io/ganttflow/`

---

## 📁 File structure

```
/
└── index.html      ← entire application (HTML + CSS + JS, ~1 000 lines)
└── README.md
```

Everything is in one file — no npm, no bundler, no backend required.

---

## 🔌 Extending the app

### Real PDF/PNG export
```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/html2canvas/1.4.1/html2canvas.min.js"></script>
```
Then in `exportAction('pdf')`, capture `#ganttContainer` with `html2canvas` and add to a `jsPDF` doc.

### PowerPoint export
```html
<script src="https://cdn.jsdelivr.net/npm/pptxgenjs@3.12.0/dist/pptxgen.bundle.js"></script>
```

### CSV import
Use the browser `FileReader` API to read an uploaded CSV and push rows into `proj.tasks`.

### Backend / multi-user
Replace `saveToStorage()` / `loadFromStorage()` with `fetch()` calls to any REST or Firebase API.

### Drag-and-drop rescheduling
Add `mousedown` / `mousemove` / `mouseup` listeners to `.gantt-bar-wrap` elements to reposition bars and update `task.start` / `task.end`.

---

## 🛠 Tech stack

| Layer | Technology |
|-------|-----------|
| Structure | HTML5 |
| Styling | CSS3 custom properties, CSS Grid, Flexbox |
| Logic | Vanilla JavaScript (ES6+) |
| Icons | [Tabler Icons](https://tabler.io/icons) webfont (CDN) |
| Fonts | [DM Sans + DM Mono](https://fonts.google.com) (CDN) |
| Persistence | `localStorage` |

Zero build steps. Zero frameworks. Zero dependencies to install.

---

## 📄 License

MIT — free to use, modify, and deploy commercially.
