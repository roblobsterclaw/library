# BUILD SPEC — JFL Project Library Dashboard

## What You're Building
A single-page, mobile-first HTML dashboard that serves as the master directory for all of Joe Lynch's projects. This is "The Map" — one page where Joe can see every project, tap to open it, and understand where everything lives.

## Tech Requirements
- **Single file: index.html** — all CSS and JS inline (no external dependencies, no build tools, no frameworks)
- **No login/auth** — public page, anyone with the URL can view
- **Works offline** — once loaded, no API calls needed (all data is embedded)
- **Mobile-first** — designed for iPhone Safari first, then scales up to desktop

## Design
- **Dark theme:** Background #0D1117, cards #161B22, borders #30363D
- **Accent color:** Orange #FF6B00 for highlights, buttons, active states
- **Secondary accent:** Gold #C59E3C for subtle highlights
- **Font:** System font stack (-apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif)
- **Border radius:** 12px on cards for modern feel
- **Smooth transitions** on hover/filter

## Layout (top to bottom)

### 1. Header
- Title: "🦞 JFL Project Library" in large text
- Subtitle: "Command Center — All Projects, All Agents, One Place"
- Stats bar showing: Total Projects | Active | Live on Web | Last Updated

### 2. Filter/Search Bar (sticky, stays at top when scrolling)
- Search input with placeholder "Search projects..."
- Filter pills/buttons: All | Active | Paused | Archived | Idea
- Filter by type: All Types | Dashboard | Website | App | Document | Game | Research | Rendering
- Filter by agent: All Agents | 🦞 Rob | ⚡ Hermes | 🔧 Claude Code | 🔨 Codex | 👤 Joe

### 3. Project Cards Grid
- Responsive grid: 1 column on mobile, 2 on tablet, 3 on desktop
- Each card shows:
  - **Project name** (large, bold)
  - **Status badge** (colored pill: green=Active, yellow=Paused, gray=Archived, blue=Idea)
  - **Type badge** (e.g., "Dashboard", "Website", "App")
  - **Description** (1-2 lines)
  - **Built by** (agent emoji icons)
  - **Links row:**
    - 🌐 "Live Site" button → GitHub Pages URL (if exists)
    - 📂 "GitHub" button → repo URL (if exists)
    - 💻 "Local" label showing Mac Mini path
  - **Last updated** date
  - **Branch info** (if has git repo)

### 4. Footer
- "Managed by Hermes | Updated automatically"
- Link to GitHub Projects board (when we set it up)

## The JSON Data Block

At the top of the JavaScript section, include a `const PROJECTS = [...]` array with ALL project data. This is the single source of truth. Any agent can update this JSON to add/modify projects.

Here is the complete project data to include (from our audit):

