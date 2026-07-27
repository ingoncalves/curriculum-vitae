# CERN IT-CA-IR-2026-66-LD | Interview Prep Plan

> Full Stack Software Engineer, CERN Document Server (CDS) / InvenioRDM.
> Application submitted **2026-04-22**. Expected interview window: mid-May to mid-June 2026.
> Budget: **1-3 hours/week** (target 2h). Total: ~12 hours across 6 weeks.

---

## How to use this document

- Each week has a **2h core block** plus an optional **+1h stretch**. If the week is tight, cover the core block only.
- Check off items as you finish them (`[x]`).
- Weeks 1-4 are independent study. Weeks 5-6 are mock interviews with Claude (paste the week marker into chat: `/mock-week-5` or `/mock-week-6`).
- If you get shortlisted earlier than week 6, jump directly to the mock weeks and use earlier weeks as reference material on-demand.
- If you want to go deeper on any topic, look for the `Deep-dive:` pointers inside each week.

---

## Weekly schedule at a glance

| Week | Theme                                   | Core h | Stretch h | Mock |
|------|------------------------------------------|--------|-----------|------|
| 1    | Flask + Jinja2 foundations              | 2      | +1        | no   |
| 2    | SQLAlchemy + relational modeling        | 2      | +1        | no   |
| 3    | ElasticSearch / OpenSearch basics       | 2      | +1        | no   |
| 4    | InvenioRDM + CDS + Open Science context | 2      | +1        | no   |
| 5    | Kubernetes / OpenShift + Mock Tech 1    | 2      | +1        | tech |
| 6    | Mock Tech 2 + Mock Behavioral + review  | 2      | +1        | both |

---

## Week 1 | Flask + Jinja2 foundations

**Why this first:** The posting explicitly asks "documented experience with web frameworks like Flask or Django." You have no production Flask, so the goal is to bridge that gap enough to discuss Flask fluently in an interview and understand InvenioRDM's request-handling conventions.

**Core (2h)**
- [ ] Read Flask quickstart end-to-end: <https://flask.palletsprojects.com/en/stable/quickstart/>. Cover routing, request/response, session, flashing, blueprints (15 min).
- [ ] Build a tiny toy Flask app locally: one blueprint, one form, one route returning JSON, one route returning a Jinja2 template (45 min). Suggested scope: a minimal "document" CRUD, no DB yet, use an in-memory dict.
- [ ] Read Jinja2 template designer docs, sections "Synopsis", "Variables", "Control Structures", "Template Inheritance": <https://jinja.palletsprojects.com/en/stable/templates/> (20 min).
- [ ] Skim Flask's application factory pattern and blueprints organization: <https://flask.palletsprojects.com/en/stable/patterns/appfactories/> and <https://flask.palletsprojects.com/en/stable/blueprints/> (20 min). This is how InvenioRDM is organized.

**Stretch (+1h)**
- [ ] Read Flask documentation on "Handling Application Errors" and "Testing Flask Applications". Understand how error handlers and `pytest` are typically wired.
- [ ] Compare-and-contrast note: write 3-5 bullet points on "how Flask blueprints relate to what I do in NestJS modules." Keep this note, you will likely use it in the interview.

**Self-check questions**
- What does `app.config.from_object()` do, and why is it often called on an application factory?
- How does `url_for()` differ from writing URLs by hand, and why is that difference important for maintenance?
- What is a Jinja2 template block, and how does `extends` + `block` enable layout reuse?

**Deep-dive pointer:** If you want to understand how a large Flask app is laid out, clone `inveniosoftware/invenio-app-rdm` and browse the blueprints registered in `invenio_app_rdm/config.py`. You do not need to understand every line; just see how the pieces fit.

---

## Week 2 | SQLAlchemy + relational modeling

**Why:** The posting asks for "Proven experience with relational databases, particularly PostgreSQL, and ORM frameworks (e.g. SQLAlchemy)." You know PostgreSQL (Aurora at Orkast) and Prisma conceptually. SQLAlchemy is a different mental model (Core vs ORM, session lifecycle, explicit commits). The goal: be able to read InvenioRDM models and write a simple SQLAlchemy query on the whiteboard.

