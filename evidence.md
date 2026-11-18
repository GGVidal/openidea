# Evidence for #4339 / PR #4363

Composer `! <command>` was sent to the agent as a normal prompt because OpenIDEA drives
`claude -p` (and other providers) over ACP — Claude Code’s interactive bash mode never runs.

## Fix
- `shell::bang_command` detects a leading `!` with a non-empty rest
- `Task::run` diverts to `run_shell` (task cwd, user’s `$SHELL` / `cmd`)
- Conversation shows an `execute` tool entry; Stop kills the child
- Finished results ride along as `<context ref="shell:…">` on the next real prompt

## Commands
```
cargo test -p ide-agent --lib shell::
cargo clippy -p ide-agent --all-targets -- -D warnings
```

## Real output used in after.png
```
## fix/agent-bang-shell-command...origin/fix/agent-bang-shell-command
?? .scratch/
```

## Context block used in after-2.png
```
<context ref="shell:!git status --short -b">
$ git status --short -b
## fix/agent-bang-shell-command...origin/fix/agent-bang-shell-command
?? .scratch/
(exit 0)
</context>
```