```javascript
const PROJECTS = [
  // === ACTIVE PROJECTS ===
  {
    name: "MOSE Dashboard",
    slug: "mose",
    status: "active",
    type: "dashboard",
    description: "Super investor 13F tracker — 6 tabs, 17 investors, SEC filing analysis",
    builtBy: ["rob", "hermes"],
    githubRepo: "https://github.com/roblobsterclaw/mose",
    githubPages: "https://roblobsterclaw.github.io/mose/",
    localPath: "~/Documents/Codex/MOSE DASHBOARD",
    branches: ["main", "gh-pages"],
    lastUpdated: "2026-05-18",
    notes: "Firebase sync, auto-deploys via GitHub Actions"
  },
  {
    name: "Mission Control",
    slug: "mission-control",
    status: "active",
    type: "dashboard",
    description: "AI team command center — daily ops dashboard for Rob, Hermes, and Joe",
    builtBy: ["rob", "hermes"],
    githubRepo: "https://github.com/roblobsterclaw/mission-control",
    githubPages: "https://roblobsterclaw.github.io/mission-control/",
    localPath: "~/.openclaw/workspace/projects/mission-control-dashboard",
    branches: ["main", "gh-pages", "mission-control-v2-ops"],
    lastUpdated: "2026-05-20",
    notes: "Updated daily by Rob"
  },
  {
    name: "World Cup Pool",
    slug: "world-cup-pool",
    status: "active",
    type: "website",
    description: "Rob Lobster Cup 2026 — World Cup prediction pool, $25 entry",
    builtBy: ["rob", "hermes", "codex"],
    githubRepo: "https://github.com/roblobsterclaw/roblobstercup",
    githubPages: "https://roblobstercup.com/",
    localPath: "~/Documents/roblobstercup",
    branches: ["main", "gh-pages"],
    lastUpdated: "2026-05-15",
    notes: "Custom domain roblobstercup.com, Supabase backend"
  },
  {
    name: "JFL TTD Dashboard",
    slug: "jfl-ttd",
    status: "active",
    type: "dashboard",
    description: "Things To Do — Joe's personal task tracker, 87 items, Firebase sync",
    builtBy: ["rob", "hermes"],
    githubRepo: "https://github.com/roblobsterclaw/jfl-ttd",
    githubPages: "https://roblobsterclaw.github.io/jfl-ttd/",
    localPath: "~/.openclaw/workspace/projects/ttd-dashboard-v2",
    branches: ["main"],
    lastUpdated: "2026-05-04",
    notes: "v5.91, PRIMARY TTD tool"
  },
  {
    name: "Lobster Press",
    slug: "lobster-press",
    status: "active",
    type: "website",
    description: "Social media content factory — TLC, Surfbox, Keli content publishing",
    builtBy: ["rob"],
    githubRepo: "https://github.com/roblobsterclaw/lobster-press",
    githubPages: "https://roblobsterclaw.github.io/lobster-press/",
    localPath: "~/.openclaw/workspace/projects/lobster-press",
    branches: ["main"],
    lastUpdated: "2026-05-20",
    notes: "Social media command center"
  },
  {
    name: "Trial Ledger",
    slug: "trial-ledger",
    status: "active",
    type: "app",
    description: "Accounting web app — bank statement processing, exports, demo mode",
    builtBy: ["codex", "rob"],
    githubRepo: "https://github.com/roblobsterclaw/trial-ledger-demo",
    githubPages: "",
    localPath: "~/Documents/Codex/Trial Ledger WS",
    branches: ["main"],
    lastUpdated: "2026-05-15",
    notes: "Private repo, Python backend"
  },
  {
    name: "Model Cost Tracker",
    slug: "model-cost-tracker",
    status: "active",
    type: "dashboard",
    description: "AI model spending tracker — monitors OpenRouter, Anthropic costs",
    builtBy: ["rob"],
    githubRepo: "",
    githubPages: "",
    localPath: "~/.openclaw/workspace/projects/model-cost-tracker",
    branches: [],
    lastUpdated: "2026-05-20",
    notes: "JS dashboard + JSON data, local only"
  },
  {
    name: "Daily Reports",
    slug: "daily-reports",
    status: "active",
    type: "document",
    description: "Morning Rundown & Mission Control daily report generator — 89 Word docs",
    builtBy: ["rob"],
    githubRepo: "",
    githubPages: "",
    localPath: "~/.openclaw/workspace/projects/daily",
    branches: [],
    lastUpdated: "2026-05-20",
    notes: "45 Python scripts, generates daily .docx reports"
  },
  {
    name: "Investing Research",
    slug: "investing",
    status: "active",
    type: "research",
    description: "Margin-of-safety engine, deep dives, MOSE data, Truist analysis",
    builtBy: ["rob", "hermes"],
    githubRepo: "",
    githubPages: "",
    localPath: "~/.openclaw/workspace/projects/investing",
    branches: [],
    lastUpdated: "2026-05-15",
    notes: "Python + HTML research, 112 images"
  },
  // === WEBSITES & GAMES ===
  {
    name: "Document Vault",
    slug: "vault",
    status: "active",
    type: "website",
    description: "Secure document vault — Word docs, Excel files organized by business area",
    builtBy: ["rob"],
    githubRepo: "https://github.com/roblobsterclaw/vault",
    githubPages: "https://roblobsterclaw.github.io/vault/",
    localPath: "~/.openclaw/workspace/projects/vault",
    branches: ["main"],
    lastUpdated: "2026-05-07",
    notes: "154 Word docs, 21 Excel files, password: soccer12"
  },
  {
    name: "Unicorn Factory",
    slug: "unicorn-factory",
    status: "paused",
    type: "dashboard",
    description: "AI-powered deal flow pipeline — 59 business ideas scored and ranked",
    builtBy: ["rob", "hermes"],
    githubRepo: "https://github.com/roblobsterclaw/unicorn-factory",
    githubPages: "https://roblobsterclaw.github.io/unicorn-factory/",
    localPath: "~/.openclaw/workspace/projects/unicorn-factory",
    branches: ["main"],
    lastUpdated: "2026-05-04",
    notes: "Scout cron paused per Joe"
  },
  {
    name: "Arcade — Joe's Old Time Video Games",
    slug: "arcade",
    status: "active",
    type: "game",
    description: "Classic arcade games playable in the browser — Asteroids, Space Invaders, hub",
    builtBy: ["codex", "rob"],
    githubRepo: "https://github.com/roblobsterclaw/arcade",
    githubPages: "https://roblobsterclaw.github.io/arcade/",
    localPath: "~/Documents/Codex/Joes Old Time Video Games",
    branches: ["main"],
    lastUpdated: "2026-05-03",
    notes: "HTML5 browser games"
  },
  {
    name: "Ms. Pac-Man",
    slug: "ms-pacman",
    status: "active",
    type: "game",
    description: "Browser-based Ms. Pac-Man game",
    builtBy: ["rob"],
    githubRepo: "https://github.com/roblobsterclaw/ms-pacman",
    githubPages: "https://roblobsterclaw.github.io/ms-pacman/",
    localPath: "",
    branches: ["main"],
    lastUpdated: "2026-05-19",
    notes: "Not cloned locally"
  },
  {
    name: "Lobster Synth",
    slug: "lobster-synth",
    status: "active",
    type: "app",
    description: "Browser-based synthesizer",
    builtBy: ["rob"],
    githubRepo: "https://github.com/roblobsterclaw/lobster-synth",
    githubPages: "https://roblobsterclaw.github.io/lobster-synth/",
    localPath: "",
    branches: ["main"],
    lastUpdated: "2026-05-19",
    notes: "Not cloned locally"
  },
  {
    name: "Asteroids",
    slug: "asteroids",
    status: "active",
    type: "game",
    description: "Browser-based Asteroids game — standalone version",
    builtBy: ["rob"],
    githubRepo: "https://github.com/roblobsterclaw/asteroids",
    githubPages: "https://roblobsterclaw.github.io/asteroids/",
    localPath: "~/.openclaw/workspace/projects/asteroids",
    branches: ["main"],
    lastUpdated: "2026-04-23",
    notes: ""
  },
  // === BUSINESS PROJECTS ===
  {
    name: "Cassidy's Kitchen",
    slug: "cassidys-kitchen",
    status: "active",
    type: "website",
    description: "Food truck website — restaurant/kitchen site with images",
    builtBy: ["rob"],
    githubRepo: "https://github.com/roblobsterclaw/cassidys-kitchen",
    githubPages: "https://roblobsterclaw.github.io/cassidys-kitchen/",
    localPath: "~/.openclaw/workspace/projects/cassidys-kitchen",
    branches: ["main"],
    lastUpdated: "2026-04-30",
    notes: "63MB repo — largest"
  },
  {
    name: "LBI Athletic Club",
    slug: "lbi-athletic-club",
    status: "active",
    type: "website",
    description: "Community athletic club website for Long Beach Island, NJ",
    builtBy: ["rob"],
    githubRepo: "https://github.com/roblobsterclaw/lbi-athletic-club",
    githubPages: "https://roblobsterclaw.github.io/lbi-athletic-club/",
    localPath: "",
    branches: ["main"],
    lastUpdated: "2026-04-20",
    notes: "Not cloned locally"
  },
  {
    name: "ReBolt",
    slug: "rebolt",
    status: "paused",
    type: "rendering",
    description: "Product renders, pitch deck, prototype tracking — lumber innovation product",
    builtBy: ["codex", "rob"],
    githubRepo: "",
    githubPages: "",
    localPath: "~/Documents/Codex/REBOLT",
    branches: [],
    lastUpdated: "2026-05-05",
    notes: "82 images, git repo but no remote"
  },
  {
    name: "ReBolt Renders",
    slug: "rebolt-renders",
    status: "paused",
    type: "rendering",
    description: "Architectural renderings for ReBolt product line",
    builtBy: ["rob"],
    githubRepo: "",
    githubPages: "",
    localPath: "~/.openclaw/workspace/projects/rebolt-renders",
    branches: [],
    lastUpdated: "2026-04-27",
    notes: "12 render images"
  },
  {
    name: "Firehouse Renderings",
    slug: "firehouse",
    status: "paused",
    type: "rendering",
    description: "Firehouse-to-residence conversion — architectural renderings and plans",
    builtBy: ["codex", "rob"],
    githubRepo: "",
    githubPages: "",
    localPath: "~/Documents/Codex/FIREHOUSE RENDERING",
    branches: [],
    lastUpdated: "2026-05-07",
    notes: "26 images + presentations. Also at ~/.openclaw/workspace/projects/firehouse (38 images)"
  },
  {
    name: "Equipment Scout",
    slug: "equipment-scout",
    status: "paused",
    type: "app",
    description: "Equipment search tool with scrapers — find deals on heavy equipment",
    builtBy: ["codex"],
    githubRepo: "",
    githubPages: "",
    localPath: "~/Documents/Codex/equipment-scout-app",
    branches: [],
    lastUpdated: "2026-05-14",
    notes: "Python app, git but no remote"
  },
  // === DOCUMENTS & RESEARCH ===
  {
    name: "Document Vault (Local Backup)",
    slug: "document-vault-local",
    status: "active",
    type: "document",
    description: "Local backup of online Document Vault — 154 Word docs, 21 Excel files",
    builtBy: ["joe", "rob"],
    githubRepo: "",
    githubPages: "",
    localPath: "~/Documents/Document Vault",
    branches: [],
    lastUpdated: "2026-05-07",
    notes: "Mirrors online vault. Categories: Research, ReBolt, Investing, Family, Firehouse, Tuckerton, Surfbox, Lobster Press, Rundowns"
  },
  {
    name: "HSA vs HRA Research",
    slug: "hsa-hra",
    status: "archived",
    type: "research",
    description: "Health Savings Account vs Health Reimbursement Arrangement comparison",
    builtBy: ["codex"],
    githubRepo: "",
    githubPages: "",
    localPath: "~/Documents/Codex/HSA vs HRA Research",
    branches: [],
    lastUpdated: "2026-05-05",
    notes: "Research project"
  },
  {
    name: "KW Coffee Room",
    slug: "kw-coffee-room",
    status: "archived",
    type: "rendering",
    description: "Keller Williams office coffee room concept images",
    builtBy: ["codex"],
    githubRepo: "",
    githubPages: "",
    localPath: "~/Documents/Codex/KW coffee room",
    branches: [],
    lastUpdated: "2026-05-03",
    notes: "10 images"
  },
  {
    name: "Social Media",
    slug: "social-media",
    status: "paused",
    type: "document",
    description: "Social media content and strategy planning",
    builtBy: ["rob"],
    githubRepo: "",
    githubPages: "",
    localPath: "~/.openclaw/workspace/projects/social-media",
    branches: [],
    lastUpdated: "2026-04-27",
    notes: "Python + documents"
  },
  {
    name: "Ceremony",
    slug: "ceremony",
    status: "archived",
    type: "document",
    description: "Event/ceremony planning documents",
    builtBy: ["rob"],
    githubRepo: "",
    githubPages: "",
    localPath: "~/.openclaw/workspace/projects/ceremony",
    branches: [],
    lastUpdated: "2026-04-27",
    notes: "3 Word docs"
  },
  {
    name: "TLC (Tuckerton Lumber)",
    slug: "tlc",
    status: "active",
    type: "document",
    description: "Tuckerton Lumber Co. — documents, zoning, business files",
    builtBy: ["rob"],
    githubRepo: "",
    githubPages: "",
    localPath: "~/.openclaw/workspace/projects/tlc",
    branches: [],
    lastUpdated: "2026-04-27",
    notes: "HTML + documents + images, includes zoning subfolder"
  },
  {
    name: "Web Clients",
    slug: "web-clients",
    status: "archived",
    type: "website",
    description: "LBI Athletic Club client site — early version",
    builtBy: ["rob"],
    githubRepo: "",
    githubPages: "",
    localPath: "~/.openclaw/workspace/projects/web-clients",
    branches: [],
    lastUpdated: "2026-04-19",
    notes: "HTML website"
  },
  {
    name: "World Cup Pool Preview",
    slug: "roblobstercup-preview",
    status: "archived",
    type: "website",
    description: "Preview/teaser site for Rob Lobster Cup XXIII",
    builtBy: ["rob"],
    githubRepo: "https://github.com/roblobsterclaw/roblobstercup-xxiii-preview",
    githubPages: "https://roblobsterclaw.github.io/roblobstercup-xxiii-preview/",
    localPath: "",
    branches: ["main"],
    lastUpdated: "2026-05-08",
    notes: "Not cloned locally"
  },
  {
    name: "TTD Dashboard v1",
    slug: "ttd-v1",
    status: "archived",
    type: "dashboard",
    description: "Original TTD dashboard — replaced by JFL TTD v5",
    builtBy: ["rob"],
    githubRepo: "https://github.com/roblobsterclaw/ttd",
    githubPages: "https://roblobsterclaw.github.io/ttd/",
    localPath: "~/.openclaw/workspace/projects/ttd-dashboard",
    branches: ["main"],
    lastUpdated: "2026-05-04",
    notes: "Legacy — redirects to jfl-ttd"
  },
  {
    name: "MOSE Project (Next.js)",
    slug: "mose-nextjs",
    status: "archived",
    type: "app",
    description: "Next.js/TypeScript version of MOSE — superseded by current HTML dashboard",
    builtBy: ["codex"],
    githubRepo: "",
    githubPages: "",
    localPath: "~/Documents/Codex/MOSE PROJECT",
    branches: [],
    lastUpdated: "2026-05-02",
    notes: "Supabase backend, not in use"
  },
  {
    name: "Rob Lobster Cup Rebuild",
    slug: "cup-rebuild",
    status: "paused",
    type: "app",
    description: "Next.js rebuild of World Cup Pool — Supabase auth",
    builtBy: ["rob"],
    githubRepo: "",
    githubPages: "",
    localPath: "~/Documents/New project/rob-lobster-cup-rebuild",
    branches: [],
    lastUpdated: "2026-05-08",
    notes: "Next.js/TypeScript, paused in favor of static site"
  },
  {
    name: "General Mini Projects",
    slug: "general",
    status: "archived",
    type: "research",
    description: "Mixed bag — GLP1/T1D report, equipment tracker, portable storage survey",
    builtBy: ["codex"],
    githubRepo: "",
    githubPages: "",
    localPath: "~/Documents/Codex/General (mini projects & chats)",
    branches: [],
    lastUpdated: "2026-05-01",
    notes: "Miscellaneous Codex Desktop outputs"
  },
  {
    name: "Claude History Archive",
    slug: "claude-history",
    status: "archived",
    type: "document",
    description: "Exported Claude conversation history",
    builtBy: ["joe"],
    githubRepo: "",
    githubPages: "",
    localPath: "~/.openclaw/workspace/projects/claude-history",
    branches: [],
    lastUpdated: "2026-04-01",
    notes: "4 JSON files"
  },
  {
    name: "Idea Factory",
    slug: "idea-factory",
    status: "archived",
    type: "app",
    description: "Idea generation and evaluation tool — predecessor to Unicorn Factory",
    builtBy: ["rob"],
    githubRepo: "",
    githubPages: "",
    localPath: "~/.openclaw/workspace/projects/idea-factory",
    branches: [],
    lastUpdated: "2026-04-27",
    notes: "Python + documents, superseded by Unicorn Factory"
  },
  // === LIBRARY META ===
  {
    name: "Project Library",
    slug: "library",
    status: "active",
    type: "dashboard",
    description: "THIS dashboard — the master directory for all projects",
    builtBy: ["claude-code", "hermes"],
    githubRepo: "https://github.com/roblobsterclaw/library",
    githubPages: "https://roblobsterclaw.github.io/library/",
    localPath: "~/Documents/GitHub/library",
    branches: ["main"],
    lastUpdated: "2026-05-20",
    notes: "You are here!"
  }
];
```

