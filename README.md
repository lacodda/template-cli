# template-cli

> Command-line tool: Rust, clap, anyhow, dialoguer

A [lyrn](https://lyrn.lacodda.com) template of the `cli` form. lyrn generates from it only at a tag whose CI passed, and the CI here generates every combination of its add-ons and runs the gate each generated project ships with.

```console
$ lyrn new my-app --template lacodda/template-cli@v1.0.0
```

## Add-ons

- `--with keyring` - Secrets in the OS keyring, never in a config file
- `--with self-update` - A `self-update` command that reads the releases page

## Changing it

The project's files live under `template/`; `template.toml` says which belong to which add-on. `lyrn template check .` holds the template to what lyrn will accept. See [writing a template](https://lyrn.lacodda.com/reference/template/).
