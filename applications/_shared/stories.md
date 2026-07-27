# STAR Stories for Behavioral Interviews

Reusable behavioral answers, each in STAR format (Situation, Task, Action, Result). Target 60–90 seconds spoken per story. Adapt phrasing per interviewer, but keep the core facts consistent.

---

## 1. Working with a non-technical stakeholder

**Situation**: At Orkast, our CEO Joao and CFO Felipe came to me with the requirements for v1.1.0. Joao wanted a "CEO Dashboard" with cross-domain KPIs and alerts. Felipe wanted fiscal-document attachments, bank reconciliation via CSV upload, and dashboard reports with charts.

**Task**: Translate five stakeholder-language requirements from two different non-technical stakeholders into a coherent three-phase implementation plan that fit our team velocity (one sole engineer, me) and our existing architecture.

**Action**: I ran short scoping sessions with each of them separately to understand not just what they wanted but *why*, and how they would use the features. I then wrote a technical plan that broke the work into three phases: (1) foundational infrastructure (attachment system on S3, ACL expansion), (2) core features (bank reconciliation with CSV parsing, financial reports with recharts), (3) executive layer (CEO Dashboard on top of the other work). I captured the plan as a written document that served as the working spec across the release.

**Result**: The release shipped in the planned phases, all five stakeholder requirements met. Felipe now uses bank reconciliation weekly, and Joao uses the CEO Dashboard as a first-thing-in-the-morning check.

---

## 2. Shipping under constraint / deadline

**Situation**: (User to fill from Siteimprove or Orkast recent release)

**Task**: (What needed to be done, under what pressure)

**Action**: (What I did)

**Result**: (Outcome, ideally quantified)

*Note: Guilherme, please fill this one with a concrete recent example. Good candidates: any Siteimprove sprint release that had a hard deadline, an Orkast release that had customer pressure, or a CERN deadline like data-taking preparation.*

---

## 3. Open-source contribution scrutinized by maintainers

**Situation**: I contributed changes to Athena (CERN ATLAS offline software) as part of my energy reconstruction algorithm work. Athena has stringent code review and CI standards because errors propagate to thousands of physicists' downstream analyses.

**Task**: Get a substantive change (new algorithm implementation) merged into the main branch through the CERN GitLab review process.

**Action**: I prepared the MR with unit tests, benchmarks against the existing baseline algorithm, and a design document explaining the mathematical basis. I iterated through multiple rounds of maintainer feedback, addressing edge cases in signal pile-up conditions and refactoring for consistency with the surrounding codebase.

**Result**: The change was merged after several rounds of review. This taught me to write PRs with the reviewer's job in mind — small commits, clear commit messages, tests included, and design context up front.

---

## 4. Resolving an ambiguous technical decision

**Situation**: When designing the Orkast backend from scratch, I had to choose an ORM. The tradeoffs were between Prisma (modern, type-safe, less mature), TypeORM (mature but less ergonomic), Sequelize (very mature but weaker TypeScript story), and raw SQL with query builders.

**Task**: Pick an ORM that would carry a multi-tenant SaaS from MVP to at least the next 2-3 years of feature development.

**Action**: I did a two-day spike: prototyped the same three-model schema (Company, User, Deal) with Prisma 7 and TypeORM 0.3, ran a set of realistic queries against each, and compared the migration workflow. I also considered team-of-one context: as sole engineer, the developer experience matters disproportionately more than in a team where you can specialize. Prisma's type-safety and migration flow won on those criteria.

**Result**: Picked Prisma 7 with the driver adapter approach against PostgreSQL. Zero regrets so far; the schema has grown from 8 models to 20+ with clean migration history. The choice would have been worth revisiting if we had scaling issues past a few hundred tenants, but we are still well within Prisma's comfortable operating range.

---

## 5. Production incident you helped resolve or prevent

**Situation**: (User to fill — Siteimprove has had incidents that could serve; also security/compliance-related work under FedRAMP.)

**Task**: 

**Action**: 

**Result**: 

*Note: Guilherme, please fill this. A great candidate is your recent work triaging Aikido security findings in the FedRAMP effort — that's incident prevention at scale.*

---

## 6. Disagreeing with a colleague or leader

**Situation**: (User to fill — could be from the O2 Filmes tech lead era, or any Siteimprove peer disagreement worth recounting.)

**Task**: 

**Action**: 

**Result**: 

*Note: Guilherme, please fill with a concrete example. Interviewers value stories where you disagreed, stated your position clearly, and either won the argument on merit or accepted the team decision gracefully. Avoid stories that end with "I was right and they were wrong."*

---

## 7. Learning a new technology fast

**Situation**: When Orkast started integrating AI features, I decided to use Claude Code as a primary development tool. I had never used an AI coding agent as a first-class part of my workflow before.

**Task**: Integrate Claude Code into my daily engineering workflow at Orkast without slowing down feature delivery.

**Action**: I spent the first week using it deliberately on lower-risk tasks (test writing, refactoring, documentation) to learn its strengths and failure modes. I built up a personal library of prompt patterns that worked. I set up guardrails: never let it commit without review, always run tests before accepting a change, keep the human-in-the-loop on architecture decisions.

**Result**: My throughput on well-scoped tasks meaningfully improved (I estimate 30–50% on scoped feature work, less on ambiguous or research-heavy tasks where the human loop dominates). The workflow is now part of how I work daily at Orkast, and I bring the same discipline to non-Orkast work.

*Alternative version for Kubernetes/EKS: Guilherme, if the interviewer probes for Kubernetes, tell the story of picking up EKS + FedRAMP port-forwarding workflows at Siteimprove.*

---

## Guidance for use in interview

- **Never memorize word-for-word**. Know the facts and the arc; let the words come naturally.
- **Match the story to the question**. "Tell me about a time you led something" → use #1 or #4. "Tell me about a difficult decision" → use #4 or #6. "Tell me about a challenge you overcame" → use #2, #3, or #7.
- **Time your delivery**. If a story runs past 90 seconds, cut Situation or Task, never Action or Result.
- **Quantify Result whenever possible**. Percentages, counts, dollar amounts, durations. Numbers stick.
