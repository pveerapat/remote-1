แก้ 2 จุดแล้วครับ: ลบ fallback `unscoped/users/...` และลบ `Admin-only maintenance commands` ออกจาก Optional Extension

# ARI V1 — P1-1 Backend Implementation Specification v1.0

## 1. Document Control

Project: ARI — Agricultural Intelligence Platform
Document: P1-1 Backend Implementation Specification
Version: v1.0
Status: Draft for Owner Review
Scope: FastAPI Backend Implementation

Source of Truth:

* #44 Farm AI Operating System
* #45 Software Architecture & Monorepo Specification Rev2.0
* #46 MVP Software Build Plan
* #46A Mobile App UX Flow & Screen Specification
* #46B Web App UX Flow & Screen Specification
* #47 AI Agent Development Workflow Framework
* ARI V1 — P0 Domain Model Specification v1.0
* ARI V1 — P0 Database Schema Specification v1.0
* ARI V1 — P0 API Specification v1.0

This document defines how to implement the frozen P0 backend specifications using FastAPI.

This document does not redesign architecture, database schema, API contracts, RBAC, or domain model.

---

## 2. Implementation Boundary

### 2.1 P1-1 Required

P1-1 is required before backend coding starts.

P1-1 covers:

* Backend folder structure
* FastAPI implementation pattern
* SQLAlchemy integration
* Alembic migration setup
* JWT authentication
* Frozen RBAC authorization
* Repository / service / router layering
* Module implementation pattern
* MinIO file upload implementation
* Offline sync implementation
* Validation rules
* Error handling
* Logging
* Configuration
* Testing
* Docker local development stack

### 2.2 Optional Extension

Optional extensions may be added later without changing architecture:

* QR APIs for Farm / Zone / Tree
* API request rate limiting
* Background worker for upload cleanup
* Media thumbnail generation
* Virus scanning for uploaded files
* Advanced observability dashboard
* Structured JSON log shipping

### 2.3 Future Enhancement

Future enhancements are not required for P0 backend implementation:

* Knowledge Services
* Knowledge Graph
* RAG
* Vector Database
* Agent Orchestration
* Commerce Services
* Robot Services
* Audit Services
* Permission Services
* Irrigation / fertilizer automation
* Compliance automation
* Marketplace / bidding
* Export / GI / carbon modules

---

## 3. Frozen Technology Stack

### 3.1 Backend

```text
FastAPI
Python 3.12+
```

### 3.2 Database

```text
PostgreSQL
TimescaleDB
SQLAlchemy
Alembic
```

### 3.3 Object Storage

```text
MinIO
```

### 3.4 Messaging

```text
EMQX MQTT
```

### 3.5 Authentication

```text
JWT
Access Token
Refresh Token
```

### 3.6 Deployment

```text
Docker
GitHub Monorepo
```

---

## 4. Backend Project Structure

The backend implementation must live under:

```text
backend/
```

Required structure:

```text
backend/
├── app/
│   ├── __init__.py
│   ├── main.py
│   ├── api/
│   │   ├── __init__.py
│   │   ├── v1/
│   │   │   ├── __init__.py
│   │   │   ├── router.py
│   │   │   ├── auth.py
│   │   │   ├── users.py
│   │   │   ├── organizations.py
│   │   │   ├── farms.py
│   │   │   ├── zones.py
│   │   │   ├── trees.py
│   │   │   ├── notebook_entries.py
│   │   │   ├── note_items.py
│   │   │   ├── follow_ups.py
│   │   │   ├── notifications.py
│   │   │   ├── upload_queue.py
│   │   │   ├── files.py
│   │   │   └── sync.py
│   ├── core/
│   │   ├── __init__.py
│   │   ├── config.py
│   │   ├── security.py
│   │   ├── enums.py
│   │   ├── errors.py
│   │   └── logging.py
│   ├── db/
│   │   ├── __init__.py
│   │   ├── base.py
│   │   ├── session.py
│   │   └── migrations/
│   ├── models/
│   │   ├── __init__.py
│   │   ├── user.py
│   │   ├── organization.py
│   │   ├── farm.py
│   │   ├── zone.py
│   │   ├── tree.py
│   │   ├── notebook_entry.py
│   │   ├── note_item.py
│   │   ├── follow_up.py
│   │   ├── notification.py
│   │   ├── upload_job.py
│   │   └── role.py
│   ├── schemas/
│   │   ├── __init__.py
│   │   ├── auth.py
│   │   ├── user.py
│   │   ├── organization.py
│   │   ├── farm.py
│   │   ├── zone.py
│   │   ├── tree.py
│   │   ├── notebook_entry.py
│   │   ├── note_item.py
│   │   ├── follow_up.py
│   │   ├── notification.py
│   │   ├── upload_job.py
│   │   ├── file.py
│   │   └── sync.py
│   ├── repositories/
│   │   ├── __init__.py
│   │   ├── base.py
│   │   ├── users.py
│   │   ├── organizations.py
│   │   ├── farms.py
│   │   ├── zones.py
│   │   ├── trees.py
│   │   ├── notebook_entries.py
│   │   ├── note_items.py
│   │   ├── follow_ups.py
│   │   ├── notifications.py
│   │   └── upload_jobs.py
│   ├── services/
│   │   ├── __init__.py
│   │   ├── auth_service.py
│   │   ├── user_service.py
│   │   ├── organization_service.py
│   │   ├── farm_service.py
│   │   ├── zone_service.py
│   │   ├── tree_service.py
│   │   ├── notebook_service.py
│   │   ├── note_item_service.py
│   │   ├── follow_up_service.py
│   │   ├── notification_service.py
│   │   ├── upload_queue_service.py
│   │   ├── file_service.py
│   │   └── sync_service.py
│   ├── dependencies/
│   │   ├── __init__.py
│   │   ├── auth.py
│   │   ├── rbac.py
│   │   ├── db.py
│   │   └── scope.py
│   ├── middleware/
│   │   ├── __init__.py
│   │   ├── request_id.py
│   │   ├── error_handler.py
│   │   └── logging.py
│   ├── utils/
│   │   ├── __init__.py
│   │   ├── uuid.py
│   │   ├── datetime.py
│   │   ├── checksum.py
│   │   ├── object_keys.py
│   │   └── pagination.py
│   └── tests/
│       ├── __init__.py
│       ├── unit/
│       ├── integration/
│       ├── api/
│       ├── repositories/
│       └── services/
├── alembic.ini
├── Dockerfile
├── docker-compose.yml
├── pyproject.toml
├── requirements.txt
└── README.md
```

