# Scenery Pack Organiser - XP10/11/12 v3.1r1

Are you tired of sifting through all the packs in the Custom Scenery folder and reordering them manually? Do you hate having to start and quit X-Plane just to add new scenery packs to the file so you can organise it? This utility is for you!

It will read and sort all scenery packs, carry over DISABLED tags, check for airport conflicts, and even warn you of faulty packages!

## Installation

### Option A: Pre-built binary (no Python needed)

| Platform | Download |
| -------- | -------- |
| Windows x64 | [`organiser-windows-x64.exe`](https://github.com/iy4vet/xplane-scenery-pack-organiser/releases/latest/download/organiser-windows-x64.exe) |
| Windows ARM64 | [`organiser-windows-arm64.exe`](https://github.com/iy4vet/xplane-scenery-pack-organiser/releases/latest/download/organiser-windows-arm64.exe) |
| macOS Apple Silicon | [`organiser-macos-arm64`](https://github.com/iy4vet/xplane-scenery-pack-organiser/releases/latest/download/organiser-macos-arm64) |
| macOS Intel | [`organiser-macos-x64`](https://github.com/iy4vet/xplane-scenery-pack-organiser/releases/latest/download/organiser-macos-x64) |
| Linux x64 | [`organiser-linux-x64`](https://github.com/iy4vet/xplane-scenery-pack-organiser/releases/latest/download/organiser-linux-x64) |
| Linux ARM64 | [`organiser-linux-arm64`](https://github.com/iy4vet/xplane-scenery-pack-organiser/releases/latest/download/organiser-linux-arm64) |

On Windows, just double-click the `.exe`. On macOS/Linux you may need to make it executable first:

```bash
# Example (Linux):
chmod +x organiser-linux-x64
./organiser-linux-x64
```

### Option B: Run with Python

Requires Python 3.10+. Install dependencies and run:

```bash
pip install -r requirements.txt
python organiser.py
```

> **Tip:** If the program crashes, re-run with `--verbose 1` or `--verbose 2` for debugging output.

## Usage

The program is interactive - it will guide you through each step:

1. **Locate X-Plane** - It auto-detects your installs and lists them. Pick one by number, or paste a path manually.
2. **Carry over preferences** - If you had disabled packs in your old `scenery_packs.ini`, it will offer to keep them disabled.
3. **Unsorted packs** - Any packs it can't categorise will be shown; you choose whether to include or disable them.
4. **Airport conflicts** - If multiple packs cover the same ICAO(s), you'll be asked to set their priority order.
5. **Backup & write** - The old `scenery_packs.ini` is renamed to `.bak` before the new one is written.
6. **Launch X-Plane** - Optionally launch X-Plane when done (keep the terminal open while it runs).

## Features

- Sorts scenery packs according to the hierarchy specified below:
  - Custom Airports
  - Default Airports
  - *[Prefab Airports](https://forums.x-plane.org/index.php?/files/file/27582-prefab-scenery-for-25000-airports/)*
  - Global Airports
  - Scenery Plugins
  - Scenery Libraries
  - *[SimHeaven](https://simheaven.com/) Overlays*
  - Custom Overlays
  - Default Overlays
  - *[AutoOrtho](https://forums.x-plane.org/index.php?/forums/topic/259020-autoortho-streaming-ortho-imagery-for-x-plane-12-and-11/) Overlays*
  - Orthophotos
  - *[AutoOrtho](https://forums.x-plane.org/index.php?/forums/topic/259020-autoortho-streaming-ortho-imagery-for-x-plane-12-and-11/) Regions*
  - Terrain Meshes
- Supports Windows shortcuts (.LNK files, eg. for SAM Library)
- Supports [Prefab Airports](https://forums.x-plane.org/index.php?/files/file/27582-prefab-scenery-for-25000-airports/) and [AutoOrtho](https://forums.x-plane.org/index.php?/forums/topic/259020-autoortho-streaming-ortho-imagery-for-x-plane-12-and-11/)
- Attempts to locate X-Plane installs automatically, letting you choose between the results or manually inputting an X-Plane install path
- Offers to carry over SCENERY_PACK_DISABLED tags from existing scenery_packs.ini
- Checks for Custom Airport overlaps and resolves them with user input
- Will warn you of folders-in-folder (It's more common than you'd think)
- Supports XP10/11's and XP12's Global Airports entry simultaneously

## Credits and Licensing

This project is licensed under the GNU GPL v2.

Any contributions (features or bugfixes) are very welcome :grin:. [Here's the project GitHub](https://github.com/iy4vet/xplane-scenery-pack-organiser). Feel free to message me on Discord - my username is `iy4vet`. I'm also present in the X-Plane Community and Official servers.

A huge thank-you to these awesome people:

- [@supercoder186](https://forums.x-plane.org/index.php?/profile/567626-supercoder186/)
- [@Brady](https://forums.x-plane.org/index.php?/profile/7654-brady/)
- [@carlos maida](https://forums.x-plane.org/index.php?/profile/113644-carlos-maida/)
- [@Birdy.dma](https://forums.x-plane.org/index.php?/profile/147165-birdydma/)
- [@cyl8](https://forums.x-plane.org/index.php?/profile/327870-cyl8/)
- [@DHF](https://forums.x-plane.org/index.php?/profile/1218415-dhf/)

## Changelog

- **3.1r1** - Add: macOS alias parsing. Add: CI/CD pipeline with 6-platform binary builds. Fix: disabled pack import. Update: all dependencies for Windows ARM64 compatibility.
- **3.0r1** - Fix: `shutil` compatibility issue.
- **3.0a3** - Add: SimHeaven quirk handling. Improve: UI spacing and stage delays.
- **3.0a2** - Add: `argparse` CLI. Refactor: programme flow and main function structure.
- **3.0a1** - Refactor: full codebase rewrite with classes for flexibility and readability.
- **2.2r1** - Add: shebang for double-click execution on Unix.
- **2.2b2** - Add: DSF parse result caching for faster repeat runs.
- **2.2b1** - Rewrite: airport overlap detection system. Fix: minor bugs.
- **2.1r6** - Fix: Windows `.lnk` shortcut parsing.
- **2.1r5** - Remove: deprecated `pkg_resources`. Add: debug verbosity CLI options.
- **2.1r4** - Fix: DSF selection bug. Add: auto-install missing libraries. Improve: performance by skipping Custom Scenery folder scan.
- **2.1r3** - Fix: unreadable DSF handling. Suppress: AutoOrtho DSF errors.
- **2.1r2** - Fix: X-Plane launch from within the programme.
- **2.1r1** - Add: AutoOrtho support, post-completion X-Plane launch. Improve: error descriptions and UI prompts.
- **2.0r1** - Fix: meshes incorrectly treated as overlays. Add: cleanup for stale X-Plane installs, retry prompts for invalid input.
- **2.0b6** - Fix: multi-codec attempt crash.
- **2.0b5** - Add: write unsorted packs option, airport conflict resolution. Fix: `apt.dat` read errors. Improve: list display and pack sorting.
- **2.0b4** - Add: carry-over of DISABLED tags from existing INI. Fix: Windows shortcut support.
- **2.0b3** - Add: Prefab Airports as a separate sorting category.
- **2.0b2** - Add: Custom Airport conflict detection, stage timers. Remove: X-Plane 9 support.
- **2.0b1** - Add: `apt.dat` parsing for airport verification, alphabetical sorting per layer. Fix: default/custom overlay ordering, case sensitivity.
- **1.4b1** - Add: automatic X-Plane install detection (direct downloads only).
- **1.3.2** - Fix: syntax error.
- **1.3.1** - Fix: jumbled pack ordering.
- **1.3.0** - Add: X-Plane 12 support. Fix: default/custom airport ordering.
- **1.2** - Add: Windows shortcut (.LNK) support, code comments.
- **1.1** - Improve: wait for user confirmation before exiting.
- **1.0** - Initial release.

## Known Issues

- Automatic location of X-Plane installs may not work for Steam users

## What's planned

Naturally, fixing the above :grin:.

There's also saving preferences of custom airport overlaps, so you can simply reuse what you did last time. I'm also considering potential options to let you decide how you want your packs sorted. Perhaps little text files you can copy-paste to your scenery pack would be a good option...

If there's anything you'd like to see added, send me a message or create a pull request on GitHub!
