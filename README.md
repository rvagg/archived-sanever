sanever
=======

**A saner semver**

This package is a fork of [node-semver](https://github.com/npm/node-semver) with some minor adjustments. The API compatible, the semver range parsing rules are not.

## Sanity?

The changes this library implements are in two areas of the **range parser**: pre-releases are not included in the lower end of an expanded range and `0.x.y` no longer has special meaning for the `^` range specifier.

### Pre-releases and ranges

* Range specifiers `^` and `~` no longer include pre-release versions at the lower bounds. For example, the `~1.2.3` range will no longer match `1.2.3-beta` etc. The range expansion has changed from `>=1.2.3-0 <1.3.0-0` to `>=1.2.3 <1.3.0-0`.
* Incomplete range range specifiers, such as `1.1` and `>1` will no longer include pre-release versions at the lower bounds.
* Range specifiers including `x` and `*`, such as `1.1.x` and `1.*` will no longer include pre-release versions at the lower bounds.

### 0.x is no longer a special case

The `^` range specifier has alternative behaviour for `0.x.x` versions. This has been removed.

node-semver interprets a `^` for `0.x.x` as an *exact* version. sanever handles a `^` at `<1` the same as `>=1`.

`0.x.x` **should not be a special case**. You should communicate the stability of your library via alternative means.

## License and Copyright

The copyright of this library remains Copyright (c) Isaac Z. Schlueter.

Licensed under the BSD License, see the LICENSE file for details.
