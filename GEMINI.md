# Gemini Context: NIS2 Survival Kit

## Directory Overview

This directory contains a **NIS2-Ready Documentation Toolkit** designed for WordPress micro-businesses and freelancers. Its purpose is to provide a simple, AI-assisted, and audit-friendly framework for creating and managing documentation required for NIS2 compliance.

The structure is organized around the 13 security measures identified by ENISA.

## Key Files

*   `README.md`: The main entry point for understanding the project. It explains the purpose, structure, and usage of the repository for both humans and AI assistants.
*   `00_context/index.md`: This is the master index for all documentation. It's intended to be a single source of truth for tracking the status, ownership, and other metadata of each document. It is currently empty.
*   `00_context/prompt_update_index.md`: A detailed prompt for AI assistants to safely update the `index.md` file. It contains strict conventions and a clear algorithm for adding or updating entries in the master index.
*   `docs/_prompts/en/Bootstrap.md`: A comprehensive prompt for AI assistants to create the initial minimal NIS2 document set. This is the recommended starting point for new users to bootstrap their compliance documentation.
*   `docs/`: This directory contains 13 subdirectories, one for each ENISA security measure. Each subdirectory is intended to hold policies, procedures, and other relevant documentation. Most of the files in this directory are currently empty placeholders.
*   `reference/`: This directory contains official reference documents, such as the "NCSC NIS2 quick reference guide.pdf" and "ENISA NIS2 Technical implementation guidance v1 June 25.pdf". These documents provide the source material for the documentation in this toolkit.

## Usage

This repository is intended to be used as a starting point for creating a NIS2-compliant documentation corpus. The workflow is as follows:

### For New Users (Bootstrap Process)
1.  **Start with Bootstrap**: Use `docs/_prompts/en/Bootstrap.md` with an AI assistant to generate your initial document set
2.  **Review generated documents**: Check the created policies and procedures in their respective folders
3.  **Customize content**: Update company-specific information and adjust to your business needs
4.  **Update the index**: Use `prompt_update_index.md` to register all new documents

### For Existing Users
1.  **Consult the `00_context/index.md` file** to get an overview of the documentation status.
2.  **Navigate to the relevant subdirectory** in the `docs/` directory to create or update a document.
3.  **Use the `prompt_create_...` files** in each subdirectory to get assistance from an AI in creating the documentation.
4.  **Update the `00_context/index.md` file** after creating or updating a document, either manually or by using the `prompt_update_index.md` with an AI assistant.
