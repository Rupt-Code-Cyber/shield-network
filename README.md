# Shield Network

**Distributed Trust, Safety, Evidence, Verification & Digital Risk Intelligence Platform**

Shield Network is a distributed B2B platform for authorized digital-risk monitoring, evidence collection, expert verification, public fact-checking, controlled mitigation workflows, provenance, and distributed execution.

The platform combines automated intelligence with human expert review and auditable execution. It is designed to help organizations investigate harmful or misleading digital content, preserve evidence, verify claims, coordinate authorized mitigation actions, and maintain an immutable chain of provenance across the lifecycle of an incident.

> **Detection is not judgment. Verification is not censorship. Execution is not guaranteed enforcement.**
>
> Shield Network provides evidence, workflows, authorization, and auditable execution while the relevant external platform remains the final decision-maker on platform-level enforcement.

---

## Table of Contents

* [Overview](#overview)
* [Core Principles](#core-principles)
* [Platform Capabilities](#platform-capabilities)
* [System Architecture](#system-architecture)
* [Repository Architecture](#repository-architecture)
* [Frontend Applications](#frontend-applications)
* [Backend Microservices](#backend-microservices)
* [AEN Network](#aen-network)
* [Trust & Verification Pipeline](#trust--verification-pipeline)
* [FactCheck](#factcheck)
* [Shield Execution](#shield-execution)
* [Blockchain & Rewards](#blockchain--rewards)
* [Data Architecture](#data-architecture)
* [Event-Driven Architecture](#event-driven-architecture)
* [Workflow Orchestration](#workflow-orchestration)
* [Security Architecture](#security-architecture)
* [Repository Boundaries](#repository-boundaries)
* [Technology Stack](#technology-stack)
* [Local Development](#local-development)
* [Environment Configuration](#environment-configuration)
* [Testing](#testing)
* [CI/CD](#cicd)
* [API Contracts](#api-contracts)
* [Observability](#observability)
* [Compliance & Governance](#compliance--governance)
* [Project Structure](#project-structure)
* [Development Guidelines](#development-guidelines)
* [Roadmap](#roadmap)
* [Contributing](#contributing)
* [Security](#security)
* [License](#license)

---

# Overview

Digital platforms generate enormous volumes of public and authorized content every day.

Organizations increasingly need systems capable of answering questions such as:

* What happened?
* Where did the content originate?
* What claim is being made?
* What evidence supports or contradicts the claim?
* Has the content been manipulated?
* What do independent experts conclude?
* How confident are those conclusions?
* What actions are authorized?
* Which platform integration can legally and technically execute those actions?
* What happened after execution?
* Can every decision and action be audited later?

Shield Network addresses these problems through a distributed architecture built around:

```text
Detection
   ↓
Evidence Collection
   ↓
Intelligence Analysis
   ↓
Independent Expert Verification
   ↓
Consensus & Uncertainty
   ↓
Authorization
   ↓
Shield Control
   ↓
Authorized Execution
   ↓
Platform Response
   ↓
Provenance & Audit
```

The platform is designed for organizations that require a defensible, evidence-based digital-risk workflow rather than an opaque automated moderation system.

---

# Core Principles

## 1. Evidence Before Action

Automated detection creates an investigation candidate. It does not automatically establish truth, wrongdoing, or liability.

## 2. Human Verification

High-impact assessments can require independent expert review before an action becomes eligible for execution.

## 3. Preserve Disagreement

The system records reviewer assessments, confidence, disagreement, evidence, methodology, and uncertainty instead of forcing artificial consensus.

## 4. Authorized Execution Only

Execution is permitted only when the relevant organization, integration, scope, policy, and platform capability authorize the requested action.

## 5. Platform Final Authority

Shield Network does not guarantee that an external platform will remove, restrict, label, or otherwise act on reported content.

## 6. Full Provenance

Incidents, evidence, expert reviews, authorizations, execution tasks, platform responses, and rewards maintain traceable relationships.

## 7. Separation of Responsibilities

Detection, evidence, verification, authorization, execution, rewards, and blockchain operations are separated into explicit domains.

## 8. Privacy by Design

Only information necessary for the relevant workflow should be collected, retained, processed, or exposed.

## 9. No Identity Deception

AEN execution events maintain their network provenance. The system does not attempt to disguise coordinated activity as unrelated organic users or circumvent platform anti-abuse systems.

---

# Platform Capabilities

Shield Network is organized around several major capabilities.

### Digital Risk Intelligence

* Authorized content ingestion
* Content classification
* Claim extraction
* Harassment detection
* Misinformation analysis
* Disinformation analysis
* Media analysis
* Manipulation detection
* Multilingual analysis
* Entity and relationship analysis
* Evidence discovery

### Evidence Management

* Evidence preservation
* Screenshots
* Media files
* Metadata
* OCR
* Transcripts
* Frame extraction
* Source references
* Evidence relationships
* Evidence integrity
* Evidence provenance

### Expert Verification

* Credentialed expert registration
* Expert assignment
* Independent review
* Confidence scoring
* Evidence-based assessments
* Reviewer disagreement
* Consensus calculation
* Review history

### Public FactCheck

* Claim pages
* Evidence cards
* Methodology
* Expert assessments
* Consensus
* Disagreement
* Corrections
* Updates
* Appeals/challenges
* Review dates
* Source references

### Shield Control

* Authorization policies
* Eligible task creation
* AEN selection
* Capability validation
* Signed execution tasks
* Expiration
* Idempotency
* Execution receipts
* Platform responses

### AEN Network

* Node registration
* Node identity
* Capability discovery
* Health monitoring
* Secure communication
* Task execution
* Receipts
* Retry
* Offline recovery
* Workload distribution
* Eligibility
* Fairness
* Rewards

### Blockchain & Rewards

* Solana wallet linking
* Wallet ownership verification
* Internal reward ledger
* $SHIELD accounting
* Reward aggregation
* Settlement
* Liquidity routing
* Swap execution
* USDC settlement
* Blockchain reconciliation

---

# System Architecture

Shield Network uses a domain-driven distributed architecture.

```text
                         ┌─────────────────────────┐
                         │     Client Platforms     │
                         │ Web / Mobile / External  │
                         └────────────┬────────────┘
                                      │
                                      ▼
                         ┌─────────────────────────┐
                         │ Kubernetes Gateway       │
                         │ Production Edge Layer    │
                         └────────────┬────────────┘
                                      │
             ┌────────────────────────┼────────────────────────┐
             │                        │                        │
             ▼                        ▼                        ▼
      Frontend Apps            Domain Services            Public APIs
             │                        │                        │
             └────────────────────────┼────────────────────────┘
                                      │
          ┌───────────────────────────┼───────────────────────────┐
          │                           │                           │
          ▼                           ▼                           ▼
     PostgreSQL                    Kafka                    Temporal
   Source of Truth            Event Streaming          Workflow Engine
          │                           │                           │
          ├──────────────┐            │            ┌──────────────┤
          ▼              ▼            ▼            ▼              ▼
       Redis         OpenSearch      S3       AEN Network     Blockchain
       Cache           Search      Evidence     Runtime          │
                                                                  ▼
                                                               Solana
                                                              $SHIELD
```

Production infrastructure is intentionally maintained outside this repository in the separate DevOps Blueprint.

---

# Repository Architecture

The repository is organized as a product monorepo.

There are:

* **13 independently deployable frontend applications**
* **14 independently deployable backend domain microservices**
* A distributed AEN subsystem
* ML/intelligence components
* Blockchain programs and integrations
* Shared application packages
* API/event contracts
* Durable workflows
* Database definitions
* External integrations
* Automated tests
* Local Docker environment
* CI/CD workflows

---

# Frontend Applications

The repository contains the following independently deployable frontend applications:

| Application            | Responsibility                                        |
| ---------------------- | ----------------------------------------------------- |
| `customer-portal`      | Customer incident, intelligence and account workflows |
| `aen-portal`           | AEN operator interface                                |
| `expert-portal`        | Expert review and verification                        |
| `operations-console`   | Operational workflows                                 |
| `admin-console`        | Platform administration                               |
| `factcheck-public`     | Public evidence and fact-check interface              |
| `intelligence-console` | Intelligence investigation interface                  |
| `platform-console`     | Platform integration management                       |
| `aen-registration`     | AEN enrollment                                        |
| `expert-registration`  | Expert onboarding                                     |
| `customer-onboarding`  | Customer onboarding                                   |
| `wallet`               | Wallet connection and reward management               |
| `status`               | Service and platform status                           |

These applications communicate with the backend through documented API contracts.

---

# Backend Microservices

Shield Network contains 14 domain-driven backend services.

## 1. Identity Service

Responsible for:

* Identity
* Authentication integration
* Authorization subjects
* User lifecycle
* Service identities
* Organization identity

---

## 2. Tenant & Billing Service

Responsible for:

* Organizations
* Tenants
* Plans
* Subscriptions
* Usage
* Billing
* Entitlements

---

## 3. Ingestion Service

Responsible for:

* Authorized content ingestion
* Source normalization
* Webhooks
* Feeds
* External content adapters
* Initial content metadata

---

## 4. Intelligence Service

Responsible for:

* Content classification
* Claim extraction
* Risk analysis
* Harassment analysis
* Misinformation analysis
* Disinformation analysis
* Entity analysis
* ML inference coordination

---

## 5. Evidence Service

Responsible for:

* Evidence records
* Evidence relationships
* Media metadata
* Screenshots
* OCR
* Transcripts
* Evidence integrity
* Evidence storage references

---

## 6. Verification Service

Responsible for:

* Expert review workflows
* Expert assignments
* Independent assessments
* Confidence
* Consensus
* Disagreement
* Review lifecycle

---

## 7. FactCheck Service

Responsible for:

* Public fact-check records
* Claim assessments
* Evidence cards
* Methodology
* Corrections
* Updates
* Challenges
* Public publication state

---

## 8. Shield Control Service

Responsible for:

* Shield authorization
* Eligibility
* Execution policies
* Task creation
* AEN selection
* Capability checks
* Signed task references
* Task expiration

---

## 9. Distributed Node Service

Responsible for:

* AEN registration
* Node state
* Capabilities
* Health
* Node authorization
* Task coordination
* Node lifecycle

---

## 10. Mitigation & Platform Integration Service

Responsible for:

* Social platform adapters
* Authorized reporting
* Platform API requests
* Platform responses
* Rate limits
* Idempotency
* Integration-specific behavior

---

## 11. Provenance Service

Responsible for:

* Incident lineage
* Evidence lineage
* Decision lineage
* Execution lineage
* Network provenance
* Batch identity
* Immutable audit references

---

## 12. Reputation & Rewards Service

Responsible for:

* AEN reputation
* Contribution accounting
* Reward calculation
* Reward ledger
* Reward eligibility
* Payout preparation

---

## 13. Blockchain Service

Responsible for:

* Solana interactions
* Wallet verification
* $SHIELD operations
* Treasury operations
* Settlement
* Swap coordination
* Transaction monitoring
* Reconciliation

---

## 14. Audit & Notification Service

Responsible for:

* Audit events
* Security notifications
* Operational notifications
* Workflow notifications
* Delivery status
* Notification preferences

---

# AEN Network

AEN stands for:

> **Authorized Execution Node**

An AEN is a distributed execution endpoint operated as part of the Shield Network.

AENs do not independently decide what content should be acted upon.

Their responsibility is to execute an already-authorized task within a defined capability and policy boundary.

## AEN lifecycle

```text
Registration
     ↓
Identity Verification
     ↓
Capability Registration
     ↓
Authorization
     ↓
Health / Availability
     ↓
Task Eligibility
     ↓
Task Assignment
     ↓
Execution
     ↓
Receipt
     ↓
Reward
```

## AEN execution model

An eligible AEN receives a task containing information such as:

```text
task_id
node_id
incident_id
authorization_id
allowed_action
policy_reference
capability_reference
expiration
execution_constraints
```

The AEN runtime validates the task before execution.

After execution, it produces an execution receipt.

---

# Trust & Verification Pipeline

The core intelligence pipeline is designed around evidence and independent review.

```text
Authorized Source
       ↓
Content Ingestion
       ↓
Content Normalization
       ↓
AI Analysis
       ↓
Claim Extraction
       ↓
Evidence Discovery
       ↓
Research Ticket
       ↓
Expert Review #1
Expert Review #2
Expert Review #3
       ↓
Consensus / Disagreement
       ↓
Authorization Decision
       ↓
Eligible Action
```

The AI layer assists investigators and experts.

It is not treated as the sole authority for high-impact decisions.

---

# FactCheck

The public FactCheck layer provides an evidence-oriented representation of reviewed claims.

A FactCheck record may contain:

```text
Original Claim
      ↓
Archived Evidence
      ↓
Media Analysis
      ↓
Transcript / OCR
      ↓
Sources
      ↓
Expert Assessments
      ↓
Disagreement
      ↓
Consensus
      ↓
Methodology
      ↓
Corrections / Updates
```

Possible assessment states include:

* `SUPPORTED`
* `CONTRADICTED`
* `MISLEADING`
* `MISSING_CONTEXT`
* `MANIPULATED_MEDIA`
* `UNVERIFIABLE`
* `INSUFFICIENT_EVIDENCE`
* `PENDING_REVIEW`

The system preserves the underlying evidence and reasoning rather than presenting an unexplained binary verdict.

---

# Shield Execution

Shield execution follows a strict authorization pipeline.

```text
AI Detection
      ↓
Evidence
      ↓
Expert Verification
      ↓
Consensus
      ↓
Authorization
      ↓
Shield Control Plane
      ↓
Eligible AEN
      ↓
Signed Task
      ↓
Deploy Shield
      ↓
AEN Runtime
      ↓
Report Generation
      ↓
Platform Integration
      ↓
Authorized Platform API
      ↓
Platform Response
      ↓
Execution Receipt
      ↓
Provenance + Audit
```

The **Deploy Shield** action is not continuously available.

It becomes available only when an AEN has an authorized and eligible task.

The AEN does not manually compose the report.

The backend generates the individualized report from the approved incident and evidence context, then the appropriate platform adapter attempts the authorized API operation.

The external platform remains responsible for the final enforcement decision.

---

# Network Provenance

Distributed execution maintains explicit provenance.

Every execution can be associated with:

```text
Network ID
Batch ID
Incident ID
Authorization ID
AEN ID
Task ID
Report ID
Execution ID
Platform Response
Timestamp
```

This allows the platform to answer:

* Which incident generated this task?
* Which authorization permitted it?
* Which AEN executed it?
* What report was generated?
* Which platform received it?
* What response was returned?
* What reward was generated?

The architecture does not attempt to disguise coordinated activity as unrelated organic activity.

---

# Blockchain & Rewards

Shield Network uses **Solana** as its primary blockchain environment.

The network uses:

> **$SHIELD**

as its native utility/reward token.

## Wallet model

AEN operators connect a Solana-compatible wallet.

The platform verifies ownership of the wallet address before associating it with the AEN account.

Private keys and seed phrases are never stored by the application.

---

# Internal Reward Ledger

Rewards are maintained internally rather than creating a blockchain transaction for every individual task.

Example:

```text
Task #001 → $0.05
Task #002 → $0.05
Task #003 → $0.10
Task #004 → $0.15
Task #005 → $0.20

Accumulated reward → $0.55
```

The internal ledger remains the accounting source of truth for accrued rewards.

A later payout can aggregate the balance.

---

# Settlement Model

A simplified payout flow is:

```text
Completed AEN Tasks
        ↓
Reward Ledger
        ↓
Eligible Balance
        ↓
Payout Request
        ↓
$SHIELD Calculation
        ↓
Liquidity / Swap
        ↓
Settlement Asset
        ↓
Verified AEN Wallet
        ↓
Blockchain Confirmation
        ↓
Reconciliation
```

A settlement asset such as USDC can be used where supported by the configured liquidity and settlement infrastructure.

The AEN wallet is separate from the company treasury wallet.

Treasury signing operations must use secure key-management infrastructure appropriate for production deployment.

---

# Data Architecture

Shield Network uses specialized infrastructure according to data responsibility.

| Technology            | Responsibility                             |
| --------------------- | ------------------------------------------ |
| PostgreSQL            | Transactional source of truth              |
| Redis                 | Cache, ephemeral state, rate limiting      |
| Kafka                 | Event streaming                            |
| Temporal              | Durable workflow orchestration             |
| OpenSearch            | Search and investigation                   |
| S3-compatible storage | Evidence and media objects                 |
| Solana                | Blockchain settlement and token operations |

The system avoids treating every infrastructure component as a general-purpose database.

---

# Event-Driven Architecture

Services communicate through explicit contracts and domain events.

Example:

```text
content.ingested
       ↓
intelligence.analysis.requested
       ↓
claim.extracted
       ↓
evidence.collection.requested
       ↓
verification.requested
       ↓
verification.completed
       ↓
consensus.calculated
       ↓
shield.authorization.created
       ↓
aen.task.created
       ↓
aen.task.executed
       ↓
platform.report.submitted
       ↓
platform.response.received
       ↓
execution.completed
       ↓
reward.eligible
```

Kafka provides the event-streaming backbone.

Events are versioned through the `contracts/events/` directory.

Consumers should be designed to tolerate retries and duplicate delivery.

Idempotency is therefore a first-class architectural concern.

---

# Workflow Orchestration

Temporal is used for workflows that require:

* Long-running execution
* Retries
* Timeouts
* Human interaction
* Scheduled operations
* Compensation
* External API waiting
* Blockchain confirmation
* Payout processing
* Disaster recovery procedures

Kafka handles event streaming.

Temporal handles durable workflow state.

These systems serve different responsibilities and are intentionally not treated as interchangeable.

---

# Security Architecture

Security is applied at multiple layers.

## Identity

* OIDC
* Keycloak integration
* Service identities
* AEN identities
* Expert identities
* Customer identities

## Authorization

* Role-based access control
* Policy-based authorization
* Tenant isolation
* Capability authorization
* Task-level authorization

## Application Security

* Pydantic validation
* Strict API contracts
* Secure secrets handling
* Idempotency
* Input validation
* Audit logging
* Cryptographic verification

## AEN Security

* Node identity
* Certificates
* Secure communication
* Sandboxing
* Capability restrictions
* Task expiration
* Policy enforcement
* Execution receipts

## Supply Chain Security

CI/CD security validation can include:

* Dependency scanning
* Secret scanning
* SAST
* Container scanning
* SBOM generation
* Artifact signing
* Dependency updates

Production security infrastructure remains part of the external DevOps Blueprint.

---

# Repository Boundaries

This repository intentionally does **not** contain the production infrastructure platform.

## Included

```text
Application Code
Frontend Applications
Backend Services
AEN Runtime
ML Components
Blockchain Application Code
Contracts
Workflows
Database Definitions
Integrations
Tests
Docker Local Environment
CI/CD
```

## Excluded

```text
Terraform Production Infrastructure
Kubernetes Production Manifests
Helm Production Charts
Kustomize Production Configuration
Argo CD Deployment Infrastructure
Cloud Networking
Production Cluster Configuration
Production Observability Infrastructure
Production Security Infrastructure
```

Those responsibilities belong to the separate:

> **Shield Network DevOps Blueprint**

This separation allows application engineers to evolve product code independently from production infrastructure.

---

# Technology Stack

## Backend

* Python 3.13
* FastAPI
* Pydantic
* SQLAlchemy 2
* Alembic

## Frontend

* Next.js
* TypeScript
* pnpm
* Biome

## Data

* PostgreSQL 18
* Redis
* OpenSearch
* S3-compatible object storage

## Distributed Systems

* Apache Kafka
* Temporal

## Identity

* Keycloak
* OpenID Connect

## Blockchain

* Solana
* Rust
* Anchor
* SPL Token / Token Extensions where appropriate
* Solana-compatible wallets

## Development

* Docker
* Docker Compose
* uv
* pnpm

## CI/CD

* GitHub Actions

---

# Local Development

## Prerequisites

Install:

* Git
* Docker
* Docker Compose
* Python 3.13
* uv
* Node.js
* pnpm
* Rust
* Solana CLI
* Anchor CLI

Verify the installation:

```bash
git --version
docker --version
docker compose version
python --version
uv --version
node --version
pnpm --version
rustc --version
solana --version
anchor --version
```

---

# Clone the Repository

```bash
git clone git@github.com:<organization>/shield-network.git
cd shield-network
```

---

# Environment Configuration

Create the local environment file:

```bash
cp .env.example .env
```

Never commit real secrets.

The `.env.example` file should contain configuration names and safe development defaults only.

Production secrets must be supplied through the production secret-management system.

---

# Start Local Infrastructure

Start the local development dependencies:

```bash
docker compose up -d
```

Check running services:

```bash
docker compose ps
```

View logs:

```bash
docker compose logs -f
```

Stop the environment:

```bash
docker compose down
```

To remove local development volumes as well:

```bash
docker compose down -v
```

> Do not use `docker compose down -v` if you need to preserve local database or development data.

---

# Python Environment

Install Python dependencies with `uv`:

```bash
uv sync
```

Run the application environment according to the service-specific development instructions.

Each independently deployable backend service should expose its own application entrypoint and health endpoint.

---

# Database Migrations

Database migrations are managed with Alembic.

Typical development workflow:

```bash
uv run alembic upgrade head
```

Create a migration only when the schema has intentionally changed:

```bash
uv run alembic revision --autogenerate -m "describe schema change"
```

Review generated migrations manually before applying them.

Never blindly trust autogenerated migrations in production.

---

# Frontend Development

Install workspace dependencies:

```bash
pnpm install
```

Run an individual frontend application from its application directory.

For example:

```bash
cd apps/customer-portal
pnpm dev
```

The same pattern applies to the other frontend applications.

---

# Testing

The project uses multiple testing layers.

## Unit Tests

Test individual functions, classes, modules, and domain logic.

```bash
pytest tests/unit
```

## Integration Tests

Validate service interactions with infrastructure dependencies.

```bash
pytest tests/integration
```

## Contract Tests

Validate API and event contracts.

```bash
pytest tests/contract
```

## End-to-End Tests

Validate complete business workflows.

```bash
pytest tests/end-to-end
```

## Performance Tests

Performance testing belongs under:

```text
tests/performance/
```

## Security Tests

Security-specific automated tests belong under:

```text
tests/security/
```

## Chaos Tests

Distributed failure scenarios belong under:

```text
tests/chaos/
```

---

# CI/CD

GitHub Actions provides repository-level CI/CD.

```text
.github/workflows/
├── ci.yml
├── security.yml
├── contract.yml
└── release.yml
```

## `ci.yml`

Responsible for:

* Dependency installation
* Formatting
* Linting
* Unit tests
* Integration validation
* Build validation

## `security.yml`

Responsible for repository-level security validation such as:

* Secret scanning
* Static analysis
* Dependency scanning
* Container scanning
* SBOM validation

## `contract.yml`

Responsible for:

* OpenAPI validation
* Schema validation
* Event contract validation
* Compatibility checks

## `release.yml`

Responsible for:

* Versioning
* Release artifacts
* Container artifacts
* Release metadata
* Signed artifacts where configured

Production deployment remains controlled by the separate DevOps Blueprint and its deployment platform.

---

# API Contracts

API contracts are maintained under:

```text
contracts/openapi/
```

Available contract domains include:

```text
public.yaml
customer.yaml
expert.yaml
aen.yaml
operations.yaml
admin.yaml
factcheck.yaml
```

Contracts should be treated as versioned interfaces.

Breaking changes require explicit review.

---

# Event Contracts

Event schemas are maintained under:

```text
contracts/events/
```

Domains include:

```text
content/
intelligence/
evidence/
verification/
factcheck/
shield/
aen/
platform/
provenance/
rewards/
blockchain/
```

Event changes must preserve compatibility according to the project's event-versioning policy.

---

# Observability

Application-level instrumentation is included in the product repository.

Shared application components include:

```text
packages/logging/
packages/telemetry/
```

Applications should emit structured logs and telemetry.

The production observability stack itself is deployed through the external DevOps Blueprint.

The production platform may integrate:

* OpenTelemetry
* Prometheus
* Grafana
* Loki
* Tempo

The product repository does not own their production deployment.

---

# Health & Reliability

Services should expose appropriate health information.

Typical health categories include:

```text
Liveness
Readiness
Dependency Health
Database Connectivity
Kafka Connectivity
Temporal Connectivity
Redis Connectivity
External Integration Health
```

Health endpoints must distinguish between:

* process availability
* readiness to receive traffic
* dependency failure

This prevents infrastructure orchestration from interpreting every dependency problem as a process failure.

---

# Compliance & Governance

Shield Network is designed around controlled and auditable operations.

Important governance capabilities include:

* Tenant isolation
* Access control
* Evidence provenance
* Expert accountability
* Audit trails
* Authorization records
* Execution provenance
* Data retention policies
* Correction workflows
* Appeals/challenges
* Platform integration scopes
* API capability validation

External platform policies remain applicable to every integration.

The system must not be designed to circumvent:

* platform rate limits
* API restrictions
* authentication controls
* anti-abuse mechanisms
* reporting restrictions
* platform enforcement policies
* access-control mechanisms

---

# Privacy

The platform should minimize unnecessary personal information.

Where practical:

* Separate identity from review content
* Minimize reviewer exposure to irrelevant identity information
* Restrict sensitive data access
* Encrypt sensitive information
* Apply retention policies
* Record access to protected data
* Use tenant isolation
* Avoid collecting data that is not required for the declared workflow

Public information does not automatically mean unrestricted internal use.

---

# Project Structure

```text
shield-network/
├── .github/
├── apps/
├── services/
├── integrations/
├── aen-network/
├── ml/
├── packages/
├── contracts/
├── workflows/
├── database/
├── blockchain/
├── docs/
├── tests/
├── scripts/
├── Dockerfile
├── docker-compose.yml
├── .env.example
├── pyproject.toml
├── uv.lock
├── package.json
├── pnpm-workspace.yaml
├── biome.json
├── README.md
├── SECURITY.md
├── CONTRIBUTING.md
└── LICENSE
```

---

# Development Guidelines

## Keep Services Domain-Focused

A service should own a coherent business capability.

Avoid creating services solely because a component happens to contain several files.

## Prefer Explicit Contracts

Communication between independently deployable components should use documented contracts.

## Preserve Idempotency

Distributed systems retry.

Every externally visible operation that may be retried should have an appropriate idempotency strategy.

## Do Not Share Database Ownership

Shared infrastructure does not mean shared domain ownership.

Services should maintain clear ownership of their transactional data.

## Keep Infrastructure Separate

Do not introduce production Kubernetes, Terraform, Helm, or Argo CD configuration into this repository unless the repository boundary is intentionally changed.

## Treat AI as an Assistant

AI-generated assessments should remain traceable to:

* input
* model/version
* evidence
* processing
* confidence
* human review where required

## Preserve Auditability

Important decisions should produce durable records.

---

# Roadmap

The project is organized around progressive implementation.

## Phase 1 — Platform Foundation

* Repository foundation
* Shared packages
* Identity
* Tenant model
* Database foundation
* Contracts
* Local infrastructure
* CI/CD

## Phase 2 — Intelligence

* Ingestion
* Content normalization
* Detection
* Claim extraction
* Evidence collection
* Search

## Phase 3 — Verification

* Expert registration
* Expert verification
* Review workflows
* Consensus
* FactCheck

## Phase 4 — Shield Control

* Authorization
* AEN registration
* Node capabilities
* Task lifecycle
* Execution receipts
* Platform integrations

## Phase 5 — Distributed Network

* AEN runtime
* Scheduling
* Health
* Capacity
* Retry
* Offline recovery
* Reputation

## Phase 6 — Blockchain

* Wallet linking
* $SHIELD
* Reward ledger
* Solana programs
* Settlement
* Reconciliation

## Phase 7 — Enterprise Hardening

* Security hardening
* Performance testing
* Disaster recovery
* Compliance controls
* Advanced observability
* Chaos testing
* Production readiness

---

# Production Architecture Boundary

Shield Network is the application platform.

The separate DevOps Blueprint is responsible for running it in production.

```text
┌─────────────────────────────────────────────────────┐
│                  SHIELD NETWORK                     │
│                                                     │
│  Frontends │ Microservices │ AEN │ ML │ Blockchain │
│  Contracts │ Workflows │ Database │ Integrations   │
└────────────────────────┬────────────────────────────┘
                         │
                         │ deployed by
                         ▼
┌─────────────────────────────────────────────────────┐
│              SHIELD DEVOPS BLUEPRINT                │
│                                                     │
│ Terraform │ Kubernetes │ Helm │ Kustomize │ ArgoCD │
│ Networking │ Security │ Observability │ Secrets    │
└─────────────────────────────────────────────────────┘
```

This boundary is intentional.

The application repository should remain focused on **what the platform does**.

The DevOps Blueprint should remain focused on **how the platform is operated in production**.

---

# Contributing

Contributions should follow the project's engineering standards.

Before submitting a change:

1. Understand the affected domain.
2. Update the relevant contract if an interface changes.
3. Add or update tests.
4. Validate migrations.
5. Run formatting and linting.
6. Run relevant integration tests.
7. Update documentation when behavior changes.
8. Never commit secrets.
9. Never bypass authorization controls.
10. Preserve provenance and auditability.

See [`CONTRIBUTING.md`](CONTRIBUTING.md) for repository-specific contribution requirements.

---

# Security

Security vulnerabilities should not be disclosed through public issues.

See [`SECURITY.md`](SECURITY.md) for the responsible disclosure process.

Security-sensitive changes should receive appropriate review before merging.

---

# License

See [`LICENSE`](LICENSE) for the applicable license.

---

# Status

**Project status:** Active development

Shield Network is being developed as a production-oriented distributed platform. Individual components may reach production readiness at different stages, and deployment readiness should be determined through the project's testing, security, compliance, and operational readiness criteria.

---

## Architecture Summary

```text
                         SHIELD NETWORK
                              │
          ┌───────────────────┼───────────────────┐
          │                   │                   │
          ▼                   ▼                   ▼
   13 Frontend Apps     14 Domain Services    Public FactCheck
          │                   │
          └───────────────────┼───────────────────┘
                              │
                 ┌────────────┼────────────┐
                 │            │            │
                 ▼            ▼            ▼
              Kafka       Temporal      PostgreSQL
                 │            │            │
                 ├────────────┼────────────┤
                 │            │            │
                 ▼            ▼            ▼
              Redis      OpenSearch       S3
                              │
                              ▼
                        Evidence Graph
                              │
                              ▼
                     Expert Verification
                              │
                              ▼
                       Shield Control
                              │
                              ▼
                       AEN Network
                              │
                              ▼
                  Platform Integrations
                              │
                              ▼
                     External Platforms
                              │
                              ▼
                       Provenance/Audit
                              │
                              ▼
                         Rewards
                              │
                              ▼
                    Solana / $SHIELD
```

**Shield Network is built around one central principle:**

> **Every meaningful action should be explainable, authorized, attributable, and auditable.**
