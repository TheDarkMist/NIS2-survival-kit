# Prompt: Create the HR Security Policy

You will act as a NIS2 documentation assistant.

Your goal is to generate the **Human Resources Security Policy** for the company, following the master prompt at `_prompts/core/Create.md`.

**Use the following parameters for the master prompt:**
- **target_path**: `docs/10_hr_security/hr_security_policy.md`
- **title**: "Human Resources Security Policy"
- **doc_id**: "NIS2-10-POL-hr-security"
- **owner**: "{{ roles.hr_manager }}"
- **enisa_mapping**: "10 / Human resources security, access control and asset management"
- **type**: "POL"
- **overwrite**: `false`

**Content guidelines (in addition to the master prompt):**
1.  **Read the context**: The policy should be practical for a company of `{{ org.headcount }}` employees, as per `00_context/company_profile.yaml`.
2.  **Purpose**: To define security responsibilities and procedures throughout the employee lifecycle to minimize human-related risks.
3.  **Scope**: This policy applies to all employees and contractors of `{{ org.name }}`.
4.  **Minimum Requirements**:
    -   **Prior to Employment**:
        -   Mention that background checks may be required for roles with access to sensitive data, depending on local regulations in `{{ org.locations }}`.
        -   State that all employees must sign a confidentiality agreement upon hiring.
    -   **During Employment**:
        -   Refer to the company's security training program (from area 08) as a mandatory requirement.
        -   Reference the `hygiene_guidelines.md` as required reading for all staff.
    -   **Termination or Change of Employment**:
        -   Define a clear offboarding process.
        -   Access to all systems (`{{ assets.systems }}`) must be revoked promptly upon termination.
        -   All company assets (laptops, phones) must be returned.
5.  **Required Evidence**: Signed confidentiality agreements, training records, and offboarding checklists.

After generating the file, remind the user to review it and then update the master index.
