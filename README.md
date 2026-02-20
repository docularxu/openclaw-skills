# OpenClaw Skills

Custom skills for [OpenClaw](https://github.com/openclaw/openclaw) - an AI assistant framework.

## Skills

### riscv-spec
Look up RISC-V ISA specification details using the local [riscv-unified-db](https://github.com/riscv/riscv-unified-db) repository. Covers extensions, instructions, encodings, CSR fields, and profile requirements.

### english-word-card
Generate illustrated English word learning cards for kids, with pronunciation, example sentences, and Chinese explanations.

## Installation

Copy the skill directory into `~/.openclaw/skills/`:

```bash
cp -r riscv-spec ~/.openclaw/skills/
```

Or clone the whole repo and symlink:

```bash
git clone https://github.com/docularxu/openclaw-skills.git
ln -s $(pwd)/openclaw-skills/riscv-spec ~/.openclaw/skills/riscv-spec
```

## License

MIT