**Core (2h)**
- [ ] Read SQLAlchemy 2.x unified tutorial, sections "Establishing Connectivity", "Working with Transactions", "Working with Data", "Working with ORM Related Objects": <https://docs.sqlalchemy.org/en/20/tutorial/index.html> (60 min). Skim if slow.
- [ ] Add a SQLAlchemy model to your Week 1 toy app. Use `Flask-SQLAlchemy`, define a `Document` model (id, title, body, created_at), wire it to SQLite, and add routes to create/list/view documents (45 min).
- [ ] Read the section on migrations with Alembic: <https://alembic.sqlalchemy.org/en/latest/tutorial.html> (15 min). You do not need to set it up; just understand the concept. InvenioRDM uses Alembic.

**Stretch (+1h)**
- [ ] Read SQLAlchemy docs on "Relationship Loading Techniques": <https://docs.sqlalchemy.org/en/20/orm/loading_relationships.html>. Understand `joinedload` vs `selectinload` vs `subqueryload`. N+1 questions are classic interview fare.
- [ ] Compare-and-contrast note: "SQLAlchemy Session vs Prisma Client". Focus on explicit commit, unit-of-work pattern, identity map. Keep this note.

**Self-check questions**
- What is the difference between SQLAlchemy Core and the ORM? When do you pick each?
- What is the identity map in SQLAlchemy, and why does it matter?
- How does SQLAlchemy handle lazy loading by default, and how can that cause N+1 problems?
- What does `relationship()` do, and what is `backref` / `back_populates`?

**Deep-dive pointer:** If you want to see real SQLAlchemy models in Invenio, browse `invenio_records/models.py` and `invenio_records_resources/records/models.py` on GitHub.

---

## Week 3 | ElasticSearch / OpenSearch basics

**Why:** "Hands-on experience with ElasticSearch/OpenSearch" is listed as a hard requirement. You have none on the CV. Goal: understand indexes, mappings, analyzers, and the Query DSL well enough to describe how InvenioRDM uses OpenSearch for record search.

**Core (2h)**
- [ ] Read the OpenSearch "Getting Started" and "Clients" overview: <https://opensearch.org/docs/latest/getting-started/>. Focus on core concepts (40 min).
- [ ] Read OpenSearch "Mappings and field types" overview: <https://opensearch.org/docs/latest/field-types/>. Focus on text vs keyword, date, nested, object (20 min).
- [ ] Read OpenSearch "Query DSL" essentials: <https://opensearch.org/docs/latest/query-dsl/>. Cover match, term, bool, filter, aggregations (40 min).
- [ ] Optional if you want hands-on: run OpenSearch locally via Docker, index 10 fake "document" records, and run a simple search + a bool query + a term aggregation (20 min).

**Stretch (+1h)**
- [ ] Read about analyzers and tokenizers. Understand what happens between "put a document in" and "get a ranked match back". Particularly: standard analyzer, keyword field, multi-field mappings.
- [ ] Read `invenio-search` README on GitHub to see how Invenio wraps the client.

**Self-check questions**
- What is the difference between a `text` and a `keyword` field? When do you need a `multi-field`?
- What does a `bool` query with `must`, `should`, `filter`, `must_not` mean, and when would you use `filter` instead of `must`?
- How does Elasticsearch score results by default, and when would you disable scoring?
- What is an analyzer, and what is the difference between a tokenizer and a token filter?

**Deep-dive pointer:** Read the blog post "Understanding analysis in Elasticsearch" (any reputable source). Bonus: read about reindexing in production, this comes up in interviews on evolving search schemas.

---

## Week 4 | InvenioRDM + CDS + Open Science context

**Why:** This is where you win or lose the domain-fit question. You want to sound like you have already started caring about this work, not just responding to a posting. Goal: be able to discuss CDS's mission, the InvenioRDM architecture at a block-diagram level, and the Open Science vocabulary (DOIs, FAIR, metadata schemas) without needing notes.

**Core (2h)**
- [ ] Read InvenioRDM docs homepage and "User Guide" overview: <https://inveniordm.docs.cern.ch/> (30 min). Focus on what a "record", "draft", "community", "vocabulary" is.
- [ ] Read InvenioRDM "Architecture" page(s): <https://inveniordm.docs.cern.ch/reference/architecture/>. Understand modules, services, resources, the request/response flow (30 min).
- [ ] Read about CDS's transition to InvenioRDM. Search for recent blog posts on <https://inveniosoftware.org/blog/> and CERN IT news. Find and skim 1-2 posts (20 min).
- [ ] Read Wikipedia on FAIR data principles: <https://en.wikipedia.org/wiki/FAIR_data>. Also a short primer on Dublin Core and DataCite metadata: they define the fields a repository records typically expose (20 min).
- [ ] Read a primer on DOIs and persistent identifiers: <https://www.doi.org/the-identifier/what-is-a-doi/> (10 min).
- [ ] Write a 1-page note to yourself: "If I were in my first week at CDS, what are the 5 things I would do in the codebase to understand it?" (10 min). This is a question they might literally ask.

