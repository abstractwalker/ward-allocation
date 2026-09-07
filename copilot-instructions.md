# Ward Allocation — Copilot Instructions

## Project background

This project, `ward-allocation`, was created as a copy of the earlier `room-reservation` project.

`room-reservation` is the original prototype and should be treated as a reference implementation only. It is not the active project and must not be modified as part of work on `ward-allocation`.

The purpose of `ward-allocation` is to evolve the prototype into a simple web application for allocating patients/clients to hospital wards/rooms over intervals of dates.

## Current technology

- Node.js
- Express
- EJS
- Bootstrap
- Supabase / PostgreSQL
- VS Code
- GitHub

Use the existing project structure and technologies unless there is a good reason to change them.

## Development principles

- Keep the application simple.
- Prefer small, understandable changes over introducing unnecessary frameworks or abstractions.
- Reuse and improve the existing code where appropriate.
- Do not rewrite working parts of the application without a concrete reason.
- Before making significant architectural changes, explain the proposed change and its consequences.
- Keep business logic separate from presentation/UI code where practical.
- Keep database structure and application code consistent.

## Database

`ward-allocation` has its own Supabase project/database.

Never reconnect the application to the old `room-reservation` Supabase project.

Do not hard-code Supabase URLs, API keys, passwords, or other credentials in source code.

Use the project's existing environment/configuration mechanism for credentials.

## Relationship to room-reservation

The original `room-reservation` implementation can be used to understand existing behavior, data structures, and design decisions.

However, `ward-allocation` is an independent project.

When requirements for `ward-allocation` differ from the old prototype, implement the new requirements rather than preserving the old behavior merely for compatibility.

## Working with the developer

When a task involves a non-trivial change:

1. Inspect the existing implementation first.
2. Explain briefly what you intend to change.
3. Identify affected files/database structures.
4. Make the smallest reasonable change.
5. Preserve existing functionality unless the task explicitly changes it.
6. Point out any assumptions or potentially breaking changes.

Do not create unnecessary files, dependencies, abstractions, or features that were not requested.