# NIS2-Ready Documentation Toolkit for WordPress Micro-Businesses

## Purpose
This repository provides a **ready-to-use documentation framework** to help **WordPress micro-businesses and freelancers** start and maintain a **NIS2-compliant documentation corpus**.  
It is designed to be:
- **Simple**: usable without advanced technical skills.
- **AI-assisted**: works with AI tools (e.g., ChatGPT, Gemini) to create, update, and review documents.
- **Audit-friendly**: structured according to the 13 security measures identified by ENISA in its *Technical Implementation Guidance on Cybersecurity Risk Management Measures*.

## How the Repository is Organized

- **`/_prompts/`** → **Your AI Toolbox**. This is the starting point for all interactions.
  - `onboarding.md` – The first prompt to use in any session to give the AI context.
  - `recipes/` – Contains a "recipe" prompt for each of the 13 security areas.
  - `update_index.md` – A specialized tool for safely updating the master index.
  - `core/` – Contains the "engine" prompts (`Create.md`, `Review.md`, `Update.md`) that the recipes use. You don't need to touch these.

- **`/00_context/`** → General context and status tracking.
  - `config.yaml` – Session mode and assistant behavior configuration (template or real).
  - `company_profile.yaml` – Where you define your company's specific details.
  - `index.md` – The master list of all your documents, their status, and other metadata.

- **`/docs/`** → Where your **final documentation** lives. It's organized into 13 folders, one for each ENISA security measure.

- **`/reference/`** → Official NIS2 and ENISA materials.

- **`/99_evidence/`** (optional) → Where you can store proof of compliance (reports, screenshots, etc.).

## How to Use This Kit

This kit is designed to be used with an AI assistant like Cursor. The workflow is simple and repeatable.

### Step 1: Fill in Your Company Profile
Before you begin, open `/00_context/company_profile.yaml` and fill in your company's details. This is crucial for personalizing the documents.

### Step 2: Start and Onboard Your AI Assistant
Each time you start a new work session, you need to give your AI the project context.
1.  Open your AI assistant (e.g., Cursor).
2.  Copy the entire content of `_prompts/onboarding.md`.
3.  Paste it as your very first message to the AI and send it. The AI will confirm it has understood.

### Step 2a: Select the Mode (Template vs Real)

- Open `/00_context/config.yaml` and set `mode` to `template` or `real`.
- You can override per-session by writing `MODE=template` or `MODE=real` in your first chat message.
- In real mode, the assistant will avoid placeholders, ask you to fill missing fields from `/00_context/company_profile.yaml`, and avoid destructive changes without confirmation.

### Step 3: Create a Document
1.  Go to the `_prompts/recipes/` folder.
2.  Find the "recipe" file that matches the document you want to create (e.g., `01_security_policy.md`).
3.  Ask the AI to create the document using that recipe. For example:
    > "Please create the security policy using the prompt in `@_prompts/recipes/01_security_policy.md`."

The AI will now follow the instructions, read the necessary context files, and generate the document for you in the correct `/docs/` subfolder.

### Step 4: Review and Update the Index
1.  Review the document the AI created.
2.  Ask the AI to help you update the master index. For example:
    > "Now, let's update the index. Use the prompt at `@_prompts/update_index.md` to add the new security policy."

Repeat steps 3 and 4 to incrementally build your full set of NIS2 documentation.

## Design Principles

- **Clarity over complexity** – A simple, clear workflow for non-technical users.
- **Centralized AI Toolbox** – All prompts are in one place (`/_prompts/`) for easy access.
- **Contextual Recipes** – Each recipe in `/_prompts/recipes/` is tailored for a specific security area.
- **Modularity** – The underlying "engine" prompts in `/_prompts/core/` are reusable and easy to maintain.
- **Source-based accuracy** – All advice and generated text should be consistent with `/reference/` materials.

## License

[MIT License](LICENSE) – You are free to use, modify, and share this project.