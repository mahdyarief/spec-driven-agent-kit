# Structure Steering Document

> Project-level code organization principles, directory patterns, and architectural rules.

## 1. Repository Architecture
- **Type:** {Polyrepo | Monorepo | Unified Fullstack}
- **Root Directories:**
  ```text
  ├── frontend/ (or apps/web)      # Client web portal / mobile app
  ├── backend/  (or apps/api)      # API server / backend services
  ├── packages/                    # Shared internal libraries (for monorepo)
  └── specs/                       # Active & archived specification briefs
  ```

## 2. Layering & Architectural Patterns
- **Backend Architecture:** {UseCase / Clean Architecture / MVC / Hexagonal}
  - `src/controllers/` or `routes/`: Transport layer, input validation (Zod/Joi).
  - `src/usecases/` or `services/`: Pure business logic, orchestration.
  - `src/repositories/` or `models/`: Database persistence, ORM models.
  - `src/schemas/`: Contract schemas, DTOs, request/response definitions.
- **Frontend Architecture:** {Feature-based / Layer-based}
  - `src/routes/` or `pages/`: Page-level components and loaders.
  - `src/components/`: Reusable presentational UI components.
  - `src/lib/` or `utils/`: Pure helper functions and calculation engines.
  - `src/sdk/` or `api/`: OpenAPI generated clients (never hand-edited).

## 3. Code Standards & Naming Conventions
- **Files:** `kebab-case.ts` (utilities), `PascalCase.tsx` (React components).
- **Functions & Methods:** `camelCase`.
- **Constants:** `UPPER_SNAKE_CASE`.
- **Database Tables & Columns:** `snake_case` (e.g. `tb_order`, `delivery_date`).
