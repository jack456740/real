# Toolkit Portfolio

**Student:** Alvin Rogers

## Featured Tools

I selected Issue Scout, Reproduction Checker, Plan Checker, and PR Precheck because they show the progression from finding a contribution to checking the evidence, evaluating a proposed implementation, and deciding whether a pull request is ready to submit. The first tool has a completed live scan, while the other three turn lessons from earlier evaluations into repeatable review procedures. Together, they show both working artifacts and the judgment rules I added when the tools' first versions were not specific enough.

### Issue Scout

**What it is, and the judgment hole I wrote:** Issue Scout searches GitHub for possible first-contribution issues, ranks candidates against a fit profile, and grades the strongest candidates. My judgment is encoded in the search strategy, fit profile, and rubric. The rubric checks maintainer activity, repository activity, scope-feasible work, whether the issue is unclaimed, and contribution policy. The scope-feasible check is deliberately about whether one identifiable piece of work exists; multiple files or an open design question raise the difficulty rather than automatically disqualifying an issue.

**How it evolved, dated:** On 2026-11-15, I changed the scope check from “Manageable scope” to “scope-feasible.” The earlier wording could reject real issues merely because they involved several files or an unresolved design edge. The revised rule rejects only work without one identifiable task and records difficulty separately. I also added a difficulty note for accepted candidates and kept it outside the accept/reject verdict. The first live scan exposed a second weakness: ranking by good-first-issue label, comment count, and recency pushed very new repositories to the top and kept the OWASP/WSTG search results out of the top five. I recorded those findings as possible future rubric and ranking changes.

**Evidence:**

The 2026-11-15 scan searched 225 issues (222 after deduplication), reduced the pool to 159 after the assigned-issue and 90-day filters, and graded the top five. Four passed and one failed.

```text
The 3 strategy queries returned 225 hits
(222 after removing duplicates).

Accepted:
- selimfirat/pysad#774
- DevelopersGlobal/ai-agent-skills#15
- flisk-sh/codeql-lobster#8
- WingedGuardian/GENesis-AGI#4726

Rejected:
- flisk-sh/codeql-goose#8 — failed Unclaimed because
  open PR #9 was linked as its fix.
```

The scan also recorded that all five top candidates came from the Python/good-first-issue query, even though the third query searched OWASP/WSTG. The scan artifact was committed in `20c3b89` on 2026-11-15. The Issue Scout rubric and fit profile were included in commit `f938c4c` on 2026-11-15.

### Reproduction Checker

**What it is, and the judgment hole I wrote:** Reproduction Checker evaluates whether a reproduction report supports the issue it claims to reproduce. My judgment is the five-part rubric: environment recorded, steps reproducible, target behavior evidenced, outcome honest, and repository conventions. This prevents a report from passing just because it contains a traceback or a plausible explanation. The evidence must show the target behavior, or show the attempted trigger and different observed behavior when reproduction did not succeed.

**How it evolved, dated:** On 2026-11-15, I refined the repository-conventions rule so it follows the repository's actual issue-comment policy. If the repository explicitly says AI disclosure is not required in issue comments, the checker must not invent that requirement. The claim comment must still name the specific investigation and must not promise a guaranteed fix or completion date. I also moved the voice guide to the shared `~/.claude/voice-guard/voice-guide.md` location and updated the tool's local guide to point to it. These changes address the friction of a checker applying generic disclosure expectations instead of the repository's explicit rules.

**Evidence:**

The rubric's required checks include:

```text
Environment recorded
Steps reproducible
Target behavior evidenced
Outcome honest
Repository conventions
```

The repository-conventions pass condition explicitly distinguishes a required disclosure from a repository that says disclosure is not required for issue comments. The tool files were committed with the review-tool collection in `c07ad7d` on 2026-11-15.

### Plan Checker

**What it is, and the judgment hole I wrote:** Plan Checker evaluates whether a proposed implementation plan is ready to build from. My judgment is the rubric and the student-authored `procedure.md`. The rubric checks evidence-grounded diagnosis, bounded change, executable implementation, observable verification, honest uncertainty, and thread and repository conventions. The procedure specifies the order in which the issue, reproduction, repository facts, plan, and draft comment must be read.

**How it evolved, dated:** The procedure file was present by 2026-11-09. Its design responds to a specific failure: an executor could understand what a rubric wanted judged but still stall because the rubric did not explain how to locate and compare the evidence. I therefore wrote concrete read-order, evidence-gathering, check-execution, and verdict-assembly steps. On 2026-11-15, the tool was included in the committed review-tool collection. The procedure also tells the evaluator to record missing evidence rather than invent repository policies, maintainer decisions, test results, or implementation details.

**Evidence:**

The procedure states:

```text
Read the reproduction evidence next. Record the observed failure
and exact triggering conditions so the diagnosis can be judged
against facts rather than assumptions.
```

It then requires each check to be graded `pass`, `fail`, or `unclear`, with a specific supporting or conflicting piece of evidence in the rationale. The procedure and rubric are included in the tool collection committed as `c07ad7d` on 2026-11-15.

### PR Precheck

**What it is, and the judgment hole I wrote:** PR Precheck answers one bounded question about a pull-request package: whether it is ready to submit. Its judgment is expressed through a contract, rubric, evidence guide, scope rules, voice guide, and procedure. This separates a readiness review from a prediction that maintainers will approve or merge the pull request.

