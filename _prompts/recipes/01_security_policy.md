# Prompt: Create the core Security Policy

You will act as a NIS2 documentation assistant.

Your goal is to populate the main **Security Policy** for the company, following the master prompt at `_prompts/core/Update.md`.

**Use the following parameters for the master prompt:**
- **target_path**: `docs/01_policy_network_and_systems/security_policy.md` # This is the file we are updating
- **title**: "Security Policy for Network and Information Systems"
- **doc_id**: "NIS2-01-POL-security-policy"
- **owner**: "{{ roles.security_owner }}"
- **enisa_mapping**: "01 / Policy on security of network and information systems"
- **type**: "POL"

**Edits to perform:**
- **change_type**: "major" # This is the first content generation
- **update_dates**: true
- **sections**:
1.  **Read the context**: Base the policy on the details in `00_context/company_profile.yaml`.
2.  **Purpose**: State that this policy establishes the security framework for all network and information systems at `{{ org.name }}` to ensure confidentiality, integrity, and availability, in compliance with NIS2.
3.  **Scope**: The policy applies to all employees, contractors, and the `{{ roles.it_admin }}`. It covers all company-managed assets, including `{{ assets.systems }}` and `{{ assets.critical_data }}`.
4.  **Roles & Responsibilities**:
    -   **`{{ roles.security_owner }}`**: Ultimately responsible for this policy.
    -   **`{{ roles.incident_manager }}`**: Responsible for handling security incidents that affect networks.
    -   **`{{ roles.it_admin }}`**: Responsible for implementing and maintaining the technical controls.
5.  **Minimum Requirements**: Generate a concise list of key requirements relevant to a micro-business using WordPress. Include topics like:
    -   Secure configuration of network devices (routers, firewalls).
    -   Regular software updates and patching for all systems (especially WordPress and plugins).
    -   Use of strong authentication.
    -   Data encryption (in transit and at rest).
    -   Basic endpoint protection (e.g., antivirus on company devices).
6.  **Required Evidence**: Mention that evidence of compliance, if generated, should be stored in the `/99_evidence/` folder. This may include firewall configurations, patch management logs, and access control reviews.

After generating the file, remind the user that the next step is to update the master index.
