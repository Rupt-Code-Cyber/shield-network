shield-network/
│
├── .github/
│   ├── CODEOWNERS
│   ├── pull_request_template.md
│   └── workflows/
│       ├── ci.yml
│       ├── security.yml
│       ├── contract.yml
│       └── release.yml
│
├── apps/
│   ├── customer-portal/
│   ├── aen-portal/
│   ├── expert-portal/
│   ├── operations-console/
│   ├── admin-console/
│   ├── factcheck-public/
│   ├── intelligence-console/
│   ├── platform-console/
│   ├── aen-registration/
│   ├── expert-registration/
│   ├── customer-onboarding/
│   ├── wallet/
│   └── status/
│
├── services/
│   ├── identity-service/
│   ├── tenant-billing-service/
│   ├── ingestion-service/
│   ├── intelligence-service/
│   ├── evidence-service/
│   ├── verification-service/
│   ├── factcheck-service/
│   ├── shield-control-service/
│   ├── distributed-node-service/
│   ├── mitigation-platform-service/
│   ├── provenance-service/
│   ├── reputation-rewards-service/
│   ├── blockchain-service/
│   └── audit-notification-service/
│
├── integrations/
│   ├── social-platforms/
│   │   ├── facebook/
│   │   ├── instagram/
│   │   ├── youtube/
│   │   ├── x/
│   │   ├── tiktok/
│   │   ├── reddit/
│   │   ├── discord/
│   │   ├── telegram/
│   │   └── generic/
│   │
│   ├── search/
│   │   ├── google/
│   │   ├── bing/
│   │   └── generic/
│   │
│   ├── factcheck-sources/
│   │   ├── news/
│   │   ├── government/
│   │   ├── public-records/
│   │   └── verification/
│   │
│   └── external-services/
│       ├── email/
│       ├── payments/
│       ├── notifications/
│       └── storage/
│
├── aen-network/
│   ├── control-plane/
│   │   ├── node-registry/
│   │   ├── enrollment/
│   │   ├── authentication/
│   │   ├── health/
│   │   ├── capabilities/
│   │   └── policy/
│   │
│   ├── runtime/
│   │   ├── agent/
│   │   ├── task-runner/
│   │   ├── execution/
│   │   ├── local-security/
│   │   ├── telemetry/
│   │   └── receipts/
│   │
│   ├── communication/
│   │   ├── messaging/
│   │   ├── heartbeat/
│   │   ├── acknowledgements/
│   │   ├── retry/
│   │   └── offline-recovery/
│   │
│   ├── scheduling/
│   │   ├── eligibility/
│   │   ├── capacity/
│   │   ├── workload-distribution/
│   │   └── fairness/
│   │
│   └── security/
│       ├── identity/
│       ├── certificates/
│       ├── sandbox/
│       └── policies/
│
├── ml/
│   ├── models/
│   ├── detection/
│   ├── harassment/
│   ├── misinformation/
│   ├── disinformation/
│   ├── media/
│   │   ├── image/
│   │   ├── video/
│   │   ├── audio/
│   │   ├── deepfake/
│   │   └── manipulation/
│   ├── claim-analysis/
│   ├── multilingual/
│   ├── inference/
│   ├── evaluation/
│   └── model-registry/
│
├── packages/
│   ├── config/
│   ├── logging/
│   ├── telemetry/
│   ├── errors/
│   ├── auth/
│   ├── authorization/
│   ├── crypto/
│   ├── database/
│   ├── kafka/
│   ├── events/
│   ├── messaging/
│   ├── storage/
│   ├── cache/
│   ├── validation/
│   ├── openapi/
│   ├── audit/
│   ├── provenance/
│   ├── policy-engine/
│   ├── idempotency/
│   ├── pagination/
│   ├── blockchain/
│   └── test-utils/
│
├── contracts/
│   ├── openapi/
│   │   ├── public.yaml
│   │   ├── customer.yaml
│   │   ├── expert.yaml
│   │   ├── aen.yaml
│   │   ├── operations.yaml
│   │   ├── admin.yaml
│   │   └── factcheck.yaml
│   │
│   ├── events/
│   │   ├── content/
│   │   ├── intelligence/
│   │   ├── evidence/
│   │   ├── verification/
│   │   ├── factcheck/
│   │   ├── shield/
│   │   ├── aen/
│   │   ├── platform/
│   │   ├── provenance/
│   │   ├── rewards/
│   │   └── blockchain/
│   │
│   └── schemas/
│       ├── common/
│       ├── identity/
│       ├── incidents/
│       ├── evidence/
│       ├── reports/
│       ├── rewards/
│       ├── wallets/
│       └── payouts/
│
├── workflows/
│   ├── incident/
│   ├── evidence/
│   ├── verification/
│   ├── factcheck/
│   ├── shield/
│   ├── aen/
│   ├── rewards/
│   ├── billing/
│   ├── blockchain/
│   └── disaster-recovery/
│
├── database/
│   ├── migrations/
│   ├── schemas/
│   ├── indexes/
│   ├── functions/
│   ├── views/
│   ├── extensions/
│   ├── seed/
│   └── policies/
│
├── blockchain/
│   ├── solana/
│   │   ├── programs/
│   │   │   ├── shield-token/
│   │   │   ├── reward-vault/
│   │   │   └── treasury/
│   │   ├── migrations/
│   │   ├── tests/
│   │   └── Anchor.toml
│   │
│   ├── wallets/
│   │   ├── authentication/
│   │   ├── linking/
│   │   └── verification/
│   │
│   ├── liquidity/
│   │   ├── pools/
│   │   ├── dex/
│   │   ├── quotes/
│   │   └── routing/
│   │
│   ├── settlement/
│   │   ├── swap/
│   │   ├── payout/
│   │   ├── claims/
│   │   └── reconciliation/
│   │
│   ├── indexers/
│   ├── sdk/
│   └── tests/
│
├── docs/
│   ├── architecture/
│   ├── domain/
│   ├── api/
│   ├── events/
│   ├── aen/
│   ├── factcheck/
│   ├── blockchain/
│   ├── rewards/
│   ├── security/
│   ├── compliance/
│   ├── operations/
│   └── runbooks/
│
├── tests/
│   ├── unit/
│   ├── integration/
│   ├── contract/
│   ├── end-to-end/
│   ├── performance/
│   ├── security/
│   └── chaos/
│
├── scripts/
│   ├── development/
│   ├── database/
│   ├── kafka/
│   ├── blockchain/
│   └── operations/
│
├── Dockerfile
├── docker-compose.yml
├── .editorconfig
├── .env.example
├── .gitignore
├── .python-version
├── pyproject.toml
├── uv.lock
├── package.json
├── pnpm-workspace.yaml
├── biome.json
├── README.md
├── SECURITY.md
├── CONTRIBUTING.md
└── LICENSE