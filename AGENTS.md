<!--
SPDX-FileCopyrightText: 2026 Mohamed Hammad <Mohamed.Hammad@SpacecraftSoftware.org>
SPDX-License-Identifier: CC-BY-SA-4.0
-->

# Branding — agent context

The single source of the current Spacecraft Software and Steelbore OS marks.
Projects read the marks from here (Bravais as a non-flake input, Gantry from a
local clone); they never keep copies of their own. Licence: CC-BY-SA-4.0 for
everything (Standard §4.1.1). Posture: Personal.

## Layout

- `logo/steelbore/sb_logo.svg`: the emblem, no text. Bravais's
  `steelbore-branding` and Gantry's `tools/logo2art.py` read it.
- `logo/steelbore/steelbore_logo.svg`: the emblem over the stencil wordmark.
  Bravais's `steelbore-ksplash` reads it.
- Everything else in this folder on the maintainer's machine (font zips, PSD
  and XCF sources, JPEG exports, numbered scratch copies such as
  `sb_logo1.svg`) is a working file and is not published.

## Current vs. previous Steelbore emblem

The emblem was redrawn on 2026-11-04 and adopted across the umbrella on
2026-11-19. **The current emblem has no inner ring.** The previous one had a
thin ring, drawn as two arcs, inside the gear and curving around the screw,
open on the left. Everything else (the gear, the screw, the "B", the slanted
bar of the "S") is identical; the two differ by the ring alone (about 1.8% of
the pixels at 600 px).

Use only the files in this repository. Before using, copying or approving any
Steelbore emblem found elsewhere, check it against the table. If it matches
the "previous" column, it is retired: replace it by reading the mark from
here, never by editing it in place.

| Check | Current (use) | Previous (retired) |
|-------|---------------|--------------------|
| Inner ring around the screw | None; the inside of the gear is open | Two thin arcs inside the gear |
| Emblem file | `logo/steelbore/sb_logo.svg` | `steelbore-os.svg` (was Bravais `assets/brand/`) |
| Emblem SHA-256 | `7240467c260e12abafb2e35665ab3630bd5191e0e90677d09a099e5838520c78` | `6e467ecb660a7bfe79ae5e4625d6de7cb41a92f82ac517133bbd7a79a0d13de0` |
| Emblem shapes | 7 `<path>`, `fill` on each | 9 `<path>`, one `fill` on the `<g>` |
| Emblem + wordmark file | `logo/steelbore/steelbore_logo.svg` (600×257) | `steelbore-os-wordmark.svg` (was Bravais `assets/brand/`) |
| Emblem + wordmark SHA-256 | `55a15b456119c8d4747b297cd0ec7c0b92e3554de3858805c0c33e13f8464b79` | `9ac441aa866a3aa9483311478abe31c19947d4f260125b8eba53c573752e644f` |
| SVG header | `<?xml version="1.0" encoding="UTF-8"?>`, `<title>` named after the file | `<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 20010904//EN" ...>`, `version="1.0"` |
| Size units | Plain numbers: `width="213"`, `viewBox="0 0 213 213"` | Points: `width="213.000000pt"` |
| Path data | Absolute coordinates, e.g. emblem starts `M78.3 21.7 C75.2 22.3` | Potrace output under `transform="translate(0.000000,213.000000) scale(0.100000,-0.100000)"`, emblem starts `M783 1913 c-31 -6` |

A quick test without rendering: a Steelbore SVG with a `DOCTYPE` line, `pt`
units or a `scale(0.100000,-0.100000)` transform is the previous version.
When in doubt, render it (`rsvg-convert -w 600 -b white file.svg -o out.png`)
and look inside the gear for the ring.

**Text art.** Gantry's half-block banner (`assets/steelbore-logo.txt`, made
by its `tools/logo2art.py`) shows the same difference. The current art's
fourth line is `    ██████▀▀     ▀▀█████▀   ▀▀█████`, blank where the
ring was. The previous art drew the ring as `▄▄` and `▄▄█▀▀▀` fragments, for
example `    ██████▀▀ ▄▄  ▀▀█████▀   ▀▀█████`.

**Where the previous version lived**, now removed: Bravais
`assets/brand/steelbore-os.svg` and `assets/brand/steelbore-logo.svg`
(Bravais #260), Bravais `assets/brand/steelbore-os-wordmark.svg` (Bravais
#261), and Gantry `assets/steelbore-logo.txt` before Gantry #11. It
survives only in git history. Unpublished working files in the maintainer's
`branding/` folder are not authoritative either: never take a mark from them.

## Rules

- **`.gitignore` is an allowlist.** It ignores everything; each published file
  is named in it. To publish a mark, add its path there, then check
  `git status` shows only what you meant to add.
- **Never rename or move a published file** without updating every consumer
  in the same change set: Bravais (`flake.nix` input users,
  `pkgs/steelbore-branding`, `pkgs/steelbore-ksplash`) and Gantry
  (`tools/logo2art.py`). A rename breaks their builds on the next lock bump.
- **Keep the marks single-colour `#000027`.** The Plasma splash recolours by
  replacing that exact fill.
- **Changing a mark** reaches consumers only after they bump their lock
  (Bravais: `nix flake update branding`) or regenerate (Gantry:
  `tools/logo2art.py`, then commit `assets/steelbore-logo.txt`).
- SVGs carry their SPDX tags through `REUSE.toml`; text files carry the two
  SPDX lines. `reuse lint` must pass.
- Do not use the marks for a new product or package name without the
  maintainer's say-so (trademark policy in the License repo).
- Commits are signed. Branch + PR, never push to `main`.
