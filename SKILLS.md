# Skills installed so far

| Skill | Source | In this repo | Upload ZIP |
| ----- | ------ | ------------ | ---------- |
| find-skills (customized: proactive, security review, persistence) | vercel-labs/skills | `.claude/skills/find-skills` | `upload-zips/find-skills.zip` |
| superpowers (15 skills) | obra/superpowers (MIT) | 15 folders in `.claude/skills/` + `SUPERPOWERS-LICENSE` | `upload-zips/superpowers.zip` (bundled as one skill) |
| gstack (62 guides, markdown only) | garrytan/gstack (MIT) | `.claude/skills/gstack` | `upload-zips/gstack.zip` |
| caveman (core skill) | JuliusBrussee/caveman (Apache-2.0) | `.claude/skills/caveman` | `upload-zips/caveman.zip` |

## Plugin install (not a file in this repo)
Caveman full plugin (hooks, auto-activates). Run on your own machine; cloud containers are temporary.

```bash
claude plugin marketplace add JuliusBrussee/caveman
```

```bash
claude plugin install caveman@caveman
```

## Persistence
- Upload each ZIP at claude.ai -> Customize -> Skills (one skill per ZIP), enable it, start a new session, check `/skills`.
- Project `.claude/skills` only load in sessions opened on that repo/branch.