**Stretch (+1h)**
- [ ] Clone `inveniosoftware/invenio-app-rdm` and browse: `invenio_app_rdm/records_ui/`, `invenio_app_rdm/communities_ui/`, and the `requirements-*.txt` files. Get a feel for the codebase layout and dependencies.
- [ ] Read the "Contributing" guide on InvenioRDM docs. Know how the community accepts PRs.
- [ ] Glance at the InvenioRDM roadmap or release notes. Being able to reference a recent change is a powerful interview signal.

**Self-check questions**
- Why is the move from legacy CDS to InvenioRDM valuable? (hint: community platform, open source, shared maintenance, modern stack)
- What is a "vocabulary" in Invenio, and why is it useful for controlled metadata?
- What is a "community" in InvenioRDM, and how does it relate to records?
- What does "FAIR" stand for, and how does a repository like CDS support each letter?
- What problems does a DOI solve that a plain URL does not?

---

## Week 5 | Kubernetes + OpenShift + Mock Technical 1

**Why:** The posting asks for OpenShift specifically. You have EKS exposure at Siteimprove but you admitted to the hiring team that you have not operated OpenShift directly. Closing this gap a bit + starting mock interviews.

**Core (2h)**
- [ ] **(45 min)** Read Kubernetes basics + concepts:
  - Pods, Deployments, ReplicaSets, Services, Ingress, ConfigMaps, Secrets
  - Namespaces, Labels, Selectors
  - `kubectl` everyday commands: `get`, `describe`, `logs`, `exec`, `port-forward`, `apply`, `rollout`
  - Reference: <https://kubernetes.io/docs/concepts/overview/>
- [ ] **(30 min)** Read the OpenShift-specific differences: Routes (instead of Ingress), ImageStreams, BuildConfigs, DeploymentConfigs (older), the `oc` CLI, Security Context Constraints (SCC), Projects (namespaces).
  - Reference: <https://docs.openshift.com/container-platform/latest/welcome/index.html>
- [ ] **(45 min)** Paste the marker `/mock-week-5` into chat. Claude will run a 30-45 min mock technical interview covering: one Flask/Jinja2 question, one SQLAlchemy/PostgreSQL question, one OpenSearch/search question, one Kubernetes/OpenShift question, one "walk me through how you would..." architecture question. Debrief after each answer.

**Stretch (+1h)**
- [ ] Install `kind` or use Docker Desktop Kubernetes locally. Deploy your Week 1-2 Flask app as a Pod + Service + Ingress. Port-forward and access it. Total: ~1h.

**Self-check questions**
- What is the difference between a Deployment and a StatefulSet?
- What is the difference between a ConfigMap and a Secret, and how are they mounted into pods?
- What does `kubectl port-forward` do, and when is it useful?
- What is a Route in OpenShift, and how does it relate to an Ingress in upstream Kubernetes?
- What is a Security Context Constraint (SCC), and why does OpenShift add it?

---

## Week 6 | Mock Technical 2 + Mock Behavioral + Final review

**Core (2h)**
- [ ] **(45 min)** Paste `/mock-week-6-tech` into chat. Claude will run a 30-45 min **deeper** technical mock, focused on the topics you were weakest on in Week 5. Expect whiteboard-style "design the search+ingest pipeline for a CDS-scale repository" type questions.
- [ ] **(45 min)** Paste `/mock-week-6-behavioral` into chat. Claude will run a 30-45 min CERN-style behavioral interview. Prepare 4-5 STAR stories in advance (see appendix for prompts).
- [ ] **(30 min)** Final review: re-read the job posting end to end, re-read your motivation message, and re-read your preliminary-question answers. Identify 2-3 likely follow-up questions they will dig into and rehearse crisp 60-second answers.

**Stretch (+1h)**
- [ ] Prepare 3-4 good questions to ask *them* at the end of the interview. Strong ones for this role:
  - *"How is the CDS migration to InvenioRDM sequenced? What is the current phase?"*
  - *"How does the CDS team collaborate with the upstream InvenioRDM community, and how much of the work lands upstream?"*
  - *"What does day-to-day user support look like? Which CERN departments use CDS most heavily?"*
  - *"How is the team sized, and what does onboarding look like in the first month?"*