Important correction:

```text
qr_registry.py
```

must not be included in Required P1-1 structure because QR is a representation, not a separate entity.

---

## 5. FastAPI Architecture

The backend must use a layered architecture:

```text
Router Layer
↓
Service Layer
↓
Repository Layer
↓
Database Layer
```

No business logic should be placed directly in routers.

No database access should be placed directly in routers.

---

## 6. Layer Responsibilities

### 6.1 Router Layer

Routers are responsible for:

* HTTP endpoint definition
* Request schema validation
* Dependency injection
* Authentication requirement
* Authorization guard usage
* Calling service methods
* Returning response schemas

Routers must not:

* Perform direct SQL queries
* Implement business rules
* Manage transactions manually unless required by service design

Example router modules:

```text
api/v1/auth.py
api/v1/farms.py
api/v1/notebook_entries.py
api/v1/sync.py
api/v1/files.py
```

### 6.2 Service Layer

Services are responsible for:

* Application rules
* Frozen domain rules
* Hierarchy validation
* Organization / farm / ownership scope checks
* Conflict handling
* Idempotency handling
* Transaction orchestration
* Calling repositories
* Calling MinIO client
* Calling MQTT publisher if required

Services must remain simple and P0-focused.

No knowledge service, agent service, commerce service, robot service, audit service, permission service, consultation service, or QR registry service should be introduced.

### 6.3 Repository Layer

Repositories are responsible for:

* SQLAlchemy query construction
* CRUD operations
* Filtering
* Pagination
* Row-level lookup
* Database constraint interaction

Repositories must not:

* Perform HTTP validation
* Interpret JWT
* Implement RBAC
* Call external services

### 6.4 Database Layer

Database layer is responsible for:

* Engine creation
* Session lifecycle
* SQLAlchemy Base
* Alembic migration binding
* Connection pooling
* Transaction commit / rollback behavior

---

## 7. Application Startup

FastAPI app entry point:

```text
app/main.py
```

Responsibilities:

* Create FastAPI application
* Load settings
* Register middleware
* Register API v1 router
* Register exception handlers
* Configure CORS
* Configure logging
* Health check endpoint

Required endpoints:

```text
GET /health
GET /api/v1/health
```

Health check must verify:

* API process is running
* Database connection is reachable

Optional health checks:

* MinIO reachable
* EMQX reachable

---

## 8. API Versioning

All P0 backend APIs must be mounted under:

```text
/api/v1
```

Example:

```text
/api/v1/auth/login
/api/v1/farms
/api/v1/notebook-entries
/api/v1/sync/batch
```

API versioning must not create another backend or service.

---

## 9. Database Integration

### 9.1 SQLAlchemy

Use SQLAlchemy ORM for frozen P0 tables.

Models must map directly to the frozen P0 database schema.

Do not add columns, remove columns, rename columns, or change relationships unless the P0 schema is formally revised.

### 9.2 Required Frozen Tables

Required frozen database scope:

```text
organizations
users
farms
zones
trees
notebook_entries
note_items
follow_ups
notifications
upload_queue
```

Role-related tables may be mapped only if already included in the frozen database schema.

### 9.3 Explicitly Not Required Tables

Do not create:

```text
qr_registry
consultations
owners
blocks
reviews
knowledge
audit_logs
permissions
```

Rules:

```text
QR = Representation, not Entity
Consultation = Notebook Entry Type, not Entity
Owner = Organization
Block = Zone
Audit = Backend / Infrastructure Logs
Permissions = RBAC + Organization Scope + Farm Scope
```

### 9.4 Alembic

Alembic is used for migrations.

Migration rules:

* Initial migration must represent frozen P0 schema.
* P0 migrations are locked after approval.
* Later migrations must be additive unless a formal revision gate approves changes.
* No destructive migration during P0 development.
* No non-frozen table may be added in P1-1.

Required files:

```text
alembic.ini
app/db/migrations/env.py
app/db/migrations/versions/
```

### 9.5 Connection Management

Database connection string must come from environment settings:

```text
DATABASE_URL=postgresql+psycopg://user:password@postgres:5432/ari
```

Connection pooling:

```text
pool_size
max_overflow
pool_pre_ping
pool_recycle
```

Default local values may be simple.

Production values must be configurable.

### 9.6 Session Management

Use request-scoped database session.

Pattern:

```text
get_db()
```

Rules:

* One session per request.
* Commit only after service success.
* Rollback on exception.
* Close session after request.
* Do not share session globally.

### 9.7 Transaction Rules

Service methods that create or update multiple records must run in one transaction.

Examples:

* Create notebook entry + note items
* Sync batch insert/update
* Upload queue status update + note item file_ref update
* Create farm record

Transaction rule:

```text
All-or-nothing for one logical backend operation.
```

---

## 10. TimescaleDB Usage

TimescaleDB is part of the frozen database stack.

For P0 backend implementation:

* Use PostgreSQL-compatible SQLAlchemy models.
* Do not introduce new hypertables unless already defined in frozen schema.
* Do not redesign notebook storage as time-series architecture.
* TimescaleDB extension may be enabled in database initialization if required by frozen schema.

