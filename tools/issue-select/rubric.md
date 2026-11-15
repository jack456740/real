# Rubric: is this a good first issue?

<!--
THIS IS THE PART YOU WRITE. The skill in SKILL.md executes whatever checks
you define here. It ships empty on purpose: the judgment is your work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where. Name the source
     (repo-facts block, issue body, comment thread, or the locations in
     references/evidence-guide.md). "The repo" is not a source; "the last
     5 default-branch commit dates" is.
   - Pass condition: a condition someone else could apply and get your
     answer. Prefer thresholds with numbers ("a maintainer commented
     within 30 days") over adjectives ("maintainer is responsive").
   - Weight: `required` (a fail here rejects the issue) or `preferred`
     (never changes the verdict; a nice-to-have that helps rank the
     issues you accept).

2. A verdict rule below the table: how the check grades combine into
   accept or reject, including how `unclear` is treated. The verdict
   space is binary. If you write no rule for `unclear`, the skill treats
   it as fail.

Cover what actually kills first contributions. The lecture named four
families: the maintainer is alive, the repo is in use, the scope fits a
newcomer, and nobody else is already on it. A rubric that ignores a family
will fail eval issues designed around that family.
-->

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Maintainer activity | Repo-facts block for default-branch commit dates and the issue's comment thread | At least 1 commit was made to the default branch within the last 90 days, and a maintainer has responded to the issue within the last 90 days | required |
| Repository in use | Repo-facts block for recent default-branch activity | The default branch has at least 3 commits within the last 90 days | required |
| Newcomer scope | Issue body, issue labels, and the relevant locations described in `references/evidence-guide.md` | The issue describes a bounded change that can reasonably be implemented without requiring a major architectural redesign or changes across 3 or more unrelated areas of the repository | required |
| No existing contributor ownership | Issue body and full comment thread | No contributor has stated that they are actively working on the issue, and there is no open pull request linked to or clearly addressing the issue | required |

## Verdict rule

Accept the issue if every required check passes. Reject the issue if any required check fails. An unclear result on any required check counts as a fail. There are no preferred checks, so the verdict is determined entirely by the required checks.
