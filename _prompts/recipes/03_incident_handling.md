# Prompt: Create Incident Handling Documents

You will act as a NIS2 documentation assistant.

Your goal is to generate a cohesive set of documents for Incident Handling, following the master prompt at `_prompts/core/Create.md` for each file.

---

### 1. Incident Response Policy

**Instruction**: Generate the main policy for handling incidents.

**Use the following parameters for the master prompt:**
- **target_path**: `docs/03_incident_handling/incident_response_policy.md`
- **title**: "Incident Response Policy"
- **doc_id**: "NIS2-03-POL-incident-response"
- **owner**: "{{ roles.security_owner }}"
- **enisa_mapping**: "03 / Incident handling"
- **type**: "policy"

**Content guidelines:**
- **Purpose**: To define a structured approach for managing security incidents, minimizing impact on `{{ org.name }}`, and ensuring timely reporting.
- **Scope**: Covers all security incidents affecting `{{ org.critical_services }}` and `{{ assets.critical_data }}`.
- **Roles**:
    -   `{{ roles.incident_manager }}`: Leads the incident response effort.
    -   `{{ roles.security_owner }}`: Provides resources and makes critical decisions.
- **Requirements**: Describe the phases of incident handling (Preparation, Identification, Containment, Eradication, Recovery, Lessons Learned). Emphasize the requirement to report significant incidents to authorities as per NIS2.
- **Evidence**: Mention the `incident_report_form.md` and logs stored in `/99_evidence/` as key evidence.

---

### 2. Incident Playbook

**Instruction**: Generate a practical playbook for common incidents.

**Use the following parameters for the master prompt:**
- **target_path**: `docs/03_incident_handling/incident_playbook.md`
- **title**: "Incident Playbook"
- **doc_id**: "NIS2-03-PBK-incident-playbook"
- **owner**: "{{ roles.incident_manager }}"
- **enisa_mapping**: "03 / Incident handling"
- **type**: "playbook"

**Content guidelines:**
- Create playbooks for 2-3 common scenarios for a WordPress business, for example:
    -   **Scenario 1: Website Defacement**
    -   **Scenario 2: Suspected Data Breach (e.g., customer data from a contact form)**
- For each scenario, use the default playbook sections from `Create.md` (Triggers, Step-by-step actions, Roles, etc.).
- The steps should be clear, concise, and actionable for a non-expert. Reference `{{ contacts.security_email }}` for internal communication.

---

### 3. Incident Report Form

**Instruction**: Generate a template for reporting incidents.

**Use the following parameters for the master prompt:**
- **target_path**: `docs/03_incident_handling/incident_report_form.md`
- **title**: "Incident Report Form"
- **doc_id**: "NIS2-03-TMP-incident-report"
- **owner**: "{{ roles.incident_manager }}"
- **enisa_mapping**: "03 / Incident handling"
- **type**: "form"

**Content guidelines:**
- Create a Markdown table that serves as a form.
- Include essential fields like:
    -   `Report ID`
    -   `Date of Detection`
    -   `Reporter Name`
    -   `Incident Type` (e.g., Malware, Phishing, Data Breach)
    -   `Description of Incident`
    -   `Affected Systems/Data` (referencing assets from `company_profile.yaml`)
    -   `Initial Actions Taken`
    -   `Status` (Open, Contained, Closed)

---

After generating the files, remind the user to review them and then update the master index.
