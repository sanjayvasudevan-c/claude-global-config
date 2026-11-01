# Format spec — derived from reference analysis

Source: two reference videos, 1080x1920 @30fps, 154s and 134s.
~68 beats in 154s = **2.2s per beat**. These are 2-2.5 min vertical
explainers, not 30s shorts.

## The core idea (this is the whole format)
**An abstract system is rendered as one tangible physical machine, and the
video is that machine changing state.**

- Load balancing -> an industrial parcel sorter ("SORTER-01"): conveyor feeds
  cubes into a hopper, a rotating arm flicks each cube down a chute into one of
  three server racks, fill-bars rise.
- File systems -> a wooden card-catalog cabinet with labelled drawers.

The metaphor is picked first. The script is then written as *operations on that
object*. Nothing is explained in the abstract.

## Layout (fixed, every frame)
```
+--------------------------------------------------+
| SECTION LABEL            12/68  ====----------    |  top: section + beat counter + progress
|                                                   |
|           [ THE MACHINE - the whole stage ]       |  center: the metaphor object
|                                                   |
|  [char]   +-----------------------------------+   |  character: lower-LEFT, small,
|           | LABEL      value   LABEL   value  |   |  full-body, standing, static
|           +-----------------------------------+   |  bottom HUD: live metrics strip
|        [ caption slab: 3-5 words ]                |
+--------------------------------------------------+
```

- **Character never overlaps the diagram.** It is a presenter standing beside a
  display, not a character in a scene. Small — roughly 1/5 of frame height.
- **Top strip:** section name in letterspaced mono caps, beat counter `27/68`,
  segmented progress bar. Tells the viewer "this is going somewhere, you are
  40% through" — a retention device.
- **Bottom HUD:** black strip, mono, 2-4 live readouts that *change with the
  animation*: `BACKENDS 3 / ACTIVE 14` -> `HEALTH 2/3 UP / FAILED 3` ->
  `TRAFFIC 10,000/s`. This is what makes it feel like an instrument rather than
  a slideshow.
- **Captions:** burned in, 3-5 words, **karaoke highlight** — words already
  spoken are solid, the rest of the line is faded. Dark slab on light bg,
  light slab on dark bg.

## Colour behaviour
Both videos use **one accent that encodes quantity/flow** (orange: requests,
fill levels, current values) plus semantic state (green dot = healthy, red =
failed). Machinery is desaturated grey-blue so the accent always reads.
Backgrounds: warm bone `#EDEBE3` (video 1) or deep navy `#1B2232` (video 2).

## Narration voice
Short declarative second person. One fact per beat. Numbers, not adjectives.
No intro, no "in this video", no sign-off until the final beat.
Observed: *"Every user... the server can't keep up... when a user... everyone
connects... then back to A... another strategy is least connections..."*

## Where we deviate (deliberately)
1. **Original host character.** The references use Rick Sanchez (Adult Swim IP)
   — unusable for a brand: strikes, no merch, no sponsorships.
2. **Two-hander, not a monologue.** A host plus a mascot who argues with him.
   The references are single-narrator. Dialogue gives us: a reason for the
   viewer to stay (tension), a natural place for the dumb question the audience
   is actually thinking, and a format nobody in this niche is running.
3. **The mascot breaks the machine.** Our series spine — each episode ends with
   the mascot breaking what was just built, which is the next episode.
