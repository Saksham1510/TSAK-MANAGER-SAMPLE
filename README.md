# TaskFlow — Project Management App

A full-featured project management web application with role-based access control, task tracking, and team collaboration — all in a single HTML file with zero dependencies except Google Fonts.

## 🚀 Live Demo

Open `index.html` in any browser, or deploy to Railway/Netlify/Vercel in seconds.

**Demo Credentials:**
| Email | Password | Role |
|---|---|---|
| alice@demo.com | demo123 | **Admin** |
| bob@demo.com | demo123 | Member |
| carol@demo.com | demo123 | Member |

---

## ✅ Features

### Authentication
- Signup / Login with validation
- Session persistence via localStorage
- Role selection on signup (Admin / Member)



### Projects
- Create, edit, and delete projects (Admin only)
- Custom color, emoji, and status per project
- Progress tracking (% based on tasks)
- Member management per project
- Filter tasks by status, priority, assignee

### Tasks
- Create, assign, and update tasks
- Priority levels: High / Medium / Low
- Statuses: To Do → In Progress → In Review → Done
- Due date with overdue detection
- Quick-complete toggle
- **List view** and **Kanban board** view

### Dashboard
- Greeting + stats overview
- Task completion metrics
- Overdue alerts
- Recent activity feed
- Project progress summary

### Team Management (Admin)
- View all team members
- Change member roles
- Add members to projects
- Remove members from projects / system

### Data Persistence
- All data stored in `localStorage` (no server needed)
- Session persists across browser refresh

---

## 🏗️ Tech Stack

| Layer | Technology |
|---|---|
| Frontend | Vanilla HTML5 / CSS3 / JavaScript (ES6+) |
| Storage | localStorage (key-value, JSON) |
| Fonts | DM Sans, DM Mono (Google Fonts) |
| Architecture | Single-file SPA, event-driven rendering |

> **No frameworks. No build tools. No server required.**

---

## 🌐 Deployment

### Option 1: Railway (Static)
1. Push the `project-manager/` folder to a GitHub repo
2. Go to [railway.app](https://railway.app) → New Project → Deploy from GitHub
3. Railway auto-detects the static HTML file
4. Get your live URL instantly

### Option 2: Netlify (Drag & Drop)
1. Go to [netlify.com](https://netlify.com) → Add new site → Deploy manually
2. Drag the `project-manager/` folder onto the deploy zone
3. Live in seconds

### Option 3: GitHub Pages
1. Push to a GitHub repo
2. Settings → Pages → Deploy from branch → `main / root`
3. Access at `https://username.github.io/repo-name/`

### Option 4: Vercel
```bash
npm i -g vercel
cd project-manager
vercel
```

---

## 📁 Project Structure

```
project-manager/
├── index.html    # Complete application (HTML + CSS + JS)
└── README.md     # This file
```

The entire app is **one self-contained file** — no build step, no package.json, no node_modules.

---

## 🔑 Key Design Decisions

1. **Single-file architecture** — Zero setup, deploy anywhere, works offline
2. **localStorage as database** — All CRUD operations persist across sessions
3. **Role-based rendering** — UI components conditionally render based on user role
4. **No framework dependencies** — Pure vanilla JS with a custom reactive render loop
5. **Relational data model** — Users → Projects → Tasks with ID references

---

## 📊 Data Model

```
Users     { id, name, email, password, role, avatar, color, joinedAt }
Projects  { id, name, description, color, emoji, status, members[], createdBy, createdAt }
Tasks     { id, projectId, title, description, priority, status, assigneeId, dueDate, tags[], createdBy, createdAt }
Activity  { id, userId, action, target, at }
```

---

## 🛡️ Validations

- Login: email + password required, must match existing user
- Signup: all fields required, unique email enforced
- Project: name required
- Task: title required
- Role checks on all admin-only actions (enforced in both UI and action layer)

---

## 📝 Notes for Reviewers

- This is a **client-side-only** implementation using localStorage as the data layer
- For a production backend version, replace the `DB.*` functions with REST API calls to an Express/Django/FastAPI backend with a real SQL/NoSQL database
- All RBAC logic is enforced in the JavaScript action layer, not just the UI
- The app ships with 3 demo users, 3 projects, and 9 tasks pre-loaded

---

## 📜 License

MIT — free to use, modify, and deploy.
