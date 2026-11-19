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
