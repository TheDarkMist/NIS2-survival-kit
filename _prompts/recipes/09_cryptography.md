# Prompt: Create the Cryptography Policy

You will act as a NIS2 documentation assistant.

Your goal is to generate the **Cryptography Policy** for the company, following the master prompt at `_prompts/core/Create.md`.

**Use the following parameters for the master prompt:**
- **target_path**: `docs/09_cryptography/cryptography_policy.md`
- **title**: "Cryptography and Encryption Policy"
- **doc_id**: "NIS2-09-POL-cryptography"
- **owner**: "{{ roles.it_admin }}"
- **enisa_mapping**: "09 / Cryptography and encryption"
- **type**: "POL"
- **overwrite**: `false`

**Content guidelines (in addition to the master prompt):**
1.  **Read the context**: The policy should be practical for `{{ org.name }}`, as described in `00_context/company_profile.yaml`.
2.  **Purpose**: To define the required use of encryption to protect the confidentiality and integrity of `{{ assets.critical_data }}`.
3.  **Scope**: This policy applies to all company data, both in transit and at rest, across all `{{ assets.systems }}`.
4.  **Minimum Requirements**:
    -   **Data in Transit**: All web traffic to client websites and company systems must be encrypted using strong, modern TLS (i.e., HTTPS).
    -   **Data at Rest**:
        -   Critical data stored on company-managed servers (e.g., `{{ assets.systems }}`) should be protected by encrypted filesystems or databases where offered by the provider.
        -   Company laptops and removable media (e.g., USB drives) containing critical data must use full-disk encryption (e.g., BitLocker for Windows, FileVault for macOS).
    -   **Cryptographic Keys**:
        -   Access to cryptographic keys (e.g., private keys for TLS certificates) must be restricted to authorized personnel (`{{ roles.it_admin }}`).
        -   Keys should be stored securely, not in code repositories.
    -   **Approved Algorithms**: State that the company relies on industry-standard, well-vetted cryptographic protocols and will avoid outdated algorithms (e.g., SSLv3, SHA-1).
5.  **Required Evidence**: Evidence of compliance includes TLS certificate configurations, screenshots of full-disk encryption being enabled, and hosting provider documentation on data-at-rest encryption.

After generating the file, remind the user to review it and then update the master index.
