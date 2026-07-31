# ComboShip

**ComboShip is a cross-game randomizer for [Ship of Harkinian](https://github.com/HarbourMasters/Shipwright) (Ocarina of Time) and [2 Ship 2 Harkinian](https://github.com/HarbourMasters/2ship2harkinian) (Majora's Mask).**

**DISCLAIMER: THIS IS AN UNOFFICIAL PROJECT AND USES AI AS PART OF THE DEVELOPMENT. IT IS NOT CREATED OR HANDLED BY THE HARBOUR MASTERS TEAM. BRING ANY IDEAS, QUESTIONS, OR CONCERNS TO ME DIRECTLY!**

## What it is

Like [OOTMM](https://ootmm.com/), ComboShip shuffles items across *both* games at once: a check in Ocarina of Time can hold a Majora's Mask item and vice-versa, and a single seed spans the two. Both games run together in one application; ComboShip builds that combined runtime on top of the existing Ship of Harkinian and 2 Ship 2 Harkinian ports.

## Features

- Anything within Ship and 2Ship is here. When those projects gets new updates, they are not far from inclusion here.
- Online Multiplayer through Anchor. And yes it works cross-game as well. Work together in OOT and MM, split or together.
- **Transformation Masks in Ocarina of Time.** This fork ports [aegiker's Fierce Deity work](https://github.com/AgitationSkeleton/soh_fd) into ComboShip's OoT side, so Link can wear the **Fierce Deity's Mask** and fight as the Fierce Deity in Ocarina of Time — the same shared mask the randomizer already places in Majora's Mask. Obtaining it in either game grants it in both.
  - **Enhancements → Transformation Masks** menu: *Give Fierce Deity's Mask* button, form rules (stuck-safeguards, restricted-action prompts), Fierce-Deity toggles (usable anywhere, play ocarina, sheathe sword, magic spin, increased strength, unrestrict items), and a **Fierce Deity Tunic Color** cosmetic (also in Cosmetics Editor → Link).
  - **Enhancements → Bonus Settings**: Majora's-Mask-flavored extras — MM jump flips, MM ledge momentum, MM roll-attack damage, Young Link hookshot sound, and a **Bunny Hood Fit** correction so the hood sits right on the taller Adult / Fierce Deity heads.
  - The Fierce Deity model and audio ship inside `fd.o2r`, generated once at first launch from your Majora's Mask ROM (the same ROM ComboShip already asks for) — no extra prompt.

## Future plans

- Possibly looking into some more OOTMM features, but it's not a priority yet.
- Possible Archipelago support as well, ideally through the existing SoH implementation

## Any bugs?

Probably many! Create an issue if you find any.

## Building

ComboShip currently builds on **Windows** only. macOS and Linux support will return later.

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

## Contributing

ComboShip is built on two upstream projects, kept as vendored copies under `soh/` and `mm/`:

- Ship of Harkinian — https://github.com/HarbourMasters/Shipwright
- 2 Ship 2 Harkinian — https://github.com/HarbourMasters/2ship2harkinian

ComboShip-specific code lives in `combo/`, and changes to the vendored ports are kept minimal and guarded behind `COMBO_BUILD`. See [`docs/ARCHITECTURE.md`](docs/ARCHITECTURE.md) for the design and [`docs/UPSTREAM_MERGES.md`](docs/UPSTREAM_MERGES.md) for how upstream changes are merged in.

## License

ComboShip combines two separately-licensed projects; each retains its own license. See the `soh/` and `mm/` directories for details.
