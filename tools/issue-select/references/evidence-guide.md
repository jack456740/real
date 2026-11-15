# Evidence guide: where first-issue signals live on GitHub

Every rubric check needs an evidence source. This guide maps the five criterion families to concrete places you can look: on github.com when you are sizing up a live issue by hand, and in the snapshot bundle when you are in eval mode. It closes with the repository-level contribution policy. If a signal is not listed here, name your own source in the rubric; just make it somewhere a grader can actually look.

## Family 1: is the maintainer alive?

A repository with code but no active maintainers may leave your pull request unreviewed.

| Signal | On github.com | In the eval bundle |
|---|---|---|
| Recent default-branch commits | The repository front page shows the newest commit and its date. Click the commit count next to it to see recent history. | "Last 5 default-branch commits" under Repo facts |
| Who is committing | The commit list shows each commit's author. A bot commit alone does not establish maintainer activity. | Commit author names in the same list |
| Issue response latency | Open recently updated issues and examine how long the first reply from an Owner, Member, or Collaborator took. | "Maintainer first-response sample" under Repo facts |
| Maintainer activity in this thread | Check the badges beside commenters' names for Owner, Member, or Collaborator. | The Comments section, including each comment's author_association |

## Family 2: is the repository in use?

Contributing to abandoned software may teach the workflow but produce a pull request nobody maintains.

| Signal | On github.com | In the eval bundle |
|---|---|---|
| Release recency | Check the Releases box on the repository front page. | "Latest release" under Repo facts |
| Last push | Check the newest commit date. The Branches page also shows when other branches last moved. | "Last push to any branch" under Repo facts |
| Archived flag | An archived repository displays an archive banner and is read-only. | "Archived:" on the repo line |
| Adoption scale | Check the star count and, for libraries, the "Used by" counter. | Stars on the repo line |

## Family 3: does the scope fit a newcomer?

This family primarily lives in the issue text and discussion.

Read the issue body and thread and ask:

- Is this one identifiable piece of work? Scope fails only when the issue is explicitly an umbrella or tracking issue, a codebase-wide checklist, or a request to improve something everywhere without identifying one piece of work.
- An unresolved design question, multiple files, or an "etc." does not automatically fail scope. Record these as difficulty considerations instead.
- A short issue is not necessarily unscoped. A terse body, acceptance-criteria checklist, or bug report without reproduction steps can still describe a bounded contribution.
- Pure usage questions ("How do I get this to work?") are support requests rather than contribution tasks.
- Age and history can reveal difficulty. An issue open for years with several abandoned attempts may require additional investigation.

Grade the identifiable work being requested, not merely the polish of the issue description.

## Family 4: is anyone already working on it?

A "good first issue" label indicates that a maintainer considers the issue suitable for newcomers. It does not establish that the issue is available.

| Signal | On github.com | In the eval bundle |
|---|---|---|
| Assignee | Check the Assignees box in the issue sidebar. | "This issue: assignees:" under Repo facts |
| Linked pull requests | Check the Development box in the issue sidebar. Look for open PRs addressing the issue. | "Linked PRs:" with the state of each PR, plus PRs mentioned in Comments |
| Claim comments | Read the thread for statements such as "I'll take this," "Can I work on this?" or "I'm working on this." | The Comments section |
| Maintainer reservations | Check whether a maintainer explicitly reserves the issue for another contributor. | Maintainer statements in the Comments section |
| Implementation progress | Look for updates showing that someone has already started investigating or implementing the change. | The Comments section |

When the issue sidebar and discussion disagree, examine the discussion rather than assuming that the sidebar tells the complete story.

## Family 5: are you allowed to contribute using your workflow?

An issue can pass the other four families but still be unsuitable if repository rules prohibit the contribution workflow.

In this course, the contribution workflow is AI-assisted, so check the repository's policies before proceeding.

| Signal | On github.com | In the eval bundle |
|---|---|---|
| Contribution policy | Check CONTRIBUTING.md in the repository root or .github directory and any contributor documents it references. | The "contribution policy" line under Repo facts |
| Dedicated AI policy files | Look for files such as AI_POLICY.md or AI_USAGE_POLICY.md. Also inspect AGENTS.md for instructions to AI coding agents. | Quoted or summarized policy information on the contribution-policy line |
| Templates | Check pull request and issue templates for required AI-use disclosure. | Relevant template requirements included in the policy summary |
| Maintainer instructions | Read maintainer statements about contribution eligibility and permitted workflows. | Maintainer policy statements in the Comments section, when captured |

### How to grade contribution policy

- An outright ban on AI-generated contributions is a fail for an AI-assisted contribution.
- Conditions are not bans. Disclosure, personal understanding, testing, and human review are requirements to follow, not automatic reasons to reject an issue.
- Silence passes. If the repository states no relevant restriction, do not invent one.
- If a policy requires disclosure, follow the exact disclosure requirements before submitting work.

## Reading the repo-facts block honestly

The repository facts are captured on a specific date.

Every recency threshold in the rubric, such as "within the last 90 days," must be measured against the capture date rather than the current date in eval mode.

In live mode, measure recency against the current date.

If the necessary evidence is missing or ambiguous, record the result as unclear. Follow the rubric's verdict rule: an unclear required check counts as a failure.
