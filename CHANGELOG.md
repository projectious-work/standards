# Changelog

All notable changes to the standards are listed here. The format follows
[Keep a Changelog](https://keepachangelog.com/en/1.1.0/); versions follow
[Semantic Versioning](https://semver.org/).

## [Unreleased]

### Added

- Agent building: definitions add context, authority, and output examples;
  named agents keep their role visible and disclose AI in external messages;
  instructions carry no emotional appeals, rewards, or invented urgency;
  skill authoring rules (frontmatter with when and when not, declared inputs
  and outputs, `references/` loaded on need, function-named chaining);
  review cadence (at least quarterly) with sessions that end in an approved
  definition diff.
- Agent use: agents draft outward-facing text for a person to send, unless
  their authority grants a bounded message class; batch-run rules (plan
  questions first, resumable progress, category with action per item,
  escalations as one batch); simulated personas are labelled and never count
  as evidence.

### Changed

- User-interface design: the brand repository's released brand contract is
  authoritative; standards and skills never restate brand values.

## [2.2.0] - 2026-11-08

### Added

- `standards/agent-building.md`: agent definitions state job, persona as Big
  Five (OCEAN) levels with a company default profile, instructions, tools,
  model, and evaluation; design with DMADV, SOTA check, control-chart evals.
- `standards/agent-use.md`: what to delegate (Value Stream Mapping), open
  work (GTD), knowledge and memory (BASB), improvement (PDCA), adoption (Team
  Topologies, Kotter).
- `standards/user-interface-design.md`: Dieter Rams, Progressive Disclosure,
  Apple HIG, Adobe Spectrum as behavior reference, Bringhurst typography,
  accessibility for all interfaces.
- `standards/command-line-interface-design.md`: a shared CLI baseline and
  three command-grammar styles to choose from per CLI (Unix utility,
  verb–resource as in kubectl, object–action as in OpenStackClient), recorded
  in an ADR; part of the `standard-application-engineering` skill.
- Skills `standard-agent-building`, `standard-agent-use`, `standard-ui-design`;
  application profile "AI agent".
- Semantic Anchors applied across the standards: KISS, YAGNI, Deep Modules,
  Conway's Law, DRY, CUPID, GoF, Design by Contract, Defensive Programming,
  ISO/IEC 25010, SOTA (architecture); Chesterton's Fence (refactoring);
  50/72 Rule (commits, titles up to 72 characters); OWASP Top 10 (security);
  Plain Language, ASD-STE100, Progressive Disclosure, MECE (documentation);
  Pyramid Principle, MECE, Plain Language (communication); Unix
  Philosophy (CLI design); Laddering, MECE tasks, ISO/IEC 25010, PDCA
  (spec-driven cycle).

### Changed

- Squash-merge titles may not exceed 72 characters (*50/72 Rule*); before,
  there was no limit.
- Refactoring procedure gains a *Chesterton's Fence* step (steps renumbered
  2–7). Untrusted input is validated where it enters and again before
  filesystem or process use. Security, refactoring, and documentation
  briefings name their new rules.
- Semantic Anchors catalog pin moved to `6554641a` (2026-11-06); anchor names
  aligned with catalog titles (SOLID Principles, Test Double (Meszaros),
  Domain-Driven Design according to Evans).

## [2.1.0] - 2026-11-07

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
- Shortened the release-note template to one paragraph, removed the aibox
  example paragraphs and non-normative reference links, merged two
  AI-accessibility principles into the MCP tools section, moved TUI layout
  tests into the host-phase operator contract, and reduced the communication
  pre-send check to a reference to its rules.

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
