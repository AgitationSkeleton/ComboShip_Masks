# ComboShip Masks

**A fork of ComboShip that adds Transformation Masks — the Fierce Deity for now — and a handful of bonus features to the Ocarina of Time side of its cross-game OoT ↔ MM randomizer.**

> **Unofficial fork.** This is built on ComboShip, which is itself an unofficial cross-game randomizer for [Ship of Harkinian](https://github.com/HarbourMasters/Shipwright) (Ocarina of Time) and [2 Ship 2 Harkinian](https://github.com/HarbourMasters/2ship2harkinian) (Majora's Mask). It is not affiliated with or supported by the Harbour Masters team or the ComboShip developers, and development uses AI assistance. Please report problems with this fork here — not to any of the upstream projects.

## The base: what ComboShip is

Like [OOTMM](https://ootmm.com/), ComboShip shuffles items across *both* games at once: a check in Ocarina of Time can hold a Majora's Mask item and vice-versa, and a single seed spans the two. Both games run together in one application, built on top of the existing Ship of Harkinian and 2 Ship 2 Harkinian ports. Everything those three projects already do — the combined randomizer, cross-game Anchor multiplayer, all the Ship/2 Ship enhancements — is still here in this fork.

## What this fork adds

- **Transformation Masks in Ocarina of Time (Fierce Deity for now).** This fork ports [aegiker's Fierce Deity work](https://github.com/AgitationSkeleton/soh_fd) into ComboShip's OoT side, so Link can wear the **Fierce Deity's Mask** and fight as the Fierce Deity in Ocarina of Time — transform cutscene, sword beams, and boss/enemy parity included.
  - **Shared across both games.** The Fierce Deity's Mask is the same mask the randomizer already places in Majora's Mask: obtaining it in *either* game unlocks the Fierce Deity form in *both* (on by default; toggle under **Enhancements → Transformation Masks**). If you start with it in one game, you start with it in the other.
  - **Enhancements → Transformation Masks** menu: a *Give Fierce Deity's Mask* button, form rules (stuck-safeguards, restricted-action prompts), and Fierce-Deity toggles (usable anywhere, play ocarina, sheathe sword, magic spin, increased strength, unrestrict items). Tint the tunic in **Cosmetics Editor → Link → "Fierce Deity Tunic"**.
  - **Enhancements → Bonus Settings**: Majora's-Mask-flavored extras — MM jump flips, MM ledge momentum, MM roll-attack damage, Young Link hookshot sound, and a **Bunny Hood Fit** correction so the hood sits right on the taller Adult / Fierce Deity heads.
  - **No assets bundled.** The Fierce Deity model and audio (`fd.o2r`) are generated once at first launch from your own Majora's Mask ROM — the same ROM ComboShip already asks for, with no extra prompt.

More transformation masks may follow; the Fierce Deity is the first.

## Notes and known limitations

- **Windows only** (matches upstream ComboShip).
- **Entrance randomization** (dungeon/boss/grotto/etc.) is not supported by ComboShip's cross-game fill. If a config you import turns it on, it is ignored during generation (with a one-time warning) so seeds still generate.

## Bugs

Probably some! Please open an issue on this repository if you find one.

## Building

This fork builds on **Windows** only.

### Prerequisites

- Windows 10/11 (x64)
- Visual Studio 2022 (MSVC, with C++20 / C23 support)
- CMake 3.26 or newer

### Configure and build

From the repository root (the clone folder, which contains this README), configure once to generate the Visual Studio solution:

```powershell
cmake -B build/x64 -A x64
```

Helper scripts in `scripts/` wrap `cmake --build` and default to a Debug build (pass `--Release` for Release):

```powershell
./scripts/build-comboship.ps1  ->  ComboShip.exe
```

## Packaging

`cpack` produces a single Windows ZIP bundling the full runtime (`ComboShip.exe`, the engine and UI DLLs, both ports, and assets):

```powershell
cpack
```

## Credits

This fork stands on:

- **ComboShip** — the cross-game OoT ↔ MM randomizer this is forked from. <!-- TODO: link the upstream ComboShip repo here -->

- **[Ship of Harkinian](https://github.com/HarbourMasters/Shipwright)** and **[2 Ship 2 Harkinian](https://github.com/HarbourMasters/2ship2harkinian)** — the underlying ports, vendored under `soh/` and `mm/`.
- **[aegiker's soh_fd](https://github.com/AgitationSkeleton/soh_fd)** — the Fierce Deity / Transformation Mask implementation ported here.

ComboShip-specific code lives in `combo/`, and changes to the vendored ports are kept minimal and guarded behind `COMBO_BUILD`. See [`docs/ARCHITECTURE.md`](docs/ARCHITECTURE.md) and [`docs/UPSTREAM_MERGES.md`](docs/UPSTREAM_MERGES.md).

## License

This project combines separately-licensed upstream projects; each retains its own license. See the `soh/` and `mm/` directories for details.
