# Rubric: is this a good first issue?

<!--
This rubric defines the checks used to decide whether an issue is a good
first contribution. Each required check must pass for an issue to be
accepted.
-->

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Maintainer activity | Comment thread: dates and authors of maintainer comments or responses. Repo-facts block: date of the most recent default-branch commit. | Pass if a maintainer has commented on the issue within the last 90 days OR the repo-facts block shows a default-branch commit within the last 90 days. | required |
| Repository activity | Repo-facts block: dates of the last 5 commits on the default branch. | Pass if at least 2 of the last 5 default-branch commits were made within the last 90 days. | required |
| scope-feasible | Issue body: the work it asks for | The issue describes one identifiable piece of work someone could start: a behavior, a gap, or a task you can point at. It fails only when there is no single piece of work in it: a codebase-wide checklist, an "improve X everywhere", or a container issue tracking many sub-tasks. An open design edge, an "etc.", or several files involved never fails this check; that raises the difficulty note instead. | required |
| Unclaimed | Repo-facts block, issue body, and comment thread: assignees, linked pull requests, contributor statements that they have started or are currently working on the issue, maintainer statements reserving the issue for a contributor, and implementation-progress updates. | Pass if the issue has no assignee, there is no open linked pull request addressing it, no contributor states that they have started or are currently working on it, and no maintainer explicitly reserves it for another contributor. | required |
| Contribution policy | Repo-facts contribution-policy summary and any maintainer policy statements in the issue or comments. | Pass if there is no repository contribution policy or maintainer instruction that prevents or disallows the prospective contributor from working on or submitting the issue. If the contribution policy contains no relevant restriction, pass. | required |

## Difficulty note

With each accepted candidate, report a one-line difficulty note in the read-out summary:

- **straightforward**: The issue names where the change lives and the change is bounded.
- **moderate**: The location is yours to find, or several files are involved.
- **ambitious**: An open design edge or an unfamiliar subsystem; name the edge because claiming this issue means raising it with the maintainer early.

The difficulty note is information for the chooser, never a verdict input. It does not appear in the fenced JSON block, never changes accept or reject, and is skipped entirely in eval mode.

## Verdict rule

Accept an issue only if every required check passes. Reject the issue if
any required check fails. Treat unclear as fail when the available evidence
is insufficient to determine whether a required check passes. Preferred
checks, if added later, do not change the accept/reject verdict and are used
only to rank accepted issues.