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

Tasks use status emoji with size in HTML comments:

```markdown
## Completed
- ✅ Task description <!-- medium -->

## In Progress
- 🔄 Task description <!-- small -->

## Planned
- ⏳ Task description <!-- large -->
```

### Groupings

Related tasks can be grouped under H3 headings within status sections:

```markdown
## Completed

### Fireplace Overhaul
- ✅ Demo old surround <!-- small -->
- ✅ Install new mantel <!-- medium -->

### Electrical
- ✅ Replace outlets <!-- small -->
```

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
