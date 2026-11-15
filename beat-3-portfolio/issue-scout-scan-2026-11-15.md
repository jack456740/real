# issue-scout scan output — 2026-11-15

## Funnel

The 3 strategy queries returned 225 hits (q1: 100, q2: 100, q3/OWASP-wstg: 25), which is 222 after removing duplicates.

- Dropping assigned issues left 167.
- Dropping issues not updated in the last 90 days left 159.
- The rest were sorted by the "good first issue" label first, then fewest comments, then most recently updated. The top 5 were graded.

All 5 came from **q1** (`good first issue` + Python). Each ranked high for the same reasons: it has the GFI label, 0 comments, and was updated today.

## Accepted (best fit first)

1. **[selimfirat/pysad#774](https://github.com/selimfirat/pysad/issues/774)**: "Test NonparametricDynamicThresholdPostprocessor with custom z_values"
   - **Why it fits:** it's a Python unit test with exact steps and an existing test file, which matches the fit profile closely.
   - **Difficulty:** straightforward. The issue names the file, the `z_values` inputs and the command (`pytest tests/transform/postprocessing`).
   - **AI policy:** AI use is allowed with conditions. Everything must be reviewed and approved by you, AI-written text must be marked, PRs stay drafts until reviewed, and `Co-Authored-By` tool trailers are not allowed.
2. **[DevelopersGlobal/ai-agent-skills#15](https://github.com/DevelopersGlobal/ai-agent-skills/issues/15)**: "Add context-loading guidance to each agent persona"
   - **Why it fits:** it's an AI/developer-tools repo (217 stars), but the work is markdown only, not code.
   - **Difficulty:** straightforward. It's three named agent files plus a clear acceptance checklist.
3. **[flisk-sh/codeql-lobster#8](https://github.com/flisk-sh/codeql-lobster/issues/8)**: release workflow fails with 422 `tag_name already exists`
   - **Why it fits:** it's a small security-tooling bug, but it's GitHub Actions CI, which leans toward the infrastructure the profile says to avoid.
   - **Difficulty:** ambitious. The issue's refactor step says to "share the same release step with the sibling codeql repos", which reaches beyond this repo. Check that with the maintainer early.
4. **[WingedGuardian/GENesis-AGI#4726](https://github.com/WingedGuardian/GENesis-AGI/issues/4726)**: flaky `test_watchdog` tw4 SIGTERM race
   - **Why it fits:** it's a Python bug fix in a test and the maintainer suggests a fix. But it involves systemd and a CI-load race, and the dev setup runs in an Incus container. That's heavy infrastructure.
   - **Difficulty:** ambitious. The cause is only a hypothesis so far: "read from the test, not yet measured".

## Rejected

- **[flisk-sh/codeql-goose#8](https://github.com/flisk-sh/codeql-goose/issues/8)**: failed **Unclaimed**. Open PR #9 ("ci: make release creation idempotent…", by HarshRajSinghania) is linked to the issue as its fix.

## Things the rubric passed that may need a look (candidates for scan-notes.md)

- **The ranking favours brand-new issues in small repos.** All 5 picks were opened today with 0 comments. codeql-lobster has 2 stars and is 3 weeks old, and the rubric has no check for how widely a repo is used.
- **Nobody responsible has backed the codeql-lobster issue.** It was opened by `odykyi`, who isn't the committer, and filed as a near-copy in a sibling repo. No maintainer has endorsed it. The rubric doesn't check this.
- **The GFI sort pushes out q3.** Sorting by label first means OWASP/wstg results never made the top 5, even though wstg is a named interest.
- **GENesis-AGI #4726 may get fixed by the maintainer.** The maintainer filed it while working on PR #4706, so they may fix it themselves. The rubric doesn't count that as a claim.

**Recommendation:** pysad#774 is the strongest fit. Before starting on any issue, post a short claim comment on it as soon as you commit, as `scope.md` requires.

## JSON grading results

```json
[
  {"item": "https://github.com/selimfirat/pysad/issues/774", "checks": [
    {"name": "Maintainer activity", "grade": "pass", "evidence": "Default-branch commit by selimfirat on 2026-11-15"},
    {"name": "Repository activity", "grade": "pass", "evidence": "All 5 latest commits dated 2026-11-14 to 2026-11-15"},
    {"name": "scope-feasible", "grade": "pass", "evidence": "Add one test in tests/transform/postprocessing/test_postprocessors.py with z_values=(1.0,) and (10.0,)"},
    {"name": "Unclaimed", "grade": "pass", "evidence": "No assignees, no linked PRs, no cross-references, 0 comments"},
    {"name": "Contribution policy", "grade": "pass", "evidence": "AGENTS.md: 'We support the use of AI tools' with conditions (review, mark AI content, draft PRs); not a ban"}
  ], "verdict": "accept"},
  {"item": "https://github.com/DevelopersGlobal/ai-agent-skills/issues/15", "checks": [
    {"name": "Maintainer activity", "grade": "pass", "evidence": "Default-branch merge by DhanushNehru on 2026-10-28"},
    {"name": "Repository activity", "grade": "pass", "evidence": "4 of last 5 commits between 2026-10-09 and 2026-10-28"},
    {"name": "scope-feasible", "grade": "pass", "evidence": "Add a Context section to the three agent files in agents/, with acceptance criteria"},
    {"name": "Unclaimed", "grade": "pass", "evidence": "No assignees, no linked or mentioning PRs, 0 comments"},
    {"name": "Contribution policy", "grade": "pass", "evidence": "CONTRIBUTING.md has no AI restriction; repo ships AGENTS.md/CLAUDE.md for agents"}
  ], "verdict": "accept"},
  {"item": "https://github.com/flisk-sh/codeql-lobster/issues/8", "checks": [
    {"name": "Maintainer activity", "grade": "pass", "evidence": "Default-branch commit by kburym on 2026-10-23"},
    {"name": "Repository activity", "grade": "pass", "evidence": "All 5 latest commits dated 2026-10-23"},
    {"name": "scope-feasible", "grade": "pass", "evidence": "Make the 'Create GitHub release' step idempotent when the tag's release already exists"},
    {"name": "Unclaimed", "grade": "pass", "evidence": "No assignees; all 7 repo PRs merged and none reference #8; 0 comments"},
    {"name": "Contribution policy", "grade": "pass", "evidence": "No CONTRIBUTING/AI policy files; silence passes"}
  ], "verdict": "accept"},
  {"item": "https://github.com/WingedGuardian/GENesis-AGI/issues/4726", "checks": [
    {"name": "Maintainer activity", "grade": "pass", "evidence": "Default-branch commit by WingedGuardian on 2026-11-15"},
    {"name": "Repository activity", "grade": "pass", "evidence": "All 5 latest commits dated 2026-11-15"},
    {"name": "scope-feasible", "grade": "pass", "evidence": "Fix one flaky test: add a readiness file after the trap and wait for it in case()"},
    {"name": "Unclaimed", "grade": "pass", "evidence": "No assignees; PR #4706 only mentions it as 'filed as #4726', not a fix; 0 comments"},
    {"name": "Contribution policy", "grade": "pass", "evidence": "CONTRIBUTING: PRs need a prior issue and maintainer review; no AI ban"}
  ], "verdict": "accept"},
  {"item": "https://github.com/flisk-sh/codeql-goose/issues/8", "checks": [
    {"name": "Maintainer activity", "grade": "pass", "evidence": "Default-branch commit by kburym on 2026-10-23"},
    {"name": "Repository activity", "grade": "pass", "evidence": "All 5 latest commits dated 2026-10-23"},
    {"name": "scope-feasible", "grade": "pass", "evidence": "Make the release 'Create release' step idempotent"},
    {"name": "Unclaimed", "grade": "fail", "evidence": "Open PR #9 'ci: make release creation idempotent when tag already exists' linked as closing PR"},
    {"name": "Contribution policy", "grade": "pass", "evidence": "No CONTRIBUTING/AI policy files; silence passes"}
  ], "verdict": "reject"}
]
```
