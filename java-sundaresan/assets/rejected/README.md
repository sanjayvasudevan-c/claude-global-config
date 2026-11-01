# Rejected attempts — keep for the lesson, do not use

## `svg-handdrawn/` — hand-authored SVG character
**Rejected: not good enough.** Hand-writing path coordinates produces flat
geometric clip-art, not a drawn character. It cannot reach the quality of a
properly drawn cartoon, and no amount of iterating on coordinates fixes that.

**Lesson:** SVG is the right *delivery* format for animation, but the
character must be **drawn first** and vectorised after. Do not try to author a
character from scratch in path data again.

## `../characters/host-forest-engineer-v1.png` — etched version
**Rejected: wrong rendering.** Right character, but came out as engraved
illustration — crosshatching, stipple, fine line texture.

**Cause:** the prompt said *"1970s engineering manual risograph print"*, which
reads as **etching**.

---

# Prompt direction for the next attempt

Both failures came from the prompt, in opposite directions:

| Attempt | Prompt said | Came out as |
|---|---|---|
| 1 | "risograph technical manual, halftone, hatching" | Etched engraving — too detailed |
| 2 | "flat cartoon, chunky, very low detail, no shading" | Crude clip-art — too simple |

The reference sits **between** these. What it actually is:
- Clean, confident, slightly varied **vector linework** — not chunky, not hairline.
- **Flat colour with exactly one soft shadow tone** per area — not zero shading,
  not halftone dots.
- **Stylised but properly drawn** anatomy: real facial structure, expressive
  eyes, hair drawn as shaped clumps — not radial spikes, not individual strands.
- Modern **adult animation** character design.

**Say this instead:** *"modern adult animation character design, clean vector
linework, flat colour with a single soft shadow tone, expressive stylised
proportions, properly drawn facial structure, character turnaround sheet."*

**Do not say:** risograph · technical manual · halftone · hatching · engraving
· woodcut · "very low detail" · "chunky" · "no shading".
