# Contributing to {{ title }}

## The gate

```console
$ cargo fmt --check && cargo clippy --all-targets -- -D warnings && cargo test
```

The same commands CI runs, so a green terminal means a green pull request.

The tests in `tests/` run the built binary the way a user does. One of them,
`tests/installers.rs`, reads the two installers rather than running them: it
holds them to what the line learned the hard way - a Windows shell running the
Unix script is sent to the PowerShell one, and both name a crate that exists.

`rust-version` in `Cargo.toml` is a promise to anyone running `cargo install`.
A CI job builds on exactly that version, so the number cannot quietly rot.

## Layout

| Path | What lives there |
| --- | --- |
| `src/cli.rs` | The command surface: every flag and subcommand |
| `src/commands/` | One module per command |
| `tests/` | Tests that run the built binary, as a user would |
| `assets/` | The mark's three master SVGs, and the `.ico` the Windows binary embeds |
| `tools/` | The installers the README points at |
| `npm/` | The npm package: a launcher that fetches the release binary |
| `docs/adr/` | Architecture decisions, newest last |

The mark in `assets/` is the line's umbrella mark - lambda on graphite - until
the product has one of its own; `lyrn.toml` says `mark = "placeholder"`
meanwhile. The `.ico` is drawn from the masters by `docs/export-assets.mjs`,
which comes with the documentation site (`lyrn new {{ name }} --form docs`).

## Commits

[Conventional Commits](https://www.conventionalcommits.org/), in English:
`feat:`, `fix:`, `docs:`, `chore:` and the rest. The changelog is generated
from them (`cliff.toml`), so a commit message is the line the release notes
will carry.

## Decisions

An architectural decision gets a record in [`docs/adr/`](docs/adr/README.md):
one file, numbered, newest last. A decision that replaces an earlier one says
so, and the earlier one is marked superseded rather than deleted.

## Dependencies

Updated by hand, at most once a week, in a commit of their own - Dependabot is
off on purpose ([ADR 0002](docs/adr/0002-dependabot-is-off.md)). The audit
workflow fails on a published advisory, and on a dependency whose license is
not on the accepted list.

## Assistant files

Instructions for coding assistants - `CLAUDE.md`, `AGENTS.md`, `.claude/`,
`.cursor/` and the like - stay on the machine they were written for, and
`.gitignore` keeps them out of the repository. What anyone needs to know about
the project, human or agent, is in this file and in [`llms.txt`](llms.txt).

## Conduct and security

Everyone taking part follows the [Code of Conduct](CODE_OF_CONDUCT.md). A
vulnerability is reported privately, as [SECURITY.md](SECURITY.md) describes -
never in a public issue.

## License

By contributing, you agree that your contributions are licensed under the
project's [MIT license](LICENSE).
