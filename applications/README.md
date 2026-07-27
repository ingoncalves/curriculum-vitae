# Applications Dashboard

Last updated: 2026-07-27

## Active pipeline

| Status | Company | Role | Applied | Location | Comp expected | Next action |
|---|---|---|---|---|---|---|
| 🔵 Applied | EPFL | Full Stack (School of Engineering) | 2026-07-27 | Lausanne | ~120k CHF (CDI, public) | wait for response |
| 🟡 To apply | Sonar | Staff Full Stack (Java, React) | — | Geneva | ~250k CHF total | submit application |
| 🟡 To apply | Proton | Senior FE (Docs / Standard Notes) | — | Geneva or London | ~170k CHF total | submit application |
| ❌ Rejected | CERN | Full-Stack Engineer (IT-CA-IR-2026-66-LD) | 2026-04-22 | Geneva | ~9.2k CHF/mo (LD staff) | debrief done |

## Status legend

- 🟡 `to-apply` — identified, not yet applied
- 🔵 `applied` — submitted, waiting for first response
- 🟠 `screening` — pre-interview screening in progress
- 🟣 `interviewing` — interview rounds in progress
- 🟢 `offer` — received offer
- ✅ `accepted` — accepted offer
- ❌ `rejected` — rejected
- ⚪ `withdrew` — withdrew
- ⏸️ `on-hold` — paused

## Folder conventions

- Application folders: `YYYY-MM-<company>-<role-slug>` (chronologically sortable)
- Metadata and deliverables (JD snapshots, cover letters, form answers): English
- Personal notes and retrospectives: Portuguese
- Each folder starts from `_template/` and only fills the files it needs

## Shared resources

Cross-cutting reusable content lives in `_shared/`:

- `stories.md` — STAR stories for behavioral interviews
- `open-source.md` — canonical descriptions of each open-source contribution
- `standard-answers.md` — boilerplate answers to frequently-asked application questions
- `values.md` — personal thesis on what I look for in roles and companies
- `linkedin-improvements.md` — LinkedIn profile maintenance guide (originally used for the 2026-05 profile overhaul; kept as reference for future revisions)

## How to use with Claude

To start a new working session on a specific application, paste something like:

> "Vamos trabalhar na aplicação em `applications/YYYY-MM-<slug>/`. Lê o README, job-posting, application-form, e os arquivos relevantes de `_shared/`."

Claude reloads the context from those files. No need to re-explain career history from scratch.
