# 🚖 Taxi App — BA Portfolio Project

[🇺🇦 Ukrainian Version](README-UA.md)

A business analysis portfolio project modeling an online taxi ordering platform.  
The goal was to practice the full BA workflow — from problem definition to requirements documentation, process modeling, and Agile project management.

---

## 📌 Problem Statement

Passengers in smaller cities often rely on phone calls to dispatchers or large third-party platforms that are not always available or affordable locally. Drivers lack a unified system for automatic order distribution and ride tracking. Administrators have no tool to manage tariffs or monitor operations in real time.

---

## 🎯 Project Goal

Design and document a taxi ordering system that addresses these pain points by supporting:

- Fast ride ordering with automatic driver matching
- Transparent pricing before order confirmation
- Secure card and cash payment processing
- Real-time ride and driver tracking
- A mutual rating system for quality control
- An admin panel for platform management

**Key success metric:** average driver waiting time ≤ 5 minutes within the city.

---

## ⚙️ Features in Scope (MVP)

| # | Feature | Status |
|---|---------|--------|
| 1 | User registration & authentication | ✅ Documented |
| 2 | Ride ordering with vehicle category selection | ✅ Documented |
| 3 | Automatic ride price calculation | ✅ Documented |
| 4 | Nearby driver search | ✅ Documented |
| 5 | Real-time ride and driver tracking | ✅ Documented |
| 6 | Card and cash payment processing | ✅ Documented |
| 7 | Mutual driver/passenger rating system | ✅ Documented |
| 8 | Ride history for passengers and drivers | ✅ Documented |
| 9 | Driver verification by administrator | ✅ Documented |
| 10 | Tariff management and ride monitoring | ✅ Documented |

**Out of scope (planned for next version):** scheduled rides, corporate accounts, promo codes, in-app chat, automated document verification.

---

## 👥 System Actors

| Actor | Role |
|-------|------|
| Passenger | Orders rides, pays, rates drivers |
| Driver | Accepts and completes rides, rates passengers |
| Administrator | Manages users, tariffs, verifications, and reports |
| Support Team | Handles complaints and disputes |
| Payment Provider | Processes card transactions (external service) |

---

## 📂 Documentation

### Requirements & Analysis

| Document | Description | Status |
|----------|-------------|--------|
| [Product Vision](docs/EN/confluence/product-vision.md) | High-level system purpose and value | ✅ Done |
| [Vision & Scope](docs/EN/confluence/vision-and-scope.md) | What is and is not in scope for MVP | ✅ Done |
| [Stakeholders](docs/EN/confluence/stakeholders.md) | Stakeholder table with interests and influence | ✅ Done |
| [User Roles](docs/EN/confluence/user-roles.md) | Role definitions | ✅ Done |
| [Business Requirements](docs/EN/confluence/business-requirements.md) | Business goals with measurable objectives | ✅ Done |
| [Functional Requirements](docs/EN/confluence/functional-requirements.md) | 28 functional requirements (FR-01–FR-28) | ✅ Done |
| [Non-Functional Requirements](docs/EN/confluence/non-functional-requirements.md) | 6 NFRs with numeric targets and rationale | ✅ Done |
| [Business Rules](docs/EN/confluence/business-rules.md) | 10 business rules (BR-01–BR-10) | ✅ Done |
| [Use Cases](docs/EN/confluence/use-cases.md) | 3 detailed use cases with alternative and exception flows | ✅ Done |
| [User Stories](docs/EN/confluence/user-story.md) | 11 user stories with acceptance criteria | ✅ Done |
| [API Documentation](docs/EN/confluence/api.md) | Key API endpoints overview | ✅ Done |

### Diagrams

| Diagram | Type | Tool |
|---------|------|------|
| Ride ordering and payment flow | Activity Diagram (UML) | Draw.io |
| System actors and interactions | Use Case Diagram (UML) | Draw.io |
| Business process flow | BPMN 2.0 | Draw.io |
| Payment subprocess | BPMN 2.0 | Draw.io |
| Data model | ERD | Draw.io |

Diagram files are located in `/docs/diagrams`.

---

## 📋 Jira Workflow

The project was managed using Jira with the following structure:

| Artifact | Details |
|----------|---------|
| Epics | 5 epics: Register Account, Login, Order Taxi, Cancel Ride, Rate Driver |
| User Stories | 17 tasks linked to epics (TA-1 – TA-17) |
| Sprint Board | Columns: To Do → In Progress → In Review → In Testing → Done |
| Timeline | Sprint planning with epic-level visualization |

Jira screenshots are located in `/jira`.

---

## 🧠 BA Skills Practiced

This project covered the following business analysis competencies:

- **Stakeholder analysis** — identifying actors, mapping interests and influence levels
- **Requirements elicitation & documentation** — writing FR, NFR, business rules, and use cases from scratch
- **Process modeling** — BPMN, UML Activity Diagrams, Use Case Diagrams
- **User story writing** — structuring stories with acceptance criteria in Agile format
- **Scope management** — defining MVP boundaries and out-of-scope items with rationale
- **Data modeling** — designing an ERD with normalized tables and relationships
- **Agile workflow** — creating and managing a product backlog, epics, and sprint board in Jira

---

## ⚠️ Challenges & Decisions

**Challenge 1 — Separating Passenger and Driver as distinct entities in the data model**  
Initially considered a single `User` table with a role field. Decided to keep `Passenger` and `Driver` as separate tables because they have fundamentally different attributes (drivers have vehicles, license data, verification status) and different system behaviors. This avoids nullable columns and keeps the schema clean.

**Challenge 2 — Defining payment timing**  
Card payment could be charged at order confirmation or at ride completion. Decided to charge at confirmation (BR-03) to prevent ride-and-dash scenarios, and documented a separate refund flow for cancellations. This is consistent with how Uklon and Uber handle it.

**Challenge 3 — Rating integrity**  
To prevent gaming, ratings are only allowed after a ride reaches "completed" status (BR-07), and administrators cannot manually edit numeric ratings (BR-10). These rules were derived from thinking about what could go wrong — not from a spec.

---

## 📚 Lessons Learned

- Writing NFRs with rationale ("why this number") forces you to think about the actual user impact, not just pick arbitrary thresholds.
- Business rules are easy to skip, but they're where the real edge cases live — things like "what happens when a driver cancels after accepting" don't appear in happy-path use cases.
- Jira and documentation need to stay in sync. In this project, acceptance criteria exist in the markdown files but are not duplicated inside Jira tickets — that's a gap I would fix in a team setting.

---

## 🛠 Tools & Technologies

- **Jira** — backlog, sprint board, epics, user stories
- **Confluence** — requirements documentation (modeled in Markdown)
- **Draw.io** — BPMN, UML Activity, Use Case, ERD diagrams
- **BPMN 2.0** — business process modeling
- **PostgreSQL** — database schema design (ERD)
- **Markdown** — documentation
- **Git & GitHub** — version control

---

## 👨‍💻 Author

**Maksym** — Junior Business Analyst  
This is an educational portfolio project created to practice business analysis skills in a realistic product context.
