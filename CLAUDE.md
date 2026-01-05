# Suntree Projects Documentation

Hugo-based documentation site for tracking home renovation projects.

## Task Tracking System

### Effort Scale

Tasks are weighted by effort, not just counted. Use these sizes:

| Size | Points | Time Estimate |
|------|--------|---------------|
| quick | 1 | ≤2 hours |
| small | 2 | 2-4 hours |
| medium | 3 | 1-2 days |
| large | 5 | 3-5 days |
| major | 10-15 | 1-2 weeks |

### Front Matter

Each page tracks aggregated effort points:

```yaml
---
title: "Room Name"
tasks_completed: 45
tasks_in_progress: 7
tasks_planned: 15
---
```

### Task Format

Tasks use status emoji with size in HTML comments. Groupings are H2 headings:

```markdown
## Shower
- ✅ Replace mixer valve <!-- quick -->
- 🔄 Repair subfloor <!-- medium -->
- ⏳ Install tile <!-- medium -->

## Electrical
- ✅ Replace outlets <!-- small -->
- ⏳ Install overhead lights <!-- large -->
```

Status is indicated by emoji only (no Completed/In Progress/Planned headings):
- ✅ = completed
- 🔄 = in progress
- ⏳ = planned

This allows all tasks for a grouping to appear together regardless of status.

### Progress Bars

Progress bars display automatically via Hugo partials:
- Section pages (`_index.md`) aggregate child page totals
- Room pages show their own front matter values
- Landing page shows overall and per-section progress

## File Structure

```
content/docs/
├── _index.md          # Landing page with overall progress
├── effort-scale.md    # Reference page for the scale
├── first-floor/
│   ├── _index.md      # Section index
│   ├── flooring.md
│   ├── family-room.md
│   └── ...
├── second-floor/
├── outside/
├── basement/
├── garage/
└── attic/
```

## Commands

```bash
# Local development
hugo server -D

# Build
hugo --minify

# Deploy (automatic via GitHub Actions on push to main)
git push
```
