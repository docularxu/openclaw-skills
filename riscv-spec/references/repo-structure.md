# riscv-unified-db Repository Structure

## Key Directories

```
riscv-unified-db/
├── spec/std/isa/
│   ├── ext/              # Extension definitions (Zicclsm.yaml, V.yaml, etc.)
│   ├── inst/             # Instruction definitions, grouped by extension
│   │   ├── I/            # Base integer (add, sub, lw, sw, ...)
│   │   ├── M/            # Multiply/divide
│   │   ├── A/            # Atomics (old, split into Zaamo/Zalrsc)
│   │   ├── F/            # Single-precision float
│   │   ├── D/            # Double-precision float
│   │   ├── V/            # Vector
│   │   ├── C/            # Compressed
│   │   ├── B/            # Bitmanip
│   │   ├── H/            # Hypervisor
│   │   ├── S/            # Supervisor
│   │   ├── Zaamo/        # Atomic memory operations
│   │   ├── Zalrsc/       # Load-reserved/store-conditional
│   │   ├── Zba/          # Address generation
│   │   ├── Zbb/          # Basic bit manipulation
│   │   ├── Zbc/          # Carry-less multiply
│   │   ├── Zbs/          # Single-bit operations
│   │   ├── Zcb/          # Compressed bitmanip
│   │   └── ...           # ~60 extension groups total
│   ├── csr/              # CSR definitions (~93 files)
│   └── profile/          # Profile definitions
├── cfgs/
│   └── profile/          # Profile configs (RVA23U64.yaml, etc.)
└── schemas/              # JSON schemas for validation
```

## Upstream Repos for What UDB Doesn't Cover

| Topic | Repo |
|-------|------|
| Profile spec prose | `riscv/riscv-profiles` (src/rva23-profile.adoc) |
| ISA manual prose | `riscv/riscv-isa-manual` |
| Vector intrinsics | `riscv-non-isa/rvv-intrinsic-doc` |
| ELF/ABI | `riscv-non-isa/riscv-elf-psabi-doc` |
| Platform specs | `riscv-non-isa/riscv-platform-specs` |