---

## Appendix A | STAR stories to prepare

CERN behavioral questions cluster around these themes. Prepare a crisp, specific, 90-second story for each:

1. **Working with a non-technical stakeholder** (e.g., your CFO/CEO requirements work at Orkast).
2. **Shipping under constraints or deadline** (e.g., a Siteimprove release, an Orkast feature launched end-to-end).
3. **Open-source contribution where your change was scrutinized by maintainers** (Athena / Etherpad / Scilab).
4. **Resolving an ambiguous technical decision** (e.g., choosing PostgreSQL + Prisma + Aurora at Orkast; or a Siteimprove architecture tradeoff).
5. **A production incident you helped resolve or prevent** (Siteimprove / Orkast).
6. **Disagreeing with a colleague or leader** (tech lead era at O2 Filmes, or any peer code-review disagreement).
7. **Learning a new technology fast** (this is the "how will you ramp on Flask/OpenShift" answer).

For each: **Situation** (1 sentence), **Task** (1 sentence), **Action** (3-4 sentences, concrete), **Result** (1-2 sentences, ideally quantified).

---

## Appendix B | Technical question bank (self-study)

Use these for self-rehearsal before the mock weeks. Try to answer each in 60-90 seconds out loud.

**Flask**
- How would you structure a medium-sized Flask app? What does the application factory pattern buy you?
- Explain how Flask handles a request from the moment it hits the WSGI server until the response goes back. Where do blueprints fit in?
- How do you handle authentication in Flask? What is `flask-login` vs `flask-principal` vs a JWT-based flow?

**SQLAlchemy + PostgreSQL**
- You want to add a JSON metadata column to a table in production with 100M rows. Walk me through how you would do it safely.
- A query is slow. How do you diagnose it (SQLAlchemy echo, PostgreSQL `EXPLAIN ANALYZE`, index review)?
- What are the common sources of N+1 queries in SQLAlchemy, and how do you fix them?

**OpenSearch**
- Design a search schema for CDS records. What fields would you index, what would you store, what would you mark `keyword` vs `text`?
- How would you implement "search across title, description, authors, and keywords, boosted by field" in Query DSL?
- How do you reindex a large index in production without downtime?

**Kubernetes / OpenShift**
- Walk me through what happens when `kubectl apply -f deployment.yaml` runs.
- What is the difference between a Pod and a Deployment?
- Your pod is CrashLoopBackOff. Walk me through your debugging steps.

**InvenioRDM / CDS**
- At a high level, how is InvenioRDM structured? What is a module, service, resource?
- How does a record go from draft to published? What validations happen?
- What is a vocabulary in Invenio, and why would you use one?

**System design (likely with diagram)**
- Design an ingestion pipeline for CDS that accepts uploads from 1000 concurrent users, stores files in object storage, extracts text for search, and notifies downstream indexers. Walk me through components, failure modes, and data flow.
- How would you design an authentication system for a multi-institution repository where some users are CERN staff, some are external scientists, and some are anonymous visitors with read-only access?

---

## Appendix C | Good-to-read before interview (when time allows)

- InvenioRDM architecture docs: <https://inveniordm.docs.cern.ch/reference/architecture/>
- CDS homepage + recent news: <https://cds.cern.ch/>
- Open Science at CERN: <https://home.cern/science/computing/open-science>
- FAIR principles one-pager: <https://www.go-fair.org/fair-principles/>
- GitHub: `inveniosoftware/invenio-app-rdm` (browse structure, not every line)

---

## Tracker

| Week | Target h | Actual h | Done | Notes |
|------|----------|----------|------|-------|
| 1    | 2        |          | ☐    |       |
| 2    | 2        |          | ☐    |       |
| 3    | 2        |          | ☐    |       |
| 4    | 2        |          | ☐    |       |
| 5    | 2        |          | ☐    |       |
| 6    | 2        |          | ☐    |       |

---

## If the call comes early (shortlist within 2 weeks)

Prioritize in this order:
1. Week 4 (InvenioRDM + CDS context): do this first, it is the highest-leverage gap filler.
2. Week 1 (Flask foundations): fastest confidence win.
3. Week 5 technical mock: call Claude and do it sooner rather than later.
4. Everything else (SQLAlchemy, OpenSearch, Kubernetes) in whatever time remains.

You already have a strong baseline. This plan is about closing the specific gaps the panel will probe, not about learning new things from zero.
