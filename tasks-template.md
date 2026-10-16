# Tasks: {Feature / Change Request Title}

> **Source Spec:** `spec.md` · **Status:** in-progress # pending | in-progress | completed

## Task Breakdown & Execution Plan

Break down the specification into small, atomic, verifiable steps that an AI coding agent or developer can execute sequentially.

---

### Phase 1: Database & Contracts (Backend)
- [ ] **Task 1.1: Schema & Entities**
  - **Action:** Create or update data models / schemas / migrations.
  - **Target Files:** `{backend_repo}/src/models/...` or migrations.
  - **Verification:** Run migration and verify table schema.
- [ ] **Task 1.2: Business Logic & Use Cases**
  - **Action:** Implement business logic rules and validation in service/usecase layer.
  - **Target Files:** `{backend_repo}/src/usecases/...`
  - **Verification:** Write unit test covering business invariant.
- [ ] **Task 1.3: API Endpoints & Contract Docs**
  - **Action:** Add/update route, controller, validation schemas, and Swagger/OpenAPI documentation.
  - **Target Files:** `{backend_repo}/src/controllers/...`
  - **Verification:** Execute integration test hitting the endpoint.

---

### Phase 2: Client SDK & Helpers (Integration)
- [ ] **Task 2.1: Regenerate Client SDK**
  - **Action:** Run SDK generator from backend OpenAPI spec (never edit generated SDK manually).
  - **Target Files:** `{frontend_repo}/src/sdk/...`
  - **Verification:** TypeScript compiles without type errors.
- [ ] **Task 2.2: Pure Helper Functions**
  - **Action:** Write pure calculation/formatting helper functions with unit tests.
  - **Target Files:** `{frontend_repo}/src/lib/...`
  - **Verification:** Vitest/Jest unit tests pass.

---

### Phase 3: UI & User Experience (Frontend)
- [ ] **Task 3.1: Form State & Input Components**
  - **Action:** Implement UI fields, validation, and dynamic visibility rules.
  - **Target Files:** `{frontend_repo}/src/components/...`
  - **Verification:** Verify form interactions match Acceptance Criteria.
- [ ] **Task 3.2: Review & Summary Screens**
  - **Action:** Display calculated summary, review steps, and confirmation dialogues.
  - **Target Files:** `{frontend_repo}/src/routes/...`
  - **Verification:** Verify end-to-end user submission flow.

---

### Phase 4: Verification & Gatekeeping
- [ ] **Task 4.1: Acceptance Criteria Matrix Verification**
  - **Action:** Test all rows in the `spec.md` Acceptance Criteria table.
  - **Verification:** Automated tests pass; manual checklist verified.
- [ ] **Task 4.2: Spec Drift Check**
  - **Action:** Compare committed code against `spec.md` and `edgecases.md`. Update docs if needed.
  - **Verification:** Run `/spec-verify <slug>` before opening Pull Requests.
