# Prompt: Create the Audit and Test Plan

You will act as a NIS2 documentation assistant.

Your goal is to generate the **Audit and Test Plan** for the company, following the master prompt at `_prompts/core/Create.md`.

**Use the following parameters for the master prompt:**
- **target_path**: `docs/07_effectiveness_assessment/audit_and_test_plan.md`
- **title**: "Effectiveness Audit and Test Plan"
- **doc_id**: "NIS2-07-PLAN-audit-test"
- **owner**: "{{ roles.security_owner }}"
- **enisa_mapping**: "07 / Assessment of the effectiveness of cybersecurity risk-management measures"
- **type**: "PLAN"
- **overwrite**: `false`

**Content guidelines (in addition to the master prompt):**
1.  **Read the context**: The plan should be realistic for `{{ org.name }}`, as described in `00_context/company_profile.yaml`.
2.  **Purpose**: To define a schedule and methodology for regularly assessing the effectiveness of the implemented NIS2 security controls.
3.  **Scope**: This plan covers all key security measures implemented, including policies, procedures, and technical controls related to `{{ org.critical_services }}`.
4.  **Audit & Test Schedule**:
    -   Create a simple Markdown table with columns: `Activity`, `Frequency`, `Responsible`, `Evidence Location`.
    -   Populate it with a few realistic activities for a micro-business, for example:
        -   **Activity**: Review Access Control Policy | **Frequency**: Annually | **Responsible**: `{{ roles.security_owner }}` | **Evidence**: `/99_evidence/reviews/`
        -   **Activity**: Test Incident Response Playbook (tabletop exercise) | **Frequency**: Annually | **Responsible**: `{{ roles.incident_manager }}` | **Evidence**: `/99_evidence/tests/`
        -   **Activity**: Restore a backup to a test environment | **Frequency**: Semi-annually | **Responsible**: `{{ roles.it_admin }}` | **Evidence**: `/99_evidence/tests/`
        -   **Activity**: Review Supplier Security | **Frequency**: Annually for critical suppliers | **Responsible**: `{{ roles.security_owner }}` | **Evidence**: `supplier_register.md`
5.  **Methodology**:
    -   Briefly explain that tests will be practical (e.g., tabletop exercises, actual backup restores).
    -   State that findings from audits and tests will be logged as risks in the `risk_register.csv` and tracked to resolution.
6.  **Required Evidence**: The primary evidence will be the test results and review reports stored under `/99_evidence/`.

After generating the file, remind the user to schedule these activities and then update the master index.
