# Changelog

All notable changes to the standards are listed here. The format follows
[Keep a Changelog](https://keepachangelog.com/en/1.1.0/); versions follow
[Semantic Versioning](https://semver.org/).

## [Unreleased]

### Changed

- Resolved contradictions across the standards: release tags bind the approved
  tree (artifacts precede the squash commit); roadmap `done` and `released`
  are set by follow-up `chore/` pull requests; product releases always use
  SemVer; no secret in any configuration layer; side-effect-free MCP tools are
  outside the agent-native standard; stdio MCP servers log to stderr; the
  execution budget no longer assumes CI.
- A final release may differ from its last accepted release candidate only in
  version metadata and changelog (previously: not silently).
- Added the MCP server application profile and a conventions section
  (Semantic Anchors pin, RFC 2119 keywords, briefings) in `standards/README.md`;
  every standard using anchors points to it.
- Condensed duplicated rules into references (Git spec and release record,
  host-phase coverage, documentation roadmap section, test-ready definition)
  and shortened several agent briefings without changing rules.

## [2.0.0] - 2026-11-06

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
