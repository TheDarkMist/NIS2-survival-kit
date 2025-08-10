# Gemini Context: NIS2 Survival Kit

## Directory Overview

This directory contains a **NIS2-Ready Documentation Toolkit** designed for WordPress micro-businesses and freelancers. Its purpose is to provide a simple, AI-assisted, and audit-friendly framework for creating and managing documentation required for NIS2 compliance.

The structure is organized around the 13 security measures identified by ENISA.

## Key Files

*   `README.md`: The main entry point for understanding the project. It explains the purpose, structure, and usage of the repository for both humans and AI assistants.
*   `00_context/index.md`: This is the master index for all documentation. It's intended to be a single source of truth for tracking the status, ownership, and other metadata of each document. It is currently empty.
*   `00_context/prompt_update_index.md`: A detailed prompt for AI assistants to safely update the `index.md` file. It contains strict conventions and a clear algorithm for adding or updating entries in the master index.
*   `docs/_prompts/en/Create.md`, `Review.md`, `Update.md`: Modular prompts to work one file at a time (default/recommended flow).
*   `docs/_prompts/en/Bootstrap.md`: Optional bulk prompt to generate multiple files; use for very small initial sets or demos.
*   `docs/`: This directory contains 13 subdirectories, one for each ENISA security measure. Each subdirectory is intended to hold policies, procedures, and other relevant documentation. Most of the files in this directory are currently empty placeholders.
*   `reference/`: This directory contains official reference documents, such as the "NCSC NIS2 quick reference guide.pdf" and "ENISA NIS2 Technical implementation guidance v1 June 25.pdf". These documents provide the source material for the documentation in this toolkit.

## Usage

This repository is intended to be used as a starting point for creating a NIS2-compliant documentation corpus. The workflow is as follows:

### Default (Modular Flow)
1. Use `docs/_prompts/en/Create.md` to generate exactly one document.
2. Use `Review.md` to quality-check and optionally fix that document.
3. Use `Update.md` to apply targeted edits and bump version/dates.
4. Update the master index using `00_context/prompt_update_index.md`.

### Optional (Bootstrap Process)
1.  Use `docs/_prompts/en/Bootstrap.md` with an AI assistant to generate a minimal initial set of documents.
2.  Review the generated files and customize them as needed.
3.  Update the index with `prompt_update_index.md`.
