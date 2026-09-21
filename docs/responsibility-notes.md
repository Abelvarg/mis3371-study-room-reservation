# Responsibility Matrix — Study Room Reservation

| Responsibility | Presentation | Application Logic | Data |
|---|---|---|---|
| Collect input | **Primary** | Receives input | — |
| Immediate feedback | **Primary** | May return validation result | — |
| Critical validation | Basic format checks | **Primary / authoritative** | May enforce structural constraints |
| Business rules | — | **Primary / authoritative** | Supports with persisted data |
| State transition | Displays state | **Primary / authoritative** | Persists resulting state |
| Generate transaction ID | — | **Primary** | Stores ID |
| Persist official record | — | Coordinates save | **Primary** |
| Audit / history | Displays when needed | Supplies event context | **Primary preservation** |
| Display response | **Primary** | Produces outcome/message data | — |

## Short Responsibility Notes

- **Presentation** handles user interaction, immediate feedback, and displaying transaction outcomes.
- **Application logic** owns critical validation, business rules, and legal state transitions.
- **Data** owns the official persistent reservation record and audit/history preservation.
- A rule is not considered safely enforced just because it appears in the presentation tier; critical rules are rechecked by application logic.
