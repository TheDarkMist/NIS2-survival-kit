# Prompt: Create Supply Chain Security Documents

You will act as a NIS2 documentation assistant.

Your goal is to generate a cohesive set of documents for Supply Chain Security, following the master prompt at `_prompts/core/Create.md` for each file.

---

### 1. Supplier Assessment Policy

**Instruction**: Generate the policy for assessing and managing suppliers.

**Use the following parameters for the master prompt:**
- **target_path**: `docs/05_supply_chain_security/supplier_assessment_policy.md`
- **title**: "Supplier Assessment Policy"
- **doc_id**: "NIS2-05-POL-supplier-assessment"
- **owner**: "{{ roles.security_owner }}"
- **enisa_mapping**: "05 / Supply chain security"
- **type**: "policy"

**Content guidelines:**
- **Purpose**: To establish a process for assessing the security posture of suppliers to minimize supply chain risks for `{{ org.name }}`.
- **Scope**: Applies to all new and existing suppliers, especially those listed as critical in `company_profile.yaml` (`{{ vendors.critical }}`).
- **Requirements**:
    -   Define criteria for classifying suppliers (e.g., critical, non-critical) based on their access to `{{ assets.critical_data }}`.
    -   Outline a simple due diligence process for new suppliers (e.g., a short questionnaire about their security practices).
    -   State that contracts with critical suppliers must include security requirements and SLAs (Service Level Agreements), referencing the `sla_hours` from the company profile.
    -   Mandate periodic review of critical suppliers.
- **Evidence**: The `supplier_register.md` is the primary evidence of this policy in action.

---

### 2. Supplier Register

**Instruction**: Generate the register to track all key suppliers.

**Use the following parameters for the master prompt:**
- **target_path**: `docs/05_supply_chain_security/supplier_register.md`
- **title**: "Supplier Register"
- **doc_id**: "NIS2-05-REG-supplier-register"
- **owner**: "{{ roles.security_owner }}"
- **enisa_mapping**: "05 / Supply chain security"
- **type**: "register"

**Content guidelines:**
- Create a Markdown table to serve as the register.
- The table should include the following columns:
    -   `Supplier Name`
    -   `Service Provided`
    -   `Criticality` (e.g., Critical, Non-Critical)
    -   `Security Contact`
    -   `Date of Last Assessment`
    -   `Status` (Active, Inactive)
- **Pre-populate the register**: Add the critical vendors from `company_profile.yaml` (`{{ vendors.critical }}`) as the initial entries in the table.

---

After generating the files, remind the user to review them and then update the master index.