---

## 11. Authentication Implementation

### 11.1 Authentication Method

Use JWT-based authentication.

Required tokens:

```text
Access Token
Refresh Token
```

### 11.2 Password Handling

Password storage:

* Never store plain text passwords.
* Store only password hash.
* Use a secure password hashing library.

Password verification flow:

```text
User submits email/password
→ Backend loads user by email
→ Verify password hash
→ Issue access token and refresh token
```

### 11.3 Access Token

Access token must include:

```text
sub = user_id
roles = user roles
organization_id = active organization scope if available
exp = expiration
iat = issued at
```

Access token is used for API authorization.

### 11.4 Refresh Token

Refresh token is used to obtain a new access token.

Refresh token may be stored server-side if frozen API requires logout invalidation.

Simplest implementation:

* Issue signed refresh token.
* Validate token signature and expiry.
* Rotate refresh token on refresh if required by P0 API.

### 11.5 Login Flow

```text
POST /api/v1/auth/login
```

Flow:

1. Validate request body.
2. Find user by email.
3. Verify password.
4. Load roles.
5. Issue access token.
6. Issue refresh token.
7. Return token response.

### 11.6 Refresh Flow

```text
POST /api/v1/auth/refresh
```

Flow:

1. Validate refresh token.
2. Load user.
3. Confirm user is active.
4. Issue new access token.
5. Return new token response.

### 11.7 Logout Flow

```text
POST /api/v1/auth/logout
```

P0 logout behavior:

* Client deletes local tokens.
* Backend may invalidate refresh token if token persistence is implemented.

Do not introduce a separate session service unless already required by frozen API.

---

## 12. Authorization Implementation

### 12.1 Frozen Roles

The backend must support the frozen RBAC roles:

```text
farmer
ari_staff
farm_coordinator
agronomist
reviewer
admin
root
```

Do not create new roles in P1-1.

### 12.2 Permission Guards

Permission guards must be implemented as FastAPI dependencies.

Examples:

```text
require_authenticated_user
require_role(...)
require_any_role(...)
require_admin_or_root
require_farm_access
require_organization_access
require_owner_or_scoped_role
```

These are implementation guards only.

They do not create a new permission system.

### 12.3 Not Allowed

Do not create:

```text
Permission Service
Permission Matrix Engine
Policy Engine
Authorization Microservice
Separate RBAC Backend
Dedicated permission tables
Permission APIs
```

### 12.4 Organization Scope

Organization scope means:

* User may only access records belonging to organizations they are authorized for.
* Admin/root may have broader access based on frozen RBAC.
* Organization ID must be validated before farm/zone/tree operations.

### 12.5 Farm Scope

Farm scope means:

* Farm must belong to the requested organization if organization_id is present.
* Zone must belong to farm.
* Tree must belong to zone.
* Notebook entry farm_id/zone_id/tree_id must pass hierarchy validation when provided.

### 12.6 Ownership Scope

Ownership scope means:

* Users may access entries they created if allowed by role.
* Staff/reviewer/admin access depends on organization/farm scope.
* Backend must not expose records outside allowed scope.

### 12.7 Role Behavior

Minimum implementation expectation:

| Role             | Backend Access Pattern                                    |
| ---------------- | --------------------------------------------------------- |
| farmer           | Create and view own/farm-scoped notebook data             |
| ari_staff        | Support farm onboarding and review-related access         |
| farm_coordinator | Coordinate farm-level records                             |
| agronomist       | Review farm notebook and consultation-related data        |
| reviewer         | Review notebook filters/status and follow-up-related data |
| admin            | Manage users, organizations, and scoped platform records  |
| root             | Full system-level access                                  |

Do not expand this into a separate permission matrix service.

---

## 13. Module Implementation Standard

Each module must follow the same implementation pattern:

```text
Model
Schema
Repository
Service
Router
```

### 13.1 Model

SQLAlchemy ORM mapping for the frozen table.

### 13.2 Schema

Pydantic request/response models.

Recommended schema types:

```text
Create
Update
Read
List
Filter
```

### 13.3 Repository

Database CRUD and query methods.

### 13.4 Service

Business rules and validation.

### 13.5 Router

HTTP endpoint binding.

---

## 14. Required Modules

### 14.1 Organizations Module

Path:

```text
organizations
```

Responsibilities:

* Create organization
* Read organization
* List organizations within user scope
* Update organization
* Validate organization scope

Components:

```text
models/organization.py
schemas/organization.py
repositories/organizations.py
services/organization_service.py
api/v1/organizations.py
```

Required service rules:

* Only authorized roles may create/update organization.
* Organization ID must be validated for child records.
* Owner = Organization.
* Do not introduce Owner Registry as a new P1-1 table.
* Do not introduce Owner API.

---

### 14.2 Users Module

Path:

```text
users
```

Responsibilities:

* User profile
* User listing for admin/root
* User role assignment based on frozen user_roles table if it exists
* User active/inactive status if defined in frozen schema

Components:

```text
models/user.py
schemas/user.py
repositories/users.py
services/user_service.py
api/v1/users.py
```

Required service rules:

* User identity must come from JWT.
* Non-admin users must not access unauthorized profiles.
* Password hash must never be returned.

---

### 14.3 Farms Module

Path:

```text
farms
```

Responsibilities:

* Create farm
* Read farm
* List farms
* Update farm
* Validate farm belongs to organization
* Generate Farm QR payload if Optional QR endpoint is implemented

Components:

```text
models/farm.py
schemas/farm.py
repositories/farms.py
services/farm_service.py
api/v1/farms.py
```

Required service rules:

