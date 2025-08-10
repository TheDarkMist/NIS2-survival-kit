# NIS2-Ready Documentation Toolkit for WordPress Micro-Businesses

## Purpose
This repository provides a **ready-to-use documentation framework** to help **WordPress micro-businesses and freelancers** start and maintain a **NIS2-compliant documentation corpus**.  
It is designed to be:
- **Simple**: usable without advanced technical skills.
- **AI-assisted**: works with AI tools (e.g., ChatGPT, Gemini) to create, update, and review documents.
- **Audit-friendly**: structured according to the 13 security measures identified by ENISA in its *Technical Implementation Guidance on Cybersecurity Risk Management Measures*.

## How the Repository is Organized

- **`/00_context/`** → General context and status tracking  
  - `index.md` – Human-readable list of all documents, their status, and last update date.  
  - `prompt_update_index.md` – AI prompt for updating the index.  

- **`/docs/`** → 13 folders, one for each ENISA security measure  
  Each folder contains:
  - Documentation files (policies, procedures, registers).  
  - Templates to help create new documents.  
  - AI prompts specific to that security measure.

- **`/reference/`** → Official NIS2 and ENISA materials  
  - PDF copies of relevant guidelines (digital text format, not scans).  
  - Short summaries and quick reference notes.

- **`/99_evidence/`** (optional) → Proof of compliance (reports, screenshots, logs).

## How Humans Should Use It

1. Open `/00_context/index.md` to see what is done, what is in progress, and what is missing.
2. Open the relevant `/docs/{area}/` folder and review or edit the documents.
3. Use the prompts inside each folder to:
   - Create a missing document.
   - Update an existing one.
4. When you change or create a document, **update `/00_context/index.md`** manually or with the help of AI using `prompt_update_index.md`.

## How AI Should Use It

When assisting a user with this repository:

1. **Read `/00_context/index.md`** to understand the current state of the documentation.
2. **Focus on the relevant `/docs/{area}/` folder** based on the task.
3. **Consult `/reference/`** for official guidance and ensure compliance with NIS2 and ENISA best practices.
4. When creating or updating documents:
   - Use Markdown format.
   - Keep filenames and folder structure unchanged.
   - Maintain the document in the user's preferred language (default: English).
5. When a document changes, **propose an updated `/00_context/index.md`** snippet ready to paste.
6. Always clearly mark when a document is **draft**, **in review**, **completed**, or **retired**.
7. **For initial document creation**, use `docs/_prompts/en/Bootstrap.md` to generate the minimal required document set.

## Quick Start

### For New Users
1. **Start with Bootstrap**: Use `docs/_prompts/en/Bootstrap.md` to create your initial NIS2 document set
2. **Review generated documents**: Check the created policies and procedures in their respective folders
3. **Customize content**: Update company-specific information and adjust to your business needs
4. **Update the index**: Use `prompt_update_index.md` to register all new documents

### For Existing Users
1. Open `/00_context/index.md` to see what is done, what is in progress, and what is missing.
2. Open the relevant `/docs/{area}/` folder and review or edit the documents.
3. Use the prompts inside each folder to:
   - Create a missing document.
   - Update an existing one.
4. When you change or create a document, **update `/00_context/index.md`** manually or with the help of AI using `prompt_update_index.md`.

## Design Principles

- **Clarity over complexity** – minimal technical barriers for micro-business users.
- **Contextual prompts** – each ENISA area has its own AI prompts to generate relevant content.
- **Modularity** – each folder can be used independently.
- **Source-based accuracy** – all advice and generated text should be consistent with `/reference/` materials.

## License

[MIT License](LICENSE) – You are free to use, modify, and share this project.