# Percy (percy)

Percy is an all-in-one visual testing and review platform, now part of **BrowserStack** (acquired 2020, offered as "Percy by BrowserStack"). In a typical workflow your test framework or CI uploads DOM snapshots via the open-source Percy CLI/SDK; Percy renders each snapshot across browsers and responsive widths, diffs it against an approved baseline, and surfaces pixel-level visual changes for review and approval. On top of that workflow Percy exposes a documented **REST API** under `https://percy.io/api/v1` for reading and managing Projects, Builds, and Snapshots, plus Visual Git (branchline) sync and merge.

**A note on the access model:** the snapshot *capture and upload* path - the part that actually creates snapshots during a build - is driven by the open-source Percy CLI and SDKs (`@percy/cli`, `@percy/core`, `@percy/client`) using a project token (`PERCY_TOKEN`), not by a public REST "create snapshot" endpoint. The public REST reference documents reading and managing the resulting Projects, Builds, and Snapshots. This repository models only the documented public REST surface and flags the CLI/SDK-internal upload path honestly.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/percy/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/percy/refs/heads/main/apis.yml)

## Tags

- Visual Testing
- Visual Regression
- Screenshots
- QA
- Testing
- CI/CD
- BrowserStack

## Timestamps

- **Created:** 2026-07-11
- **Modified:** 2026-07-11

## Authentication

- **Reads** (list/get on projects, builds, snapshots, and all Visual Git calls): per-project token in the Authorization header - `Authorization: Token token=<PROJECT_TOKEN>`.
- **Writes** (approve/unapprove/reject a build, fail or delete a build, create or update a project): BrowserStack HTTP Basic auth using your BrowserStack username and access key.

## APIs

### Percy Builds API

A build logically groups the test sessions and snapshots produced by a single run. List recent builds (last 30 days) with filters for SHA, branch, and state; fetch a single build's details and summary; and drive review actions - approve, unapprove, or reject via the reviews endpoint, and manually fail or delete a build.

- **Human URL:** [https://www.browserstack.com/docs/percy/api-reference/builds](https://www.browserstack.com/docs/percy/api-reference/builds)
- **Base URL:** `https://percy.io/api/v1`

#### Tags

- Builds
- Visual Testing
- QA

#### Properties

- [Documentation](https://www.browserstack.com/docs/percy/api-reference/percy-apis)
- [API Reference](https://www.browserstack.com/docs/percy/api-reference/builds)
- [OpenAPI](openapi/percy-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/percy.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/percy.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Percy Snapshots API

Read the snapshots that make up a build. List snapshots for a given `build_id` with pagination and filters (review state reason, snapshot IDs, name search), and fetch a single snapshot's details including its review state and per-browser/width comparisons. Snapshots are created during a build by the Percy CLI/SDK, not through a public REST create endpoint; this API is the read/inspect surface for them.

- **Human URL:** [https://www.browserstack.com/docs/percy/api-reference/snapshots](https://www.browserstack.com/docs/percy/api-reference/snapshots)
- **Base URL:** `https://percy.io/api/v1`

#### Tags

- Snapshots
- Visual Regression
- Screenshots

#### Properties

- [API Reference](https://www.browserstack.com/docs/percy/api-reference/snapshots)
- [OpenAPI](openapi/percy-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/percy.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/percy.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Percy Projects API

A project logically groups builds. Retrieve the details of the project tied to a given project token, create a new web or app project programmatically, and update an existing project's settings - base branch, approval and branch filters, screenshot limits, intelli-ignore, and visibility.

- **Human URL:** [https://www.browserstack.com/docs/percy/api-reference/projects](https://www.browserstack.com/docs/percy/api-reference/projects)
- **Base URL:** `https://percy.io/api/v1`

#### Tags

- Projects
- Configuration
- QA

#### Properties

- [API Reference](https://www.browserstack.com/docs/percy/api-reference/projects)
- [OpenAPI](openapi/percy-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/percy.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/percy.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Percy Visual Git API

Visual Git (branchline) synchronizes approved snapshots across branch lines. Trigger a sync of a project's snapshots with a target branch filter, poll the status of a sync operation by `sync_id`, and merge approved snapshots from a feature branch into the master branchline.

- **Human URL:** [https://www.browserstack.com/docs/percy/api-reference/visual-git](https://www.browserstack.com/docs/percy/api-reference/visual-git)
- **Base URL:** `https://percy.io/api/v1`

#### Tags

- Visual Git
- Branchline
- Snapshots

#### Properties

- [API Reference](https://www.browserstack.com/docs/percy/api-reference/visual-git)
- [OpenAPI](openapi/percy-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/percy.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/percy.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [Authentication](authentication/percy-authentication.yml)
- [GitHub Organization](https://github.com/percy)
- [LinkedIn](https://www.linkedin.com/company/browserstack)
- [Website](https://percy.io)
- [Documentation](https://www.browserstack.com/docs/percy)
- [Plans](plans/percy-plans-pricing.yml)
- [Rate Limits](rate-limits/percy-rate-limits.yml)
- [Fin Ops](finops/percy-finops.yml)
- [Blog](https://percy.io/blog)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
