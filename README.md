# Claude agents

This project provides an optional routing policy for using Fable as the main
model and pinned Sonnet agents for bounded work. It is not a mandatory pipeline:
Fable should work directly when a handoff would add more overhead than value.

## Setup

Start Claude Code from this directory with Fable as the main model:

```sh
claude --model fable
```

Keep `CLAUDE_CODE_SUBAGENT_MODEL` unset, or set it to Sonnet:

```sh
unset CLAUDE_CODE_SUBAGENT_MODEL
# or
export CLAUDE_CODE_SUBAGENT_MODEL=sonnet
```

That environment variable takes precedence over the `model` field in an agent
definition. The three definitions in `.claude/agents/` pin their workers to
Sonnet and choose effort and tools for each role:

- `executor` owns a substantial implementation unit from investigation through
  tests;
- `researcher` gathers focused read-only evidence when separate context helps;
- `verifier` independently checks completed material or risky changes.

Fable may use none, one, or several of them. Parallel implementation work must
have disjoint file ownership. Describe a task naturally or adapt
`task-template.md`; `CLAUDE.md` supplies the routing policy.

## Reuse

These files are project-local: they apply only to sessions started in this
directory. To use the setup in another repo, copy or symlink `CLAUDE.md` and
`.claude/agents/` into it, or install the agent files to `~/.claude/agents/`
to make them available globally.