* farm.organization_id must be valid when present.
* Farm selector in mobile depends on this module.
* Simulator farm flag must be supported if frozen in schema.
* Farm QR is generated from farm_id as representation only.
* No Farm Registry table.
* No QR Registry table.

Optional QR endpoint:

```text
GET /api/v1/farms/{farm_id}/qr
```

Example payload:

```text
ari://farm/{farm_id}
```

---

### 14.4 Zones Module

Path:

```text
zones
```

Responsibilities:

* Create zone
* Read zone
* List zones by farm
* Update zone
* Validate zone belongs to farm
* Generate Zone QR payload if Optional QR endpoint is implemented

Components:

```text
models/zone.py
schemas/zone.py
repositories/zones.py
services/zone_service.py
api/v1/zones.py
```

Required service rules:

* zone.farm_id must exist.
* zone.farm_id must be accessible by current user scope.
* Block = Zone.
* Do not introduce Block Registry.
* Do not introduce Block API.
* Zone QR is generated from zone_id as representation only.

Optional QR endpoint:

```text
GET /api/v1/zones/{zone_id}/qr
```

Example payload:

```text
ari://zone/{zone_id}
```

---

### 14.5 Trees Module

Path:

```text
trees
```

Responsibilities:

* Create tree
* Read tree
* List trees by zone
* Update tree
* Validate tree belongs to zone
* Generate Tree QR payload if Optional QR endpoint is implemented

Components:

```text
models/tree.py
schemas/tree.py
repositories/trees.py
services/tree_service.py
api/v1/trees.py
```

Required service rules:

* tree.zone_id must exist.
* tree.zone_id must be accessible by current user scope.
* Tree registration may remain optional during P0 deployment.
* Tree QR is generated from tree_id as representation only.
* No Tree Registry table.
* No QR Registry table.

Optional QR endpoint:

```text
GET /api/v1/trees/{tree_id}/qr
```

Example payload:

```text
ari://tree/{tree_id}
```

---

### 14.6 Notebook Entries Module

Path:

```text
notebook_entries
```

Responsibilities:

* Create notebook entry
* Read notebook entry
* List notebook entries
* Search notebook entries
* Update entry status
* Filter by farm/zone/tree/date/type/status
* Support consultation entry context
* Support offline-created entries

Components:

```text
models/notebook_entry.py
schemas/notebook_entry.py
repositories/notebook_entries.py
services/notebook_service.py
api/v1/notebook_entries.py
```

Required service rules:

* Notebook Entry = Note Session.
* created_by_user_id must be current user.
* organization_id is required according to frozen Domain Model.
* farm_id, zone_id, tree_id may be nullable.
* created_at must store UTC.
* Device local time may be preserved in metadata if frozen schema supports it.
* If zone_id is provided, farm_id consistency must be validated.
* If tree_id is provided, zone_id/farm_id consistency must be validated.
* Save, upload, and analyze statuses must remain distinct.
* entry_context exists in the domain model but mobile P0 may not force manual selection.
* Consultation-specific fields are handled inside notebook entry logic.

---

### 14.7 Consultation Implementation Rule

Consultation is implemented as:

```text
Notebook Entry Type = consultation
```

Consultation is not a separate domain entity.

Do not create:

```text
models/consultation.py
schemas/consultation.py
repositories/consultations.py
services/consultation_service.py
api/v1/consultations.py
```

Consultation logic belongs inside:

```text
models/notebook_entry.py
schemas/notebook_entry.py
repositories/notebook_entries.py
services/notebook_service.py
api/v1/notebook_entries.py
```

Consultation-related fields must be handled as part of notebook entry logic:

```text
entry_type / entry_context = consultation
external_ai
ai_result_status
learned_summary
follow_up
outcome
```

---

### 14.8 Note Items Module

Path:

```text
note_items
```

Responsibilities:

* Create note item
* List note items by notebook entry
* Update file_ref after upload
* Preserve sequence_order
* Support photo/video/voice/text/file/link according to frozen enum

Components:

```text
models/note_item.py
schemas/note_item.py
repositories/note_items.py
services/note_item_service.py
api/v1/note_items.py
```

Required service rules:

* note_item.entry_id must exist.
* sequence_order must be unique or ordered per notebook entry according to frozen schema.
* item_type must match frozen enum.
* file_ref must point to MinIO object after upload.
* checksum should be used for duplicate detection if provided.
* link_url only allowed for link item type.

---

### 14.9 Follow Ups Module

Path:

```text
follow_ups
```

Responsibilities:

* Store consultation follow-up schedule
* List pending follow-ups
* Update outcome
* Support 3/7/14 day reminders according to frozen UX

Components:

```text
models/follow_up.py
schemas/follow_up.py
repositories/follow_ups.py
services/follow_up_service.py
api/v1/follow_ups.py
```

Required service rules:

* Follow-up must reference notebook entry or consultation entry according to frozen schema.
* Allowed outcome values:

```text
improved
same
worse
unknown
```

* Follow-up schedule must not introduce new workflow beyond frozen Ask AI Now flow.

---

### 14.10 Notifications Module

Path:

```text
notifications
```

Responsibilities:

* List user notifications
* Mark notification as read
* Support upload reminders
* Support follow-up reminders
* Support ARI reply notification if frozen API includes it

Components:

```text
models/notification.py
schemas/notification.py
repositories/notifications.py
services/notification_service.py
api/v1/notifications.py
```

Required service rules:

* User may only see own notifications unless admin/root.
* Notification is not an audit log.
* Do not introduce notification service as separate microservice.

---

### 14.11 Upload Queue Module

Path:

```text
upload_queue
```

Responsibilities:

* Track upload jobs
* Track local saved → pending upload → uploaded / failed
* Retry failed jobs
* Update upload status
* Support offline sync

Components:

