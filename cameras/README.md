# cameras

A registry of camera models, scored on how much each one tells you about its own
image pipeline. Use it to decide how to handle a camera type before its frames reach a
model.

## Why this matters

A model sees what the camera's image signal processor (ISP) made of the scene, not the
scene. Cameras that report or let you lock their ISP settings can be measured and
corrected. Cameras that hide them can only be characterized from outside and monitored.

## Tiers

| Tier | What the camera gives you | How to handle it |
| --- | --- | --- |
| A | Raw output and per-frame ISP metadata | Record the metadata with every frame; invert the reversible blocks if needed |
| B | Lockable ISP, little or no metadata | Lock the settings, log what you locked |
| C | Sealed ISP, compressed output | Characterize once with targets, log per-frame image statistics, fix what you can (e.g. stream encoding), robustify the model for the rest |

## Columns in `registry.csv`

| Column | Values | Meaning |
| --- | --- | --- |
| `camera` | text | Make and model |
| `tier` | `A` / `B` / `C` | See above |
| `raw_output` | `yes` / `partial` / `no` / `unknown` | Can it hand you Bayer data instead of processed RGB? |
| `per_frame_metadata` | same | Does it report exposure, gain, white-balance gains or colour matrix with each frame? |
| `lockable_isp` | same | Can you turn off auto exposure and auto white balance, and fix denoise and sharpening? |
| `isp_access` | same | Can you read or set its tuning? |
| `uncompressed_out` | same | Can you get frames without H.264/H.265/JPEG compression? |
| `calibration` | same | Are lens intrinsics available or measurable, and do they stay fixed? |
| `interface` | text | Outputs, protocols, resolutions |
| `status` | `verified` / `inferred` / `candidate` | As in the playbook: how the row was checked |
| `evidence` | text | Documents and sections the row rests on |
| `notes` | text | Caveats, and which cells are inferred |
| `ask_whom` | text | Who to ask about this camera (default: the repo owner) |
| `recorded` | `YYYY-MM-DD` | When the row was last checked |

`unknown` means not found in the sources, not confirmed absent.

## Adding a camera

Add one row. Fill every column; an unknown cell says `unknown`, not blank. Cite the
document and section for each `yes` or `no`.
