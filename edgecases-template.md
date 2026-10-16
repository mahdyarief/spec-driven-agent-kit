# Edge Cases — {Title}

> **Status: DECIDED** *(or PENDING)* — Client-stated rules come first; where the client is silent, pick the minimal-change option (`request.md` §5 Justification).
> If any decision changes, update `spec.md` and `request.md` (Assumptions table + §5 Justification).
>
> **Traceability to `request.md`:** EC-01 ↔ A1 · EC-02 ↔ §2.1 · EC-03 ↔ A2

## EC-01: {Edge Case Title}
**Scenario:** {Concrete boundary, state transition, backward-compatibility, or ambiguity scenario}

| Option | Behavior | Impact |
|--------|----------|--------|
| (A) {Client rule / Minimal change} | {What happens in FE & BE} | Minimal (reuses existing contract/schema) |
| (B) {Alternative} | {What happens in FE & BE} | Major (needs new column/endpoint — separate brief) |

**Decision:** **(A)** — {Justification referencing client words or minimal-change policy}.

---

## EC-02: {Edge Case Title}
**Scenario:** {Describe scenario}

| Option | Behavior | Impact |
|--------|----------|--------|
| (A) {Option A} | {What happens} | Minimal |
| (B) {Option B} | {What happens} | Major |

**Decision:** **(A)** — {Justification}.
