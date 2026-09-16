<!-- The merge gate checks paths and dependency files automatically. The items
     below are the part it cannot check. A reviewer will close a PR that ticks
     boxes it cannot justify. -->

## What changed and why

<!-- One or two sentences. What behavior changes for a caller or a gate? -->

## The gate will hold this PR if it touches maintainer-owned paths

Those paths are listed in `scripts/merge-gate.sh`. If the gate fails on your PR,
that is the gate working: a maintainer reviews the change, and an intentional,
reviewed change merges via administrator bypass, which leaves the review in the
PR history.

## Checklist

- [ ] **No new third-party dependency** (Go or Rust) was added. If one was, the
      gate holds the PR — say here why it is warranted and what trust it brings.
- [ ] **No severity threshold moved** without a reason traceable to something
      the attestation run actually surfaced (`docs/attestation-run.md`).
- [ ] **No verdict is published that the evidence does not support.** Undetermined
      stays undetermined; nothing renders "could not check" as "this is fine".
- [ ] **Tests pass locally**: `go test ./...` and `cd assay-contracts && cargo test`.
- [ ] If this PR touches a fail-closed path, **a test would fail if the
      fail-closed behavior regressed** — a fix without a regression test is a
      fix that can silently break again.
