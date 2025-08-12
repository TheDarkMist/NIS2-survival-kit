# Prompt: Create the Asset Inventory

You will act as a NIS2 documentation assistant.

Your goal is to populate the **Asset Inventory** document for the company, following the master prompt at `_prompts/core/Update.md`.

**Use the following parameters for the master prompt:**
- **target_path**: `docs/12_asset_management/asset_inventory.md`
- **title**: "Asset Inventory"
- **doc_id**: "NIS2-12-REG-asset-inventory"
- **owner**: "{{ roles.it_admin }}"
- **enisa_mapping**: "12 / Asset management"
- **type**: "REG"

**Edits to perform:**
- **change_type**: "major"
- **update_dates**: true
- **sections**:
    1.  **Read the context**: The inventory MUST be based on the `assets` section of `00_context/company_profile.yaml`.
    2.  **Purpose**: To create and maintain a comprehensive inventory of all critical information assets owned and managed by `{{ org.name }}`.
    3.  **Inventory Table**:
        -   Create a Markdown table to serve as the inventory.
        -   Include key columns like: `Asset ID`, `Asset Name/Description`, `Type` (e.g., Software, Hardware, Data), `Owner`, `Location/System`.
    4.  **Pre-populate the Inventory**:
        -   Use the information from `company_profile.yaml` to create initial entries.
        -   Create an entry for each of the `{{ assets.systems }}`.
        -   Create an entry for each type of `{{ assets.critical_data }}`.
        -   Create an entry for each of the `{{ assets.repositories }}`.
        -   The user can then expand this list with more detail.
    5.  **Asset Classification**:
        -   Briefly explain that assets should be classified based on their criticality to the business.
        -   Suggest a simple classification scheme (e.g., Critical, Important, Supporting) that aligns with the risk management process.
    6.  **Required Evidence**: This document itself is the primary evidence. It should be reviewed and updated regularly.

After generating the file, remind the user to complete the inventory with all relevant assets and then update the master index.
