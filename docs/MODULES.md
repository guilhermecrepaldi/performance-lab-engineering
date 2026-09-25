# Module map

This is a public map of responsibilities, not a feature-availability or API specification. Individual areas have different levels of maturity. The [website](https://performancelab.dev/) is the current place to check the public pilot offering.

| Area | Responsibility | Technical shape | Typical relationship |
| --- | --- | --- | --- |
| Platform core | Tenant, access and workspace context | Shared API and web foundations | Governs what other areas may expose. |
| Conversations & Interview | Guided interactions and interview journeys | Web workflows and backend records | Connects interaction context to authorized clients, tasks and follow-up. |
| Telemetry | Operational signals from enrolled Windows machines | Windows agent, ingestion and analysis surfaces | Produces limited context for authorized attention views. |
| Sales / CRM & Clients | Commercial activity and client context | Domain records, API and web views | Links follow-up, conversations, agenda and other permitted context. |
| Tasks, Agenda & Attention | Work, time and prioritized signals | Domain workflows and composed views | Helps a user move from a signal to a responsible action. |
| Product & Inventory | Item identity and physical stock | Catalog and stock domain services | Supports commercial and purchasing journeys without duplicating stock ownership. |
| Purchasing, Finance & Fiscal | Procurement and operational financial/fiscal context | Domain services and regional adapters | Exchanges approved business facts across domain boundaries. |
| Connections & external channels | Provider communication | Adapters and integration contracts | Separates external transport from domain ownership. |
| X-Ray & Logistics | Assisted onboarding and operational movement | Guided workflows and domain-specific records | Connects imported or movement context to its responsible module. |

## How a module is developed

1. Define the **owner** of each fact and state transition.
2. Describe the **user journey**: entry, decision, feedback, error and recovery.
3. Separate **tenant access**, **person's permission** and **scope of visible resources**.
4. Specify **incoming and outgoing contracts** without copying another module's storage model.
5. Identify **failure behavior**, observability and evidence needed for release.
6. Mark the implementation stage explicitly: concept, foundation, pilot or validated operation.

This is the organization principle, not a source-code template or a statement that every historical component already complies with it.
