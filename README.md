# Basler Playground Plugins

This is an artifact-only public release repository. It contains no plugin
implementation, build system, or deployment tooling.

Build and publication logic is maintained in the parent workspace under
`deploy/`. This repository receives only independently versioned plugin
release assets and the mutable `plugin-channel` catalog through GitHub
Releases.

## Release assets

- Package releases use `plugin-<id>-v<plugin-version>` tags.
- Each package release contains a Windows ZIP and its SHA-256 sidecar.
- `plugin-channel` exposes `plugins-index.json` with exact package URLs and
  SHA-256 values.

Published assets are consumed by the host application; Git history in this
repository is not a source checkout and must not gain generated package,
catalog, or deployment files.

Existing release tags and assets are immutable and are not rewritten during
repository cleanup.
