# Architecture, at a public level

KNOTEN's backend is a .NET 8 modular monolith. React and TypeScript provide the web experience; PostgreSQL stores tenant-scoped application data. A Windows agent sends operational telemetry to backend surfaces. Integrations with external services are represented through adapters and domain boundaries.

## Boundaries

1. **Platform core** resolves identity, tenant, module availability and authorization context.
2. **Domain modules** own their records and transitions. Other modules request a limited view or a permitted operation rather than writing another domain's facts directly.
3. **Experience layer** composes authorized information around the person's task. It should reveal why an item appeared and where the user can act.
4. **External adapters** isolate provider-specific communication from the domain's business concepts.

An effective view depends on the intersection of tenant availability, user capability, organizational scope and, where relevant, assignment to a resource. This is an architectural rule, not a claim that every older path has already completed migration to the same enforcement mechanism.

## Example: contextual attention

A module can identify an operational condition. A cross-module experience may show a short, authorized explanation and a link to the responsible domain. The owning module remains responsible for the underlying fact and action. Missing permission, stale data and unavailable providers should appear as distinct states, rather than as an invented result.

## Stack and organization

| Area | Technology / approach | Role |
| --- | --- | --- |
| API | .NET 8, C# | Request handling and domain composition. |
| Web | React 18, TypeScript, Vite | Workspace and module interfaces. |
| Persistence | PostgreSQL 16, EF Core | Tenant-scoped data and migrations. |
| Telemetry | Windows agent | Collection and delivery of permitted machine signals. |
| Operations | Cloud deployment and monitoring tooling | Build, deploy and runtime observation. |

The active codebase contains both extracted module boundaries and older routes. Consolidating those paths is ongoing; this overview does not imply a complete separation into independent services, a durable distributed event bus or universal enforcement across every legacy route.

## Design review questions

- Which module owns this fact and which modules need an authorized projection?
- How does the user know whether information is current, missing or unavailable?
- What happens if an entitlement changes after data has already been created?
- Can the journey be completed without making the user understand internal service boundaries?
- What evidence proves a behavior in source, tests, a candidate deployment and production?

The private product and security documentation provides the detailed answers. This page records the public engineering model.
