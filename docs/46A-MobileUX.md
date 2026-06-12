# Context-Aware Note Capture

## Frozen Decision

ARI P0 shall support context-aware data capture using:

* Farm QR / Farm ID
* Zone QR / Zone ID
* Tree QR / Tree ID

---

## User Experience Principle

QR / ID assignment is:

### Optional

but

### Recommended

Users shall be able to create:

* Notes
* Ask AI Sessions
* Reminders
* Follow-up Records

without QR scanning.

---

## Capture Priority

The system shall prioritize the following order:

### 1. Capture Data

Capture the information as quickly and naturally as possible.

### 2. Attach Context

Attach Farm, Zone, Tree, or other contextual references when available.

### 3. Validate Later

Additional validation and enrichment may occur later if necessary.

---

## Design Principle

The system shall prioritize:

> Ease of Capture
> over
> Strict Data Entry Requirements

The objective of P0 is maximizing real-world data collection while minimizing user friction.

---

## Supported Context Sources

### Explicit Context

User explicitly provides context through:

* QR Scan
* ID Selection

### Implicit Context

The system may infer context from:

* Current Farm
* Current Zone
* Current Tree
* GPS Location
* Previous Activity
* User Context

Implicit context shall not be treated as confirmed context unless validated.

---

## Active Context

The mobile application may maintain:

* Current Farm
* Current Zone
* Current Tree

as the active working context.

Users may continue creating multiple records within the active context without re-scanning QR codes for every operation.

Users shall be able to:

* Change Context
* Clear Context
* Scan New Context

at any time.

---

## QR / ID Workflow

### Optional Context Assignment

When creating a new record, users may:

#### Option A — Scan QR

Farm QR

↓

Zone QR

↓

Tree QR

↓

Create Record

#### Option B — Select ID

Farm

↓

Zone

↓

Tree

↓

Create Record

#### Option C — No Context

Create Record

↓

Save Record

↓

Attach Context Later (Optional)

---

## Supported Record Types

Context references may be attached to:

* Ask AI Sessions
* Notebook Records
* Photos
* Videos
* Voice Notes
* Text Notes
* Reminders
* Follow-up Records
* Evidence Records
* Sensor Readings
* Future AI Insights

---

## Future Digital Twin Integration

Context linkage enables:

* Digital Twin Integration
* Evidence Management
* Knowledge Generation
* Traceability
* Compliance Workflows
* Commerce Workflows
* Fruit Identity Integration
* Harvest Intelligence
* Farm AIOS Integration

---

## Strategic Objective

The Digital Farm Notebook shall be designed so that every captured memory can be linked to the correct Farm, Zone, and Tree context whenever practical, while preserving a low-friction user experience.

The primary objective is ensuring that valuable field knowledge is captured first and enriched with contextual references whenever available.
