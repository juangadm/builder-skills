# Builder Skills

Claude Code skills for people who build products. Clone real UIs and turn ideas into specs — all from the terminal.

## Skills

| Skill | What it does | Status |
|-------|-------------|--------|
| [dupe](./skills/dupe/) | Clone any website into working code via DOM extraction | v0.2 — finalizing |
| [product-pathing](./skills/product-pathing/) | Frame → Research → Path workflow for product specs | Ready |

## Install

### Option 1: Install all skills

```bash
claude plugin install juangadm/builder-skills
```

### Option 2: Install individually

Copy the `skills/{name}/` folder into your project's `.claude/skills/` directory:

```bash
# Example: install just product-pathing
cp -r skills/product-pathing/ .claude/skills/product-pathing/
```

### Looking for pre-post?

pre-post now lives in its own repo. Install it with: `npx skills add juangadm/pre-post -y`

### Requirements

- **dupe** requires [Playwright MCP](https://github.com/anthropics/mcp-playwright) — the skill will prompt you if it's missing
- **product-pathing** has no dependencies

## Skill Details

### dupe

Clone a live website into editable HTML/CSS/JS. Extracts real DOM structure, computed styles, dimensions, and interactions — not screenshots.

```
/dupe https://try.ramp.com
```

**Includes:** SKILL.md + 3 phase files (extract, build, verify) + 12 browser scripts + extraction reference doc

**Use case:** Clone Ramp's dashboard, add your proposed feature, demo it in an interview.

### product-pathing

Three-phase workflow: Frame the problem, research the evidence, converge on a direction. Outputs `path-draft.md` + validation plan.

**Includes:** SKILL.md (self-contained)

**Use case:** You have a feature idea. Structure your thinking, run competitive research, produce a tight spec — all in one session.

## Structure

```
skills/
├── dupe/
│   ├── SKILL.md              # Orchestrator (5-phase pipeline)
│   ├── phases/               # Extract, build, verify phase prompts
│   ├── scripts/              # Playwright browser_evaluate scripts
│   └── references/           # Extraction format reference
└── product-pathing/
    └── SKILL.md              # Frame → Research → Path workflow
```

## Contributing

Use a skill on a real task and report what breaks. That's the most valuable contribution.

## License

MIT