**How it evolved, dated:** The PR Precheck files were present by 2026-10-19, including its contract, procedure, rubric, and scope. On 2026-11-15, the tool was included in the committed review-tool collection. Its structure makes the evaluator read the required files before grading, refuse to grade when the rubric or procedure has no substantive student-authored content, and use the defined checks rather than inventing new ones. This addresses the risk of an evaluator improvising a standard that the contributor did not write.

**Evidence:**

The skill's stated interface is:

```text
Answer exactly one question about one PR package:
is it ready to submit?
```

Its instructions also say not to invent checks or change the rubric during a run. The tool collection was committed in `c07ad7d` on 2026-11-15.

## Inventory

- **Issue Select:** Grades one candidate issue against a written first-contribution rubric. Its public-repository scope was updated so it could evaluate issues beyond the original Path Review repository.
- **Ship Gate:** A planned submission-readiness check in the toolkit; its results have not yet been verified in the contribution record.
- **PR Monitor:** A tool intended to monitor pull-request activity and follow-up; its results have not yet been verified in the contribution record.
- **Git and GitHub CLI:** Used to inspect repository history, stage and commit portfolio evidence, authenticate to GitHub, and push the portfolio repository.
- **pytest and GitHub Actions:** Used in the PySAD contribution workflow to run and report regression-test and automated-check results.

## The Arc

**Beat 1**

Date: 2026-10-19

Friction: A pull-request readiness review needed a fixed contract and repeatable criteria; otherwise the evaluator could change the standard from one run to another.

Change: I created the PR Precheck contract, rubric, procedure, scope, and voice-guide files.

Result: The tool had a defined one-question interface and a documented evaluation sequence. The files were later included in the review-tool commit `c07ad7d` on 2026-11-15.

**Beat 2**

Date: 2026-11-09

Friction: The Plan Checker rubric described what to judge, but an executor could still stall because it did not say exactly how to find and order the evidence.

Change: I wrote `procedure.md` with a read order, evidence-gathering steps, six check-execution steps, and verdict-assembly rules.

Result: The procedure gave another evaluator a repeatable way to move from issue context and reproduction evidence to a plan verdict without silently filling gaps.

**Beat 3**

Date: 2026-11-15

Friction: The first Issue Scout scan showed that a good-first-issue-first ranking could over-favour brand-new repositories, while the OWASP/WSTG query did not reach the top five. It also surfaced a candidate that looked unclaimed even though related maintainer work might cover it.

Change: I recorded the scan's ranking weaknesses and hidden-work concern. I also revised the scope check to `scope-feasible`, separating the existence of one identifiable task from difficulty caused by multiple files or open design questions.

Result: The live scan processed 225 hits, deduplicated them to 222, and graded five candidates: four passed and one failed because an open linked pull request already addressed it. The scan was committed as `20c3b89` on 2026-11-15.

**Beat 4**

Date: 2026-11-15

Friction: A reproduction checker could incorrectly demand AI disclosure even when a repository explicitly says disclosure is not required for issue comments. Generic communication rules could also produce vague claims or promises of a fix.

Change: I refined the repository-conventions check to follow the repository's actual policy and required claim comments to name the specific investigation without guaranteeing a fix or completion date.

Result: The reproduction rubric now distinguishes an actual repository requirement from an invented one and evaluates communication against the repository's conventions. The review-tool collection was committed as `c07ad7d` on 2026-11-15.

## Limitations and What's Next

The toolkit makes evaluations more consistent, but it does not make the evidence complete or guarantee that a contribution will be accepted. Issue Scout can rank a newly created repository highly because it currently gives strong priority to the good-first-issue label, low comment count, and recent updates. A maintainer may also be working on an issue without an assignee, linked pull request, or public claim comment. The first scan demonstrated both risks: codeql-lobster had only two stars and no maintainer endorsement in the captured evidence, while GENesis-AGI#4726 may have been covered by the maintainer's related work on PR #4706.

The review tools also depend on the quality of the supplied package. Reproduction Checker cannot establish a target behavior if the report lacks the relevant environment, steps, or output. Plan Checker cannot verify a proposed test merely because the plan says the test will be run. PR Precheck can assess the submitted evidence and repository requirements, but it cannot predict maintainer approval or replace an actual review. Ship Gate and PR Monitor have not yet had verified results recorded here.

My next step is to improve Issue Scout's ranking and unclaimed-work investigation. I will test a ranking that gives the named OWASP/WSTG interest a fair chance to reach the graded shortlist, and investigate maintainer endorsement and related in-progress pull requests before treating an issue as a strong candidate. I will then run the revised scout on another public-repository batch and compare its shortlist with the November 15 scan.

**Tool limits.**

issue-scout: It can miss hidden maintainer work and over-rank very new repositories; its current label-first sorting can also crowd out a named search interest such as OWASP/WSTG.

repro-check: It cannot prove a reproduction from a report that lacks the environment, rerunnable steps, or artifacts showing the target behavior.

plan-check: It can judge only the plan and evidence supplied; it cannot confirm that an implementation or test works before those changes are actually run.

pr-precheck: It can identify readiness gaps in the package, but it cannot guarantee maintainer approval, merge, or release.
