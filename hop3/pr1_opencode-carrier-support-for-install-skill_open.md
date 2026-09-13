---
id: pr1
from: hoplogic3 maintainer session (dogfood run of this channel)
to: hop3
severity: low
probe: hopjit install-skill --carrier opencode → exit 0, driver skill files present under opencode's skill directory; then in an opencode session, /hopspec run <any example spec> drives one step successfully
fix_commit:
verified_at:
---

## Symptom

`hopjit install-skill` currently supports the carriers `claude-code` (default), `codex`, `cfuse-cc`, and `cfuse-codex`. There is no carrier option for [opencode](https://github.com/sst/opencode). Users who run opencode as their coding agent cannot install the HopSpec driver skill through the supported path — they would have to hand-copy skill files and guess at the correct layout, with no engine/driver version pairing guarantee (the exact tearing that `install-skill` exists to prevent).

## Reproduction / Evidence

```
$ hopjit install-skill --carrier opencode
→ rejected: unknown carrier (current carrier set: claude-code | codex | cfuse-cc | cfuse-codex)
```

## Expected behavior

`--carrier opencode` is accepted and installs the driver skill set (hopspec + hopspec-mcp, matching the dual-name dual-shell convention of the existing carriers) into the directory opencode reads skills from, so that an opencode session can drive HopSpec execution the same way Claude Code and Codex sessions do. Carrier-specific adaptation (prompt-format differences, tool-invocation conventions) should follow the existing thin-protocol precedent: the carrier layer stays thin, engine-side protocol stays identical across carriers.

## Log

- 2026-09-13 open (hoplogic3, lenx.wei@gmail.com): filed. Also a dogfood run of the PR-as-card flow on this freshly published channel. probe: install via `--carrier opencode` succeeds and an opencode session drives one step.
