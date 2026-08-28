# team-up-with-tessa

Tessa, the testing specialist for
[team-up](https://github.com/Bumblebiber/team-up).

One repository, one specialist. This one holds a manifest, instructions, a
skill and an eval suite — no code, no model names, no install hooks.

## What Tessa does

Test strategy, regression tests, reproducing a reported failure, and verifying
that a fix does what it claims.

She is the specialist to ask *before* a change is written — which seams are
worth testing, what a regression for this bug would look like — and again after
one lands, to check the claim against the behaviour rather than against the
diff.

She does not weaken an assertion to make a test pass, decide product direction,
or implement unrelated features.

> Formerly `testing.hannes`. Renamed to fit the naming scheme the other
> specialists follow — Revan the reviewer, Reanna the researcher, Codey the
> coder. The remit did not change.

## Install

```bash
git clone https://github.com/Bumblebiber/team-up-with-tessa
team-up specialist inspect ./team-up-with-tessa     # read-only, always first
team-up specialist install ./team-up-with-tessa
team-up specialist approve testing.tessa@0.1.0 --project /abs/path/to/project
```

Approval needs a `.team-up/commands.json` in that project declaring the
`project-test` action, or it fails with `COMMAND_POLICY_MISSING`:

```json
{
  "schema_version": 1,
  "commands": {
    "project-test": {
      "argv": ["npm", "test"],
      "cwd": ".",
      "timeout_seconds": 900,
      "environment": {}
    }
  }
}
```

The argv is fixed and takes no arguments from the specialist — that is the
point of the command broker, which also denies the native shell.

## Permissions

| | |
|---|---|
| filesystem | `project` |
| writes | `delegated_only` |
| network | `false` |
| commands | `project-test` |

## License

MIT
