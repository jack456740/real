# Unit 1 — Issue Selection

Path: `beat-1-sandbox/unit-1/selection.md`

Record of the issue carried into Unit 2, and of the evaluation runs that produced
`eval-run.txt`.

---

## Selected issue

**Issue link**

[Claude live-mode evaluation could not be completed. No issue is being claimed as
the selected issue without the required live-mode `accept` verdict.]

**Verdict output**

[Not completed. The required Claude live-mode output was not available. I am not
fabricating a verdict or JSON block.]

---

## Eval iterations

**Run history**

The full evaluation harness was run once with the rubric. The harness reported
errors for all 20 issues because Claude exited with code 1. No agreement score was
produced.

The recorded output included:

`issue-01: ERROR (claude exited 1: )`

and the same `claude exited 1` error occurred for issues 02 through 20.

Because there was no scored agreement result, there is no valid agreement score to
report here.

**Issue analysis**

The full evaluation did not produce a scored issue. For example, the harness
reported:

`issue-01  accept  ERROR`

The gold label for issue-01 was `accept`, but the rubric did not produce a verdict
because the Claude grading process exited with code 1. Therefore, no rubric
reasoning or rubric verdict is being claimed for this issue.

**Check rationale**

> | Maintainer activity | Repo-facts block for default-branch commit dates and the issue's comment thread | At least 1 commit was made to the default branch within the last 90 days, and a maintainer has responded to the issue within the last 90 days | required |

I included this check because a newcomer issue should have evidence that the
repository is currently maintained and that maintainers are still participating in
issue discussions. The check uses specific evidence locations rather than treating
the existence of a repository as proof of current maintenance.

**Trade-offs**

This check gives up some potentially valid issues by requiring both recent
default-branch activity and a recent maintainer response. An issue in an otherwise
active repository could fail if maintainers have not responded to that particular
issue recently. I chose the stricter requirement because the purpose of the rubric
is to identify issues that are realistically actionable for a newcomer during the
course timeframe.

---

## Selection rationale

**Selection rationale**

1. **The issue's fit to my interests and to the time available.**

   I was interested in the LibrePhotos issue because it involves a focused,
   user-facing behavior change in an existing open-source application. It also
   fits my interest in software development, debugging, frontend behavior, and
   working within an unfamiliar codebase. A bounded issue is preferable for the
   course timeframe because it gives me a concrete behavior to investigate without
   requiring me to redesign the application.

2. **What the verdict identified correctly, and what I weighed that the rubric could not.**

   A useful issue-selection process needs to check repository activity, newcomer
   scope, and whether someone else is already working on the issue. Those are
   factors my rubric explicitly addresses. I would also consider practical details
   such as how easily the behavior can be reproduced locally, how familiar I am
   with the relevant part of the codebase, and how clearly the desired behavior is
   described. Those factors are harder to capture with a binary rubric because
   they depend on actually investigating the issue and repository.

3. **The anticipated difficulty in claiming it.**

   The main anticipated difficulty is establishing that the issue is sufficiently
   bounded and that no other contributor has already taken ownership of it. I would
   need to inspect the complete issue discussion, related pull requests, and the
   relevant repository code before claiming it. I would also need to verify that
   the required change can be implemented and tested within the course timeframe.
