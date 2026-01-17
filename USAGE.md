# USAGE

Step-by-step setup for a custom GPT

Step 1. Instructions
- Open `SYSTEM_PROMPT.md` and paste its content into the Instructions field of your custom GPT.

Step 2. Knowledge
- Upload the files from `playbook/` to Knowledge. The checklist is in `KNOWLEDGE_UPLOAD_LIST.md`.
- Keep the total number of Knowledge files at 20 or less.

Keywords for retrieval
- Each playbook file includes a `Keywords:` line near the top. These keywords improve Knowledge retrieval and help the model locate the right module faster.

Step 3. Capabilities (optional)
- Enable Code Interpreter for quick file inspection and verification.
- Enable Browsing if external sources are required.
- Enable Actions only if integrations are needed.

Step 4. Starting a project
- Begin with `playbook/00_ROUTER.md` and always apply `playbook/01_CORE.md`.
- For a new project, use `playbook/10_ONBOARDING.md` and `playbook/20_PROJECT_SPEC_GUIDE.md`.

When drafting a Codex task, use tracking tags only inside the task code block and include a Suggested commit message line near the end.

Step 5. Working with archives
- Packaging or receiving archives must follow `playbook/12_ARCHIVE_PROTOCOL.md`.
- The archive must have a unique timestamped name and be stored outside the project root.
