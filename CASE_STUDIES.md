# Case studies: independent software built with AI-assisted development

These public summaries describe **problems, engineering decisions and technical evidence** without exposing private source code, company credentials or sensitive operational data. I use coding assistants to accelerate iteration, while owning requirements, integration, code review and validation.

## 1. KlinikSys — Offline-first clinical workflows

**Problem.** Volunteer medical teams working in remote communities cannot rely on continuous internet access. Records, prescriptions and stock workflows still need to function during connectivity gaps.

**What I built.** A React/TypeScript progressive web app with local data in IndexedDB, synchronization queues, role-based workflows and a Supabase/PostgreSQL backend. The system is designed around offline operation, organization boundaries and predictable recovery when connectivity returns.

**Engineering challenges.** Data consistency after reconnection, safe write paths, access separation, clinical workflow usability and testable synchronization behavior.

**Verification.** Unit, browser E2E, database/RLS and security-oriented automated checks form part of the development workflow; a green build does not itself establish clinical effectiveness or real-world adoption.

**Role.** Independent product design and implementation, with AI-assisted coding and human technical review.

**Status / evidence.** [Product website](https://kliniksys.com) · Source private · No patient outcome or institutional adoption figures claimed.

## 2. Mackenzo — Retrieval-augmented academic assistant

**Problem.** University policies, syllabi and course information are distributed across HTML pages and downloadable documents, increasing the effort needed to answer practical student questions.

**What I built.** A retrieval-augmented generation workflow with hybrid document collection, PDF/Excel/HTML ingestion, FastAPI application services, PostgreSQL/pgvector-backed retrieval and a student-facing interface.

**Engineering challenges.** Keeping ingested content traceable, retrieving relevant passages rather than guessing, parsing course syllabi and handling diverse document structures.

**Role.** Independent research, data pipeline, API and product development with LLM/agent assistance.

**Status / evidence.** [Live site](https://www.mackenzo.com/) · Source private · Educational project, not an official university service.

## 3. K-Ops — Read-only security operations prototype

**Problem.** Security teams often need to cross-reference identity posture, vulnerabilities and endpoint coverage across multiple tools before deciding which items deserve attention.

**What I built.** A private Python/FastAPI and PostgreSQL-based prototype to ingest data through read-only integrations, organize findings, prioritize risk and generate traceable reports and dashboards.

**Engineering challenges.** Source freshness, data reconciliation, permissions boundaries, traceability, avoiding destructive actions and maintaining clear distinction between evidence and recommendations.

**Role.** Independent architecture and development, with AI-assisted engineering.

**Status / evidence.** Private technical work. This case study intentionally excludes company data, integrations' credentials, internal URLs, live metrics and adoption claims. Not described as an officially deployed corporate system.

## 4. OpenEMS Server — Open-source endpoint management

**Problem.** There is value in accessible tools for evaluating endpoint registration, configuration distribution and policy management without committing to proprietary control planes.

**What I built.** An experimental FastAPI management server, React admin interface, PostgreSQL/Redis backends, policy distribution, authentication, audit trails and a Rust Windows agent.

**Engineering challenges.** Cross-platform compatibility, policy behavior, secure client/server communication and verifiable acceptance across real target environments.

**Role.** Independent open-source implementation and documentation with AI-assisted development.

**Status / evidence.** [Source, tests and technical documentation](https://github.com/kenzofujimoto/openems-server). Experimental prototype, with platform and compatibility limitations openly documented. Not affiliated with Fortinet.

---

### The AI-assisted engineering workflow

1. Frame the real-world problem and its constraints.
2. Decompose it into data model, API contracts, UX and acceptance criteria.
3. Use AI agents and coding assistants to propose or implement increments.
4. Independently review architecture, access controls, generated code and edge cases.
5. Validate with automated tests, static analysis and real browser workflows where available.
6. Deploy prototypes, inspect failures and refine the product.

**What I do not claim:** verified hours saved, commercial revenue, medical outcomes, deployment inside RSM Brasil or production-ready platform interoperability without independent evidence. These figures can be added only once measured and authorized for publication.
