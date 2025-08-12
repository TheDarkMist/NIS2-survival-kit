# Prompt — Safely update `/00_context/index.md`

This prompt is meant for an AI assistant (or a careful human) to **append or update rows** in the **Master index** table inside `/00_context/index.md`, without breaking formatting, IDs, or conventions. Keep it minimal, deterministic, and auditable.

> Usage note (modular flow recommended)
> - After creating, reviewing, or updating a single document using `_prompts/core/Create.md`, `Review.md`, or `Update.md`, use this prompt to add/update the corresponding row in `/00_context/index.md`.
> - If you generate multiple files, run this prompt afterwards to register each file in the index.

---

## Scope (what you may change)

* **Only** edit the markdown table under **“Master index”**.
* You may **add new rows** or **update existing rows**.
* Do **not** delete rows, re‑order rows, change the table header, or modify other sections.
* If a field is unknown, leave it blank except where defaults are required below.

## Table header (must remain exactly this)

```
| Doc ID | Title | File path | Type | Status | Owner | Version | Last updated | Next review | NIS2 mapping (Art/Annex) | ENISA measure (# / name) | Risk covered (short) | Evidence link |
| ------ | ----- | --------- | ---- | ------ | ----- | ------: | ------------ | ----------- | ------------------------ | ------------------------ | -------------------- | ------------- |
```

## Conventions to enforce

* **Doc ID format:** `NIS2-<ENISA#>-<TYPE>-<slug>` (lowercase slug from Title, hyphens only). Example: `NIS2-03-PBK-incident-response-playbook`.
* **Type codes:** `POL` policy, `PROC` procedure, `SOP` operating procedure, `PLAN`, `PBK` playbook, `CHK` checklist, `TMP` template, `REG` register, `WG` work guideline.
* **Status values:** `Draft`, `In review`, `Completed`, `Retired`.
* **Dates:** ISO `YYYY-MM-DD`.
* **Version:** semantic `MAJOR.MINOR` (default `0.1` for new docs if not provided).
* **Next review:** if empty, set to `Last updated + 6 months`.
* **Evidence link:** must point under `/99_evidence/` (file or folder). If not available, leave blank.
* **Owners:** a real person (primary). Optional backup in parentheses.

## ENISA measure mapping (authoritative wording)

Use exactly one of the following for the column **ENISA measure (# / name)**:

```
01 / Policy on security of network and information systems
02 / Risk management
03 / Incident handling
04 / Business continuity and crisis management
05 / Supply chain security
06 / Security in acquisition, development and maintenance
07 / Assessment of the effectiveness of cybersecurity risk-management measures
08 / Basic cyber hygiene and cybersecurity training
09 / Cryptography and encryption
10 / Human resources security, access control and asset management
11 / Access control
12 / Asset management
13 / Physical and environmental security
```

> Note: The repository keeps 10/11/12 separated for operational clarity; still use the wording above.

---

## Input format (what you receive)

Provide a **Change Request** in one of two formats.

### A) Single change (natural language)

Short instruction like:

> *Add a Completed access control policy owned by Jane Doe at `/docs/11_access_control/access_control_policy.md`, ENISA 11, last updated today.*

### B) Batch changes (YAML)

Supply a YAML block using this schema (fields are case‑sensitive):

```yaml
changes:
  - action: add | update
    title: "..."                   # required for add; optional for update
    file_path: "/docs/...md"       # required
    type: POL | PROC | SOP | PLAN | PBK | CHK | TMP | REG | WG
    status: Draft | In review | Completed | Retired
    owner: "Full Name (optional backup)"
    version: "1.0"                 # default 0.1 if missing on add
    last_updated: "YYYY-MM-DD"     # if "today" is given, replace with today’s date
    next_review: "YYYY-MM-DD"      # optional; if missing, auto = last_updated + 6 months
    enisa_no: 1..13                 # integer, required
    nis2_mapping: "Art. 21/23 ..." # optional free text
    risk_short: "..."              # short phrase
    evidence_link: "/99_evidence/..." # optional
    doc_id: "NIS2-.."              # optional; if absent, auto‑generate per rules
    bump: minor | major             # optional; when action=update and version omitted
```

---

## Algorithm (step by step)

1. **Load** `/00_context/index.md`. Locate the **Master index** table; read rows as CSV‑like cells split by `|`. Preserve column order and spacing.
2. **Normalize input:**

   * Map any `today` value to the current date in `YYYY-MM-DD`.
   * If `doc_id` missing, **generate** from `enisa_no`, `type`, and `title` (slug = lowercase, hyphen‑separated, ASCII only).
   * If `version` missing and `action=add`, set `0.1`. If `action=update` and `bump` provided, increment accordingly.
   * If `next_review` missing, compute `last_updated + 6 months`.
3. **Upsert logic:**

   * Prefer **Doc ID** to find an existing row. If not found, try unique match on **File path**.
   * **Add** inserts a new row at the **end** of the table. **Update** only edits cells in the matched row.
   * Never delete or reorder existing rows.
4. **Validate:**

   * `Type`, `Status`, and `ENISA measure` must match the allowed values.
   * `File path` must start with `/docs/` (or valid repo path) and use forward slashes.
   * Dates must be valid ISO. Versions must be `N.N` integers.
5. **Write back** the table preserving the existing header exactly as found in `/00_context/index.md`. Keep a trailing newline.
6. **Change log:** Append a bullet at the bottom of `/00_context/index.md` under **“Change log (high level)”** with today’s date and a short summary, e.g.:
   `- 2025-08-10: Added NIS2-11-POL-access-control-policy (Completed).`
7. **Output (to console/chat):** Print a compact summary of added/updated Doc IDs and any warnings.

---

## Examples

### Example A — Add one document

Instruction:

> Add a Completed access control policy owned by Jane Doe at `/docs/11_access_control/access_control_policy.md`, ENISA 11, last updated today.

Resulting row (values you would produce):

```
| NIS2-11-POL-access-control-policy | Access control policy | /docs/11_access_control/access_control_policy.md | POL | Completed | Jane Doe | 1.0 | 2025-08-10 | 2026-02-10 |  | 11 / Access control | Unauthorized access |  |
```

### Example B — Batch (YAML)

```yaml
changes:
  - action: add
    title: Incident response playbook
    file_path: /docs/03_incident_handling/incident_playbook.md
    type: PBK
    status: Draft
    owner: "Alex Smith"
    version: "0.1"
    last_updated: "today"
    enisa_no: 3
    risk_short: Major incidents
  - action: update
    doc_id: NIS2-05-REG-supplier-register
    file_path: /docs/05_supply_chain_security/supplier_register.md
    status: In review
    bump: minor
    last_updated: "2025-08-10"
    enisa_no: 5
```

Expected changes summary:

```
Added: NIS2-03-PBK-incident-response-playbook
Updated: NIS2-05-REG-supplier-register (to In review, version 0.2)
```

---

## Warnings & edge cases

* If both **Doc ID** and **File path** conflict with different rows, do not proceed; report a **conflict** and list the rows.
* If **File path** does not exist in the repo yet, still add/update the row but keep **Status=Draft** and mention a warning in the output.
* Never insert commas, extra pipes, HTML, or code blocks into the table cells.
* Keep lines under ~300 characters; abbreviate **Risk covered** if needed.
* Do not translate or rewrite titles arbitrarily; keep the user’s wording.