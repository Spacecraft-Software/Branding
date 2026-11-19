<!--
SPDX-FileCopyrightText: 2026 Mohamed Hammad <Mohamed.Hammad@SpacecraftSoftware.org>
SPDX-License-Identifier: CC-BY-SA-4.0
-->

# Branding

The current Spacecraft Software and Steelbore OS marks, kept in one place so
every project draws them from the same source instead of carrying its own copy.

## Marks

| File | What it is | Used by |
|------|------------|---------|
| `logo/steelbore/sb_logo.svg` | The Steelbore OS emblem: gear, screw and "S B", no text | Bravais (`steelbore-branding`: the os-release logo and icons), Gantry (`tools/logo2art.py`, the login-screen banner) |
| `logo/steelbore/steelbore_logo.svg` | The emblem stacked over the STEELBORE stencil wordmark | Bravais (`steelbore-ksplash`, the Plasma splash) |

The marks are single-colour (`#000027`) so a consumer can recolour them to a
theme role, as the Plasma splash does.

**Which emblem is current.** The current emblem has **no inner ring**: the
inside of the gear is open around the screw. The previous emblem, retired on
2026-11-19, had a thin ring of two arcs there; it is otherwise identical. Any
Steelbore emblem with that ring is out of date, and so is any copy kept outside
this repository. `AGENTS.md` lists the checksums and file signatures that tell
the two apart.

## Using the marks

- **Nix.** Add the repository as a non-flake input and read the files from it:

  ```nix
  inputs.branding = {
    url = "github:Spacecraft-Software/Branding";
    flake = false;
  };
  # then: "${inputs.branding}/logo/steelbore/sb_logo.svg"
  ```

  Updating a mark everywhere is then a lock bump (`nix flake update branding`).
- **Elsewhere.** Point at the file in a local clone; do not copy it into the
  consuming repository.

## Trademarks

The Spacecraft Software and Steelbore names and marks are covered by the
umbrella [trademark policy](https://github.com/Spacecraft-Software/License/blob/main/TRADEMARKS.md).
The copyright licence below lets you share and adapt the artwork; it does not
grant the right to use the marks to brand your own product.

## Project Posture

Spacecraft Software is a **personal hobby project**. This repository holds
artwork shaped around the maintainer's own projects, not a general-purpose
asset library.

- **No warranty, no liability.** See [`NOTICE.md`](./NOTICE.md).
- **Contributions are welcome but not guaranteed.** See [`CONTRIBUTING.md`](./CONTRIBUTING.md).

---

**Maintainer:** Mohamed Hammad &lt;Mohamed.Hammad@SpacecraftSoftware.org&gt;
**License:** CC-BY-SA-4.0 (artwork and documents; Standard §4.1.1)
**Website:** <https://SpacecraftSoftware.org/>
