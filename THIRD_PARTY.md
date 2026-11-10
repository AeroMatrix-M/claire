# Third-party software

Claire's proprietary notice applies to Claire itself. Included third-party
software retains its own licences. Complete original notices, attribution,
GPL worker sources and corresponding-source locations are shipped in the
components and the release's
[THIRD_PARTY_LICENSES.tar.zst](https://github.com/AeroMatrix-M/claire/releases/download/v0.1.0-beta/THIRD_PARTY_LICENSES.tar.zst).
Verify that archive with the release's `SHA256SUMS`. The installed index is
`app/licenses/THIRD_PARTY.md`, with GPL details in `THIRD_PARTY_GPL.md`.
The exact runtime versions and build hashes are in the release's `versions.lock`.

**This product includes Kratos Multi-Physics technology.**

**This product includes Kratos Structural Mechanics technology.**

| Component | Shipped version | Licence / source |
|---|---|---|
| Kratos Multiphysics and used applications | 10.4.2, wheel build 1 | BSD terms with required acknowledgements; [Kratos](https://github.com/KratosMultiphysics/Kratos/tree/v10.4.2) |
| build123d | 0.10.0 | Apache-2.0; [source](https://github.com/gumyr/build123d) |
| OCP / Open CASCADE | 7.8.1.1.post1 / 7.8.1 | LGPL-2.1 with OCCT exception; [OCP](https://github.com/CadQuery/OCP), [OCCT](https://dev.opencascade.org/) |
| PySide6 / Qt / shiboken6 | 6.11.0 | Supplied LGPL/GPL notices and exceptions; [Qt for Python](https://code.qt.io/cgit/pyside/pyside-setup.git/) |
| NumPy / SciPy | 2.4.4 / 1.17.1 | BSD and bundled-library notices; [NumPy](https://github.com/numpy/numpy), [SciPy](https://github.com/scipy/scipy) |
| Python | 3.12.3 | PSF and included notices; [source](https://www.python.org/downloads/source/) |
| Gmsh | 4.15.2 | GPL-2.0-or-later with linking exception; [exact source](https://gmsh.info/src/gmsh-4.15.2-source.tgz) |
| foamlib | 1.8.1 | GPL-3.0-only; [exact source](https://github.com/gerlero/foamlib/tree/v1.8.1) |
| OpenFOAM | 2406, patch 260127 | GPL-3.0-or-later; [upstream source](https://dl.openfoam.com/source/v2406/OpenFOAM-v2406.tgz); shipped helper modifications are included as source |
| Open MPI | 4.1.6 | BSD and bundled-component notices; [source](https://www.open-mpi.org/software/ompi/v4.1/) |
| GNU Bash | 5.2.21, Ubuntu 5.2.21-2ubuntu4 | GPL-3.0-or-later; complete corresponding upstream and Ubuntu source archives included in CFD's `licenses/bash-source` |
| Makeself | 2.5.0 | GPL-2.0-or-later; [exact source](https://github.com/megastep/makeself/tree/release-2.5.0), original shell source included in installer |

OCP/OCCT and PySide6/Qt are dynamically loaded and unmodified. You may replace
LGPL libraries and reverse engineer Claire to debug modifications to those
libraries as their licences permit. Claire makes use of facilities provided
by Open CASCADE Technology. Qt PDF/PDFium and transitive libraries have their
own notices in the full archive.

Gmsh, foamlib, OpenFOAM and Bash run as separate processes. The two Claire GPL
workers, `core/gmsh_worker.py` and `core/foam_worker.py`, are GPL-3.0-or-later;
their complete source is supplied in both the app and notices archive.

The gateway retains its upstream MIT notice and notices for 151 locked Linux
Rust dependencies. Python/conda packages, MPI, decoder libraries, fonts and
other transitive libraries retain their original notices in component licence
directories. Materials include permitted FreeCAD CC-BY cards with attribution
and recorded corrections, and documented public-domain entries; see installed
`app/licenses/MATERIALS_ATTRIBUTION.md`. No GPU driver, libGL or Mesa is bundled.
