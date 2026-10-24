# Change branches

These four independent branches start from upstream development at
`6cbd7c6b016f0afba0f0e92a0366b0ba469e2cfd` (2026-10-24, after PR #99).
Their diffs against upstream are separated by category. None requires another
category branch to build or merge. The existing shader_fixes history is retained;
its current tree is cleaned with a forward commit rather than a force push.

| Branch | Outstanding changes |
|---|---|
| `performance` | Native pattern-transfer fills (renderer patch 0076) |
| `shader_fixes` | MED3 quiet-NaN semantics and shader binary revision refresh (0078) |
| `launcher_features` | Vulkan device selector and Fast flips under Display |
| `stability_fixes` | Layered render-target slice-stride compatibility (0077) |

Renderer patch numbers 0073-0075 are reserved for upstream PR #100. That PR is
being tested separately and is not a dependency of these branches. Patch numbers
0076-0078 are globally distinct so the category branches can be combined later.

The earlier VRAM cache bounds, first-load shadow preservation, menu compilation
responsiveness, texture-upload ordering and fiber stack-watch invalidation are
already in the common upstream base through PR #88. They are not duplicated here.

Existing `performance_dev` and `compiler_dev` branches remain unchanged for
historical references and existing users. `shader_fixes` remains the shader branch,
with its unrelated outstanding performance and stability changes moved out. Start new categorized work
from the corresponding clean branch above; do not merge an old mixed branch into it.

Only extracted production changes belong here. Capture tools, GPU value probes,
timing instrumentation, private caches and binaries stay local. Unpublished
compiler-worker, imported-memory lookup, write-accounting and image-clear
experiments require their own clean extraction and validation before promotion.
Split commits that touch multiple categories unless the parts are inseparable;
record any unavoidable cross-category dependency explicitly in its PR.
