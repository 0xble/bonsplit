# Maintenance

## Background

Maintained source fork: `0xble/bonsplit` of `manaflow-ai/bonsplit`; both use
`main`. This temporary clone was inspected from owned `origin/main`
`d395b38281dc508dd937d1db6e0176bfb4ec37c0`; its accepted upstream baseline is
`836e52483df65933744025f8cd4ab48c6f6d2d22`. Publish only to `origin`, never
upstream. Installation and any running app are separate stages.

## Preserve

- Pane zoom must notify the hosting controller; tab-bar placement remains a
  public configuration choice and preserves pane/tab interaction.

## Active patches

### BONSPLIT-001: `fix(zoom): notify hosts on pane zoom changes`

- **Provenance:** `13e6de47317172e2e9487fe97dc4c1171f804d2f`.
- **Surfaces:** `SplitViewController.swift`, `BonsplitController.swift`.
- **Upstream issue / PR:** None after checked 2026-09-09 / None after checked 2026-09-09.
- **Regression:** Blocked: this patch added no focused test; add a host-notification regression before reconciliation or publication.
- **Rollback:** Revert `13e6de47317172e2e9487fe97dc4c1171f804d2f` and run the complete gate.
- **Retire when:** an upstream release supplies equivalent notification behavior and focused proof.

### BONSPLIT-002: `feat(appearance): add tab bar position`

- **Provenance:** `d395b38281dc508dd937d1db6e0176bfb4ec37c0`.
- **Surfaces:** `PaneContainerView.swift`, `TabBarView.swift`, `TabItemView.swift`, `BonsplitConfiguration.swift`.
- **Upstream issue / PR:** None after checked 2026-09-09 / None after checked 2026-09-09.
- **Regression:** Blocked: no focused placement/interaction regression was added; add one before reconciliation or publication.
- **Rollback:** Revert `d395b38281dc508dd937d1db6e0176bfb4ec37c0` and run the complete gate.
- **Retire when:** an upstream release supplies the configuration and interaction contract with focused proof.

## Update and verify

Every run fetches owned `main` and the latest upstream `main`, reconciles only
these active patches, runs `swift test` and `swift build`, then publishes only
when both blocked regressions are resolved. Immediately fetch upstream again;
`git rev-list --left-right --count upstream/main...main` must have zero
upstream-only commits. After authorized publication, require local/`origin/main`
SHA parity. Report `Blocked` with exact refs and failed proof otherwise. Do not
install, activate, or validate runtime without separate authorization and exact
runtime-SHA proof.