## Functional Requirements

### Search
- Real-time filtering as user types in search box
- Search across: name, description, notes, localPath
- Case-insensitive

### Filters
- Status filter (All, Active, Paused, Archived, Idea) — pill buttons, one active at a time
- Type filter (dropdown or pills): All Types, Dashboard, Website, App, Document, Game, Research, Rendering
- Agent filter (dropdown or pills): All Agents, Rob 🦞, Hermes ⚡, Claude Code 🔧, Codex 🔨, Joe 👤
- Filters combine (AND logic) — e.g., Active + Dashboard shows only active dashboards
- Show count of matching results

### Cards
- Tapping the card name or a "Live Site" button opens the GitHub Pages URL in a new tab
- "GitHub" button opens the repo in a new tab
- If no live site exists, show the local path instead
- Status badge colors: Active=#238636, Paused=#D29922, Archived=#6E7681, Idea=#1F6FEB
- Agent icons should be small emoji badges in a row

### Stats Bar
- Dynamically calculated from the PROJECTS array
- Show: Total | Active | Live on Web | On GitHub

### Responsive
- Mobile (< 640px): 1 column, full-width cards, larger tap targets
- Tablet (640-1024px): 2 columns
- Desktop (> 1024px): 3 columns

### Sorting
- Default sort: Active first, then by lastUpdated descending
- Projects with live sites should feel prominent

## DO NOT
- Do not use React, Vue, or any framework
- Do not use external CSS or JS files
- Do not make any API calls
- Do not add authentication
- Do not split into multiple files — everything in index.html
- Do not use tables — use CSS grid for the card layout

## WHEN DONE
- Save the file as index.html in the current working directory
- The file should be complete and ready to deploy
- Test that it renders properly by checking the HTML is valid
