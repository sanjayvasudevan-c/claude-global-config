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
All 62 gstack skills (https://github.com/garrytan/gstack, MIT) bundled as ONE skill at `.claude/skills/gstack` (router SKILL.md + references/<name>/GUIDE.md), because claude.ai accepts one skill per ZIP. One GUIDE.md per skill; no binaries, scripts, hooks or setup.

## Caveman
Core `caveman` skill from https://github.com/JuliusBrussee/caveman (Apache-2.0): terse output to save tokens. Skill only, no hooks or CLI.

## upload-zips/
Ready-to-upload ZIPs for claude.ai (Customize -> Skills): `find-skills`, `superpowers` (15 guides bundled), `gstack` (62 guides bundled), `caveman`, `skill-creator-custom`, `mcp-builder-custom`, `webapp-testing`, `context7`, `impeccable`, `taste-skill`, `hyperframes`, `ui-ux-pro-max`, `onetake`, `gbro-collage-broll`, `ponytail`, `lemo-opuscar`. Each has exactly one top-level folder and one SKILL.md.

## Skills, commands and descriptions

A skill's command is `/<name>`. Descriptions are shortened.

A skill's command is `/<name>`. Descriptions are shortened.
### Your skills (in this repo and uploaded to claude.ai)

| Skill | Command | What it does |
|---|---|---|
| find-skills | `/find-skills <query>` | Finds skills, reviews them for safety, installs them only after you approve. Also runs proactively. |
| caveman | `/caveman` | Terse replies to save tokens. Stays on until you say "stop caveman". |
| gstack | `/gstack`, then guides such as `/office-hours`, `/review`, `/qa`, `/ship`, `/autoplan`, `/cso`, `/investigate` | 62 engineering-team role guides bundled as one skill: planning, design review, code review, QA, security, deploy, retros. |
| superpowers (15 skills) | `/brainstorming`, `/writing-plans`, `/executing-plans`, `/test-driven-development`, `/systematic-debugging`, `/requesting-code-review`, `/receiving-code-review`, `/verification-before-completion`, `/using-git-worktrees`, `/finishing-a-development-branch`, `/dispatching-parallel-agents`, `/subagent-driven-development`, `/writing-skills`, `/using-superpowers`, `/diagnosing-superpowers` | Engineering workflow skills: design before building, plans, TDD, debugging, review, verification, worktrees, parallel agents. |
| skill-creator-custom | `/skill-creator-custom` | Creates, improves and evaluates skills. |
| mcp-builder-custom | `/mcp-builder-custom` | Guide for building MCP servers in Python (FastMCP) or Node/TypeScript. |
| webapp-testing | `/webapp-testing` | Tests local web apps with Playwright: screenshots, UI debugging, browser logs. |
| context7 | `/context7` | Fetches up-to-date library and framework docs and code examples. |
| impeccable | `/impeccable` | Designs, critiques, audits and polishes frontend interfaces. |
| taste-skill | `/taste-skill` | Anti-generic art direction for websites, with a browser inspector. |
| ui-ux-pro-max | `/ui-ux-pro-max` | UI/UX design data: styles, palettes, font pairings, UX guidelines, chart types. |
| hyperframes | `/hyperframes` | Makes and renders videos from HTML: explainers, captions, overlays. |
| onetake | `/onetake` | Short product launch motion videos (10-30 s). Noncommercial licence. |
| gbro-collage-broll | `/gbro-collage-broll` | Paper-collage B-roll from a script line. Needs `GEMINI_API_KEY`. |
| ponytail | `/ponytail [lite\|full\|ultra\|off]` | Smallest-change "lazy senior dev" mode for coding. |
| lemo-opuscar | `/lemo-opuscar` | Short films made in code, in 51 named styles. Downloads its library at run time. |

### Already in Claude Code sessions (not from this repo)

| Group | Commands | What it does |
|---|---|---|
| Claude Code built-ins | `/code-review`, `/simplify`, `/security-review`, `/init`, `/loop`, `/run`, `/update-config`, `/fewer-permission-prompts`, `/keybindings-help`, `/claude-api` | Code review, cleanup, security review, setup, recurring tasks, running the app, settings, Claude API help. |
| Anthropic synced skills | `/anthropic-skills:docx`, `:pdf`, `:pptx`, `:xlsx`, `:docs`, `:google-workspace`, `:deep-research`, `:skill-creator`, `:morning` | Word, PDF, PowerPoint, Excel, docs, Google Workspace files, research reports. |
| Browser and computer | `/anthropic-skills:built-in-browser`, `:chrome-browser`, `:computer-use` | Drive the in-app browser, your Chrome, or your desktop. |
| Remotion | `/remotion:remotion-create`, `:remotion-render`, `:remotion-captions`, and others | Create, preview, render and caption Remotion videos. |
| FFmpeg | `/ffmpeg-llm:ffmpeg`, `/ffmpeg-llm:ffmpeg-command` | Build FFmpeg commands from plain-English requests. |
| Artifacts and charts | `artifact-design`, `artifact-capabilities`, `artifact-diagramming`, `dataviz` | Guidance for published pages and charts. |
| Other | `/plugin-authoring`, `/session-start-hook`, `/import-memory` | Build mods and hooks, import memory from another assistant. |

### Notes
- Some names appear twice in a session (for example `caveman`): one copy is from this repo, one is the claude.ai upload prefixed `anthropic-skills:`.
- Skills from this repo's `.claude/skills/` only load in sessions on this repo. The claude.ai uploads load in your other cloud sessions.
- `/gstack` is one skill with 62 guides inside it, not 62 separate commands.
