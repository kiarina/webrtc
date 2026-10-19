# External-media integration branch

This branch combines core PR#314 with the wrapper's existing m150 custom-audio,
libwebrtc GN target and extended shared-mode format patches. The PR topic remains
separate. These integration commits are not upstream merge claims.

Base:51c367e209f8f12b39bd8dd0ca70bf588f42cb48. Recording policy proposal:
543b9cb70ee7b07311d4f4ddefc014278d6066d4. The three ordinary wrapper patches come
from libwebrtc f9a23f98e19c2784fd293941b9e67a43977f1635, in this order:

1. patches/custom_audio_source_m150.patch
2. patches/add_libwebrtc_build_target.patch
3. patches/allow_176k4_192k_shared_mode_formats.patch

The15 changed production/build files match the previously tested Windows x64
candidate after line-ending normalization. The candidate DLL SHA-256 is
73b672f90beba282e04ae6dd9dbcb7b3af574d192977ae9224c382075dbcd740.
This is a source reconstruction check, not a new all-platform/full-presubmit pass.
The focused core70/wrapper25 tests and the known broad-core test failures are
recorded in the validation lab:
https://github.com/kiarina/labs/tree/main/2026/10/19/flutter-windows-upstream-external-input

Pin source and corresponding headers/import library/DLL together. Ordinary
recording remains the default; only explicitly external-input factories disable
recording. Source owners and a caller-owned capture pipeline remain separate.
