# openclaw-skills

Personal [OpenClaw](https://openclaw.ai) agent skills. Synced via git.

## Skills

| Skill | Description | Requires |
|-------|-------------|----------|
| [linear](./linear/) | Query and manage Linear issues, projects, and team workflows |  |

## Structure

Each skill follows the OpenClaw skill format:

```
<skill-name>/
├── SKILL.md          # Agent instructions (loaded as context)
├── scripts/          # Bash/Python scripts the agent can call
│   └── *.sh
└── _meta.json        # Version and ownership metadata
```

## Workflow

```bash
# Edit a skill
nano ~/.openclaw/workspace/skills/<skill>/SKILL.md

# Push changes to GitHub
skills-sync push

# Pull latest from GitHub (e.g. edited on another machine)
skills-sync pull

# Add a new skill manually
mkdir -p ~/.openclaw/workspace/skills/my-skill/scripts
# ... create SKILL.md ...
skills-sync push
```

## Adding a new skill

1. Create a folder under `~/.openclaw/workspace/skills/<name>/`
2. Add a `SKILL.md` with the frontmatter header:

```markdown
---
name: my-skill
description: What this skill does.
---

# My Skill

Instructions for the agent...
```

3. Optionally add scripts in `scripts/` and reference them with `{baseDir}/scripts/`
4. Run `skills-sync push`

## Install on a new machine

```bash
# Clone into OpenClaw workspace
git clone git@github.com:pepajimenezrovira-sys/openclaw-skills.git ~/.openclaw/workspace/skills

# Install the sync helper
curl -sL https://raw.githubusercontent.com/pepajimenezrovira-sys/openclaw-skills/main/bin/skills-sync -o /usr/local/bin/skills-sync
chmod +x /usr/local/bin/skills-sync
```
