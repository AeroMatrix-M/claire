# Claire — Linux beta

Claire is an AI-driven parametric CAD application with a graphical interface:
describe a design, review and edit the geometry, mesh it, and run structural FEA
or optional CFD. Parts are parametric build123d models using Open CASCADE;
meshing uses Gmsh, FEA uses Kratos Multiphysics, and CFD uses OpenFOAM.
Engineering results require independent verification.

This repository distributes the proprietary beta. Application source is private.
Use is governed by the [Claire Beta Tester Terms, agreement 0.1](LICENSE).
Claire Free records scrubbed training data locally; Enterprise excludes the
collector. Bring your own model-provider API key; you enter it in Claire
(Settings → AI), not in the installer.

## Install v0.1.2-beta

Download the installer from the [prerelease](https://github.com/AeroMatrix-M/claire/releases/tag/v0.1.2-beta):

```sh
curl -fLO https://github.com/AeroMatrix-M/claire/releases/download/v0.1.2-beta/claire-installer-regular.run
curl -fLO https://github.com/AeroMatrix-M/claire/releases/download/v0.1.2-beta/SHA256SUMS
awk '$2=="claire-installer-regular.run"' SHA256SUMS | sha256sum -c -
sh claire-installer-regular.run
```

Or use the verified-installer entrypoint:

```sh
curl -fsSL https://github.com/AeroMatrix-M/claire/releases/download/v0.1.2-beta/install.sh | sh
```

No GitHub login, systemd or sudo is needed by Claire. The installer uses a
dialog (kdialog on KDE, otherwise zenity or kdialog), then a PySide6 wizard for
component selection, with sizes and live progress; without a display it asks everything on the terminal,
so `curl … | sh` works over SSH too. Nothing is staged in `/tmp`; downloads
resume from the install directory after an interruption. Choose
CFD only on a compatible system. Enterprise uses `claire-installer-enterprise.run`
or `curl -fsSL https://github.com/AeroMatrix-M/claire/releases/download/v0.1.2-beta/install.sh | CLAIRE_EDITION=enterprise sh`.

Default install: `~/.local/share/claire`; launcher: `~/.local/bin/claire`;
workspace: `~/Claire_Workspace`. AI providers are set up inside Claire (Settings → AI); keys are local, mode 600.
Updates retain unchanged components. Run the installed `uninstall.sh` to remove
Claire while preserving the workspace and configuration; `uninstall.sh --purge`
removes everything Claire created, **including `~/Claire_Workspace` and your
Vault**, after you confirm.

For offline installation, download the installer, `manifest.json`, `SHA256SUMS`
and the desired component archives into one directory, verify the checksums,
then run `sh claire-installer-regular.run -- --from "$PWD"`.
Full instructions and tested dependency commands are in the release's
[INSTALL.md](https://github.com/AeroMatrix-M/claire/releases/download/v0.1.2-beta/INSTALL.md).

## Requirements and limits

- Linux x86_64; core/CAD/mesh/FEA/gateway require glibc >= 2.34.
- **CFD requires glibc >= 2.38: Ubuntu 24.04+, Fedora 39+, Arch, Debian 13.**
  Ubuntu 22.04 and Debian 12 run CAD/mesh/FEA only. **Ubuntu 24.04 is not yet
  container-tested.** The installer detects incompatible components and refuses
  them before downloading.
- GPU and system driver with OpenGL 3.3+; system graphics, XCB/Wayland and font
  libraries. The installer reports missing libraries and the exact package-manager
  command; drivers, libGL and Mesa are not bundled.
- 16–32 GiB RAM recommended; about 4 GiB free disk (checked by the installer). Network access for online installation
  and your chosen AI provider; `curl` for the download commands above.
- Linux only; external CFD remains unvalidated, with no boundary layers.
  Offscreen tests do not prove rendering on your display.

v0.1.2-beta is tested on Arch and Fedora 44 (public online install, an
installed AI turn, packaged numerical gate). Ubuntu 22.04/Debian 12 passed
CAD/mesh/FEA and verified CFD refusal with v0.1.0-beta's runtime, which this
release reuses unchanged. Earlier releases stay available on the
[releases page](https://github.com/AeroMatrix-M/claire/releases).

## Acknowledgements and support

**This product includes Kratos Multi-Physics technology.**

**This product includes Kratos Structural Mechanics technology.**

See [THIRD_PARTY.md](THIRD_PARTY.md) for dependency licences, source locations
and the downloadable full notices. Third-party rights remain unchanged.
For beta support, Terms or Enterprise enquiries, [open an issue](https://github.com/AeroMatrix-M/claire/issues).
