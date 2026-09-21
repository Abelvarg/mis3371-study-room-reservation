# MIS 3371 — Study Room Reservation System

This repository contains design artifacts for the MIS 3371 Transaction Processing Systems I capstone project.

## Project
**Study Room Reservation System**

The system models a student reserving a study room for a specific date and time.

## Week 3 Design Artifacts
The Week 3 design files are in the `docs` folder:

- [Transaction Workflow](docs/workflow-v1.md)
- [State Transition Model + State Definitions](docs/state-model-v1.md)
- [Data Dictionary](docs/data-dictionary.md)
- [Three-Tier Architecture](docs/architecture-v1.md)
- [Responsibility Notes](docs/responsibility-notes.md)

## Repository Structure

```text
/
├── README.md
└── docs/
    ├── workflow-v1.md
    ├── state-model-v1.md
    ├── data-dictionary.md
    ├── architecture-v1.md
    └── responsibility-notes.md
```

## Week 3 Requirements Covered
- Clear transaction trigger and outcome
- 5–8 meaningful workflow actions
- At least 2 decision points
- At least 1 exception/failure path
- 4–6 transaction states
- Allowed state transitions
- Data dictionary with meaningful fields
- Stable transaction ID and status
- At least two timestamps
- Three-tier architecture
- Application-tier business rules
- Audit/history responsibility
- Official persistent record in the data tier

## Project Assumptions
The Week 3 activity defines the design requirements but does not specify detailed business rules for this project. The following are team design assumptions:

1. Campus-login integration is outside the project scope; the reservation workflow assumes an authorized student identifier is already available when the transaction begins.
2. A room cannot be double-booked for an overlapping time slot.
3. A reservation request becomes an official transaction when submitted, at which point it receives a stable reservation ID and `Submitted` status.
4. A submitted request becomes either `Confirmed` or `Rejected`; every rejected request preserves a rejection reason.
5. A confirmed reservation may be cancelled before its scheduled start time.
6. Application logic is authoritative for critical validation, business rules, and state transitions.
7. The data tier preserves the official transaction, status, rejection reason, timestamps, and audit record.
