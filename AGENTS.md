# AGENTS.md

Onboarding brief for AI agents (and humans) who pick up work in this repo.
The goal is that any new session can continue where the last one left off
without re-explaining the project from scratch.

---

## 1. What this repo is

A personal career portfolio for **Guilherme Inácio Gonçalves, Ph.D.** It
holds the CV, cover letters, LinkedIn plan, and a per-application
workspace tracking every job he is applying to.

Guilherme is a Brazilian Senior Full-Stack Software Engineer with:

- PhD in Computational Modeling (UERJ, defended Feb 2026) on signal
  estimation for high-energy calorimeters under HL-LHC conditions
- CERN ATLAS Tile Calorimeter user since 2019; full ATLAS authorship in 2024
- Current role: Senior Full-Stack Engineer at Siteimprove (via Prime IT)
- Co-founder and sole engineer of Orkast (SaaS ERP/CRM for Portuguese SMEs)
- DELF B2 in French; lived in Geneva 2019 to 2020
- Family: wife + one-year-old daughter; aligned with returning to Geneva

The central career goal driving every application: **return to Geneva
(or Lausanne) to work as a scientific/full-stack software engineer**,
ideally at CERN, EPFL, Proton, or Sonar.

## 2. Repository layout

```
curriculum-vitae/
├── AGENTS.md                      <- this file
├── README.md                      <- high-level repo README
├── english/
│   ├── curriculum-en.tex          <- the CV source (altacv class)
│   ├── curriculum-en.pdf          <- latest compiled CV
│   └── profile.jpg                <- headshot used by CV and cover letters
├── portuguese/                    <- older PT CV, not maintained
├── applications/                  <- active job-application workspace
│   ├── README.md                  <- authoritative dashboard (status table)
│   ├── _shared/
│   │   ├── latex/
│   │   │   ├── identity.tex       <- shared visual identity for letters
│   │   │   └── cover-letter-template.tex
│   │   ├── stories.md             <- STAR interview stories
│   │   ├── open-source.md         <- canonical OSS descriptions
│   │   ├── standard-answers.md    <- common form answers
│   │   ├── values.md              <- personal thesis on roles he wants
│   │   └── linkedin-improvements.md
│   ├── _template/                 <- scaffold for new applications
│   ├── 2026-04-cern-cds/          <- archived, rejected
│   ├── 2026-07-cern-sy-bi-sw/     <- APPLIED 2026-08-24 (priority)
│   ├── 2026-07-epfl-fs-soe/       <- APPLIED 2026-07-27
│   ├── 2026-07-proton-sn/         <- to apply
│   └── 2026-07-sonar-staff-fs/    <- to apply
└── email-gil-cambio-primeit.md    <- unrelated personal admin draft
```

Each application folder usually contains: `README.md` (fit assessment,
notes in PT), `job-posting.md` (JD snapshot), `application-form.md`
(copy-paste answers to form fields), `cover-letter.tex` + `.pdf`.

**Authoritative status source: `applications/README.md`.** When status
in a folder's README disagrees with the dashboard, the dashboard wins.

## 3. Writing conventions (preserve these verbatim across sessions)

- **No em-dashes.** Guilherme dislikes the `--` double-dash (and the `—`
  Unicode em-dash). Use colons, commas, parentheses, or sentence breaks
  instead. This applies to every deliverable: cover letters, form
  answers, outreach messages, dashboards, READMEs.
- **Language split:** English for deliverables and metadata (CVs, cover
  letters, form answers, job-posting snapshots, dashboards). Portuguese
  for personal notes, retrospectives, strategy sections (any "Notas (PT)"
  block).
- **Tone:** concise, not overly polite, not artificial. Outreach messages
  especially must not sound like a cover letter. No "Prometo não abusar
  do teu tempo" filler.
- **Specific to Proton cover letter:** do NOT name "Claude Code"
  specifically. Use "AI-driven development" or "LLM-based tools"
  instead. (Other applications can name Claude Code directly.)
- **Do NOT refactor `english/curriculum-en.tex` to use the shared
  `identity.tex`** without explicit approval. The CV is intentionally
  independent of the cover-letter shared stack.

## 4. LaTeX conventions

### CV (`english/curriculum-en.tex`)
- Class: `altacv`
- Compile: `pdflatex curriculum-en.tex` twice
- Postnominal `, Ph.D.` sits on the name, not under Education

### Cover letters (`applications/<folder>/cover-letter.tex`)
- Class: `article`, 11pt, A4
- Load shared identity: `\input{../_shared/latex/identity}`
- Fonts: `lato` (via `\usepackage[default]{lato}`)
- URLs: always `\PassOptionsToPackage{hyphens}{url}` BEFORE `\usepackage{hyperref}`
  so long URLs break at hyphens. Wrap each URL in
  `\href{full-url}{\nolinkurl{visible-text}}`. `urlstyle{same}` is set
  globally in `identity.tex` and renders them in the body font.
