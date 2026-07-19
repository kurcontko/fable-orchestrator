# Fable + Sonnet orchestration

Use this routing policy when Fable is the main model. Custom agents still
follow these project instructions together with their agent definition and task
packet.

## Roles and routing

- Fable owns user intent, cross-cutting decisions, integration, risk, and the
  final response. Keep project agents on the model pinned in their definitions
  unless the user explicitly requests an override.
- Work inline by default. Dispatch an agent only when a task matches a bullet
  below and is large enough that delegation costs less than doing it directly.
- Use `researcher` for independent, high-volume read-only work whose raw context
  should stay out of the main conversation.
- Use `executor` for a substantial, self-contained implementation unit:
  investigate, implement, test, and self-verify. Parallel executors must own
  disjoint files.
- Use `verifier` for a fresh independent check after material or risky work,
  especially when behavior can be checked independently. Skip it for trivial
  changes.
- Parallelize only independent work. Keep tightly coupled work in one context —
  usually Fable's own; otherwise one agent, resumed for follow-ups.

## Delegation

Each task packet states the outcome, relevant context and prior decisions,
owned scope and non-goals, and observable acceptance checks. Request a compact
return containing the outcome, files or evidence, checks, and unresolved risks.

Workers may make reversible local decisions within their assigned scope.
Escalate only an unresolved choice that the task packet does not settle and that
would materially change architecture, user-visible behavior, a public interface,
security or data handling, or expand assigned scope—or that requires information
only the user has.

## Completion

Preserve existing user changes. Assessment requests are read-only. Ground
progress and completion in files, diffs, tool results, or tests. Fable reviews
integration and returns one synthesized answer rather than agent transcripts.
