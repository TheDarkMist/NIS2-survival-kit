Perfetto, allineo i valori di `enisa_mapping` al formato richiesto. Ecco **Bootstrap.md** aggiornato:
---
id: "prompt-bootstrap"
title: "Bootstrap — minimal NIS2 document set for microbusinesses"
lang: "en"
version: "1.0"
last_updated: "YYYY-MM-DD"
inputs:
  - "00_context/company_profile.yaml"
outputs:
  - "docs/01_policy_network_and_systems/security_policy.md"
  - "docs/02_risk_management/risk_management_policy.md"
  - "docs/02_risk_management/risk_register.csv"
  - "docs/03_incident_handling/incident_response_policy.md"
  - "docs/03_incident_handling/incident_playbook.md"
  - "docs/03_incident_handling/incident_report_form.md"
  - "docs/04_business_continuity_and_crisis/business_continuity_plan.md"
notes: "Copy the fenced block below exactly as the prompt for your AI tool. Paths, IDs and ENISA mappings follow the NIS2 Survival Kit conventions."
---

> IMPORTANT
> - Prefer the modular flow: use `docs/_prompts/en/Create.md`, `docs/_prompts/en/Review.md`, and `docs/_prompts/en/Update.md` to work one file at a time.
> - This bulk prompt generates multiple files and can be less reliable with long outputs. Use it only for very small initial sets or demos.

## Prompt to copy

~~~
You are a compliance assistant for NIS2 readiness in microbusinesses (WordPress-centric).
Goal: bootstrap the minimal document set in clear, practical English.

INPUTS
- Read data exclusively from: 00_context/company_profile.yaml
- Do NOT invent data. If something is missing, FIRST list 5–10 short clarification questions.
- If answers are not provided, proceed but add explicit TODOs in each file where data is missing.

GUARDRAILS
- Keep it short and actionable: policies ≤ ~700 words; playbooks ≤ ~400 words.
- No legalese. Plain English. Guidance, not legal advice.
- Preserve any placeholders like {{ ... }} if used.
- Never change folder/file names provided below.
- Front matter: add YAML front matter at the top of each Markdown file with:
  doc_id, title, owner, version, last_updated (YYYY-MM-DD), next_review (YYYY-MM-DD, +180 days),
  enisa_mapping, source_lang: "en".

OUTPUT FORMAT (STRICT)
Return ONLY a sequence of file blocks using this exact wrapper. No extra commentary.
For each file:
BEGIN FILE: <relative/path/filename>
<file content>
END FILE

FILES TO GENERATE

1) docs/01_policy_network_and_systems/security_policy.md
Front matter example:
---
doc_id: "NIS2-01-POL-base"
title: "Security Policy"
owner: "{{ roles.security_owner }}"
version: "0.1-draft"
last_updated: "<YYYY-MM-DD>"
next_review: "<YYYY-MM-DD>"
enisa_mapping: "01 / Policy on security of network and information systems"
source_lang: "en"
---
Sections (in this order):
- Purpose
- Scope
- Roles & Responsibilities (RACI)
- Minimum Requirements (bulleted, pragmatic)
- Required Evidence (what to keep as proof)
- Review & Maintenance (frequency, owner)

2) docs/02_risk_management/risk_management_policy.md
Front matter:
---
doc_id: "NIS2-02-POL-base"
title: "Risk Management Policy"
owner: "{{ roles.security_owner }}"
version: "0.1-draft"
last_updated: "<YYYY-MM-DD>"
next_review: "<YYYY-MM-DD>"
enisa_mapping: "02 / Risk management"
source_lang: "en"
---
Sections:
- Purpose
- Scope
- Roles & Responsibilities
- Risk Method (impact/likelihood scale from 00_context/company_profile.yaml)
- Acceptance & Exceptions
- Required Evidence
- Review & Maintenance

3) docs/02_risk_management/risk_register.csv
CSV header ONLY (no extra text). Use commas. One sample empty row allowed.
Columns:
asset,threat,vulnerability,impact,likelihood,inherent_risk,controls,residual_risk,owner,due_date

4) docs/03_incident_handling/incident_response_policy.md
Front matter:
---
doc_id: "NIS2-03-POL-base"
title: "Incident Response Policy"
owner: "{{ roles.incident_manager }}"
version: "0.1-draft"
last_updated: "<YYYY-MM-DD>"
next_review: "<YYYY-MM-DD>"
enisa_mapping: "03 / Incident handling"
source_lang: "en"
---
Sections:
- Purpose
- Scope
- Roles & Responsibilities
- Classification & Severity (tie to downtime/data impact)
- Notification & Escalation (internal flows; use contacts from 00_context/company_profile.yaml)
- Evidence & Records
- Review & Maintenance

5) docs/03_incident_handling/incident_playbook.md
Front matter:
---
doc_id: "NIS2-03-PBK-base"
title: "Incident Response Playbook"
owner: "{{ roles.incident_manager }}"
version: "0.1-draft"
last_updated: "<YYYY-MM-DD>"
next_review: "<YYYY-MM-DD>"
enisa_mapping: "03 / Incident handling"
source_lang: "en"
---
Structure:
- Triggers
- Step-by-step actions (T+0, T+30m, T+2h, T+24h)
- Roles (who does what)
- Communications (internal/external)
- KPIs & Timelines
- Outputs/Evidence

6) docs/03_incident_handling/incident_report_form.md
Front matter:
---
doc_id: "NIS2-03-FORM-incident-report"
title: "Incident Report Form"
owner: "{{ roles.incident_manager }}"
version: "0.1-draft"
last_updated: "<YYYY-MM-DD>"
next_review: "<YYYY-MM-DD>"
enisa_mapping: "03 / Incident handling"
source_lang: "en"
---
Provide a simple form (Markdown table) with fields:
- Reporter, Date/Time, Affected service/asset, Severity, Impact, Summary,
- Actions taken, Evidence links, Current status, Next steps, Owner

7) docs/04_business_continuity_and_crisis/business_continuity_plan.md
Front matter:
---
doc_id: "NIS2-04-POL-bcp"
title: "Business Continuity Plan"
owner: "{{ roles.security_owner }}"
version: "0.1-draft"
last_updated: "<YYYY-MM-DD>"
next_review: "<YYYY-MM-DD>"
enisa_mapping: "04 / Business continuity and crisis"
source_lang: "en"
---
Sections:
- Purpose & Objectives
- Scope (critical services from 00_context/company_profile.yaml)
- RTO/RPO Targets (use bcdr.rto_hours and bcdr.rpo_hours)
- Minimum Service Levels & Workarounds
- Backup & Restore (frequency from 00_context/company_profile.yaml)
- Roles & Communication
- Required Evidence
- Review & Exercises

NOTES
- Do not update 00_context/index.md in this step. That will be handled by a separate "Update Index" prompt later.
- If you create any TODOs, prefix them with "TODO:" and assign an owner when possible (e.g., TODO: set provider SLA — Owner: {{ roles.security_owner }}).
~~~