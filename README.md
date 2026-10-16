# Basler Playground Plugins

Public distribution of independently versioned Playground device plugins.
Download plugin packages through **Device > Manage Plugins** or the Releases page.
Core installers are distributed separately in `Minu-Park/Basler-Playground`.

This repository contains release ZIPs, `plugin-artifacts.json`, the mutable
`plugin-channel/plugins-index.json` catalog.
Source pins, builds, tests, packaging and full diagnostic logs belong to the
private `Minu-Park/pg-plugins` integration repository. There are no public build or dispatch workflows. Device implementation,
source tags and release notes remain in each owning source repository.

The private Publishing workflow uploads verified drafts here. A person performs
final publication. After publication, run the private Catalog workflow for the
exact plugin release tag; it verifies published assets before updating the catalog.
No workflow deletes historical releases or resets the catalog. This public
repository requires no CI secret or private-workflow dispatch token.
