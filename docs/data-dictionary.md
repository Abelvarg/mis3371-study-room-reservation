# Data Dictionary — Study Room Reservation

| Field | Meaning | Type | Req? | Source | Rule / Constraint | Example |
|---|---|---|---|---|---|---|
| reservation_id | Stable identifier for the reservation transaction | String / UUID | Yes | System-assigned | Unique, immutable, and assigned when the request becomes Submitted | RSV-10482 |
| student_id | Identifier for the student making the reservation | String | Yes | Derived / reference | Supplied by an existing authorized-student context; campus-login integration is outside scope | 2145678 |
| room_id | Identifier for selected study room | String | Yes at confirmation | User selection | Must reference a valid room | SR-204 |
| reservation_date | Date of reservation | Date | Yes | User-entered | Cannot be blank at confirmation | 2026-09-25 |
| start_time | Reservation start time | Time | Yes | User-entered | Must be before end_time | 14:00 |
| end_time | Reservation end time | Time | Yes | User-entered | Must be after start_time | 15:30 |
| duration_minutes | Length of reservation | Integer | Yes | Derived | end_time minus start_time | 90 |
| status | Current transaction state | Enum / String | Yes | System-assigned | Submitted, Confirmed, Rejected, Cancelled, or Completed | Confirmed |
| created_at | When the official Submitted transaction was created | Timestamp | Yes | System-assigned | Set once when the reservation ID is generated | 2026-09-20 20:15 |
| updated_at | Most recent transaction update time | Timestamp | Yes | System-assigned | Updated on each persisted change | 2026-09-20 20:18 |
| confirmed_at | When reservation entered Confirmed state | Timestamp | Conditional | System-assigned | Required when status = Confirmed | 2026-09-20 20:18 |
| cancelled_at | When reservation entered Cancelled state | Timestamp | Conditional | System-assigned | Required when status = Cancelled | 2026-09-21 09:12 |
| rejected_at | When the reservation entered Rejected state | Timestamp | Conditional | System-assigned | Required when status = Rejected | 2026-09-20 20:18 |
| rejection_reason | Explanation of the authoritative rule that failed | Text | Conditional | Application-assigned | Required when status = Rejected | Requested room is no longer available |
| party_size | Number of students expected | Integer | Yes | User-entered | Must be positive and within room capacity | 4 |
| room_capacity | Maximum room occupancy | Integer | Yes | Derived / reference | Retrieved from the selected room record and must be >= party_size | 6 |
| availability_result | Result of availability validation | Boolean | Yes before confirmation | Derived | Must be true to confirm | true |
| last_modified_by | Actor responsible for latest persisted change | String | Yes | System-assigned | Student/system identifier | student:2145678 |

## Authoritative Application-Tier Business Rule
A reservation may enter **Confirmed** only if the selected room is still available for the entire requested time interval and the request satisfies overlap, capacity, and time rules. Otherwise, the official Submitted transaction must enter **Rejected** with a rejection reason.

## Audit Requirement
The system must preserve the reservation ID, state/status changes, rejection reason when applicable, timestamps, and the actor responsible for persisted changes so transaction history can be reconstructed.
