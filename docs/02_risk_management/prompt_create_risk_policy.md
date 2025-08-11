# Prompt: Create the Risk Management Policy

You will act as a NIS2 documentation assistant.

Your goal is to generate the **Risk Management Policy** for the company, following the master prompt at `/docs/_prompts/en/Create.md`.

**Use the following parameters for the master prompt:**
- **target_path**: `docs/02_risk_management/risk_management_policy.md`
- **title**: "Risk Management Policy"
- **doc_id**: "NIS2-02-POL-risk-management"
- **owner**: "{{ roles.security_owner }}"
- **enisa_mapping**: "02 / Risk management"
- **type**: "policy"
- **overwrite**: `false` (unless the user specifies otherwise)

**Content guidelines (in addition to the master prompt):**
1.  **Read the context**: Base the policy on `00_context/company_profile.yaml`, paying close attention to the `risk` section.
2.  **Purpose**: Explain that the purpose of this policy is to establish a systematic approach to identifying, assessing, and treating cybersecurity risks to protect the assets of `{{ org.name }}`.
3.  **Scope**: This policy applies to all risks affecting the company's critical services, such as `{{ org.critical_services }}`.
4.  **Roles & Responsibilities**:
    -   **`{{ roles.security_owner }}`**: Owns the risk management process and accepts residual risks.
    -   All team members are responsible for identifying and reporting risks.
5.  **Minimum Requirements**: Describe a simple risk management process suitable for a micro-business:
    -   **Risk Identification**: How risks are identified (e.g., brainstorming, incident reviews).
    -   **Risk Assessment**: Explain that risks will be assessed based on impact and likelihood, using the company's defined `{{ risk.rating_scale }}`.
    -   **Risk Treatment**: Describe the four standard options (Avoid, Mitigate, Transfer, Accept) and state that treatment decisions will align with the company's risk appetite, defined as `{{ risk.appetite }}`.
    -   **Risk Monitoring**: State that the `risk_register.csv` will be reviewed periodically.
6.  **Required Evidence**: Note that the primary evidence for this process is the `risk_register.csv` file located in the same directory.

After generating the file, remind the user that the next step is to populate the `risk_register.csv` and then update the master index.
