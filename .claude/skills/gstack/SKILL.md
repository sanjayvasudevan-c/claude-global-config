---
name: gstack
description: Virtual engineering team (gstack by Garry Tan) - 62 role guides for product strategy, planning, design review, code review, QA, security audit, debugging, shipping/deploy, retros. Use for non-trivial product or engineering work; open only the single guide matching the task (/office-hours, /review, /qa, /ship, /autoplan, /investigate, /cso ...).
license: MIT
---

# gstack (bundled)

Router for 62 role guides. Read ONLY the guide(s) matching the task; never load them all.

Open `references/<name>/GUIDE.md` and follow it. Each guide is a single file; helper scripts, templates and checklists it mentions are not bundled.

| Guide | What it is |
| ----- | ---------- |
| `autoplan` | Auto-review pipeline — reads the full CEO, design, eng, and DX review skills from disk and runs |
| `benchmark` | Web performance regression detection. (gstack) |
| `benchmark-models` | Cross-model benchmark for gstack skills. (gstack) |
| `browse` | Drive a real browser through Aside: open a page, read it, click through a flow, take screenshot |
| `canary` | Post-deploy canary monitoring. (gstack) |
| `captain` | Run a crew of coding agents from one controller (also /crew): lanes send READY blocks and never |
| `careful` | Safety guardrails for destructive commands. (gstack) |
| `codex` | OpenAI Codex CLI wrapper — three modes. (gstack) |
| `connect-chrome` | Launch GStack Browser — AI-controlled Chromium with the sidebar extension baked in. |
| `context-restore` | Restore working context saved earlier by /context-save. (gstack) |
| `context-save` | Save working context. (gstack) |
| `cso` | Security audit: supported static findings; qualified profiles add reproduction and repair candi |
| `design-consultation` | Design consultation: understands your product, researches the landscape, proposes a complete de |
| `design-html` | Design finalization: generates production-quality Pretext-native HTML/CSS. (gstack) |
| `design-motion` | Design motion: animate an approved design into a seamless MP4 and GIF loop. (gstack) |
| `design-review` | Designer's eye QA: finds visual inconsistency, spacing issues, hierarchy problems, AI slop patt |
| `design-shotgun` | Design shotgun: generate multiple AI design variants, open a comparison board, collect structur |
| `deslop-shared-libs` | Find worthwhile shared-code extractions in recent work. (gstack) |
| `devex-review` | Live developer experience audit. (gstack) |
| `diagram` | Turn an English description (or mermaid source) into a diagram triplet: the source, an editable |
| `document-generate` | Generate missing documentation from scratch for a feature, module, or entire project. (gstack) |
| `document-release` | Release documentation audit. (gstack) |
| `eval-plan` | Preregister a paid eval (bars, arms, decoys, stop rules), dry-run it at zero cost, then run a t |
| `freeze` | Restrict file edits to a specific directory for the session. (gstack) |
| `gstack-upgrade` | Upgrade gstack to the latest version. |
| `guard` | Full safety mode: destructive command warnings + directory-scoped edits. (gstack) |
| `health` | Code quality dashboard. (gstack) |
| `investigate` | Systematic debugging with root cause investigation. (gstack) |
| `ios-clean` | Remove the DebugBridge SPM package and all #if DEBUG wiring from an iOS app. (gstack) |
| `ios-design-review` | Visual design audit for iOS apps on real hardware. (gstack) |
| `ios-fix` | Autonomous iOS bug fixer. (gstack) |
| `ios-qa` | Live-device iOS QA for SwiftUI apps. (gstack) |
| `ios-sync` | Regenerate the iOS debug bridge against the latest upstream gstack templates. (gstack) |
| `land-and-deploy` | Land and deploy workflow. (gstack) |
| `landing-report` | Read-only queue dashboard for workspace-aware ship. (gstack) |
| `learn` | Manage project learnings. |
| `make-pdf` | Turn any markdown file into a publication-quality PDF. (gstack) |
| `modernize` | Bring an aging pull request onto its current base and decide whether it should still exist: MOD |
| `office-hours` | YC Office Hours — two modes. (gstack) |
| `open-gstack-browser` | Launch GStack Browser — AI-controlled Chromium with the sidebar extension baked in. |
| `pair-agent` | Pair a remote AI agent with your browser. (gstack) |
| `plan-ceo-review` | CEO/founder-mode plan review. (gstack) |
| `plan-design-review` | Designer's eye plan review — interactive, like CEO and Eng review. (gstack) |
| `plan-devex-review` | Interactive developer experience plan review. (gstack) |
| `plan-eng-review` | Eng manager-mode plan review. (gstack) |
| `plan-tune` | Self-tuning question sensitivity + developer psychographic for gstack (v1: observational). (gst |
| `qa` | Fix browser/API/CLI/job/worker/webhook bugs. (gstack) |
| `qa-only` | Report browser/API/CLI/job/worker/webhook bugs. (gstack) |
| `retro` | Weekly engineering retrospective. (gstack) |
| `review` | Pre-landing PR review. (gstack) |
| `scrape` | Pull data from a web page through the Aside browser — your real, already signed-in sessions. (g |
| `setup-browser-cookies` | Import cookies from your real Chromium browser into the headless browse session. (gstack) |
| `setup-deploy` | Configure deployment settings for /land-and-deploy. |
| `setup-gbrain` | Set up gbrain for this coding agent: install the CLI, initialize a local PGLite or Supabase bra |
| `ship` | Ship workflow: detect + merge base branch, run tests, review diff, bump VERSION, update CHANGEL |
| `skillify` | Codify the most recent successful /scrape flow into a permanent browser-skill on disk. (gstack) |
| `spec` | Turn vague intent into a precise, executable spec in five phases. (gstack) |
| `sync-gbrain` | Keep gbrain current with this repo's code and refresh agent search guidance in CLAUDE.md. (gsta |
| `test-audit` | Find low-value or duplicate tests and the test-only code they keep alive. (gstack) |
| `ubicloud` | Run a heavy suite, build or eval on an ephemeral 16-vCPU Ubicloud VM: TTL-named VMs, a reaper,  |
| `unfreeze` | Clear the freeze boundary set by /freeze, allowing edits to all directories again. (gstack) |
| `write-skill` | Write a new agent skill or improve one without bloat: the edit ladder, levels, drift and size c |

## Notes
- Original slash commands (`/review`, `/qa` ...) map to the guide of the same name. If the user types one, open that guide.
- Overview of the whole system: `references/_overview/GUIDE.md`.
- This is the markdown-only bundle. Guides that call gstack binaries (`browse`, `gstack-*` helpers), compiled tools, hooks or `./setup` will not have them here; do that step manually or tell the user it needs a full local install (https://github.com/garrytan/gstack).
- Frontmatter in guides (`hooks`, `allowed-tools`, `triggers`) is informational only in this bundle.
