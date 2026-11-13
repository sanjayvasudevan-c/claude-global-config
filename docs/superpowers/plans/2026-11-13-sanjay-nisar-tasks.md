# Sanjay's NISAR Change Explorer Tasks Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Deliver Sanjay's share of NISAR Change Explorer: the validated flood/wetland science core, its accuracy numbers, and sign-off, on the 48-hour schedule.

**Architecture:** One callable science function (area + dates in, result map + results file out) built first as a notebook "golden sample", then wrapped and plugged into Arshad's FastAPI job. Validation compares output to NASA OPERA water maps and Nevedha's check points.

**Tech Stack:** Python, asf_search, earthaccess, xarray, numpy, scipy, rasterio; QGIS for checks.

**Spec:** `NISAR_Change_Explorer_Final_Plan.pdf` (sections 4, 5, 11) and `NISAR_Change_Explorer_48_Hour_Sprint_Plan_1_1.pdf` (Sanjay's tables, pp. 3, 5, 8).

## Global Constraints

- Calibrated GCOV starts 17 Jun 2026; permanent gap 27 Jul-10 Aug 2026, never filled.
- Same track, frame and direction only; never mix BETA with calibrated data without a warning label.
- Compare groups of 2-3 passes before vs after, not single images.
- Drop changes under 1 ha; mask permanent water and steep slopes.
- High confidence needs the change on at least 2 passes.
- Insufficient data: fewer than 2 good passes on either side, or more than 30% of the area masked.
- Honest wording: "likely became water", "likely water receded", "no change detected / insufficient data". Never "confirmed".
- Check points are never the points used to set thresholds. Publish real accuracy, whatever it is.
- Sample data is always labelled sample; never presented as live.
- No credentials in the repo; Earthdata login lives only on the server.
- Fixed times (IST): C0 Fri 8 PM; M0 Fri 9:00-9:30 PM; C1 Sat 6 AM; C3 Sat 7 PM; C4 Sun 3 AM; C6 Sun 7 PM freeze; M7 rehearsal Sun 8 PM; no code changes after Sun 11 PM.

## Review Focus

1. Demo area has a before/after pair only across the 27 Jul-10 Aug gap: expect "insufficient data", not a made-up result.
2. Only one pass on one side: expect "insufficient data".
3. More than 30% of the area masked (steep terrain, permanent water): expect "insufficient data".
4. Mixed BETA and calibrated passes in the selection: expect a warning label or exclusion.
5. OPERA water map date is far from the NISAR pass date: expect the agreement number to carry that date gap.

Each line gets a test in Task 3 (the data-quality function, `assess_availability`) and Task 5 (validation).

---

## Section A: Tonight (Fri 13 Nov, deadline 8 PM)

### Task 1: Setup and access

- [ ] **Step 1:** Create a free NASA Earthdata Login and test one NISAR download. Done when one file or subset opens locally.
- [ ] **Step 2:** Join the repository and team chat (main channel plus help thread). Done when repo clones and runs locally.
- [ ] **Step 3:** Install asf_search, earthaccess, xarray, numpy, scipy, rasterio; install QGIS. Done when `python -c "import asf_search, earthaccess, xarray, scipy, rasterio"` exits 0.

### Task 2: Demo areas and pass-count table

**Files:** Create: `data/demo_areas/` (subsets), `data/pass_counts.csv`, `notebooks/first_area.ipynb`, `docs/science_note.md`

- [ ] **Step 1:** Choose 3-4 demo areas plus one spare per process, flat and low latitude. Done when each has a same-track pre-event and post-event pass pair outside the 27 Jul-10 Aug gap.
- [ ] **Step 2:** Download the GCOV subsets (chosen area only). Done when the data folder is complete.
- [ ] **Step 3:** Write `pass_counts.csv` with columns `area, track, direction, quality_level, date`, and the number of calibrated passes since 17 Jun. Done when every area has a row per pass.
- [ ] **Step 4:** Send the area list to Nevedha so OPERA maps and photos match your dates. Done when her reference folder lists the same areas and dates.
- [ ] **Step 5:** Run the first area end to end in the notebook; write the one-page science note (inputs, steps, outputs, limits). Done when the notebook runs top to bottom.
- [ ] **Step 6:** Attend M0 (9:00 PM). Done when C0 items are confirmed: data, notebook, science note.

## Section B: Saturday

### Task 3: Golden sample and science function (Sat 12-6 AM, then Sat 6 PM-12 AM)

**Files:** Create: `science/detect_change.py`, `science/availability.py`, `golden_sample/` (map + results file), `tests/test_availability.py`

**Interfaces:**
- Produces: `assess_availability(area, dates) -> {passes, quality_levels, masked_fraction, status}`; `detect_change(area, before_dates, after_dates) -> ResultFile`. Field names are frozen at M3 with Arshad.

- [ ] **Step 1 (Sat 12-6 AM):** Run the nine steps on area 1: load GCOV passes; group by track/direction/quality and drop bad passes; apply the NISAR mask and smooth speckle; build before/after composites (typical of 2-3 passes); compute and threshold brightness change; remove permanent water and steep slopes, drop patches under 1 ha; total area per category; save the result map and results file; record step timings. Done when the golden sample is saved.
- [ ] **Step 2:** Write the label rules (likely became water / likely water receded / no change), confidence rules (High, Medium, Lower) and the insufficient-data rule with Abilash. Done when C1 (Sat 6 AM) is met.
- [ ] **Step 3 (tests first):** Write failing tests in `tests/test_availability.py` for the Review Focus lines 1-4. Run `pytest tests/test_availability.py -v`; expect FAIL.
- [ ] **Step 4:** Implement `assess_availability` and `detect_change` as one function with area and dates in, result files out; add progress step names ("finding passes", "fetching", "comparing", "saving"). Run the tests; expect PASS.
- [ ] **Step 5 (Sat 5-6 PM):** Join M3 (from 6 PM) and freeze each API field with Arshad. Done when C3 (Sat 7 PM) is met.
- [ ] **Step 6:** Run the other demo areas through the function. Done when results exist for all demo areas.
- [ ] **Step 7 (Sat 9 PM, M4):** With Arshad, plug the function into the server job; fix any contract mismatch. Done when the server returns real results for demo areas.

## Section C: Sunday

### Task 4: Hand-offs while you sleep (Sun 12-3 AM)

- [ ] **Step 1:** Before you stop, leave a written handover (Completed / In progress / Blocked by / Next action / Files / Evidence). Done when it's in the help thread.

### Task 5: Validation (Sun 3-6 AM)

**Files:** Create: `science/validate.py`, `tests/test_validate.py`, `docs/validation.md`

**Interfaces:**
- Consumes: result map, Nevedha's OPERA map and check points.
- Produces: `validate(result_map, opera_map, checkpoints) -> {overlap, precision, recall, opera_date_gap_days}`

- [ ] **Step 1:** Write a failing test for Review Focus line 5 (the result must carry `opera_date_gap_days`). Expect FAIL.
- [ ] **Step 2:** Implement `validate`; run the test; expect PASS.
- [ ] **Step 3:** Compare flood map vs OPERA water map (overlap, precision, recall) and score Nevedha's check points (never the threshold-setting points). Done when numbers are saved.
- [ ] **Step 4:** Produce the per-pass change series for the timeline chart.
- [ ] **Step 5:** If time: one experimental layer (ground movement from GUNW if data exists, otherwise vegetation loss), labelled experimental.
- [ ] **Step 6:** Finish the science note with limits; hand Abilash the validation text. Done when accuracy numbers and the chart data are handed over (M5 at 6 AM).

### Task 6: Verify and prepare (Sun 2-8 PM)

- [ ] **Step 1:** Check every number and label in the app against the saved results; fix science issues from the day team's log.
- [ ] **Step 2:** Review caveat wording on screen against the honest-wording table.
- [ ] **Step 3:** Prepare answers to likely judge questions on method and accuracy.
- [ ] **Step 4:** Attend M6 (6 PM), the freeze (7 PM) and M7 rehearsal (8 PM). Done when the demo runs as shown.

### Task 7: Final sign-off (Sun 9-11 PM)

- [ ] **Step 1:** Check numbers on the frozen build and in the video. Done when you send the sign-off before 11 PM.

## Self-Review

- **Spec coverage:** all of Sanjay's rows in the Sprint Plan tables are mapped (pre-event, Sat 12-6 AM, Sat 6 PM-12 AM, Sun 3-6 AM, Sun 2-8 PM, Sun 9-11 PM), plus the validation plan (section 11) and data rules (section 5).
- **Gaps in the spec to settle with Abilash:** exact field names (set at M3), and which experimental layer to choose.
- **Type consistency:** `assess_availability` and `detect_change` are used under the same names throughout.
- **Proportion:** a short plan; the code stays in the notebook and the modules, not here.
