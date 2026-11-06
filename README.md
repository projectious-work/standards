# projectious.work standards

The engineering and agent-operation standards of
[projectious.work](https://projectious.work), plus the tooling that delivers
them to AI coding agents (Claude Code, Codex, and any harness that reads
`AGENTS.md` and `.agents/skills/`).

## What is here

| Path | Content |
|---|---|
| `standards/` | One Markdown file per standard; each ends with an `## Agent briefing`. |
| `standards/schemas/` | JSON schemas referenced by standards. |
| `standards/sources/` | Third-party material that standards adapt, kept unmodified. |
| `scripts/standards.py` | Installs, regenerates, and checks the standards in a repository. |

The standards cover agent communication and execution budget, Git branching
(*GitHub Flow*) and releases, specification layout and spec-driven development, architecture and
refactoring, application engineering (*Twelve-Factor App* alignment), agent
interfaces, security, public documentation, and roadmaps.

## How agents receive them

Each standard loads in three levels so only what a task needs enters context:

1. **Always on:** the communication and execution-budget briefings, written
   into the repository's `AGENTS.md` between `COMPANY_STANDARDS` markers.
2. **Skills:** one `standard-*` skill per standard group in
   `.agents/skills/` (with `.claude/skills/` symlinks), loaded when the task
   matches.
3. **Full standard:** the file the skill names; it is authoritative.

## Use in a repository

From a clean checkout of a release tag:

```sh
git clone --branch v1.0.0 https://github.com/projectious-work/standards /tmp/standards
python3 /tmp/standards/scripts/standards.py install /path/to/repo
```

This vendors the bundle into `.standards/` (with `lock.json` recording version,
commit, and file hashes), generates the skills, and writes the always-on block
into `AGENTS.md`. Commit the result through a `chore/` pull request.

In the repository afterwards:

```sh
python3 .standards/standards.py check   # exit 1 on local edits or drift
python3 .standards/standards.py sync    # regenerate skills and AGENTS.md block
python3 .standards/standards.py check-specs [--base main]   # spec/ layout and freezes
```

To upgrade, rerun `install` from a newer tag.

## Changing a standard

1. Edit `standards/<file>.md` on a `chore/` branch, including its
   `## Agent briefing`.
2. Run `python3 scripts/standards.py sync`; `sync --check` exits 1 on drift.
3. Merge after owner approval; releases follow
   `standards/git-branching-and-releases.md` and are listed in `CHANGELOG.md`.

## License

Standards text: [CC BY 4.0](LICENSE). Scripts: [MIT](LICENSE-CODE).
`standards/sources/` keeps its own licenses.
