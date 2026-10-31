---
name: gbro-collage-broll
description: Turns a roughly 5-second voice-over line, opinion sentence or abstract concept into a premium editorial halftone paper-collage B-roll clip. Must be used when the user says "collage b-roll", "paper collage b-roll", "halftone collage", "collage-style visuals", "make a collage animation from this script", "gbro-collage-broll", or wants a sentence of script turned into a collage visual metaphor. Enforces a three-stage approval flow - first propose only the visual metaphor; after the user confirms, generate color collage stills; after the stills are confirmed again, generate the first/last-frame assembly animation with Gemini Omni Flash (default model gemini-omni-flash-preview, never Veo unless the user explicitly asks for another model).
compatibility: Written for the Codex environment (Gate 2 relies on the built-in image_gen tool). The video generation script ships with this skill (scripts/generate_video.py). Also needs Python >= 3.10, google-genai >= 2.10.0, a configured GEMINI_API_KEY, and ffmpeg / ffprobe. On first use, complete the setup in "First use - environment check".
---

# gbro Collage B-roll

Compress a roughly 5-second voice-over line into one sharp visual idea, then turn it into a premium editorial paper-collage assembly animation.

Default pipeline:

1. Design only the visual metaphor, then wait for the user to confirm
2. Generate only the final still frames, then wait for the user to confirm
3. Automatically call Gemini Omni Flash to generate the video and run QA

The two confirmation gates are part of the workflow. They keep the user's attention on taste and direction, and stop a wrong metaphor or wrong still from burning video-generation cost.

## First use - environment check

Every time this skill is triggered, run the check script before entering Gate 1:

```bash
bash <this-skill-directory>/scripts/check_setup.sh
```

If everything passes, go straight to Gate 1 and do not repeat the configuration details to the user. If any item fails, treat it as first use: do not enter Gate 1; print the setup guide below (listing only the missing items), wait for the user to confirm setup is done, then re-run the check.

### Setup guide (output per missing item)

