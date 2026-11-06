# Changelog

All notable changes to the standards are listed here. The format follows
[Keep a Changelog](https://keepachangelog.com/en/1.1.0/); versions follow
[Semantic Versioning](https://semver.org/).

## [Unreleased]

### Added

- `standards/specification-layout-and-lifecycle.md`: every feature has a
  specification in self-sufficient `spec/<slug>/vN/` directories (`SPEC.toml`,
  EARS requirements, interface catalog, journeys); freezing by owner
  approval, `FREEZE.sha256`, squash merge, and tag `spec/<slug>/vN`; frozen
  versions are never edited or deleted.
- `standards.py check-specs [--base <ref>]` validates layout, freeze hashes,
  tags, `CHANGES.md`, and immutability.
- Roadmap field `specs` (`<slug>@vN`).

### Changed

- **Breaking:** the spec-driven cycle freezes specification versions per
  feature instead of a phase contract; a phase references its features'
  specifications.
- **Breaking:** spec branches are always versioned: `spec/[<issue>-]<slug>-vN`.
- The small-change path freezes the next specification version first.

## [1.0.0] - 2026-11-06

### Added

- First public release of the projectious.work standards: 18 standards,
  agent skills, and `scripts/standards.py` to install, regenerate, and check
  them in a repository.
