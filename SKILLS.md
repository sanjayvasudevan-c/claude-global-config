# Skills installed so far

| Skill | Source | In this repo | Upload ZIP |
| ----- | ------ | ------------ | ---------- |
| find-skills (customized: proactive, security review, persistence) | vercel-labs/skills | `.claude/skills/find-skills` | `upload-zips/find-skills.zip` |
| superpowers (15 skills) | obra/superpowers (MIT) | 15 folders in `.claude/skills/` + `SUPERPOWERS-LICENSE` | `upload-zips/superpowers.zip` (bundled as one skill) |
| gstack (62 guides, markdown only) | garrytan/gstack (MIT) | `.claude/skills/gstack` | `upload-zips/gstack.zip` |
| caveman (core skill) | JuliusBrussee/caveman (Apache-2.0) | `.claude/skills/caveman` | `upload-zips/caveman.zip` |
| skill-creator-custom | anthropics/skills | `.claude/skills/skill-creator-custom` | `upload-zips/skill-creator-custom.zip` |
| mcp-builder-custom | anthropics/skills | `.claude/skills/mcp-builder-custom` | `upload-zips/mcp-builder-custom.zip` |
| webapp-testing | anthropics/skills | `.claude/skills/webapp-testing` | `upload-zips/webapp-testing.zip` |
| context7 (context7-mcp skill) | upstash/context7 | `.claude/skills/context7` | `upload-zips/context7.zip` |
| impeccable | pbakaus/impeccable (Apache-2.0) | `.claude/skills/impeccable` | `upload-zips/impeccable.zip` |
| taste-skill | Leonxlnx/taste-skill | `.claude/skills/taste-skill` | `upload-zips/taste-skill.zip` |
| hyperframes | heygen-com/hyperframes | `.claude/skills/hyperframes` | `upload-zips/hyperframes.zip` |
| ui-ux-pro-max | nextlevelbuilder/ui-ux-pro-max-skill | `.claude/skills/ui-ux-pro-max` | `upload-zips/ui-ux-pro-max.zip` |
| onetake (noncommercial licence; cases/assets/gallery omitted) | feitangyuan/onetake (PolyForm Noncommercial 1.0.0) | `.claude/skills/onetake` | `upload-zips/onetake.zip` |
| gbro-collage-broll (needs GEMINI_API_KEY; written for Codex image_gen) | pyang5166/gbro-collage-broll (MIT) | `.claude/skills/gbro-collage-broll` | `upload-zips/gbro-collage-broll.zip` |

Frontmatter trimmed to claude.ai-allowed keys (impeccable: removed version/user-invocable/argument-hint; taste-skill and context7 renamed to match their folder).

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
