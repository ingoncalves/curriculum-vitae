# Screening Questions — CERN, Full Stack Engineer (IT-CA-IR-2026-66-LD)

**Submitted on**: 2026-04-22
**Character limits**: 1440 characters per answer

Preliminary Questions page in SmartRecruiters; six screening questions that appear after the main application form.

---

## Q1: Can you briefly describe a web project where you used Flask/Python as a primary technology?

```
My Python experience is predominantly in large-scale scientific computing rather than Flask web applications. Since 2019 at CERN I have worked within the Athena framework (C++/Python, a large open-source platform) designing energy reconstruction algorithms for the ATLAS Tile Calorimeter, including a machine-learning-based energy estimation tool fully integrated into Athena in C++ and Python. I also designed an open-source pulse generator and signal simulation library in C++ with Python bindings, now used by multiple international research groups. My PhD research is in Python and C++ on signal reconstruction algorithms.

My production web-application experience has been in Node.js (NestJS, Express), Ruby on Rails, Java (Spring Boot), C# (ASP.NET), and React. I have not yet shipped a Flask application in production, but the programming model (routing, request handling, ORM integration, templating) is familiar from equivalent work in those frameworks. Given my deep Python background, a decade of full-stack experience on large platforms, and prior open-source contributions to Athena at CERN, Etherpad, and Scilab, I am confident I can ramp up on InvenioRDM's Flask and SQLAlchemy stack quickly.
```

**Character count**: 1208 / 1440

---

## Q2: Do you have experience programming with languages such as Javascript/React? If yes, please briefly explain how and specify years experience.

```
Yes, extensively. I have worked with JavaScript/TypeScript and React for over 10 years across multiple senior roles.

At Siteimprove (via Prime IT, Feb 2022 to Present) I develop front-end applications and shared libraries in JavaScript/TypeScript and React, including ongoing maintenance of the Fancy Design System, a large React component library with WAI-ARIA accessibility compliance consumed by multiple enterprise products.

At Orkast (Mar 2026 to Present), as sole engineer, I designed and built the front-end in React 19 and TypeScript using Vite, MUI, and TanStack Query, including Kanban drag-and-drop boards, financial dashboards, and reporting interfaces for tenant organizations.

At O2 Filmes (Sept 2018 to Jan 2022) I architected front-end applications in React on top of Etherpad, with real-time multi-user collaboration and data visualization in D3.js.

Earlier I also built cross-platform mobile apps in Ionic and JavaScript (Vista Group, 2014 to 2016), AngularJS back-office interfaces (DataHex, 2016 to 2018), and a TypeScript/Electron cross-platform desktop application with peer-to-peer data sync. Total: approximately 11 years of JavaScript/TypeScript and 7+ years of React specifically.
```

**Character count**: 1211 / 1440

---

## Q3: Do you have experience in drafting technical requirements? If so, please provide an example.

```
Yes, regularly. A concrete recent example is the planning work I led for Orkast v1.1.0.

I gathered two sets of stakeholder requirements: three financial requirements from the CFO (a fiscal-document attachment system with S3, bank reconciliation via CSV upload with matching UI, and dashboard reports with charts) and two executive requirements from the CEO (a cross-domain CEO Dashboard with trends and alerts, and a granular ACL expansion of the role-based access model). I translated these into a concrete three-phase implementation plan covering data model changes (new Attachment/BankStatement/BankTransaction models, extended RolesGuard), back-end endpoints, front-end components, infrastructure updates (new S3 bucket in Terraform, task-role IAM permissions), and new third-party dependencies (AWS S3 SDKs, csv-parse, recharts). The plan was captured as a written technical document and used as the working specification across the release.

I also routinely produce technical documentation as part of agile ceremonies at Siteimprove (story refinement, architectural decisions, API specifications), and at O2 Filmes I acted as technical lead defining architectural decisions and prioritizing the backlog for a collaborative editor platform. I am comfortable drafting requirements at both product and system levels.
```

**Character count**: 1322 / 1440

---

## Q4: Do you have experience with configuration management utilities like Puppet? If yes, please provide examples.

```
No direct production experience with Puppet. My infrastructure and configuration work has been centred on Infrastructure as Code and container tooling.

At Orkast I own the entire cloud configuration in Terraform, including VPC/networking, Aurora PostgreSQL Serverless, ECS Fargate services, ALB with HTTPS, ACM, ECR, IAM roles, and S3, together with Docker-based container builds and deployment scripts.

At O2 Filmes I designed infrastructure as code using Terraform, deploying containerized services with Docker on Amazon ECS clusters.

At Siteimprove I work within an AWS cloud-native environment (DynamoDB, CloudFront, ElastiCache, Redis), where configuration is largely code-driven.

I am comfortable picking up Puppet if needed. The core concepts (declarative resource description, idempotent state convergence, node classification, templated manifests) are conceptually very similar to Terraform and Ansible, and my background in scripting (Shell, Python) and in maintaining long-lived production services would transfer cleanly to a Puppet-managed environment.
```

**Character count**: 1070 / 1440

---

## Q5: Do you have experience working with containerised deployments (Openshift, Kubernetes)? If yes, please provide examples.

```
Yes, extensively with Docker, and with some hands-on Kubernetes exposure through AWS EKS.

At Siteimprove I contribute to maintaining services deployed on EKS, and in the FedRAMP-compliant environment I develop against cluster-hosted services via kubectl port-forwarding, since direct cluster access is restricted by the controls of that environment. This has given me practical familiarity with the Kubernetes CLI, Pods, Services, and the operational workflows around a production EKS cluster.

At Orkast I build and deploy multi-stage Docker images for both the NestJS back-end and the Vite-built React front-end (served via NGINX), pushing them to ECR and running them on ECS Fargate behind an ALB, with ECS Exec enabled for running Prisma migrations safely against Aurora PostgreSQL. The deployment pipeline (build, push, deploy, migrate) is scripted from a single CLI.

At O2 Filmes I deployed containerized microservices with Docker on Amazon ECS clusters, using Terraform for the cluster definitions and CI-driven image promotion.

I have not yet operated OpenShift directly, but I am familiar with its core abstractions (Pods, Deployments, Services, Ingress, ConfigMaps/Secrets) and the additions it layers on top of upstream Kubernetes (Routes, ImageStreams, BuildConfigs, the oc CLI, security contexts). Given my Docker, EKS, and IaC background, ramping up on OpenShift for the CDS/InvenioRDM stack should be straightforward.
```

**Character count**: 1436 / 1440

---

## Q6: Please share a public link to your codebase if any (GitHub, or others).

```
GitHub: https://github.com/ingoncalves

Relevant open-source contributions:

Athena (CERN ATLAS offline software): https://gitlab.cern.ch/atlas/athena/-/merge_requests?state=all&author_username=ginaciog

Etherpad (real-time collaborative editor): https://github.com/ether/etherpad-lite/commits?author=ingoncalves

Scilab (open-source numerical computation): https://github.com/scilab/scilab/commits?author=ingoncalves
```

**Character count**: 418 / 1440

---

## Retrospective note

- **Honesty over inflation**: chose to be transparent about the Flask/Puppet/OpenShift gaps rather than inflate. That was the ethically correct choice but likely triggered the automated pre-selection filter to cut the application.
- **Learnings for future CERN applications**: target postings where the stack overlap is stronger. If a CERN role requires a technology not on the CV, an internal contact / referral becomes essential to bypass the filter.
- **Q5 was later strengthened**: added EKS/FedRAMP hands-on context mid-application (from an insight during the review), which is a good example of iterating an answer as new information surfaces.