- Header layout: a single `\noindent` + two minipages
  (`\dimexpr\linewidth-3cm\relax` wide on the left, `2.7cm` wide on the
  right). Left contains name, tagline, and contact bar stacked with
  `\\[0.8em]`. Right contains `\circularPhoto{2.5cm}{profile}`.
- The `\circularPhoto` macro uses TikZ `path picture` clipping with
  `[baseline=(currentphoto.north)]` to align tops across minipages.
- Build locally: `latexmk -pdf cover-letter.tex` or `pdflatex` twice.
- **Deliverable filename convention:**
  `Goncalves_Guilherme_CV.pdf` and
  `Goncalves_Guilherme_CoverLetter_<role-ref>.pdf`.

### Sandbox build note

The agent sandbox typically lacks `lato.sty`, `fontawesome5`, and
`academicons`. You can read/edit `.tex` files but CANNOT compile. Ask
the user to compile locally on their Mac (`latexmk -pdf <file>.tex`),
then they bring the PDF back.

## 5. Git workflow

- **Inline identity, no config changes.** Never modify `.git/config`
  or run `git config --global`. Commit with:
  ```
  git -c user.name="Guilherme Goncalves" \
      -c user.email="inacio.guilherme@gmail.com" \
      commit -m "..."
  ```
- **Create new commits, never amend** (unless the user asks). If a
  pre-commit hook fails, fix and make a new commit.
- **Commit attribution:** end messages with
  `Co-Authored-By: Claude Opus 4.7 <noreply@anthropic.com>`
  (follow whatever model line the active session reminder specifies).
- **The sandbox cannot push to GitHub** (no SSH credentials). Push is
  done by Guilherme locally. The agent commits and stops there.
- **Default branch:** `master`.
- **Granularity:** one application = one commit (unless the change
  spans multiple apps, in which case group by concern: shared infra,
  per-app content, dashboard update).

## 6. Active pipeline snapshot (as of 2026-11-13)

| Status | Role | Notes |
|---|---|---|
| Applied | CERN SY-BI-SW-2026-175-LD | submitted 2026-08-24. Dream fit. Consider nudging Bernardo Peralva as referee. |
| Applied | EPFL Full Stack (School of Engineering) | submitted 2026-07-27 |
| To apply | Sonar Staff Full Stack (Geneva) | ~250k CHF total comp target; stretch on "Staff" seniority |
| To apply | Proton Senior FE (Standard Notes) | lead with O2 Filmes Teksto editor + FedRAMP/crypto angle |
| Rejected | CERN IT-CA-IR-2026-66-LD (CDS) | April 2026; lost at pre-selection on Flask/SQLAlchemy/OpenShift gap |

Confirm the live state via `applications/README.md` on each session start.

## 7. Character-limit crib sheet

Learned from empirical form truncation during submissions:

- **CERN SmartRecruiters "motivation" field:** 1440 chars (hard limit,
  confirmed on both CERN applications).
- **Proton (Greenhouse) Q1:** ~250 chars (truncated a longer answer at
  "pagin").
- **Proton Q2:** no observed limit, but keep it substantive, not sprawling.
- **EPFL (SuccessFactors):** large text areas, no tight limit observed.

## 8. How to start a new session cleanly

Paste something like:

> "Vamos trabalhar na aplicação em `applications/<YYYY-MM-slug>/`. Lê o
> README, job-posting, application-form, e os arquivos relevantes de
> `_shared/`. Também lê o AGENTS.md na raiz."

Then the agent should:

1. `Read` the folder's `README.md`, `job-posting.md`, and `application-form.md`.
2. `Read` any `_shared/` file the task touches (stories, open-source,
   standard-answers, values).
3. `Read` `applications/README.md` for current status.
4. Follow the conventions above (no em-dashes, EN deliverables, PT notes,
   inline git identity, no CV shared-identity refactor).

## 9. Known quirks to remember

- Guilherme's CERN email `ginaciog@cern.ch` matters for Proton (CERN-
  founded) and any CERN application, but use `inacio.guilherme@gmail.com`
  as the public/identity email elsewhere.
- Brazil is a CERN Associate Member State (since 2024), which affects
  eligibility answers.
- Notice period at current role: 1 month.
- Earliest start on a new role: 2 to 3 months (permit + relocation).
- Relevant professional experience is counted from Master's graduation
  (April 2020) for CERN forms.
- Referees already in CV include Bernardo Peralva (CERN) and PhD
  advisor at UERJ; mention them when a referee section needs a name.

---

Last reviewed: 2026-11-13.
