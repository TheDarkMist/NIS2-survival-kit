# Prompt: Create the Risk Management documents

You will act as a NIS2 documentation assistant.

Your goal is to generate the **Risk Management Policy** and the **Risk Register** for the company, following the master prompt at `_prompts/core/Create.md` for each.

---

### File 1: Risk Management Policy

**Use the following parameters for the master prompt:**
- **target_path**: `docs/02_risk_management/risk_management_policy.md`
- **title**: "Risk Management Policy"
- **doc_id**: "NIS2-02-POL-risk-management"
- **owner**: "{{ roles.security_owner }}"
- **enisa_mapping**: "02 / Risk management"
- **type**: "POL"
- **overwrite**: `false`

**Content guidelines:**
1.  **Purpose**: Explain that the policy defines how `{{ org.name }}` identifies, assesses, and treats cybersecurity risks.
2.  **Scope**: Applies to all systems, assets, and data, especially `{{ assets.systems }}` and `{{ assets.critical_data }}`.
3.  **Roles & Responsibilities**:
    -   `{{ roles.security_owner }}`: Owns the risk management process.
    -   `{{ roles.it_admin }}`: Implements risk treatment measures.
4.  **Risk Management Framework**: Briefly describe the cycle: Identify -> Analyze -> Evaluate -> Treat -> Monitor.
5.  **Risk Appetite**: State that the company has a low appetite for risks that could impact `{{ org.services }}` or compromise `{{ assets.critical_data }}`.
6.  **Required Evidence**: Mention the `risk_register.csv` as the primary evidence.

---

### File 2: Risk Register

**Use the following parameters for the master prompt:**
- **target_path**: `docs/02_risk_management/risk_register.csv`
- **title**: "Risk Register"
- **doc_id**: "NIS2-02-REG-risk-register"
- **owner**: "{{ roles.security_owner }}"
- **enisa_mapping**: "02 / Risk management"
- **type**: "REG"
- **overwrite**: `false`

**Content guidelines:**
- The file is a CSV.
- Generate only the header row with the following columns:
  `Risk ID,Date Identified,Risk Description,Asset(s) Affected,Threat,Likelihood (1-5),Impact (1-5),Risk Score,Risk Owner,Treatment,Status,Control(s),Next Review Date`
- Provide a short note to the user explaining that they need to fill this register with actual risks.

After generating the files, remind the user to update the master index for both.
