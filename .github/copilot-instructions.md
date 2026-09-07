# Ward Allocation — Copilot Instructions

## Project background

This project, `ward-allocation`, was created as a copy of the earlier `room-reservation` project.

`room-reservation` is the original prototype and should be treated as a reference implementation only. It is not the active project and must not be modified as part of work on `ward-allocation`.

`ward-allocation` is an independent project that will evolve from the prototype toward a simple application for allocating clients/patients to hospital wards/rooms over intervals of dates.

## Current architecture

The current application is a small client-side single-page application:

- `index.html` — UI structure
- `app.js` — application state, event handling, validation, rendering, and Supabase calls
- `style.css` — custom styling
- Bootstrap 5.3.3 — loaded from CDN
- Supabase JavaScript v2 — loaded from CDN

There is currently no Node.js server, Express application, EJS rendering, build system, npm package configuration, or local database layer.

Do not introduce these technologies merely because they were considered for the project. Use the existing architecture unless a task explicitly requires an architectural change.

## Current database model

The current prototype uses these Supabase/PostgreSQL tables:

- `rooms`
  - `id`
  - `name`
  - `description`

- `clients`
  - `id`
  - `name`
  - `description`

- `reservations`
  - `id`
  - `room_id`
  - `client_id`
  - `date_from`
  - `date_to`

The reservation queries use Supabase relationships to retrieve related room and client names.

## Important business behavior

Reservations must not overlap for the same room.

The current overlap test is:

`dateFrom < existing.date_to && dateTo > existing.date_from`

Therefore, a reservation ending on the same date/time at which another reservation begins is currently considered non-overlapping.

Before changing reservation behavior, understand and preserve this rule unless the task explicitly changes it.

## Development principles

- Keep the application simple.
- Prefer small, understandable changes.
- Reuse and improve the existing code where appropriate.
- Do not introduce unnecessary frameworks, libraries, abstractions, or infrastructure.
- Do not rewrite working parts without a concrete reason.
- Inspect the existing implementation before making changes.
- Preserve existing functionality unless the task explicitly changes it.
- For significant changes, explain the proposed approach before implementing it.
- Keep business logic reasonably separate from UI manipulation where practical.

## Supabase

`ward-allocation` has its own Supabase project/database.

Never reconnect the application to the old `room-reservation` Supabase project.

Never hard-code Supabase credentials into new code.

Use the project's configuration mechanism for the Supabase URL and key.

## Relationship to room-reservation

The old `room-reservation` project may be consulted to understand the original implementation and its design decisions.

However, `ward-allocation` is an independent project.

When the requirements of `ward-allocation` differ from the old prototype, implement the new requirements rather than preserving the old behavior merely for compatibility.

## Domain evolution

The current implementation still uses the concepts:

- rooms
- clients
- reservations

The target domain is hospital ward allocation.

Do not rename or restructure the existing domain model automatically. Make domain changes deliberately as requirements are established.

## Security and robustness

Be aware of the following existing limitations:

- Authentication and authorization are not currently implemented.
- Reservation conflict checking currently happens in the browser.
- There is no visible database-side constraint or transaction preventing concurrent conflicting reservations.
- User-entered values are currently inserted into generated HTML and should be handled safely.

When modifying relevant code, do not make these limitations worse.

## Working procedure

For non-trivial tasks:

1. Inspect the existing implementation.
2. Identify the affected files and database structures.
3. Explain the proposed change briefly.
4. Make the smallest reasonable change.
5. Check that existing functionality remains intact.
6. Point out assumptions, limitations, or potentially breaking changes.

Do not modify unrelated parts of the project.