```text
models/upload_job.py
schemas/upload_job.py
repositories/upload_jobs.py
services/upload_queue_service.py
api/v1/upload_queue.py
```

Required service rules:

* Upload job must reference user and target entity where applicable.
* Upload retry must be idempotent.
* Failed uploads must preserve error reason.
* Queue status must not be confused with notebook analysis status.

---

## 15. File Upload Implementation

### 15.1 Storage System

Use MinIO as object storage.

Database stores metadata and object references.

Media files are not stored in PostgreSQL.

### 15.2 Presigned Upload Flow

Required flow:

```text
Client requests upload URL
→ Backend validates user and target context
→ Backend generates object key
→ Backend creates or updates upload job
→ Backend returns presigned MinIO upload URL
→ Client uploads directly to MinIO
→ Client confirms upload
→ Backend validates metadata/checksum
→ Backend updates note_item.file_ref and upload_job status
```

### 15.3 Required Endpoints

```text
POST /api/v1/files/presign-upload
POST /api/v1/files/confirm-upload
GET  /api/v1/files/{file_id or object_key}/download-url
```

Endpoint names must align with frozen P0 API if names are already defined there.

### 15.4 Object Key Strategy

Object keys must be deterministic enough for organization and retrieval, but should avoid exposing sensitive user data.

Recommended pattern:

```text
organizations/{organization_id}/farms/{farm_id}/entries/{entry_id}/items/{note_item_id}/{uuid}.{ext}
```

If farm_id is nullable:

```text
organizations/{organization_id}/unscoped/entries/{entry_id}/items/{note_item_id}/{uuid}.{ext}
```

### 15.5 Upload Validation

Backend must validate:

* Authenticated user
* Target notebook entry access
* Target note item access
* Allowed item_type
* Allowed file extension if defined
* Declared content type
* Declared file size
* Checksum if provided

### 15.6 Media Retrieval

Media retrieval must use presigned download URLs.

Backend should not proxy large media files unless required later.

---

## 16. Offline Sync Implementation

### 16.1 Client ID

Offline-created records must use client-generated IDs where frozen API requires:

```text
client_id
```

The backend must support idempotent creation using client_id.

### 16.2 Sync Batch Endpoint

Required endpoint:

```text
POST /api/v1/sync/batch
```

Responsibilities:

* Receive multiple local operations
* Validate each operation
* Apply operations safely
* Return per-item result
* Preserve idempotency

### 16.3 Idempotency Strategy

Idempotency must use:

```text
user_id + client_id
```

or equivalent frozen API rule.

If the same client_id is submitted again:

* Return existing server record.
* Do not duplicate notebook entry, note item, or upload job.

### 16.4 Conflict Handling

P0 conflict handling must be simple.

Rules:

* Server ID wins for already-synced records.
* Duplicate client_id returns existing record.
* Invalid hierarchy returns 409 or 422 depending on case.
* Records outside user scope return 403.
* Missing referenced record returns 404.
* Backend must not silently overwrite another user's data.

### 16.5 Retry Logic

Retry behavior:

* Client may retry failed sync items.
* Backend must be idempotent.
* Upload queue tracks failed upload attempts.
* Retry count may be stored if frozen schema supports it.

### 16.6 Queue Processing

P0 queue processing may be request-driven.

No separate background worker is required for P1-1.

Optional Extension:

* Background queue worker for cleanup, retry, and media validation.

---

## 17. Validation Strategy

### 17.1 Pydantic Models

Use Pydantic models for:

* Request validation
* Response serialization
* Enum validation
* UUID parsing
* Optional field rules
* Nested sync payload validation

### 17.2 UUID Validation

All IDs must be validated as UUID where frozen schema uses UUID.

Invalid UUID:

```text
422 Unprocessable Entity
```

### 17.3 Enum Validation

Enums must match frozen P0 schema exactly.

Examples:

```text
entry_context
entry_type
source_type
item_type
external_ai
status
follow_up
outcome
role
```

Invalid enum:

```text
422 Unprocessable Entity
```

### 17.4 Hierarchy Validation

The backend must validate:

```text
Organization
→ Farm
→ Zone
→ Tree
```

Rules:

* Farm must belong to organization.
* Zone must belong to farm.
* Tree must belong to zone.
* Notebook entry may have nullable farm/zone/tree.
* If lower-level entity is provided, parent consistency must be verified.

Example:

```text
tree_id provided
→ tree.zone_id must match provided zone_id if zone_id exists
→ tree.zone.farm_id must match provided farm_id if farm_id exists
```

### 17.5 Consultation Validation

Consultation-specific validation:

* entry_type = consultation identifies consultation.
* Consultation is not a separate entity.
* external_ai may be required if frozen API requires it.
* learned_summary may be nullable until AI result is received.
* follow_up values must be frozen enum only.
* outcome must be frozen enum only.

---

## 18. Error Handling Strategy

Use consistent JSON error responses.

Recommended format:

```json
{
  "error": {
    "code": "RESOURCE_NOT_FOUND",
    "message": "Notebook entry not found",
    "details": {}
  }
}
```

### 18.1 400 Bad Request

Use when:

* Request is syntactically valid but semantically invalid
* Invalid state transition
* Unsupported upload confirmation state

### 18.2 401 Unauthorized

Use when:

* Missing token
* Invalid token
* Expired token
* Invalid refresh token

### 18.3 403 Forbidden

Use when:

* Authenticated user lacks role
* User lacks organization scope
* User lacks farm scope
* User tries to access another user's private record

### 18.4 404 Not Found

Use when:

* Entity does not exist
* Entity is outside allowed visibility and should not be disclosed

### 18.5 409 Conflict

Use when:

* Duplicate unique value
* Idempotency conflict
* Hierarchy conflict
* Upload already confirmed
* Record state conflict

### 18.6 422 Unprocessable Entity

Use when:

