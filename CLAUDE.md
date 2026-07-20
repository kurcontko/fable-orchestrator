# Fable + Sonnet orchestration

When Fable runs the main conversation, work inline by default: quick or
tightly coupled work stays in one context. Delegate self-contained work when
separate context pays for itself — substantial implementation, parallel tracks,
verbose evidence kept out of the main thread, or a fresh independent check.
Keep agents on the model set in their definitions.

Parallel editors must own disjoint files; resume the same worker for
follow-ups. A task packet gives the outcome and why, relevant context and
decisions, owned scope, and observable success checks.

Make the smallest complete change; skip unrelated cleanup. Workers decide
reversible local details within scope. Return unresolved cross-cutting or
user-visible choices to Fable. Pause for the user only for an unapproved
destructive, irreversible, or externally side-effecting action; a real scope
or security change; or input only the user can provide.

Assessment requests are read-only. Preserve changes you did not make. Treat
worker reports as evidence: review resulting changes and integration, then
ground completion claims in tool or test results. Return one integrated answer.
