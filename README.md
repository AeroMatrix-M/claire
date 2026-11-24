# Claire — Linux beta (Windows experimental)

Claire is an AI-driven parametric CAD application with a graphical interface:
describe a design, review and edit the geometry, mesh it, and run structural FEA
or optional CFD. Parts are parametric build123d models using Open CASCADE;
meshing uses Gmsh, FEA uses Kratos Multiphysics, and CFD uses a bundled open-source CFD solver.
Engineering results require independent verification.

This repository distributes the proprietary beta. Application source is private.
Use is governed by the [Claire Beta Tester Terms, agreement 0.1](LICENSE).
Claire Free records scrubbed training data locally; Enterprise excludes the
collector. Bring your own model-provider API key; you enter it in Claire
(Settings → AI), not in the installer.

## Install v0.1.7-beta

One version, two installers — Linux: `install.sh` · Windows: `Claire-Setup.exe` (experimental until tested on hardware).

Download the installer from the [prerelease](https://github.com/AeroMatrix-M/claire/releases/tag/v0.1.7-beta):

```sh
curl -fLO https://github.com/AeroMatrix-M/claire/releases/download/v0.1.7-beta/claire-installer-regular.run
curl -fLO https://github.com/AeroMatrix-M/claire/releases/download/v0.1.7-beta/SHA256SUMS
awk '$2=="claire-installer-regular.run"' SHA256SUMS | sha256sum -c -
sh claire-installer-regular.run
```

Or use the verified-installer entrypoint:

```sh
curl -fsSL https://github.com/AeroMatrix-M/claire/releases/download/v0.1.7-beta/install.sh | sh
```

No GitHub login, systemd or sudo is needed by Claire. The installer uses a
dialog (kdialog on KDE, otherwise zenity or kdialog), then a PySide6 wizard for
component selection, with sizes and live progress; without a display it asks everything on the terminal,
so `curl … | sh` works over SSH too. Nothing is staged in `/tmp`; downloads
resume from the install directory after an interruption. Choose
CFD only on a compatible system. Enterprise uses `claire-installer-enterprise.run`
or `curl -fsSL https://github.com/AeroMatrix-M/claire/releases/download/v0.1.7-beta/install.sh | CLAIRE_EDITION=enterprise sh`.

Default install: `~/.local/share/claire`; launcher: `~/.local/bin/claire`;
workspace: `~/Claire_Workspace`. AI providers are set up inside Claire (Settings → AI); keys are local, mode 600.
Claire checks for a new release once a day (an anonymous request to this
repository's `channels/beta.json`; nothing about your install is sent), and
Settings → General → **Check for updates** checks on request. **Install**
downloads and verifies the new installer, closes Claire, updates it and starts
it again. Updates retain unchanged components, your workspace and settings.
Run the installed `uninstall.sh` to remove
Claire while preserving the workspace and configuration; `uninstall.sh --purge`
removes everything Claire created, **including `~/Claire_Workspace` and your
Vault**, after you confirm.

For offline installation, download the installer, `manifest.json`, `SHA256SUMS`
and the desired component archives into one directory, verify the checksums,
then run `sh claire-installer-regular.run -- --from "$PWD"`.
Full instructions and tested dependency commands are in the release's
[INSTALL.md](https://github.com/AeroMatrix-M/claire/releases/download/v0.1.7-beta/INSTALL.md).

## Windows (experimental)

**Experimental — not yet tested on Windows hardware; Linux recommended.**
The steps Setup runs inside Linux are tested on Canonical's Ubuntu 24.04 WSL
image, but the Windows side (the wizard, turning on WSL, the restart,
shortcuts, uninstall) has not yet been run on a Windows PC. Please report
what happens in an [issue](https://github.com/AeroMatrix-M/claire/issues).

Download `Claire-Setup.exe` from the release page (it is listed in the
release's `SHA256SUMS`) and run it. No Linux terminal is shown at any point.

- Needs Windows 11, or Windows 10 version 22H2 or newer, 64-bit (x64), with
  virtualization turned on, and 12 GB free disk space.
- Setup gives Claire its own Linux environment, a WSL distribution named
  `Claire` (it never touches an `Ubuntu` distribution you may have). It
  downloads Canonical's official Ubuntu 24.04 WSL image from
  releases.ubuntu.com and checks its SHA-256, then installs Claire inside it.
  If the PC does not have WSL yet, Setup turns it on (administrator
  permission) and restarts the PC once; Setup continues by itself.
- Start Claire from the Start menu or the desktop. Claire runs best on Linux:
  under WSL, large meshes, FEA and CFD are slower, and Linux gets about half of
  the PC's memory by default.
- Updates: Settings → General → Check for updates, as on Linux. Running
  `Claire-Setup.exe` again repairs or updates the installation and keeps your
  designs.
- Uninstall from Settings → Apps (or Add or remove programs). It asks whether
  to delete your designs, and keeps them by default: they are copied to
  `Documents\Claire_Workspace` and checked first. WSL itself stays installed.
- To skip the large downloads, put a `claire-assets` folder next to
  `Claire-Setup.exe` with this release's files (and optionally Canonical's
  Ubuntu WSL image); see [INSTALL.md](https://github.com/AeroMatrix-M/claire/releases/download/v0.1.7-beta/INSTALL.md).

**SmartScreen:** beta builds of `Claire-Setup.exe` are not code-signed, so
Windows may show "Windows protected your PC". Check the file against
`SHA256SUMS` (in PowerShell: `Get-FileHash Claire-Setup.exe`), then choose
**More info → Run anyway**.

## Requirements and limits

- Linux x86_64; core/CAD/mesh/FEA/gateway require glibc >= 2.34.
- **CFD requires glibc >= 2.38: Ubuntu 24.04+, Fedora 39+, Arch, Debian 13.**
  Ubuntu 22.04 and Debian 12 run CAD/mesh/FEA only. Ubuntu 24.04 (the Windows
  setup's base) is a required release test: install, AI turn, numerical gate
  and every CFD solver family. The installer detects incompatible components and refuses
  them before downloading.
- GPU and system driver with OpenGL 3.3+; system graphics, XCB/Wayland and font
  libraries. The installer reports missing libraries and the exact package-manager
  command; drivers, libGL and Mesa are not bundled.
- 16–32 GiB RAM recommended; about 4 GiB free disk (checked by the installer). Network access for online installation
  and your chosen AI provider; `curl` for the download commands above.
- Linux; Windows is experimental (through WSL, above). External CFD remains unvalidated, with no boundary layers.
  Offscreen tests do not prove rendering on your display.

v0.1.7-beta is tested on Ubuntu 24.04, Arch and Fedora 44 (public online
install, an installed AI turn, packaged numerical gate, every CFD solver
family). Ubuntu 22.04/Debian 12 passed CAD/mesh/FEA and verified CFD refusal
with v0.1.0-beta's Python runtime, whose conda builds this release keeps
(since v0.1.4 the core adds the Optimise packages and a JBIG-free libtiff);
the FEA and CFD components are unchanged since v0.1.3. Earlier releases stay available on the
[releases page](https://github.com/AeroMatrix-M/claire/releases).

## Acknowledgements and support

**This product includes Kratos Multi-Physics technology.**

**This product includes Kratos Structural Mechanics technology.**

**This product includes Kratos CoSimulation technology.**

**This product includes Kratos Optimization technology.**

**This product includes Kratos Shape Optimization technology.**

See [THIRD_PARTY.md](THIRD_PARTY.md) for dependency licences, source locations
and the downloadable full notices. The exact source of every GPL and LGPL
component shipped is published with the release
([SOURCES.md](https://github.com/AeroMatrix-M/claire/releases/download/v0.1.7-beta/SOURCES.md)). Third-party rights remain unchanged.
For beta support, Terms or Enterprise enquiries, [open an issue](https://github.com/AeroMatrix-M/claire/issues).
