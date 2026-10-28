# OpenCourant external libraries for OpenReader

This fork publishes the SDK-free dependency package used by the OpenReader-only
OpenCourant removal branch. OpenReader is built from the solver source.

## Current package

| Release | Archive | SHA-256 |
| --- | --- | --- |
| [v82-openreader-1](https://github.com/SyazwanSamad/extlib/releases/tag/v82-openreader-1) | `extlib.zip` | `72831a1b3e95910e20e24cceb6fb6c4295cfab1fade01144f2cee53c603442a3` |

The 26,112,105-byte archive contains 3,327 files. `extlib.manifest.json` lists
their sizes and hashes, and `SHA256SUMS` covers both release assets.
The solver's `EXTLIB_VERSION.json` pins the URL/digest; its loader validates the
package identity, rejects retired/unsafe payloads and refreshes stale caches.

| Retained component | License |
| --- | --- |
| Boost 1.70.0 | BSL-1.0 |
| exprtk | MIT |
| LAPACK 3.10.0 | BSD-style upstream notice |
| metis | Original upstream notice |
| MD5 | RSA MD5 notice |
| zlib | zlib |

Component bytes are unchanged from authenticated upstream v82. The embedded
package identity is updated. All eleven remaining open-source notices are
preserved in `extlib/license/` and [LICENSES](LICENSES/), including notices for
code used by the in-tree reader. Compiler, math and MPI runtimes remain separate
solver-package dependencies.

HM Reader, H3D Reader/Writer, their SDK headers/import/shared libraries, their
limited-use notices, and the reader's private APR payload/notice are absent from
this package. Use native animation, history, STATE or DYNAIN outputs with current
solver builds; removed output requests fail explicitly.

## Provenance and reproduction

The source is the authenticated, unmodified
[upstream v82 archive](https://github.com/OpenCourant/extlib/releases/tag/upstream-v82-extlib),
SHA-256 `2d0365018e67dd4813e6a2cf2ebf19d00d4771aa1aeb9b9706b7ea45fbb56982`.
It is a historical source artifact and is not a fallback for current builds.

`Compiling_tools/script/repack_extlib.py` in the solver checkout filters that
archive, preserves retained bytes/notices and writes deterministic ZIP metadata.
Two independent repacks produced the published digest. Older solver versions
requiring the retired libraries use their historical dependency releases.

This is a dependency publication; it does not publish solver binaries or claim
the full cross-platform solver release gate.
