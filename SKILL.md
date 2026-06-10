---
name: hitl-harness
description: Zero-proactivity 4-phase Agentic Engineering loop and documentation scaffold.
---

# HITL Harness Skill

A globally installable Gemini CLI skill that transforms any blank repository into a production-ready Agentic Engineering factory.

## Usage
When the user runs `/hitl-init` (or when invoked directly to initialize the harness):

1. **Context Gathering**
   - Use `ask_user` to query the user's frontend and backend tech stack. (e.g., "What is your frontend stack? What is your backend stack?").

2. **Recommend Variable Skills**
   - Use the `find-skills` tool (or run a shell command against the global skills registry) using the user's stack as keywords.
   - Review the returned list of available official/community skills.
   - Use the `ask_user` tool to present a multiple-choice checklist of the most relevant skills found for their tech stack.
   - For every skill the user selects, use `run_shell_command` to execute `gemini skills install [skill-name]`.

3. **Scaffold Documentation Brain**
   - Copy the files from `templates/` to the project root:
     - `GEMINI.template.md` -> `GEMINI.md`
     - `CONTEXT.template.md` -> `CONTEXT.md`
     - `DESIGN.template.md` -> `DESIGN.md`
     - `SKILLS.template.md` -> `SKILLS.md`
     - `AGENTS.template.md` -> `AGENTS.md`
     - `MEMORY.template.md` -> `MEMORY.md`
   - Create directories: `docs/compounding/` and `.gemini/agents/`.
   - Ensure the managed block tags `<!-- BEGIN HITL HARNESS MANAGED BLOCK -->` are preserved in `GEMINI.md`.

4. **Configure Agents**
   - Copy the agent profiles from `agents/` to `.gemini/agents/`.
   - Dynamically inject the skills the user selected in Step 2 into the `skills:` array of `.gemini/agents/developer.md` and `.gemini/agents/tester.md`.

5. **Setup Zero-Cost Testing Gate**
   - Use `run_shell_command` to run:
     - `npm i -D husky`
     - `npx husky init`
   - Modify `.husky/pre-push` to execute `npm run test` to enforce the zero-cost testing gate.
   - Remove or rename the default `pre-commit` to prevent slow commits.

## Commands

### `/hitl-sync-down`
Pulls the latest workflow from the core `hitl-harness` repo into an older project. Finds the `<!-- BEGIN HITL HARNESS MANAGED BLOCK -->` in the project's `GEMINI.md` and replaces it with the updated version from the global skill `templates/GEMINI.template.md`.

### `/hitl-sync-up`
Exports workflow improvements from the current project back to the global skill. Reads the current project's `GEMINI.md`, extracts the `<!-- BEGIN HITL HARNESS MANAGED BLOCK -->`, updates the global `templates/GEMINI.template.md`, commits the change to the skill's GitHub repo, and pushes it.