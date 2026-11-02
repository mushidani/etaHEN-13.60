# Credits

This project is an unofficial community build of **etaHEN 2.5B Unified** with an updated **kstuff-lite** build integrated for improved PS4-format homebrew compatibility on PS5 firmware 13.60.

This repository does not claim ownership of etaHEN, kstuff-lite, the PS5 payload SDK, or any other upstream component.

All original authors retain their respective copyrights, credits, and licenses.

## etaHEN

Original etaHEN:

- **LightningMods**
- etaHEN contributors

Unified PS5 11.00–13.60 port:

- **GronedWaffel**

Upstream repository:

`https://github.com/GronedWaffel/etahen-11.00-13.60`

This build is based on:

- etaHEN 2.5B Unified
- Base commit: `89123ff`
- Tag: `v2.5B-unified.1`

## kstuff-lite

kstuff-lite:

- **EchoStretch**
- sleirsgoevy
- kstuff contributors

Upstream repository:

`https://github.com/EchoStretch/kstuff-lite`

The bundled version used in this build is:

`aaf921e608c9a3aaff753d92d4b3b16d2724b32d`

This includes the firmware 13.60 launch-context fix:

`Fix PS4 launch-context title override on retail 13.60`

The relevant upstream change preserves the launch-context title ID supplied to ShellCore on retail firmware 13.60.

## PS5 Payload Development

Thanks to:

- **John Törnblom**
- PS5-Payload-dev contributors
- PS5 payload SDK contributors
- libelfldr contributors

These projects provide core tooling and infrastructure used throughout the PS5 homebrew ecosystem.

## Additional Components

Thanks to the authors and contributors of the additional projects and libraries used by etaHEN and its build system, including:

- PS5Debug-NG — Pharaoh2k / OSR and contributors
- PS5 App Dumper — EchoStretch and contributors
- libcurl
- OpenSSL
- zlib
- zstd
- minizip
- libmicrohttpd
- libpsl
- SQLite
- and all other upstream dependencies retained by etaHEN

Each third-party component remains subject to its own license and attribution requirements.

## 13.60 Integration Build

This repository integrates the newer kstuff-lite build into etaHEN and includes build-system adjustments required to reproduce the build under Linux/WSL.

Integration changes include:

- Updated bundled `kstuff.elf`
- Updated kstuff SHA-256 validation
- Updated diagnostic/version strings
- Linux-compatible host tests
- Serial test execution under WSL
- Removal of a stale `wolfssl` linker dependency
- Required external payload/build assets

The integration commit used for the tested build is:

`3dc4453`

## Hardware Validation

The resulting etaHEN ELF was tested on a retail PS5 running firmware **13.60**.

Confirmed working after integrating kstuff-lite `aaf921e`:

- Itemzflow
- PKG-Zone Homebrew Store

These applications previously displayed:

`This PS4 game or demo isn't playable on PS5.`

with the older bundled kstuff configuration.

## Disclaimer

This is an unofficial community project.

It is not affiliated with or endorsed by Sony Interactive Entertainment, LightningMods, EchoStretch, GronedWaffel, or any other upstream project unless explicitly stated by those projects.

Please support and credit the original developers.
