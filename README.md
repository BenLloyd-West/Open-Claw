# Open-Claw · Task Dashboard

A lightweight GitHub-hosted task management system for agentic workflows.

## Architecture

```
.github/
  ISSUE_TEMPLATE/task.yml   → Structured task form (started_at, finished_at, models_used, duration)
  workflows/
    task-automation.yml     → Auto-stamps timestamps + syncs data/tasks.json
    pages.yml               → Deploys dashboard to GitHub Pages
data/
  tasks.json                → Source of truth for dashboard (auto-generated)
dashboard/
  index.html                → Kanban board + completed tasks view (GitHub Pages)
```

## How It Works

1. **Create a task** → Open a GitHub Issue using the Task template
2. **Label it `status: in-progress`** → `started_at` is auto-stamped
3. **Label it `status: done`** → `finished_at` is stamped + `duration_minutes` calculated
4. **`data/tasks.json`** is automatically synced on every label change
5. **Dashboard** at `https://BenLloyd-West.github.io/Open-Claw` auto-refreshes every 60s

## Labels

### Status
| Label | Meaning |
|-------|---------|
| `status: backlog` | Not started |
| `status: in-progress` | Being worked on |
| `status: blocked` | Waiting on something |
| `status: review` | Needs review |
| `status: done` | Complete |

### Priority
| Label | Meaning |
|-------|---------|
| `priority: p0` | Critical |
| `priority: p1` | High |
| `priority: p2` | Medium |
| `priority: p3` | Low |

## Agentic Model Rules

- **Default:** Use local model for planning, routine coding, refactors
- **Escalate to CodeX** for: complex logic, multi-file architecture, security-sensitive code
- **Log model usage** in each task's `Models Used` field (e.g. `local`, `local→CodeX`)

## Dashboard

Live at: `https://BenLloyd-West.github.io/Open-Claw`

Features:
- Kanban view (backlog → done)
- Filter by status, priority, model
- Completed tasks table with duration + model tracking
- Auto-refreshes every 60 seconds
