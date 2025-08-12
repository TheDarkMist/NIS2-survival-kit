# Prompt: Create Secure Development Documents

You will act as a NIS2 documentation assistant.

Your goal is to generate a cohesive set of documents for Secure Acquisition, Development, and Maintenance, following the master prompt at `_prompts/core/Create.md` for each file.

---

### 1. Secure Development Policy

**Instruction**: Generate the policy for secure development and maintenance.

**Use the following parameters for the master prompt:**
- **target_path**: `docs/06_secure_acquisition_development_maintenance/secure_development_policy.md`
- **title**: "Secure Development Policy"
- **doc_id**: "NIS2-06-POL-secure-development"
- **owner**: "{{ roles.it_admin }}"
- **enisa_mapping**: "06 / Security in acquisition, development and maintenance"
- **type**: "POL"
- **overwrite**: `false`

**Content guidelines:**
- **Purpose**: To ensure that all software and systems, particularly the WordPress client sites, are developed, acquired, and maintained securely.
- **Scope**: Applies to the entire lifecycle of software used by `{{ org.name }}`, including custom code, plugins, and themes. It covers development activities in repositories like `{{ assets.repositories }}`.
- **Requirements**:
    -   **Vulnerability Management**: Mandate regular scanning and timely patching of vulnerabilities in all software components.
    -   **Change Management**: Define a simple process for approving and deploying changes to production environments.
    -   **Third-Party Components**: State that all new WordPress plugins and themes must be vetted for security and sourced from reputable marketplaces.
    -   **Developer Guidelines**: Mention that development must follow basic security principles (e.g., input validation, least privilege). Reference the `code_review_checklist.md`.
- **Evidence**: Code review records, vulnerability scan reports, and change logs.

---

### 2. Code Review Checklist

**Instruction**: Generate a simple checklist for code reviews.

**Use the following parameters for the master prompt:**
- **target_path**: `docs/06_secure_acquisition_development_maintenance/code_review_checklist.md`
- **title**: "Code Review Checklist"
- **doc_id**: "NIS2-06-CHK-code-review"
- **owner**: "{{ roles.it_admin }}"
- **enisa_mapping**: "06 / Security in acquisition, development and maintenance"
- **type**: "CHK"
- **overwrite**: `false`

**Content guidelines:**
- Create a Markdown checklist (`- [ ] Item`).
- The checklist should be practical for a small WordPress-focused team.
- Include key security checks like:
    -   `[ ]` No hard-coded secrets (API keys, passwords).
    -   `[ ]` All user inputs are sanitized and validated.
    -   `[ ]` Database queries are parameterized (to prevent SQL injection).
    -   `[ ]` Error handling does not reveal sensitive information.
    -   `[ ]` Code follows WordPress coding standards.
    -   `[ ]` Dependencies (e.g., third-party libraries) are up-to-date.

---

After generating the files, remind the user to review them and then update the master index.
