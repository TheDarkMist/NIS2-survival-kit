# Prompt: Create Cyber Hygiene and Training Documents

You will act as a NIS2 documentation assistant.

Your goal is to generate a cohesive set of documents for Cyber Hygiene and Training, following the master prompt at `_prompts/core/Create.md` for each file.

---

### 1. Hygiene Guidelines

**Instruction**: Generate a document with basic cyber hygiene guidelines for all employees.

**Use the following parameters for the master prompt:**
- **target_path**: `docs/08_cyber_hygiene_and_training/hygiene_guidelines.md`
- **title**: "Cyber Hygiene Guidelines"
- **doc_id**: "NIS2-08-WG-hygiene-guidelines"
- **owner**: "{{ roles.security_owner }}"
- **enisa_mapping**: "08 / Basic cyber hygiene and cybersecurity training"
- **type**: "WG" (Work Guideline)

**Content guidelines:**
- **Purpose**: To provide all personnel of `{{ org.name }}` with clear, actionable rules for everyday secure behavior.
- **Scope**: These guidelines apply to all employees and contractors.
- **Guidelines**: Create a list of essential, easy-to-understand hygiene rules. Include topics like:
    -   **Password Security**: Use strong, unique passwords. Enable MFA wherever possible.
    -   **Phishing Awareness**: How to spot and report suspicious emails. Never click links or download attachments from unknown senders. Report to `{{ contacts.security_email }}`.
    -   **Safe Browsing**: Avoid untrusted websites and downloads.
    -   **Device Security**: Keep operating systems and software updated. Lock screens when away from the device.
    -   **Data Handling**: Be mindful when handling `{{ assets.critical_data }}`. Do not share it without authorization.

---

### 2. Security Training Plan

**Instruction**: Generate a simple plan for security awareness training.

**Use the following parameters for the master prompt:**
- **target_path**: `docs/08_cyber_hygiene_and_training/security_training_plan.md`
- **title**: "Security Training Plan"
- **doc_id**: "NIS2-08-PLAN-security-training"
- **owner**: "{{ roles.security_owner }}"
- **enisa_mapping**: "08 / Basic cyber hygiene and cybersecurity training"
- **type**: "PLAN"

**Content guidelines:**
- **Purpose**: To outline the security training program for `{{ org.name }}`.
- **Scope**: The plan applies to all new and existing employees.
- **Training Schedule & Topics**:
    -   Create a simple Markdown table: `Topic`, `Method`, `Frequency`, `Audience`.
    -   Populate with a realistic training plan:
        -   **Topic**: Onboarding Security Training | **Method**: Review of Hygiene Guidelines | **Frequency**: On hiring | **Audience**: New Employees
        -   **Topic**: Annual Security Refresher | **Method**: Online video / short presentation | **Frequency**: Annually | **Audience**: All Employees
        -   **Topic**: Phishing Simulation | **Method**: Simulated phishing campaign | **Frequency**: Semi-annually | **Audience**: All Employees
- **Evidence**: Training completion records and phishing simulation results will be stored in `/99_evidence/training/`.

---

After generating the files, remind the user to review them and then update the master index.