* Pydantic validation fails
* UUID invalid
* Enum invalid
* Required field missing
* Data type invalid

### 18.7 500 Internal Server Error

Use when:

* Unexpected server failure
* Database unavailable
* MinIO unavailable
* Unhandled exception

500 responses must not expose secrets or stack traces.

---

## 19. Logging Strategy

Do not introduce an audit_logs table.

Logging must use application logs.

### 19.1 Application Logs

Capture:

* Startup
* Shutdown
* Configuration environment
* Health check failures
* Unexpected exceptions

### 19.2 API Logs

Capture:

* Request ID
* Method
* Path
* Status code
* Latency
* User ID if authenticated
* Error code if failed

Do not log passwords, tokens, or sensitive media URLs.

### 19.3 Upload Logs

Capture:

* Upload job ID
* Note item ID
* Object key
* Upload status
* Failure reason
* Retry count if available

### 19.4 Sync Logs

Capture:

* Sync batch ID if provided
* User ID
* Number of items
* Success count
* Failure count
* Conflict count

### 19.5 Authentication Logs

Capture:

* Login success/failure
* Refresh success/failure
* Logout request
* User ID if known
* Email may be masked

---

## 20. Configuration Management

### 20.1 Environment Files

Use:

```text
.env
.env.local
.env.dev
.env.staging
.env.production
```

Do not commit real secrets.

### 20.2 Settings Class

Use a centralized settings class:

```text
app/core/config.py
```

Settings groups:

* App settings
* Database settings
* JWT settings
* MinIO settings
* EMQX settings
* CORS settings
* Logging settings

### 20.3 Required Environment Variables

```text
APP_ENV
APP_NAME
API_V1_PREFIX

DATABASE_URL

JWT_SECRET_KEY
JWT_ALGORITHM
ACCESS_TOKEN_EXPIRE_MINUTES
REFRESH_TOKEN_EXPIRE_DAYS

MINIO_ENDPOINT
MINIO_ACCESS_KEY
MINIO_SECRET_KEY
MINIO_BUCKET
MINIO_SECURE

MQTT_HOST
MQTT_PORT
MQTT_USERNAME
MQTT_PASSWORD

CORS_ALLOWED_ORIGINS
LOG_LEVEL
```

### 20.4 Environment Separation

```text
local
dev
staging
production
```

Rules:

* local: docker-compose development
* dev: shared development server
* staging: production-like testing
* production: live deployment

Production rules:

* No debug mode
* Strong JWT secret
* Restricted CORS
* No stack traces in API response
* Secrets provided by deployment environment

---

## 21. EMQX MQTT Integration

EMQX is part of the frozen stack.

For P1-1 backend:

* MQTT integration is limited to publishing backend events if frozen API requires.
* Do not build robot services.
* Do not build agent orchestration.
* Do not create microservice messaging architecture.

Allowed P0-compatible events:

```text
upload.completed
sync.completed
notification.created
```

Optional Extension:

* MQTT subscriber for internal backend events.

---

## 22. Docker Implementation

### 22.1 Dockerfile

Backend Dockerfile must support:

* Python 3.12+
* FastAPI app
* Dependency installation
* Uvicorn runtime
* Environment variable configuration

Runtime command:

```text
uvicorn app.main:app --host 0.0.0.0 --port 8000
```

### 22.2 docker-compose

Local docker-compose must include:

```text
FastAPI
PostgreSQL
MinIO
EMQX
```

Recommended services:

```text
api
postgres
minio
emqx
```

Optional local services:

```text
pgadmin
minio-console
```

### 22.3 Docker Compose Rules

* Use one backend container.
* Use one PostgreSQL database.
* Use MinIO for object storage.
* Use EMQX for MQTT.
* Do not split backend into microservices.
* Volumes must persist database and MinIO data.

---

## 23. Testing Strategy

Use:

```text
pytest
```

### 23.1 Unit Tests

Test:

* Utility functions
* JWT creation/validation
* Password hashing
* Object key generation
* QR payload generation if optional QR endpoint is implemented
* Validation helpers
* Scope guards

### 23.2 Repository Tests

Test:

* Create/read/update operations
* Filters
* Pagination
* Unique constraints
* Nullable FK behavior
* Hierarchy lookup queries

Repository tests must not include qr_registry, consultation, owner, block, review, knowledge, audit_logs, or permissions tables.

### 23.3 Service Tests

Test:

* Organization scope validation
* Farm/zone/tree hierarchy validation
* Notebook entry creation
* Note item ordering
* Consultation as notebook entry type
* Upload confirmation
* Sync idempotency
* Conflict handling

### 23.4 API Tests

Test:

* Auth login
* Auth refresh
* RBAC restrictions
* CRUD endpoints
* File presign endpoint
* Sync batch endpoint
* Optional QR endpoints if implemented
* Error response format

### 23.5 Integration Tests

Test with real containers or test database:

* PostgreSQL connection
* Alembic migration
* MinIO presigned upload flow
* Full notebook entry + note item + upload flow
* Offline sync batch flow

---

## 24. Implementation Order

Recommended backend implementation order:

1. Project skeleton
2. Configuration
3. Database session
4. SQLAlchemy models
5. Alembic initial migration
6. Core enums
7. Error handling
8. Auth service
9. RBAC dependencies
10. Organizations
11. Users
12. Farms
13. Zones
14. Trees
15. Notebook entries
16. Note items
17. File upload / MinIO
18. Upload queue
19. Sync batch
20. Follow-ups
21. Notifications
22. Tests
23. Docker compose validation

Optional QR endpoints may be implemented after core farm/zone/tree endpoints are stable and must not introduce a QR table/entity.

---

## 25. QR / ID Implementation Rule

P0 supports:

```text
Farm QR
Zone QR
Tree QR
```

QR is:

```text
Representation
```

