# Third-party software

Claire's proprietary notice applies to Claire itself. Included third-party
software retains its own licences. Complete original notices, attribution,
GPL worker sources and corresponding-source locations are shipped in the
components and the release's
[THIRD_PARTY_LICENSES.tar.zst](https://github.com/AeroMatrix-M/claire/releases/download/v0.1.5-beta/THIRD_PARTY_LICENSES.tar.zst).
Verify that archive with the release's `SHA256SUMS`. The installed index is
`app/licenses/THIRD_PARTY.md`, with GPL details in `THIRD_PARTY_GPL.md`.
The exact runtime versions and build hashes are in the release's `versions.lock`.

**Corresponding source.** The exact source of every GPL and LGPL component
this release ships is published with it as `src_*` assets, listed with their
SHA-256 in [SOURCES.md](https://github.com/AeroMatrix-M/claire/releases/download/v0.1.5-beta/SOURCES.md) and in `SHA256SUMS`.

**This product includes Kratos Multi-Physics technology.**

**This product includes Kratos Structural Mechanics technology.**

**This product includes Kratos CoSimulation technology.**

**This product includes Kratos Optimization technology.**

**This product includes Kratos Shape Optimization technology.**

| Component | Shipped version | Licence / source |
|---|---|---|
| Kratos Multiphysics and applications (Structural, Contact, ConstitutiveLaws, LinearSolvers, ConvectionDiffusion, Meshing, MeshMoving, Mapping, Statistics, DEM, CoSimulation, Rom, Optimization, ShapeOptimization) | 10.4.2, wheel build 1 | BSD terms with required acknowledgements; [Kratos](https://github.com/KratosMultiphysics/Kratos/tree/v10.4.2); bundled third-party code (AMGCL, Eigen and Spectra (MPL-2.0), pybind11, nanoflann, CoSimIO, Triangle and others) listed in `THIRD_PARTY.md` |
| MMG (inside Kratos MeshingApplication) | 5.5.1 | LGPL-3.0-or-later, unmodified shared libraries, dynamically linked; [exact source](https://github.com/AeroMatrix-M/claire/releases/download/v0.1.5-beta/SOURCES.md) |
| build123d | 0.10.0 | Apache-2.0; [source](https://github.com/gumyr/build123d) |
| OCP / Open CASCADE | 7.8.1.1.post1 / 7.8.1 | LGPL-2.1 with OCCT exception; [OCP](https://github.com/CadQuery/OCP), [OCCT](https://dev.opencascade.org/) |
| PySide6 / Qt / shiboken6 | 6.11.0 | Supplied LGPL/GPL notices and exceptions; [exact source](https://github.com/AeroMatrix-M/claire/releases/download/v0.1.5-beta/SOURCES.md) (Qt and Qt for Python 6.11.0) |
| FFmpeg (inside Qt Multimedia) | n7.1.3 | LGPL-2.1-or-later build; [exact source](https://github.com/AeroMatrix-M/claire/releases/download/v0.1.5-beta/SOURCES.md) |
| LibRaw (inside the OCP wheel) | 0.19.5 | LGPL-2.1 or CDDL-1.0; [exact source](https://github.com/AeroMatrix-M/claire/releases/download/v0.1.5-beta/SOURCES.md) |
| libtiff (inside the OCP wheel; rebuilt by Claire without JBIG) | 4.1.0+git191117-2ubuntu0.20.04.14 | libtiff licence (BSD-style), `licenses/libtiff-COPYRIGHT.txt`; [Ubuntu source](https://launchpad.net/ubuntu/+source/tiff/4.1.0+git191117-2ubuntu0.20.04.14). JBIG-KIT is no longer shipped. |
| FreeImage (inside the OCP wheel) | 3.18.0 | FreeImage Public License 1.0 (Claire takes FreeImage under the FIPL, one of its three licences); text in `licenses/FreeImage-FIPL-1.0.txt`; [exact source](https://github.com/AeroMatrix-M/claire/releases/download/v0.1.5-beta/SOURCES.md) |
| NumPy / SciPy | 2.4.4 / 1.17.1 | BSD and bundled-library notices; [NumPy](https://github.com/numpy/numpy), [SciPy](https://github.com/scipy/scipy) |
| libquadmath (GCC; numpy.libs, scipy.libs, core runtime) | GCC 4.8.5-44.el7 / 8.5.0-26.el8_10.alma.1 / 16.2.0 (conda-forge) | LGPL-2.1-or-later, unmodified shared libraries; [exact GCC source](https://github.com/AeroMatrix-M/claire/releases/download/v0.1.5-beta/SOURCES.md) |
| Python | 3.12.3 | PSF and included notices; [source](https://www.python.org/downloads/source/) |
| GNU Readline, libnsl, libxcrypt, GNU binutils ld, xz GPL scripts (core runtime, conda-forge) | 8.3 / 2.0.1 / 4.4.38 / 2.46.1 / 5.8.3 | GPL-3.0 / LGPL-2.1 / LGPL-2.1+ / GPL-3.0 / GPL-2.0+; [exact source and recipes](https://github.com/AeroMatrix-M/claire/releases/download/v0.1.5-beta/SOURCES.md) |
| FFTW, GNU Readline, GMP, MPFR, MUNGE, libnl, libnuma, libudev, Scotch (CFD, Ubuntu 24.04 packages) | see SOURCES.md | GPL / LGPL / CeCILL-C; [exact Ubuntu source packages](https://github.com/AeroMatrix-M/claire/releases/download/v0.1.5-beta/SOURCES.md) |
| Gmsh | 4.15.2 | GPL-2.0-or-later with linking exception; [exact source](https://github.com/AeroMatrix-M/claire/releases/download/v0.1.5-beta/SOURCES.md) |
| foamlib | 1.8.1 | GPL-3.0-only; [exact source](https://github.com/AeroMatrix-M/claire/releases/download/v0.1.5-beta/SOURCES.md) |
| OpenFOAM | 2406, patch 260127 | GPL-3.0-or-later; [exact source](https://github.com/AeroMatrix-M/claire/releases/download/v0.1.5-beta/SOURCES.md) (maintenance-v2406 commit 1653fa08); shipped helper modifications are included as source |
| Open MPI | 4.1.6 | BSD and bundled-component notices; [source](https://www.open-mpi.org/software/ompi/v4.1/) |
| OpenPMIx (Open MPI's launch layer; libpmix, plugins, help) | 5.0.1 (Ubuntu 5.0.1-4.1build1) | BSD-style (Open MPI licence family); notice in CFD `licenses/system/libpmix2t64-copyright.txt`; [source](https://github.com/openpmix/openpmix/tree/v5.0.1) |
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
