# Builder Skills

Claude Code skills for builders — PMs, designers, and engineers who want to move fast from idea to artifact.

Each skill is a standalone tool that plugs into [Claude Code](https://claude.ai/claude-code). They're designed for people who build products: prototype on real UIs, turn ideas into validated paths, ship things that look and work like the real deal.

## Skills

### [dupe](./dupe/)

Clone any live website into working, editable code using DOM extraction. Not screenshots — real structure, styles, dimensions, and interactions extracted from the actual DOM.

**Use case:** You're interviewing at Ramp. Clone their expense dashboard, add your proposed feature, demo a working prototype in the interview.

**Status:** v0.2.0 — works end-to-end, tested against 1 site. Still finalizing.

### [pre-post](./pre-post/)

Before/after screenshot tool for PRs. Captures visual diffs across routes and viewports, uploads images, and generates markdown tables for pull request documentation.

**Use case:** You just changed the dashboard layout. Run pre-post to capture desktop + mobile screenshots of production vs. localhost, then paste the visual diff into your PR.

**Status:** Working CLI + Claude Code skill. Published as `@juangadm/pre-post`.

### [product-pathing](./product-pathing/)

Three-phase workflow for turning a product idea into a validated path forward. Frame the problem, research the evidence, converge on a direction.

**Use case:** You have a feature idea but need to build conviction before committing. Run `/product-pathing` to structure your thinking, gather competitive intel, and produce a tight spec.

**Status:** Ready to use.

## Install

### Dupe

Dupe is a Claude Code plugin (skill + Playwright MCP server bundled together):

```bash
claude plugin install juangadm/builder-skills --dir dupe
```

Then invoke:

```
/dupe:dupe https://example.com
```

> Requires Playwright MCP — auto-configures when the plugin loads.

### Pre-Post

Pre-Post is a CLI tool + Claude Code skill:

```bash
# Install the CLI
npm install -g @juangadm/pre-post

# Or use via npx
npx pre-post compare --before-base https://prod.com --after-base http://localhost:3000
```

As a Claude Code skill, add it to your settings or say "take before and after screenshots" during a session.

### Product Pathing

Product Pathing is a standalone skill. Add it to your Claude Code settings:

```bash
claude skill add juangadm/builder-skills --dir product-pathing
```

Or manually: copy `product-pathing/SKILL.md` to your `.claude/skills/` directory.

Then invoke by saying "path this", "spec this", "scope this", or any product thinking trigger.

## Philosophy

These skills share a design philosophy:

1. **Opinionated, not neutral.** They push back, challenge scope, and recommend directions — not just execute instructions.
2. **Artifact-first.** Every skill produces something tangible: working code, a spec, a research file. No hand-waving.
3. **Token-intensive by design.** They spend compute generously because the alternative (doing it manually) costs hours. Tokens are cheap, time isn't.

## Contributing

Each skill has its own development workflow. See the README in each skill's directory for details.

The most valuable contribution for any skill: **use it on a real task and report what breaks.**

## License

MIT