not:

```text
Separate Entity
```

Therefore P1-1 must not create:

```text
qr_registry table
models/qr_registry.py
schemas/qr_registry.py
repositories/qr_registry.py
services/qr_registry_service.py
api/v1/qr_registry.py
```

QR payloads are generated from existing entity IDs:

```text
ari://farm/{farm_id}
ari://zone/{zone_id}
ari://tree/{tree_id}
```

Optional endpoints:

```text
GET /api/v1/farms/{farm_id}/qr
GET /api/v1/zones/{zone_id}/qr
GET /api/v1/trees/{tree_id}/qr
```

Example response:

```json
{
  "entity_type": "tree",
  "entity_id": "uuid",
  "qr_payload": "ari://tree/{tree_id}"
}
```

No QR persistence is required in P1-1.

---

## 26. P1-1 Required Checklist

Before backend coding starts, confirm:

* [ ] Backend folder structure approved
* [ ] `__init__.py` files included in Python packages
* [ ] FastAPI layering approved
* [ ] SQLAlchemy model mapping matches frozen DB schema
* [ ] No qr_registry table/module/service/router
* [ ] QR confirmed as representation only
* [ ] Consultation confirmed as Notebook Entry Type only
* [ ] No separate consultation entity/module/service/router
* [ ] RBAC implemented only as FastAPI dependency guards
* [ ] No Permission Service or policy engine introduced
* [ ] Alembic migration strategy approved
* [ ] JWT flow approved
* [ ] Organization/farm/tree scope rules approved
* [ ] MinIO presigned upload flow approved
* [ ] Offline sync idempotency approved
* [ ] Error response format approved
* [ ] Logging scope approved
* [ ] Docker compose stack approved
* [ ] Test categories approved

---

## 27. Non-Goals

P1-1 must not implement or define:

* New domain model
* New database architecture
* New API design
* New RBAC system
* Microservices
* Knowledge graph
* Vector database
* RAG
* Agent orchestration
* Commerce service
* Robot service
* Audit log table
* Permission service
* Consultation entity
* QR Registry as required module
* Owner Registry
* Block Registry
* Review table
* Knowledge table
* Compliance automation
* Export system
* Irrigation/fertilizer automation

---

## 28. Freeze Boundary

When approved, this document becomes the implementation guide for the P0 backend.

Any change that affects:

* Domain model
* Database schema
* API contract
* RBAC roles
* Architecture
* Service boundaries

must go through a formal revision process and must not be silently introduced during coding.

---

## 29. Final Statement

ARI V1 — P1-1 Backend Implementation Specification v1.0 defines how to implement the frozen P0 backend using FastAPI, PostgreSQL/TimescaleDB, MinIO, EMQX, JWT, Docker, and GitHub Monorepo.

It preserves:

* One Platform
* One Backend
* One Database Architecture
* One Mobile App
* One Web App
* One Domain Model
* One RBAC System

It implements only:

* Capture
* Store
* Search
* Consultation Tracking as Notebook Entry Type
* Follow-Up Tracking
* Notifications
* File Upload
* Offline Sync
* RBAC Scope

It does not redesign ARI.



******************************
0k, Freeze now
******************************

รับทราบครับ

ARI V1 — P1-1 Backend Implementation Specification v1.0
Status: FROZEN

Freeze Decision Recorded:

Project: ARI — Agricultural Intelligence Platform
Document: ARI V1 — P1-1 Backend Implementation Specification v1.0
Status: FROZEN
Freeze Scope: FastAPI Backend Implementation Specification
Freeze Authority: Project Owner Confirmed
Frozen Scope

P1-1 now becomes the implementation guide for:

FastAPI Backend
PostgreSQL / TimescaleDB
SQLAlchemy / Alembic
MinIO Upload Flow
JWT Authentication
RBAC Dependency Guards
Offline Sync
Upload Queue
Notifications
Follow-ups
Notebook Entries
Note Items
Farm / Zone / Tree Structure
Docker Backend Stack
pytest Testing Strategy
Frozen Corrections Included
QR = Representation, not Entity
No qr_registry table/module/service/router
Consultation = Notebook Entry Type
No consultation entity/module/service/router
RBAC = FastAPI Dependency Guards
No Permission Service
__init__.py included in Python packages
organization_id required
No unscoped user object-key fallback
Change Control

After this freeze:

No backend redesign
No database redesign
No API redesign
No new core entity
No new permission system
No microservice split

unless processed through:

Revision Proposal
→ Review
→ Approval
→ New Version
Next Recommended Document
ARI V1 — P1-2 Mobile App Implementation Specification v1.0

Purpose:

Translate #46A Mobile UX + P0 API + P1-1 Backend Spec
into Flutter Mobile App Implementation Specification

P1-1 Freeze complete.


*************************
2026-06-18
************************

Revision Note — ARI V1 P0 API Specification v1.0
1. Revision Purpose

This revision note records required API changes caused by Owner-approved P1-2 mobile onboarding decisions.

This note does not replace the full P0 API Specification.

This note identifies additive API changes that must be merged into the P0 API Specification before P1-2 Freeze or before mobile coding starts.

2. Revision Scope

This revision affects:

Authentication API
User API
Organization assignment
Farm API
Farm join / membership status
Farm location payload

This revision must not affect:

Notebook Entry API structure
Note Item API structure
Consultation as Notebook Entry Type
QR as representation
MinIO upload endpoints
Sync batch endpoint
Notification API
Follow-up API
3. New / Revised Authentication API
3.1 Register

Add:

POST /api/v1/auth/register

Purpose:

Allow new mobile users to self-register from Android/iOS app.

Request:

{
  "phone": "0812345678",
  "name": "Somchai",
  "password": "1234",
  "farmer_status": "owner",
  "farm_id": null
}

