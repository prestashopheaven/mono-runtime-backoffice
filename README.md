# mono-runtime-backoffice

Back-office building blocks of PrestaHaven modules: loading the module's admin scripts on its own pages, the admin TypeScript helpers, and later the settings page, grids, messages and the product form.

A monorepo of the PrestaHaven package collection: every folder in `packages/` is one Composer package, published as a
read-only repo `prestashopheaven/runtime-<folder>` on Packagist. All packages of this monorepo share one version.
The plan, the rules and the other monorepos: `docs/packages/` in the PrestaHaven workspace.

## Packages

| Package | Use when |
|---|---|

(`ps-module mono packages` lists them; the package index in the workspace has every class.)

## Work on it

```
composer install
composer check                 # ps-module mono check: the definition of done of every package
ps-module mono package <dir> "<description>" "<use when>" <keywords>   # a new package
```

Changes are made here, never in a split repo.

## Release

1. Write the changes under `## X.Y.Z` in `CHANGELOG.md` (and in the `CHANGELOG.md` of each changed package).
2. `ps-module mono set-version X.Y.Z` (root version, branch aliases, internal constraints).
3. Commit `Release X.Y.Z - <notes>` on `main` and push.

The release workflow checks everything, tags `vX.Y.Z`, makes the GitHub release, splits every package to its repo with
the same tag and updates Packagist. Never tag by hand.
