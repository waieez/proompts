---
name: review-pull-request
description: >
  Evaluate a pull request and provide specific, actionable feedback or an
  approval recommendation. Use when a PR is ready for review — for example,
  "review this PR", "look at this pull request", "check this code", or "is this
  ready to merge?".
metadata:
  author: proompts
  version: 1.1.0
---

# Review Pull Request

Evaluate a pull request and provide feedback that helps the contributor improve or confirms the work is ready.

## Procedure

1. **Read the diff first.** Form your own understanding of what the change does before reading the PR description. Note whether it solves the problem logically.

2. **Read the description and linked issue.** Compare your understanding to what was claimed. Flag any mismatch between the description and the actual change.

3. **Check contribution standards.** Look for the repository's contributing guide, style rules, and CI requirements. Verify the PR follows them. If the repository doesn't define its own, use [ours](../../CONTRIBUTING.md) as a reference.

4. **Verify evidence.** Confirm that objective proof exists — test results, CI output, before/after comparisons. If evidence is missing, request it. If evidence *cannot* be provided (e.g., UI changes without screenshot tooling), note this as a gap and suggest how to address it.

5. **Assess scope.** Confirm the change is appropriate to the issue. Flag unrelated changes, unnecessary complexity, or missing pieces.

6. **Write feedback.** Be specific and actionable. Reference exact lines or files. Use inline comments for precise issues and a summary comment for high-level observations. Categorize feedback by severity:
   - **Blocking** — must be fixed before merge (bugs, incorrect logic, missing tests, standard violations).
   - **Suggestion** — would improve the change but does not block merge (style, naming, minor refactors).
   - **Observation** — context or questions for the contributor, no action required (design alternatives, future considerations).

7. **State your recommendation.** Either:
   - **Approve** — all standards met, evidence confirmed, no outstanding blocking issues.
   - **Request changes** — specify exactly what needs to change and why, limited to blocking items.
   - **Comment** — observations that don't block merge but should be considered.

## When Steps Fail

- **PR description is missing or inadequate.** Request a proper description before reviewing the code. Without context on *why*, you cannot assess whether the approach is appropriate.
- **Evidence cannot be provided.** Some changes (UI, infrastructure, environment-specific behavior) are hard to prove in CI. Note the gap explicitly, suggest a mitigation (manual test script, screenshot, screencast), and assess the rest of the PR normally.
- **Contributor disagrees with feedback.** If the disagreement is on standards, cite the specific standard. If it's on approach, present your reasoning with evidence and be open to being wrong. If you cannot converge, recommend involving a third party.

## Examples

### Example 1: Approving a clean PR

**Summary comment:**

> Clean implementation. The change matches the issue, tests cover the acceptance criteria, and CI is green.
>
> One minor suggestion on naming (inline), but it doesn't block merge.
>
> **Recommendation: Approve**

**Inline comment (suggestion):**
> `src/client.py` line 34: Consider naming this `request_timeout_seconds` instead of `timeout` to avoid ambiguity with connection timeouts. Not blocking.

### Example 2: Requesting changes

**Summary comment:**

> The approach is sound, but there are two blocking issues:
>
> 1. The regression test doesn't cover the empty-input edge case from the acceptance criteria.
> 2. The encoding fallback in `upload.py` silently swallows `UnicodeDecodeError` — this should log a warning at minimum.
>
> One suggestion inline on error message clarity.
>
> **Recommendation: Request changes**

## Troubleshooting

**Diff is too large to review effectively.**
Cause: The PR bundles multiple logical changes.
Solution: Request the contributor split the PR into smaller, reviewable units. Each PR should represent one logical change.

**CI is failing but the contributor says "it's unrelated".**
Cause: Pre-existing CI failures or flaky tests.
Solution: Verify by checking the CI failure on the default branch. If it fails there too, note it and review the PR normally. If it only fails on the PR branch, it's the contributor's responsibility to fix.

**No linked issue.**
Cause: The PR was opened without an associated issue.
Solution: Ask the contributor to link an issue or explain the motivation directly in the description. Without a "why", scope assessment is guesswork.

## Verification

Every piece of feedback references a specific part of the change. The contributor can act on each comment without asking for clarification. The recommendation is grounded in evidence, and feedback is categorized by severity.
