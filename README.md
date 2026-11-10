# Claire — Linux beta

Claire is an AI-driven parametric CAD application with a graphical interface:
describe a design, review and edit the geometry, mesh it, and run structural FEA
or optional CFD. Parts are parametric build123d models using Open CASCADE;
meshing uses Gmsh, FEA uses Kratos Multiphysics, and CFD uses OpenFOAM.
Engineering results require independent verification.

This repository distributes the proprietary beta. Application source is private.
Use is governed by the [Claire Beta Tester Terms, agreement 0.1](LICENSE).
Claire Free records scrubbed training data locally; Enterprise excludes the
collector. Bring your own model-provider API key.

## Install v0.1.0-beta

Download the installer from the [prerelease](https://github.com/AeroMatrix-M/claire/releases/tag/v0.1.0-beta):

```sh
curl -fLO https://github.com/AeroMatrix-M/claire/releases/download/v0.1.0-beta/claire-installer-regular.run
curl -fLO https://github.com/AeroMatrix-M/claire/releases/download/v0.1.0-beta/SHA256SUMS
awk '$2=="claire-installer-regular.run"' SHA256SUMS | sha256sum -c -
chmod +x claire-installer-regular.run
./claire-installer-regular.run
```

Or use the verified-installer entrypoint:

```sh
curl -fsSL https://github.com/AeroMatrix-M/claire/releases/download/v0.1.0-beta/install.sh | sh
```

No GitHub login, systemd or sudo is needed by Claire. The installer uses zenity,
kdialog or a terminal, then a PySide6 wizard for component and API setup. Choose
CFD only on a compatible system. Enterprise uses `claire-installer-enterprise.run`
or `curl -fsSL https://github.com/AeroMatrix-M/claire/releases/download/v0.1.0-beta/install.sh | CLAIRE_EDITION=enterprise sh`.

Default install: `~/.local/share/claire`; launcher: `~/.local/bin/claire`;
workspace: `~/Claire_Workspace`. API configuration is local and mode 600.
Updates retain unchanged components. Run the installed `uninstall.sh` to remove
Claire while preserving the workspace and configuration; `--purge` also removes
configuration and keys, never the workspace.

For offline installation, download the installer, `manifest.json`, `SHA256SUMS`
and the desired component archives into one directory, verify the checksums,
then run `./claire-installer-regular.run -- --from "$PWD"`.
Full instructions and tested dependency commands are in the release's
[INSTALL.md](https://github.com/AeroMatrix-M/claire/releases/download/v0.1.0-beta/INSTALL.md).

## Requirements and limits

- Linux x86_64; core/CAD/mesh/FEA/gateway require glibc >= 2.34.
- **CFD requires glibc >= 2.38: Ubuntu 24.04+, Fedora 39+, Arch, Debian 13.**
  Ubuntu 22.04 and Debian 12 run CAD/mesh/FEA only. **Ubuntu 24.04 is not yet
  container-tested.** The installer detects incompatible components and refuses
  them before downloading.
- GPU and system driver with OpenGL 3.3+; system graphics, XCB/Wayland and font
  libraries. The installer reports missing libraries and the exact package-manager
  command; drivers, libGL and Mesa are not bundled.
- 16–32 GiB RAM recommended; 8 GiB free disk. Network access for online installation
  and your chosen AI provider; `curl` for the download commands above.
- Linux only; external CFD remains unvalidated, with no boundary layers.
  Offscreen tests do not prove rendering on your display.

The existing offline matrix passes Ubuntu 22.04/Debian 12 for CAD/mesh/FEA and
verified CFD refusal, and Arch/Fedora 44 including pipe CFD. See the release's
validation evidence for its exact scope.

## Acknowledgements and support

**This product includes Kratos Multi-Physics technology.**

**This product includes Kratos Structural Mechanics technology.**

See [THIRD_PARTY.md](THIRD_PARTY.md) for dependency licences, source locations
and the downloadable full notices. Third-party rights remain unchanged.
For beta support, Terms or Enterprise enquiries, [open an issue](https://github.com/AeroMatrix-M/claire/issues).
