# 0001: One metric scale per frame holds out to 40 m; beyond that it is unproven

- **Status:** `verified` within 40 m; `candidate` beyond 40 m
- **Camera / conditions:** SIYI A8 mini (monocular EO) on a multirotor, gimbal pitched
  down, low hover (a few metres AGL), outdoor scenes with mostly flat ground. Eight
  recorded flights.
- **Model:** MoGe-2, run offline, given one metric scale per frame by fitting its depth
  against the flat ground plane (camera height from odometry plus camera pose).
- **Claim:** Within 40 m, the model's scale does not drift with distance inside a frame:
  fits in 0-10, 10-20 and 20-40 m ground bands agree to about ±5% on all but one short
  flight, with or without the fit's inlier gate. So one scale per frame is enough there,
  and a spatially varying metricization (e.g. MTDv2, arXiv
  [2610.16749](https://arxiv.org/abs/2610.16749)) buys little. Beyond 40 m the far band
  reads 0.59-0.94 of the 10-20 m band once ungated, and this check cannot say whether
  the model or the ground causes it.
- **Limits:** A flat-ground check cannot separate model error from non-flat far ground
  (rising terrain, vegetation) or camera pitch error. A constant pitch shift explains
  the far band on only 2 of 8 flights. Ground rays only reach far range from higher up:
  at 3 m AGL the fit sees ground to about 43 m.
- **Evidence (private):** internal project repository, commit `fbf9351`: band-spread and
  band-refit scripts plus a results table. Ask the repo owner for access.
- **Next probe:** measure far range directly with a rangefinder beside the camera
  (planned rig in `tools/`), or survey targets at 50-70 m in view. If the model reads
  true distance evenly to 80 m, the far drop is the ground. If not, revisit MTDv2.
- **Ask-whom:** Teyr
- **Recorded:** 2026-10-27
