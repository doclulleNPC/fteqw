# NOTICE — modified version of FTEQW (quoom fork)

This repository is a **modified version of FTEQW**, used by the *quoom* project to run
classic **Doom** natively inside the engine. It is a **derivative work** and remains
licensed under the **GNU General Public License, version 2** — the same license as
upstream FTEQW. See `LICENSE`.

## Upstream

- Upstream project: **FTEQW** — https://github.com/fte-team/fteqw
- This fork: `doclulleNPC/fteqw`, branch `doom-support`, which tracks upstream and adds
  the Doom modifications described below.
- Original copyright notices of the FTE Team and id Software (the Quake source on which
  FTEQW is based) are **retained** in the source files. This NOTICE does not replace or
  supersede them; it documents the modifications and their provenance.

## Modifications (native Doom support)

Added an engine-side Doom game mode (`MAP_DOOM` / `fromgame == fg_doom`), with no
QuakeC. The main areas changed/added:

- `engine/gl/glmod_doom.c` — Doom map/flat/sprite loading, world + thing rendering
  (sprites, voxels, MD2 models), HUD, first-person weapon viewmodel, collision trace.
- `engine/server/sv_user.c`, `sv_phys.c`, `sv_init.c`, `sv_send.c`, `pr_cmds.c` —
  server-side Doom game logic (movement/use, monster AI, weapons, pickups, sounds,
  precaching) running with `svprogfuncs == NULL`.
- `engine/common/fs.c` — a `-doom` / `-doom2` game mode and WAD/flat loading.
- `engine/client/cl_main.c`, `engine/server/server.h` — supporting glue.

All of the above are distributed under the GPLv2, like the rest of the engine.

## Provenance / AI assistance

The Doom modifications in this fork were produced with **substantial assistance from a
large language model** (Anthropic's Claude), under human direction, integration, and
testing. This is disclosed for transparency.

## Relationship to the FTEQW project

This fork is **not affiliated with, endorsed by, or part of** the upstream FTEQW
project, and these modifications are **not submitted for upstream inclusion**. The
FTEQW project does not accept LLM-generated contributions; these changes are
intentionally maintained downstream only. Please do not report issues with this fork to
the upstream FTEQW maintainers.
