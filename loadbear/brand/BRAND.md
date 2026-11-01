# LOADBEAR — Brand Bible

## The one-line
Short-form system design, explained by a calm engineer and an anxious bear who keeps setting the servers on fire.

## Why "LoadBear"
- **Load bearing** — the structural-engineering term. System design *is* architecture.
- **Load balancer / load testing** — the actual vocabulary of the field.
- **Bear** — the mascot comes free with the name. No separate character naming problem.
- One word, one syllable each, spellable after hearing it once, handle-shaped: `@loadbear`.
- Scales into episode and merch titles: *Load Test*, *Bear Minimum* (MVP episodes), *Unbearable Latency*.

## The series thesis (this is the retention engine)
**Every episode breaks what the last episode built.**

Episode 1 builds a load balancer. Episode 2 opens with the load balancer dead.
Each video ends on the failure that the next video solves. The feed becomes a
causal chain instead of a bag of unrelated tips — so the viewer who finishes
one video has a reason to watch the next one, and the series has a spine.

Format name on screen: **THE STACK THAT KEEPS BREAKING**

## Voice
- Kai never condescends and never hypes. Short declarative sentences.
- No "in today's video". No "let's dive in". The first frame is already the problem.
- Real numbers over adjectives: "latency climbs to 4 seconds", not "it gets really slow".
- Every episode names the real term at least once, plainly, so it's searchable.
- One joke per episode, carried by Nines, never by Kai.

## Palette
| Token | Hex | Use |
|---|---|---|
| `ink` | `#0B1220` | Background. Deep navy-black, never pure black. |
| `paper` | `#F4F1EA` | Body text, blueprint lines. Warm off-white. |
| `honey` | `#E8A33D` | **Primary.** Brand marks, Nines' fur, the thing being built. |
| `alert` | `#FF4D3D` | Failure, saturation, the thing on fire. |
| `healthy` | `#2DD4BF` | Working state, passed health checks, resolved. |

Honey-on-navy is the signature. Coral and teal appear **only** as state —
never decoratively — so the viewer learns to read colour as status.

## Type
- **Display / wordmark:** geometric sans, tight tracking, heavy weight (Outfit, Satoshi, Poppins SemiBold).
- **Technical labels, counters, code:** JetBrains Mono.
- **Captions (burned in, always):** geometric sans Bold, `paper` on a 70%-opacity `ink` slab, 2–4 words per card, bottom third but above the Instagram UI safe area.

## Logo
**Mark:** a bear head whose silhouette is drawn as a node graph — two ear nodes,
two cheek nodes, one chin node, connected by straight edges, with the interior
filled `honey`. Reads as a bear at 1024px and as a hexagonal mark at 40px.

**Wordmark:** `LOADBEAR` set solid, no space, tight tracking, `paper` on `ink`.

**Lockups:** (1) mark + wordmark horizontal, for the profile banner.
(2) mark alone, circular `honey` on `ink`, for the avatar.
(3) mark at 60% opacity, bottom-right corner bug, present in every frame of every video.

**Rules:** never rotate; never gradient; never outline the wordmark; the mark's
interior is always a single flat fill.

## Grid / format
- 1080 × 1920, 30fps.
- Safe area: 220px top, 420px bottom (Instagram caption + UI).
- Faint `paper` blueprint grid at 6% opacity over `ink`, always. It is the stage.
- Kai anchors frame-right, Nines frame-left. Never swapped — the viewer should
  know who is speaking before reading a word.
