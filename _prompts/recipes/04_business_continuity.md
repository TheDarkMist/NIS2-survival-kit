# Prompt: Create the Business Continuity Plan

You will act as a NIS2 documentation assistant.

Your goal is to generate the **Business Continuity Plan** for the company, following the master prompt at `_prompts/core/Create.md`.

**Use the following parameters for the master prompt:**
- **target_path**: `docs/04_business_continuity_and_crisis/business_continuity_plan.md`
- **title**: "Business Continuity Plan"
- **doc_id**: "NIS2-04-PLAN-business-continuity"
- **owner**: "{{ roles.security_owner }}"
- **enisa_mapping**: "04 / Business continuity and crisis management"
- **type**: "PLAN"
- **overwrite**: `false`

**Content guidelines (in addition to the master prompt):**
1.  **Read the context**: The plan MUST be based on the `bcdr` (Business Continuity and Disaster Recovery) section of `00_context/company_profile.yaml`.
2.  **Purpose**: To outline the strategy for `{{ org.name }}` to maintain its `{{ org.critical_services }}` during and after a significant disruption.
3.  **Scope**: This plan covers disruptions to critical assets, including `{{ assets.critical_data }}` and `{{ assets.systems }}`.
4.  **Key Objectives**:
    -   **Recovery Time Objective (RTO)**: State that the RTO for critical services is **`{{ bcdr.rto_hours }}` hours**, as defined in the company profile.
    -   **Recovery Point Objective (RPO)**: State that the RPO is **`{{ bcdr.rpo_hours }}` hours**, meaning data loss will not exceed this window.
5.  **Activation Criteria**: Describe the types of events that would trigger this plan (e.g., hosting provider outage, office inaccessibility, key personnel unavailability).
6.  **Recovery Procedures**:
    -   Outline a high-level recovery strategy suitable for a WordPress-based business.
    -   Focus on restoring website functionality from backups. Mention the responsible `{{ vendors.critical }}` that are involved (e.g., Hosting Provider, Backup Provider).
    -   Include steps for communication with clients via alternative channels (e.g., social media, status page).
7.  **Roles & Responsibilities**:
    -   **`{{ roles.security_owner }}`**: Authorizes the activation of the plan.
    -   **`{{ roles.it_admin }}`**: Executes the technical recovery steps.
8.  **Required Evidence**: Mention that evidence of plan testing, such as backup restoration tests, will be stored in `/99_evidence/`.

After generating the file, remind the user to review it, especially the RTO/RPO values, and then update the master index.
