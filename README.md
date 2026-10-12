# CS:GO Legacy custom characters

This repository distributes ported player models and their associated first-person arms, sleeves, hands, and custom materials where available.

## Downloads

Download the ZIP for the character you want from the [Model packages v1 release](https://github.com/lanesuwu/csgo-playermodels/releases/tag/models-v1). Each package contains its runtime dependencies. The GitHub-generated source archives are not model packages.

For manual installation, extract the ZIP into the game's **csgo** content folder, preserving the `models/` and `materials/` directory layout. `package.json` is package metadata; it is not required by the engine. No drive letter is required or assumed.

`catalog.json` provides the exact player and first-person model paths, categories, package versions, download URLs, archive SHA256 checksums, sizes, and preview framing. `registry.json` preserves stable sharing IDs. A model package includes only runtime assets and package metadata, not authoring sources or local logs.

## Loader status

The Unified online catalog and installer integration is still in development. The currently installed Unified v2.24 does not automatically download this catalog. The tested native installer supports streamed extraction, archive SHA256 validation, actual MOD content-root resolution, resumable journals, and removal of the temporary ZIP after a successful committed installation. In-game testing remains manual.

The initial Mamehinata package uses versioned `mamehinata/v1/` paths. The other initial packages retain their established canonical paths. Do not replace files for an actively loaded model; future package updates should use new compiled model and material paths.

## Catalog maintenance

Publish all ZIP assets before updating `catalog.json`. Keep published package URLs and ZIP bytes immutable. Add new models with new stable IDs; never reuse a retired wire ID. Change categories or labels in the catalog without changing the stable model ID. Retire a model by setting `active` to false or removing it from the visible catalog while retaining its ID in `registry.json`.

For an asset update, publish a new package version and compile a new model/material namespace, then update its catalog entry. Clients should refresh metadata automatically and offer an explicit Update action; an update must not silently equip a different revision.
