# claude-global-config

Personal Claude Code config: global instructions and custom skills.

## Layout
```
CLAUDE.md                      # global instructions
.claude/skills/<skill-name>/   # one folder per skill
  SKILL.md                     # required: frontmatter (name, description) + instructions
  scripts/, references/        # optional helper files
.claude/skills/_template/      # copy this to start a new skill
```

## Add a custom skill
```bash
cp -r .claude/skills/_template .claude/skills/my-new-skill
# edit .claude/skills/my-new-skill/SKILL.md (set name + description)
```

## Install an existing skill from the community
```bash
npx skills add <owner>/<repo> --skill <skill-name> -a claude-code
```

## Use globally (all projects)
```bash
cp -r .claude/skills/* ~/.claude/skills/
cp CLAUDE.md ~/.claude/CLAUDE.md
```

## Superpowers
Skills copied from https://github.com/obra/superpowers (MIT, see .claude/skills/SUPERPOWERS-LICENSE), without its SessionStart hook. Upload each skill folder as its own ZIP.

## gstack
All 62 gstack skills (https://github.com/garrytan/gstack, MIT) bundled as ONE skill at `.claude/skills/gstack` (router SKILL.md + references/<name>/GUIDE.md), because claude.ai accepts one skill per ZIP. Markdown only: no binaries, hooks or setup.
