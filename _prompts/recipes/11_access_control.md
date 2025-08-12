# Prompt: Create the Access Control Policy

You will act as a NIS2 documentation assistant.

Your goal is to generate the **Access Control Policy** for the company, following the master prompt at `_prompts/core/Create.md`.

**Use the following parameters for the master prompt:**
- **target_path**: `docs/11_access_control/access_control_policy.md`
- **title**: "Access Control Policy"
- **doc_id**: "NIS2-11-POL-access-control"
- **owner**: "{{ roles.it_admin }}"
- **enisa_mapping**: "11 / Access control"
- **type**: "POL"
- **overwrite**: `false`

**Content guidelines (in addition to the master prompt):**
1.  **Read the context**: The policy must align with the roles and assets defined in `00_context/company_profile.yaml`.
2.  **Purpose**: To establish rules for granting, reviewing, and revoking access to `{{ org.name }}`'s information systems and data, based on the principles of least privilege and need-to-know.
3.  **Scope**: This policy applies to all employees, contractors, and systems, including `{{ assets.systems }}` and access to `{{ assets.critical_data }}`.
4.  **Minimum Requirements**:
    -   **Access Provisioning**: Access will be granted based on job role and responsibilities. The `{{ roles.security_owner }}` must approve access to critical systems.
    -   **Authentication**:
        -   All users must have a unique user ID. Shared accounts are prohibited.
        -   Mandate the use of strong passwords and Multi-Factor Authentication (MFA) on all critical systems.
    -   **Access Reviews**: User access rights to critical systems will be reviewed periodically (e.g., annually) to ensure they are still appropriate. The `{{ roles.security_owner }}` is responsible for conducting these reviews.
    -   **Access Revocation**: Access must be removed immediately upon employee termination, as defined in the HR Security Policy.
5.  **Required Evidence**: Records of access reviews, approval forms for new access grants, and logs showing timely access revocation.

After generating the file, remind the user to review it and then update the master index.
