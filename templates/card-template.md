---
id: prNN                    # your PR number, e.g. pr17
from:                       # your project / agent context, e.g. "my-pipeline-agent"
to: hop3                    # the project being reported (= directory name)
severity:                   # high = blocks your work / mid = workaround exists / low = improvement
probe:                      # REQUIRED. Executable command + expected result, runnable in YOUR environment.
                            # e.g.: npx hopjit validate attachments/min-repro.md → exit 0, 0 errors
fix_commit:                 # leave empty — filled by fixer
verified_at:                # leave empty — filled by you when your probe passes after the fix
---

## Symptom

<!-- What happens and why it hurts. Write it self-contained: the fixer should be able to
     understand and act after reading this card alone, without asking you anything. -->

## Reproduction / Evidence

<!-- Steps or a minimal repro. Put evidence FILES (minimal spec, log slices, state snapshots)
     into the attachment directory named after this card (prNN_<statement>_open/).
     Do NOT reference volatile runtime paths alone (logs that rotate, temp dirs) —
     slice the relevant part into an attachment and cite the attachment path. -->

## Expected behavior

<!-- What "correct" looks like. -->

## Log

<!-- Append-only, one line per action, newest last. Format:
- YYYY-MM-DD open (<your-context>, <your-git-email>): filed. probe: <one-line restatement>
-->
