# Basler Playground Plugins

This repository is the public distribution plane for Basler Playground device
plugins. It owns plugin package metadata, catalog generation, release assets,
and the tooling that builds a package from an immutable Playground source ref.

Device-plugin implementation remains in the Playground host workspace and its
independently versioned device modules. This repository does not replace those
source repositories or duplicate their implementation.

## Plugins

| ID | Display name | Current package baseline |
| --- | --- | --- |
| `camera` | Basler Camera | `1.0.1` |
| `framegrabber` | Basler Frame Grabber | `0.1.1` |
| `gocator` | LMI Gocator | `0.1.1` |
| `heliotis-c4` | Heliotis C4 | `0.1.2` |

Each package contains the generated `plugin.json`, the platform plugin
library, and the package-owned runtime payload. A package release is named
`plugin-<id>-v<plugin-version>` and publishes a ZIP plus its SHA-256 sidecar.
The package manifest records the compatible Core version, source ref, source
commit, package version, release tag, and platform.

## Migration baseline

The `plugins/` directory contains the four canonical package-manifest
snapshots. `catalog/v0.5.0-candidate/plugins-index.json` records the current
four-plugin candidate and points to exact future assets in this repository.
It is intentionally not the active Core catalog yet: the Core `v0.5.0`
release and the separate package releases must be verified before the host is
switched from the legacy catalog location.

The old `Basler-Playground` release repository remains unchanged during this
staged migration. Existing tags and assets are not moved or rewritten.

## Package workflow

Build one package from an immutable host ref:

```powershell
.\plugin-package.ps1 `
    --core-tag v0.5.0 `
    --source-ref v0.5.0 `
    --plugin camera `
    --version 1.0.1
```

Validate and upload the resulting artifact as a draft package release:

```powershell
.\plugin-deployment.ps1 -ArtifactDirectory .\dist\plugin-camera-v1.0.1
```

Generate the four-entry catalog from package artifact manifests:

```powershell
.\plugin-catalog.ps1 `
    -CoreTag v0.5.0 `
    -ArtifactRoot .\dist `
    -OutputPath .\dist\plugins-index.json
```

The catalog uses each plugin's immutable release tag and exact SHA-256. Core
and Full installers consume a pinned package snapshot; they never resolve a
package through a moving `latest` URL.

## Release policy

- Keep package versions independent from the Core version.
- Create and verify draft releases before publication.
- Never move an existing tag or overwrite a published package.
- Keep the product's Core `Latest` policy separate from plugin package releases.
- Preserve the Basler Playground EULA and all applicable vendor SDK terms.
