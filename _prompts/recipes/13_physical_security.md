# Prompt: Create the Physical Security Document

You will act as a NIS2 documentation assistant.

Your goal is to populate the **Physical Security Measures** document for the company, following the master prompt at `_prompts/core/Update.md`.

**Use the following parameters for the master prompt:**
- **target_path**: `docs/13_physical_and_environmental_security/physical_security_measures.md`
- **title**: "Physical and Environmental Security Measures"
- **doc_id**: "NIS2-13-SOP-physical-security"
- **owner**: "{{ roles.security_owner }}"
- **enisa_mapping**: "13 / Physical and environmental security"
- **type**: "SOP"

**Edits to perform:**
- **change_type**: "major"
- **update_dates**: true
- **sections**:
    1.  **Read the context**: The measures should be relevant to the company's `{{ org.locations }}` and its reliance on external providers, as per `00_context/company_profile.yaml`.
    2.  **Purpose**: To describe the measures taken by `{{ org.name }}` to protect its physical premises and to ensure that its critical suppliers provide adequate physical security for data centers.
    3.  **Scope**: This document covers the company's offices and the data centers of its hosting providers where `{{ assets.critical_data }}` is stored.
    4.  **Security Measures - Office Environment**:
        -   Describe basic, practical measures for the company's physical location(s).
        -   Include topics like:
            -   Secure entry (e.g., locked doors).
            -   Visitor policy (e.g., visitors must be escorted).
            -   Clean desk policy (e.g., sensitive documents locked away, screens locked when unattended).
            -   Protection against environmental threats (e.g., smoke detectors).
    5.  **Security Measures - Data Centers (Suppliers)**:
        -   State that `{{ org.name }}` relies on its hosting and cloud providers (from `{{ vendors.critical }}`) for the physical security of its servers.
        -   Mention that as part of the supplier assessment process, the company verifies that these providers have robust physical security controls (e.g., 24/7 security, access control, fire suppression, redundant power).
        -   Reference the provider's compliance certifications (e.g., ISO 27001) as evidence.
    6.  **Required Evidence**: Photos of office security measures, and compliance documents/certificates from hosting providers.

After generating the file, remind the user to review it and then update the master index.
