# Catalogs

Catalogs map a plugin ID to an exact package release asset and SHA-256 value.
They are generated from `plugin-artifacts.json` files rather than edited by
hand for an active channel.

The `v0.5.0-candidate` catalog is a migration snapshot. Do not point a
published Core build at it until all four package releases and the matching
Core compatibility release have passed their package and clean-install gates.
