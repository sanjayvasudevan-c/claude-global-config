# Production pipeline

One episode, start to finish. Steps 1–3 are the ones that decide whether the
video is good; everything after is execution.

## 1. Pick the machine (do this first, always)
Before any script. Name the one physical object that *is* the concept.

A good machine metaphor:
- has **visible internal state** you can watch change (fill levels, a queue, a
  valve, a switch),
- can **fail in an obvious physical way**,
- is a real object the viewer has seen, not an invented abstraction.

If you can't draw its failure, it's the wrong metaphor. Go back.

## 2. Write the beat sheet, not prose
Columns: `time · VO · machine state · HUD values · mascot pressure`.
One fact per beat. ~6s per beat, ~20–24 beats for a 2:15 episode.

The HUD and the mascot are not decoration — they are a second and third
channel of information running in parallel with the voice. If a beat doesn't
change at least one of them, the beat is dead. Cut it.

## 3. Cold open and cliffhanger
- **First 2 seconds are the failure**, not an introduction. No "today we're
  looking at". The machine is already broken when the video starts.
- **Last beat breaks the thing just built** and names the next episode.

## 4. Assets
Reuse before generating. The machine is built from a standing parts library
(rack, pipe, valve, conveyor, gauge, crate) so episodes share a visual world
and get cheaper over time. Only genuinely new parts get drawn.

## 5. Animate
Vertical 1080×1920 @30fps. Layout per `brand/FORMAT.md` — top section label and
beat counter, centre stage, Dr. Sparks lower-left, bottom HUD strip.

Motion rules: **snap, don't glide.** Parts move on 2s with hard eases. No
smooth drifting, no slow fades — flat cartoon moves in decisive steps. The only
continuous motion is flow (items moving through the machine).

Candidate tooling, all already available in this workspace:
- `hyperframes` — HTML rendered to video; best fit for the HUD, captions and
  vertical layout, since the HUD is literally text and boxes.
- `remotion:*` — React video, strong captions support.
- `onetake` — single HTML composition driven by time, with shutter motion blur.

## 6. Voice
Dr. Sparks: short declarative sentences, real numbers, delighted when things
break. Record or synthesise, then time the beat sheet to the actual audio —
never the other way round.

## 7. Captions
Burned in, always. 3–5 words, karaoke highlight (spoken solid, upcoming at
35%), on a flat slab with a hard border. Bottom third but **above** the
Instagram UI safe area — 420px bottom margin.

## 8. Ship
Export H.264, 1080×1920, 30fps. Cover frame is the beat where the machine is
most obviously broken — not the title card.
