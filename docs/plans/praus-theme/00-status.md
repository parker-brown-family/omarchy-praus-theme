# Praus — plan status

**Difficulty: 5 / 10** (predicted 2026-10-15, before work). A colours-only Omarchy theme
follows a well-worn template; the art direction and an ascetic palette that must stay readable
could be wrong for a long time before anyone noticed. That bought one combined plan page and one
approval.

## Gate state

| Gate | Document | State |
|---|---|---|
| Combined plan | `reports/2026-10-15-praus-theme-plan.html` (local, not published) | **approved** 2026-10-16 — "Very pleasing theme... yes … let's finalize this theme for submission" |

How the nine decisions on the plan page landed:

| # | Decision | Outcome |
|---|---|---|
| 1 | Shape of the art | Replaced by Parker's own set: knight (primary), cell, lamp, and the word |
| 2 | Palette | The seven named colours, extended — as recommended |
| 3 | Error red | Lifted to `#B05F55` — as recommended |
| 4 | Focused border | Solid worn sage — as recommended |
| 5 | Warrior's eyes | Moot: the new knight has none (checked for saturated red) |
| 6 | The passage | Dropped with the rest of the generated set |
| 7 | Inscription | The word only, ΠΡΑΫΣ |
| 8 | Name and home | `parker-brown-family/omarchy-praus-theme`, public for the registry at Parker's word ("SEND") |
| 9 | Upscaling | Faithful Lanczos to 3840×2160, so the approved paintings do not drift |

## Inputs

- Parker's ChatGPT design session (2026-10-15). The seven named colours come from the turn he
  screenshotted: Vantablack `#000000`, Iron `#292F2B`, Monastic olive `#536049`, Worn sage
  `#86917B`, Aged linen `#D4D0BF`, Ancient bronze `#A18C60`, Dried blood `#813B35`.
- Parker's paintings, 2026-10-16, ChatGPT, 1672×941 each: `art/the-meek-warrior.png`,
  `art/the-cell.png`, `art/the-lamp.png`. The cell carries an AI-painted icon of a saint with no
  lettering; named to Parker and kept at his call.
- Parker's words: "PRAUS (meekness)", "VERY SERIOUS. like immortal soul seriousness.. Eastern
  warrior monk roots", and the README epigraph.

## Measured

- Contrast on black: linen 13.57, bronze 6.44, sage 6.35, olive 3.14, blood 2.61 (lifted red
  4.61), iron 1.54. Derived terminal colours 4.91–6.82.
- Mean luma source → graded: knight 7.1 → 5.8, cell 5.0 → 4.2 (8K master, 2026-10-16 06:18), lamp 3.1 → 2.5, word 0.35.
  Backgrounds total 1.1 MB as WebP. Lamp smoke checked for banding at 3× stretch: none.
- Target: Omarchy 4.0.4. The wallpaper plugin is still-image only, `PreserveAspectCrop`.
- Registry rules read live 2026-10-16 (`omacom/omarchy-theme-registry`, `validate.ts`): the
  published tree avoids every warning — no scripts, no images outside `backgrounds/`, a 16:9
  `preview.png` ≥ 1000 px, README, LICENSE, `mode` declared, `icons.theme` a Yaru variant.

## Local runs

- Installed for Parker as a symlink, `~/.config/omarchy/themes/praus → ~/Work/omarchy-praus-theme`,
  the same pattern as Bright Future; applied with `omarchy-theme-set praus`.
- Glass is not theme-owned: `~/.config/hypr/looknfeel.lua` carries the rounding and blur under
  every theme, and the bar's opacity widget sets 0.73 / 0.59.
- Terminal Delight reads palettes only at window start; its session state was pushed to `praus`
  (outer and all panes) across one window restart. Backup:
  `~/.config/terminal-delight/sessions/1.toml.bak-2026-10-15-praus-pushdown`.
- `preview.png` comes from `bin/shoot-terminals` (local, untracked): the scene composed in a 16:9
  band of the laptop panel, btop on preset 2 so no process list or username is photographed. Its
  first run spawned the panes onto the portrait monitor's workspace (follow-mouse focus); the
  shot was correct, and the rig now warps the pointer onto the shot monitor before spawning.

## Submission (2026-10-16)

- Public repository `parker-brown-family/omarchy-praus-theme` (GitHub id 1422164207), MIT,
  topics `omarchy-theme` plus descriptive tags.
- Registry issue `omacom/omarchy-theme-registry#122` — "Submit: Praus", filed through the web
  form as parker-brown-family so the `submission` label applied. First report passed with one
  warning (`PALETTE_UNKNOWN_KEYS`: selection_foreground/selection_background); fixed by moving the
  value into `selection`, then `/recheck` passed with no warnings.
- Pull request `omacom/omarchy-theme-registry#123` — "Add theme: Praus (praus)", labelled
  `auto-approve` (owner submission). Live listing **not yet observed**: it needs a maintainer merge
  and the next six-hourly catalog build; check https://themes.omarchy.org before calling it listed.
- Local: `omarchy-theme-list` shows Praus; it is the current theme.

## Unpublished on purpose (`.gitignore`)

`_local/` (retired art, scratch tools), `bin/` (the rig: scripts draw a registry warning),
`reports/` (the plan page, which shows the retired drafts), `screenshots/`, and the raw chat
extract.

## Post-hoc difficulty

**5 held.** The risk the score priced was the art, and it resolved by Parker making the art
himself after seeing drafts; the palette shipped as first measured. The time went to the
environment rather than the theme: Terminal Delight's startup-only palette scan, the shell
allowlist, and the rig's focus race.
