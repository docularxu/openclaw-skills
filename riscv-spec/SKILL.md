---
name: riscv-spec
description: Look up RISC-V ISA specification details using the local riscv-unified-db repository. Activate when answering questions about RISC-V extensions, instructions, encodings, assembly syntax, CSR fields, profile requirements, or any ISA-level spec claim. Also use for verifying RISC-V spec claims before stating them. For intrinsics (compiler-level), check the rvv-intrinsic-doc repo via GitHub API instead.
---

# RISC-V Spec Lookup

## Rule
Never state RISC-V spec claims without verifying against the local UDB or upstream spec sources. If UDB doesn't cover it, say so.

## Local Database

Path: `~/`.openclaw/workspace/riscv-unified-db/

### Extensions
```
spec/std/isa/ext/<Name>.yaml
```
Example: `spec/std/isa/ext/Zicclsm.yaml`

Fields: `name`, `long_name`, `description`, `versions[]` (state, ratification_date), `requirements`

### Instructions
```
spec/std/isa/inst/<Ext>/<name>.yaml
```
Example: `spec/std/isa/inst/I/add.yaml`, `spec/std/isa/inst/V/vadd.vv.yaml`

Fields: `name`, `long_name`, `description`, `assembly` (syntax), `encoding.match` (bitmask), `encoding.variables[]` (operand bit locations), `access` (s/u/vs/vu permissions)

### CSRs
```
spec/std/isa/csr/<name>.yaml  or  spec/std/isa/csr/<Ext>/<name>.yaml
```
Fields: register fields, access modes, descriptions

### Profiles
```
cfgs/profile/RVA23U64.yaml
cfgs/profile/RVA22U64.yaml
cfgs/profile/RVA20U64.yaml
```
Check mandatory/optional extension lists for profile conformance questions.

## Lookup Procedure

1. **Extension questions** - Read `spec/std/isa/ext/<Name>.yaml`. Use `find ... -iname '*keyword*'` if unsure of exact filename.
2. **Instruction questions** - Read `spec/std/isa/inst/<Ext>/<name>.yaml`. List directory first if unsure: `ls spec/std/isa/inst/<Ext>/`
3. **CSR questions** - Search: `grep -rl '<csr_name>' spec/std/isa/csr/`
4. **Profile questions** - Read `cfgs/profile/<Profile>.yaml` for extension lists. For profile spec prose, fetch from `riscv/riscv-profiles` repo via `gh api`.
5. **Cross-reference** - Use `grep -r '<term>' spec/std/isa/` to find all mentions.

## What UDB Does NOT Cover

- **Intrinsics**: Compiler-level (e.g., `__riscv_vadd_vv_i32m1`). Use `riscv/rvv-intrinsic-doc` repo via `gh api`.
- **ABI/calling conventions**: See `riscv/riscv-elf-psabi-doc`.
- **Platform specs**: See `riscv/riscv-platform-specs`.
- **Prose-heavy spec text**: UDB has structured data; for full rationale or detailed notes, check `riscv/riscv-isa-manual` or `riscv/riscv-profiles`.