1. **GEMINI_API_KEY not set**
   Create an API key in [Google AI Studio](https://aistudio.google.com/apikey), then add it to the shell config:

   ```bash
   echo 'export GEMINI_API_KEY="your-key"' >> ~/.zshrc && source ~/.zshrc
   ```

   Note: video generation is billed per use, to the Google account that owns this key.

2. **ffmpeg / ffprobe missing**
   macOS: `brew install ffmpeg`; Debian/Ubuntu: `sudo apt install ffmpeg`.

3. **Python missing or too old** (needs >= 3.10)
   macOS: `brew install python3`; or install from python.org.

4. **Shared venv not created** (google-genai >= 2.10.0)
   With the user's consent, create it automatically; the user does not need to do anything by hand:

   ```bash
   python3 -m venv ~/hyperframes-projects/.omni-venv
   ~/hyperframes-projects/.omni-venv/bin/python -m pip install --upgrade "google-genai>=2.10.0" "httpx[socks]"
   ```

5. **Not running in Codex / no built-in image_gen**
   The Gate 2 still-frame generation relies on Codex's built-in `image_gen` tool. When running in another agent environment, tell the user they need to supply an equivalent image-generation method (or provide the still images themselves and continue from the Gate 2 confirmation).

## Mandatory approval protocol

### Gate 1: metaphor confirmation

After receiving the script, propose the visual metaphor first. Do not generate images, do not generate video, and do not call any video model.

For each item, deliver:

- Core meaning
- Emotion
- One-sentence visual proposition
- 3-6 key objects
- Suggested background color and spot accent colors
- Expected assembly order

Then stop explicitly and wait for the user to reply "OK", "approved", "all approved", or to give per-item revisions.

If the user confirms only some numbers, only the approved items go on to Gate 2; unapproved items keep revising the metaphor.

### Gate 2: still-frame confirmation

Only after the metaphor is confirmed, write the visual spec and the imagegen prompt, and generate the final stills with Codex `imagegen`.

Save the originals in the project directory, build a numbered still-frame contact sheet, show it to the user and stop again. Still no Omni Flash call and no video at this stage.

If the user confirms only some stills, only those items go on to Gate 3; stills that need changes are regenerated and re-confirmed first.

### Gate 3: video generation

After the stills are confirmed, do not ask which video model to use. Use the bundled `scripts/generate_video.py` directly, which by default calls:

```text
gemini-omni-flash-preview
```

Override this default only when the user explicitly names a different video model. Do not call Veo automatically, and do not push the model choice back to the user.

## Success criteria

- One sentence expresses exactly one clear metaphor
- The batch shares one design language, but not necessarily an all-blue background
- The background is a strong, flat, uniform color field that may change with the meaning
- The subject is built on black-and-white halftone photographic cut-outs
- Key cards, buttons, film strips, rule books, etc. may use colored paper: red, yellow, cyan, orange, purple, cream
- All paper pieces have clean cut edges, cream keylines, low-opacity soft shadows and paper grain
- Motion is assemble-from-empty, not slight drift, wobble or slow zoom
- No subtitles, no full voice-over text, no logo, no watermark, no UI
- Default deliverable: 9:16, 5 seconds, 720x1280, 24fps, silent MP4

## When not to use

- You need precise control over layers, occlusion, camera moves through the scene or an editable timeline: use a layered animation tool instead (e.g. an HTML-rendered video approach such as HyperFrames)
- You only need a video prompt, not a finished clip: just write the prompt, no need for this flow
- You need a realistic person-based product ad or an on-camera presenter: do not use this collage flow
- The user explicitly wants transparent assets editable layer by layer: this skill does not split out transparent layers by default

## Default project directory

Name it using Beijing time (`Asia/Shanghai`):

```text
~/hyperframes-projects/YYYY-MM-DD-collage-broll-title/
```

Recommended structure for batch projects:

```text
<project>/
├── brief.md
├── visual-spec.json
├── imagegen-prompts.md
├── omni-jobs.json
├── gate2-qa.md
├── gate3-qa.md
├── still-contact-sheet.jpg
├── omni-contact-sheet-all.jpg
├── video-first-frame-all.jpg
├── end-frame-comparison-all.jpg
├── 01-concept-name/
│   ├── omni-prompt.txt
│   ├── frames/
│   │   ├── last-frame-original.png
│   │   ├── first-frame.png
│   │   └── last-frame.png
│   └── omni/run-v01/
│       ├── final-5s.mp4
│       ├── final-5s-noaudio.mp4
│       ├── contact-sheet.jpg
│       ├── video-last-frame.jpg
│       └── end-frame-comparison.jpg
└── 02-concept-name/...
```

## Phase 1: design the visual metaphor

First compress the script into one visual proposition.

Extract:

- Core meaning: what the viewer should finally understand
- Emotion: calm, surprise, urgency, sudden clarity, absurdity, irony
- Action verbs: open, connect, leak, bind, archive, light up, compress, fork, assemble
- Visual metaphors: machine, clock, film strip, filing cabinet, console, rule book, funnel, track, chess piece

Do not put the script word for word into the picture. By default one script line gets one metaphor with 3-6 key objects; too many elements weaken the meaning and make Omni's assembly unstable.

For batches, prefer a before/after narrative: for example, first show manual drudgery and lost experience, then show codified standards and human-machine division of labor.

### Gate 1 output example

```text
1. Core meaning: experience is burned up again and again
   Visual metaphor: a skilled editor trims frame by frame around a giant film clock; the clock runs a full circle yet yields only a short cut
   Key objects: film clock, editor, scissors, short film strip
   Color: burnt-orange field, cream and light-cyan accents
   Assembly order: clock -> person and scissors -> film strip -> final short output
```

Stop after the output and wait for confirmation.

## Phase 2: generate color collage stills

After the metaphor is confirmed, first write a self-contained `visual-spec.json`, then the imagegen prompt.

### Visual spec

```json
{
  "script_meaning": "",
  "visual_metaphor": "",
  "style_signature": "flat bold color field, mixed black-and-white halftone cut-outs and colored cardstock accents, crisp cut edges, cream keylines, soft paper shadows, editorial paper collage",
  "aspect_ratio": "9:16",
  "color_field": {
    "background_hex": "",
    "accent_colors": [],
    "paper_grain": "fine uncoated-paper fiber"
  },
  "elements": [
    {
      "what": "",
      "role": "",
      "motion": "",
      "placement": ""
    }
  ],
  "composition": {
    "layout": "",
    "negative_space": "",
    "final_frame": ""
  },
  "motion_plan": "structure first, subject or cards second, action and result last",
  "avoid": "typography, readable letters, numerals, logos, watermark, UI, subtitles, glossy 3D, photoreal environment"
}
```

### Color rules

Do not treat cobalt blue as the only default. Pick a strong color field by meaning, and keep "same design language, different background color" across a batch:

- Burnt orange / red: time consumed, labor, urgency
- Mustard yellow: tools, warnings, lost experience
- Dark green: cognition, taste, system reset
- Deep purple: standards, accumulation, long-term memory
- Teal: judgment, collaboration, automatic execution

The subject can be mostly black-and-white halftone, but colored paper accents must serve the information hierarchy; do not add color for its own sake.

### Imagegen prompt template

Use Codex's built-in `image_gen` tool (and follow the local `imagegen` skill too if there is one):

```text
Use case: ads-marketing
Asset type: final still frame for a 9:16 image-to-video B-roll clip
Primary request: Create a finished editorial paper-collage image expressing [one-sentence visual proposition].
Scene/backdrop: perfectly flat [color] paper field [hex] with subtle uncoated paper fiber.
Style/medium: premium editorial stop-motion paper collage; black-and-white halftone photographic cut-outs mixed with selective [accent color] colored cardstock.
Composition/framing: vertical 9:16 locked poster frame; central subject within the middle 70 percent; generous clean color-field negative space; 3-6 large separable paper groups for later assemble-from-empty animation.
Materials/textures: visible printed halftone dots, crisp machine-cut edges, thin warm-cream paper keylines, soft low-opacity physical drop shadows.
Constraints: [the relationship this metaphor must make clear at a glance].
Avoid: no typography, no readable letters, no numerals, no logos, no watermark, no UI, no subtitles, no glossy 3D, no photoreal environment, no clutter.
```

### Still-frame QA

- Is the metaphor clear at a glance?
- Is the subject concentrated?
- Any fake text, logo, watermark or UI?
- Is enough plain color field left to assemble from empty?
- Are there 3-6 clear large groups, rather than screenfuls of fragments?
- Does the batch share one texture but vary in color?

Copy the originals that pass QA into the project directory, build a numbered still-frame contact sheet, show it to the user and stop to wait for Gate 2 confirmation. Write the still QA conclusions to `<project>/gate2-qa.md`.

If the user asks to regenerate some stills, produce `still-contact-sheet-v2.jpg` afterwards (v3, v4... for later rounds) and keep the old contact sheets rather than overwriting, so they can be compared.

## Phase 3: generate video with Omni Flash

### 1. Prepare first and last frames

Keep the imagegen original, then normalize the last frame:

```bash
ffmpeg -y -i <item>/frames/last-frame-original.png \
  -vf "scale=1080:1920:force_original_aspect_ratio=increase,crop=1080:1920" \
  <item>/frames/last-frame.png
```

The first frame defaults to a plain empty paper surface in the same color as the last frame's background:

```bash
ffmpeg -y -f lavfi -i color=c=0x<HEX>:s=1080x1920 \
  -frames:v 1 <item>/frames/first-frame.png
```

Only if the user explicitly asks not to start from fully blank, keep one base object in the first frame.

### 2. Write the Omni animation prompt

Default order of motion:

```text
base structure -> person or key card -> connectors -> action -> final result
```

Prompt template:

```text
Paper-collage stop-motion assembly, using Image 1 as the exact empty first frame and Image 2 as the exact completed last frame. In one continuous locked-off vertical shot, open on the empty flat [color] paper field.

Assemble the scene piece by piece with crisp physical stop-motion timing: [describe in order how the 3-6 elements slide in, lock into place, connect and complete the action]. End by holding the supplied completed composition.

Preserve the exact 9:16 framing, [hex] color field, colored cardstock accents, uncoated paper grain, halftone dots, cream keylines, crisp cut edges and soft shadows. Restrained tactile 2D paper craft only.

No scene cuts, no camera movement, no zoom, no morphing, no new objects, no text, no letters, no numbers, no logos, no watermark, no UI, no sound.
```

Every prompt must state clearly that Image 1 is the empty first frame and Image 2 is the confirmed completed frame. The final composition must stay close to Image 2; do not let the model freely rework the last frame.

### 3. Check the Omni runtime

Check the `google-genai` version with the same Python interpreter that will run the script. It must be `>= 2.10.0`.

If the system Python is too old or is an externally managed environment, do not use `--break-system-packages`. Use the shared isolated environment `~/hyperframes-projects/.omni-venv/` - reuse it if it exists, create it only if missing, and do not create a new `.venv` inside each project:

```bash
[ -x ~/hyperframes-projects/.omni-venv/bin/python ] || {
  python3 -m venv ~/hyperframes-projects/.omni-venv
  ~/hyperframes-projects/.omni-venv/bin/python -m pip install --upgrade "google-genai>=2.10.0" "httpx[socks]"
}
```

Confirm `GEMINI_API_KEY` is set, but never print or record the key.

### 4. Batch-call Gemini Omni Flash

Create `omni-jobs.json`. Each job uses two images for keyframe interpolation:

```json
{
  "prompt": "<omni prompt>",
  "image": [
    "<item>/frames/first-frame.png",
    "<item>/frames/last-frame.png"
  ],
  "output": "<item>/omni/run-v01/final-5s.mp4",
  "aspect_ratio": "9:16",
  "duration": 5
}
```

Use the bundled script:

```bash
~/hyperframes-projects/.omni-venv/bin/python \
  <this-skill-directory>/scripts/generate_video.py \
  --batch <project>/omni-jobs.json \
  --concurrency 3
```

The script's default model is `gemini-omni-flash-preview`. If you get a legacy Interactions API schema error, the old SDK was used; switch to the shared environment `~/hyperframes-projects/.omni-venv/bin/python` and retry. Do not fall back to Veo.

### 5. Force silent delivery

Even if the prompt says `no sound`, still output a zero-audio-track version with ffmpeg:

```bash
ffmpeg -y -i <run>/final-5s.mp4 \
  -map 0:v:0 -c:v copy -an \
  <run>/final-5s-noaudio.mp4
```

Deliver `final-5s-noaudio.mp4` by default and keep the original `final-5s.mp4` as an intermediate.

## Video QA

Do not look at the last frame only; check the assembly process and the final placement.

### Contact sheet

```bash
ffmpeg -y -i <run>/final-5s-noaudio.mp4 \
  -vf "fps=1,scale=270:480,tile=5x1" \
  -frames:v 1 <run>/contact-sheet.jpg
```

Pass criteria:

- The first frame is close to a plain empty field; a slight early peek of paper at the edges is acceptable
- The middle shows structure, people or cards entering step by step, not the whole thing fading in
- No scene cuts, zoom, 3D-ification or photoreal scene drift
- No fake text, logo, watermark or UI
- The final frame matches the confirmed still; slight pose or detail drift (a person's pose changing slightly, a small part added or removed) passes as long as it does not affect the metaphor - do not rerun for that
- Output is 720x1280, 24fps, 5 seconds, zero audio tracks

Also extract the video's last frame and put it beside the confirmed still as `end-frame-comparison.jpg`. For batch projects, merge three overview images:

- `omni-contact-sheet-all.jpg`: every clip sampled once per second
- `video-first-frame-all.jpg`: the actual first frame of every clip, to verify each really starts from an empty color field
- `end-frame-comparison-all.jpg`: confirmed stills and video last frames side by side

Write per-item QA conclusions (including the reason for passing anything with flaws) to `<project>/gate3-qa.md`.

### Common problems

- First-frame edges peek early: slight is acceptable; if a strictly empty start is required, use HyperFrames to fill in the opening
- Weak assembly feel: reduce the number of elements and rewrite the prompt with an explicit piece-by-piece slide-in / snap-into-place order
- Last frame drifts: strengthen "Image 2 is the exact completed last frame" and "End by holding the supplied completed composition"
- Fake text appears: go back and regenerate the still; do not try to patch it with the video prompt
- A single video fails: rerun only that job; do not rerun items that already passed

## Default deliverables

Deliver to the user:

- Each `<item>/omni/run-v01/final-5s-noaudio.mp4`
- Each contact sheet
- The batch overview contact sheets
- The last-frame comparison images
- One sentence per script line explaining how it became a visual metaphor

If a clip's problem comes from Omni's fast-generation limits, say so directly; suggest switching to HyperFrames only when precise layer control is needed.

## Legacy Veo script

`scripts/generate_veo_first_last.py` in this directory is kept only for compatibility with old projects. Do not call it in the default flow. Use it only when the user explicitly asks for Veo.
