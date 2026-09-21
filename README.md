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

1. A student must be authenticated before confirming a reservation.
2. A room cannot be double-booked for an overlapping time slot.
3. A reservation may be cancelled before its scheduled start time.
4. A temporary room/time selection can expire if confirmation is not completed.
5. Application logic is authoritative for critical validation, business rules, and state transitions.
6. The data tier preserves the official transaction and audit record.
