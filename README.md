<div align="center">

# R-MIGRATOR

**Automated migration tool for legacy Ren'Py mods — Python 2 → Ren'Py 8**

*Migrates old DDLC / Ren'Py mods to run on modern Ren'Py 8 engines. One click, no manual script editing.*

[![Download](https://img.shields.io/badge/download-latest--release-A2FF00)](../../releases/latest)
[![Platform](https://img.shields.io/badge/platform-Windows-blue)](#requirements)
[![Guide](https://img.shields.io/badge/user--guide-rootwin.vercel.app-A2FF00)](https://rootwin.vercel.app/r-migrator-guide)
[![YouTube](https://img.shields.io/badge/video--guide-YouTube-FF4B4B)](https://youtu.be/cWujaKRdWEE)

**[Website](https://rootwin.vercel.app/software/r-migrator)** · **[User Guide](https://rootwin.vercel.app/r-migrator-guide)** · **[Video Guide (YouTube)](https://youtu.be/cWujaKRdWEE)** · **[Download](https://rootwin-project.itch.io/rmigrator-beta-v1-1)**

</div>

---

## What is this?

R-MIGRATOR automatically converts legacy Ren'Py mods (written for Python 2 / Ren'Py 6–7) into Python 3 compatible code that runs on **Ren'Py 8**. Instead of hours of manual `2to3`-style editing — and breaking your mod — you select a folder, press one button, and get a migrated mod with a full report.

It also unpacks `.rpa` archives and decompiles `.rpyc` bytecode, so even "compiled-only" legacy mods can be migrated.

## What it fixes

| Category | What gets patched |
|---|---|
| ATL transforms | Float/int coordinates, `random.randint` ranges |
| Dict iteration | `iteritems` / `iterkeys` / `itervalues` → `items()` etc. |
| `xrange` | → `range` |
| Exception syntax | `except X, e:` → `except X as e:` |
| Raise syntax | `raise X, msg` → `raise X(msg)` |
| Print | `print "..."` → `print("...")` |
| `has_key` | `d.has_key(x)` → `x in d` |
| Numeric literals | `long` / `L`-suffix → `int`, octal `0755` → `0o755` |
| Strings | `ur"..."` → `r"..."`, backtick `` `expr` `` → `repr(expr)` |
| `unicode` / `basestring` | → `str` |
| bytes/str | Special patch for poem & game scripts (DDLC-style mods) |
| Sorting | `.sort(cmp=...)` — flagged for manual review |
| Imports | Implicit relative imports → explicit |

## Features

- **One-click migration** — recursive processing of selected folders
- **.bak backups** created before every patch
- **Full report** — per-file and per-category statistics after migration
- **RPA unpacking & RPYC decompilation** built into the pipeline
- **RU / EN interface**, dark & light themes

## Documentation

- 📖 **User Guide** — [rootwin.vercel.app/r-migrator-guide](https://rootwin.vercel.app/r-migrator-guide): installation, interface, backup mode, automatic `.rpa` / `.rpyc` unpacking and every migration step
- 🎬 **Video Guide (YouTube)** — [youtu.be/cWujaKRdWEE](https://youtu.be/cWujaKRdWEE)
- 🌐 **Project page** — [rootwin.vercel.app/software/r-migrator](https://rootwin.vercel.app/software/r-migrator)
- 📰 **Release notes** — [R-MIGRATOR v1.1 and auto-unpacking](https://rootwin.vercel.app/news/r-migrator-v1-1-release)

## Requirements

- Windows 10/11 (64-bit)
- No Python installation needed — everything is bundled

## Usage

1. Download the latest release from the [Releases](../../releases) page or from [itch.io](https://rootwin-project.itch.io/rmigrator-beta-v1-1)
2. Run `R-MIGRATOR.exe`
3. Select the mod folder(s), press **EXECUTE**
4. Done — check the report and launch your mod on Ren'Py 8

> **New to R-MIGRATOR?** Follow the step-by-step [User Guide](https://rootwin.vercel.app/r-migrator-guide) or watch the [video guide on YouTube](https://youtu.be/cWujaKRdWEE).

> **Tip:** always migrate a copy of your mod. R-MIGRATOR creates `.bak` backups for every touched file, so you can always roll back manually.

## Third-party components

R-MIGRATOR uses the open-source utilities **rpatool** (RPA archive extraction) and **unrpyc** (Ren'Py bytecode decompiler), © their respective authors.

These utilities are distributed separately: place them into a `deps\` folder next to `R-MIGRATOR.exe` to enable `.rpa` unpacking and `.rpyc` decompilation. Migration of `.rpy` scripts works without them.

## Feedback

Found a mod that migrates incorrectly? Open an [Issue](../../issues) — real-world test cases make the tool better for everyone.

---

<div align="center">

**R-MIGRATOR** — developed by **ROOTWIN PROJECT**

</div>
