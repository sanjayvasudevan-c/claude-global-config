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