For Owner's Family / Farm Staff:

{
  "phone": "0812345678",
  "name": "Worker Name",
  "password": "1234",
  "farmer_status": "farm_staff",
  "farm_id": "ARI-FARM-A123"
}

Allowed farmer_status values:

owner
owner_family
farm_staff

Rules:

Registration requires internet.
Phone number must be unique.
Phone number must be normalized before storage.
Password must be stored only as password_hash.
Default password 1234 is allowed only for P0 pilot.
role must be assigned as farmer.
3.2 Register Response

For owner:

{
  "user_id": "uuid",
  "phone": "0812345678",
  "role": "farmer",
  "farmer_status": "owner",
  "organization_id": "uuid",
  "account_status": "active_pending_verification",
  "access_token": "jwt",
  "refresh_token": "jwt"
}

For owner_family / farm_staff:

{
  "user_id": "uuid",
  "phone": "0812345678",
  "role": "farmer",
  "farmer_status": "farm_staff",
  "organization_id": "uuid",
  "primary_farm_id": "ARI-FARM-A123",
  "membership_status": "pending_farm_approval",
  "access_token": "jwt",
  "refresh_token": "jwt"
}

If backend chooses not to return tokens after registration, it must return a clear response requiring login.

3.3 Login

Existing login must be revised to accept phone number.

POST /api/v1/auth/login

Request:

{
  "phone": "0812345678",
  "password": "1234"
}

Response:

{
  "access_token": "jwt",
  "refresh_token": "jwt",
  "token_type": "bearer"
}

Rules:

Login by email may remain supported if already implemented.
Phone-number login is required for P1-2 mobile.
Backend must look up user by normalized phone.
Backend must verify password_hash.
3.4 Current User
GET /api/v1/auth/me

Response must include:

{
  "user_id": "uuid",
  "phone": "0812345678",
  "name": "Somchai",
  "role": "farmer",
  "farmer_status": "owner",
  "organization_id": "uuid",
  "primary_farm_id": null,
  "membership_status": "active",
  "account_status": "active"
}
4. User Model API Additions

The user API must support or expose:

phone
farmer_status
membership_status
primary_farm_id
account_status

Recommended additive fields:

users.phone unique
users.farmer_status nullable
users.membership_status nullable
users.primary_farm_id nullable
users.account_status

This is an additive change.

Do not create:

member_registry
owner_registry
farmer_registry
separate mobile_user table
permission table
5. Owner Registration Behavior

When farmer_status = owner:

Backend creates user_id.
Backend assigns role = farmer.
Backend creates or assigns organization_id immediately.
Backend returns organization_id.
Backend allows owner to create Farm under own organization.
Account may be marked active_pending_verification or pending_review.
Admin may later suspend/revoke if false registration is detected.

Owner may have multiple farms:

organization_id
  ├── farm_id_1
  ├── farm_id_2
  └── farm_id_3
6. Owner's Family / Farm Staff Registration Behavior

When farmer_status = owner_family or farm_staff:

farm_id is required.
Backend validates Farm ID exists.
Backend resolves farm_id → organization_id.
Backend creates user_id.
Backend assigns role = farmer.
Backend sets primary_farm_id = provided farm_id.
Backend sets membership_status = pending_farm_approval.
User must not be able to create Farm/Zone/Tree.

Required pending message:

ส่งคำขอเข้าร่วมสวนแล้ว
กรุณารอเจ้าของสวนหรือผู้ดูแลระบบอนุมัติ
7. Membership Status

Allowed values:

pending_farm_approval
active
rejected
suspended
revoked

Behavior:

pending_farm_approval:
  user registered but not yet approved for farm access

active:
  user can access approved farm scope

rejected:
  join request rejected

suspended:
  access temporarily blocked

revoked:
  access removed
8. Farm API Revision

Existing Farm API must allow self-registered owner to create farm under own organization.

POST /api/v1/farms

Required request:

{
  "farm_name": "สวนทุเรียนคลองสิบ",
  "location": {
    "province": "จันทบุรี",
    "district": "ท่าใหม่",
    "subdistrict": "เขาบายศรี",
    "address": "ใกล้วัด เข้าซอย 2 กม.",
    "gps_latitude": 12.345678,
    "gps_longitude": 102.345678,
    "source": "device_gps"
  },
  "description": "สวนหลักของครอบครัว"
}

Only farm_name is required from user in P1-2.

System-generated:

farm_id
farm_code
organization_id
created_by_user_id
status
created_at

Owner must not manually provide:

farm_id
organization_id
created_by_user_id
status
9. Farm Location Storage

Backend must choose and document one approved strategy.

Recommended:

farms.location = structured JSON/object

Supported structure:

{
  "province": "จันทบุรี",
  "district": "ท่าใหม่",
  "subdistrict": "เขาบายศรี",
  "address": "ใกล้วัด เข้าซอย 2 กม.",
  "gps_latitude": 12.345678,
  "gps_longitude": 102.345678,
  "source": "device_gps"
}

Alternative:

If farms.location is text only, mobile may serialize location summary into location/description only if explicitly approved.
10. Farm Join Approval

P1-2 minimal policy:

Admin / ARI Staff handles approval through backend/admin workflow.
Owner self-approval screen is Future Enhancement.

No P1-2 requirement for:

Owner-managed member approval screen
Invite code
farm_memberships table
multi-farm membership management
11. P0 API Non-Changes

Do not change:

Consultation = Notebook Entry Type
QR = Representation only
No qr_registry
No consultation entity
No permission service
Upload endpoints:
  POST /api/v1/files/upload-url
  POST /api/v1/files/complete
Sync endpoint:
  POST /api/v1/sync/batch
Follow-up periods:
  3 / 7 / 14 days
Outcome values:
  improved / same / worse / unknown
Search:
  keyword/filter search only