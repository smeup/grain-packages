# Grain packages

The store of the grain packages installed by Kokos.

## Layout

```
packages/<name>/package.yaml             name, description, publisher
packages/<name>/versions/<version>.yaml  grainVersion, publishedAt, components
index.yaml                               catalog read by Kokos (generated)
```

The name of a package and its versions are defined by the paths. A version is a
[semantic version](https://semver.org) (e.g. `1.2.0`, `1.3.0-rc.1`) and the latest is the highest one.

## Publishing a version

A published version is immutable: to change a package publish a new version, with a new file in its `versions`
folder, and rebuild the index:

```
python3 scripts/build_index.py
```

The CI checks that the index is up to date and that no published version is changed or removed.
