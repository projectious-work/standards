# projectious.work company standards

Engineering and agent-operation standards of projectious.work, vendored from
<https://github.com/projectious-work/standards>. Each file is one standard; its
`## Agent briefing` is the short binding summary.

Do not edit this directory in a consuming repository. Change a standard
upstream, release it, and reinstall; `python3 .standards/standards.py check`
reports local edits and drift. The exact version is recorded in `lock.json`.

## License and attribution

- Standards text: © projectious.work, licensed under
  [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).
- `standards.py`: MIT License, © projectious.work.
- `sources/i-have-adhd/`: third-party, MIT License, © 2026 Ayoub Ghriss; see
  its `LICENSE` and `UPSTREAM.md`. `agent-communication.md` adapts it.
