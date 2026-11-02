# etaHEN 2.5B Unified + kstuff-lite 13.60 Launch Fix

Unofficial community build of **etaHEN 2.5B Unified** with the newer **kstuff-lite `aaf921e`** build integrated directly into etaHEN.

This build fixes the PS4 launch-context issue on **retail PS5 firmware 13.60** that can cause PS4-format homebrew applications to display:

> This PS4 game or demo isn't playable on PS5.

[![Downloads](https://img.shields.io/github/downloads/mushidani/etaHEN-13.60/total?label=Downloads)](https://github.com/mushidani/etaHEN-13.60/releases/latest)
[![Latest Release](https://img.shields.io/github/v/release/mushidani/etaHEN-13.60?label=Latest%20Release)](https://github.com/mushidani/etaHEN-13.60/releases/latest)

## Download

[⬇️ Download Latest Release](https://github.com/mushidani/etaHEN-13.60/releases/latest)

[⬇️ Direct ELF Download](https://github.com/mushidani/etaHEN-13.60/releases/latest/download/etaHEN-13.60-working-aaf921e.elf)

## What was fixed

The original etaHEN 2.5B Unified build bundled **kstuff-lite v1.11**.

kstuff-lite later received a firmware 13.60 fix:

**Commit:** `aaf921e608c9a3aaff753d92d4b3b16d2724b32d`

**Upstream change:**
`Fix PS4 launch-context title override on retail 13.60`

The fix preserves the supplied launch-context title ID instead of allowing ShellCore to override it.

The relevant firmware 13.60 patch added upstream is:

```c
{0x8239BF, "\xeb\x46", 2},
```

This skips the ShellCore title-ID override and preserves the title ID supplied by the launcher.

## Confirmed working

Hardware tested on a retail PS5 running:

- Firmware **13.60**
- Relapse jailbreak / ELF loader
- etaHEN 2.5B Unified
- kstuff-lite commit `aaf921e`

Confirmed applications:

- Itemzflow
- PKG-Zone Homebrew Store

Both previously produced the PS4 compatibility message and launch correctly with this build.

## Included kstuff

This etaHEN build bundles:

```text
EchoStretch/kstuff-lite
Commit: aaf921e608c9a3aaff753d92d4b3b16d2724b32d
```

Do **not** load standalone kstuff before or after loading this etaHEN build.

Loading multiple kstuff instances may cause instability or freezes.

## Installation

Start from a fresh PS5 boot.

Run your compatible jailbreak / ELF loader and send the included etaHEN ELF.

Example with an ELF loader listening on port `9021`:

```bash
nc -w 15 <PS5_IP> 9021 < etaHEN-13.60-kstuff-aaf921e.elf
```

Do not load another etaHEN instance or standalone kstuff during the same boot.

## Build information

Base etaHEN:

```text
GronedWaffel/etahen-11.00-13.60
etaHEN 2.5B Unified
Base commit: 89123ff
Tag: v2.5B-unified.1
```

Integrated kstuff:

```text
EchoStretch/kstuff-lite
Commit: aaf921e
```

Custom integration commit:

```text
3dc4453
Integrate kstuff 13.60 launch-context fix and Linux build fixes
```

## Tested ELF

SHA-256:

```text
0cce7da6fba48665bc05633f2c6378cc711daaee86859560450cc5a236fbbd70
```

Size:

```text
42795336 bytes
```

## Additional build changes

In addition to updating the bundled kstuff ELF, several build-system fixes were required for reproducible Linux/WSL builds:

- Updated expected bundled kstuff hash.
- Updated etaHEN diagnostics to identify kstuff `aaf921e`.
- Removed stale `wolfssl` linker dependency.
- Fixed Linux compatibility in host tests.
- Changed tests to run serially under WSL.
- Added required `elfldr.elf` build asset.
- Preserved upstream etaHEN functionality.

All local tests passed:

```text
tests 21
pass 21
fail 0
cancelled 0
```

## Why this works

The issue was not primarily caused by Itemzflow or Homebrew Store.

Both applications are PS4-format homebrew applications running through PS5 backward-compatibility functionality.

On firmware 13.60, the older bundled kstuff could allow ShellCore to replace the supplied PS4 launch-context title ID.

The newer kstuff patch prevents this override, allowing the application launch context to remain valid.

## Credits

This is an unofficial community build.

Original projects and contributors retain all credit.

### etaHEN

Original etaHEN by **LightningMods** and etaHEN contributors.

Unified 11.00–13.60 port maintained by **GronedWaffel**.

### kstuff-lite

kstuff-lite maintained by **EchoStretch** and contributors.

Firmware 13.60 launch-context fix by the upstream contributors responsible for:

```text
Fix PS4 launch-context title override on retail 13.60
```

### Other upstream work

Thanks to:

- sleirsgoevy
- EchoStretch
- LightningMods
- GronedWaffel
- PS5-Payload-dev contributors
- etaHEN contributors
- kstuff contributors
- everyone involved in PS5 homebrew development

## Disclaimer

This project is unofficial and is not affiliated with Sony Interactive Entertainment.

Use at your own risk.

This repository exists to document and distribute a reproducible integration of upstream open-source fixes.

## Upstream repositories

etaHEN Unified:

```text
https://github.com/GronedWaffel/etahen-11.00-13.60
```

kstuff-lite:

```text
https://github.com/EchoStretch/kstuff-lite
```
