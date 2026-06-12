# Project Instructions

## Core Principles
- **Zero-Proactivity Mandate (CRITICAL):** Agents MUST NOT be proactive in starting, planning, or implementing new issues/tasks without explicit user instruction. **Bypassing Phase C (The Human Gate) of the Development Loop is explicitly forbidden.** The system MUST strictly wait for the human operator to type the exact phrase "QA Passed" before proceeding to Phase D (Finalization/Merge). Always ask for permission before moving to the next task in the roadmap.

## Performance & Initialization Mandates
- **Performance Yield Mandate:** Any iteration over local database records (scans, migrations, sync pre-checks) MUST use chunked processing (e.g., batches of 100) and yield to the main thread via \`setTimeout(resolve, 0)\` between chunks to maintain UI responsiveness.
- **Auth Override Warning:** Third-party Auth listeners MUST be attached conditionally and carefully managed to prevent unexpected \`SIGNED_OUT\` events from overriding or clearing local state. Always ensure a fallback to the guest user if no session is active.

<!-- BEGIN HITL HARNESS MANAGED BLOCK -->
## Development Workflow
- Always refer to root \`.md\` files (\`DESIGN.md\`, \`CONTEXT.md\`, etc.) as the source of truth.
- **HITL Lock Mandate:** Agents are strictly forbidden from starting Phase B (Implementation) for any issue until Phase A (Definition) is fully complete (Technical Criteria + Mermaid Diagram) and the user has explicitly typed 'Approved'. No feature branches or PRs should be created before this checkpoint.
- **Coding Mandate:** ONLY the \`developer\`, \`lead-dev\`, and \`tester\` subagents are authorized to write, modify, or scaffold code. The \`tester\` agent is strictly restricted to test files and infrastructure. All other agents (\`planner\`, \`designer\`, \`github-manager\`, \`auditor\`, \`compound\`) are STRICTLY FORBIDDEN from modifying the codebase; they may only update documentation or perform operational tasks.

**The Development Loop (HITL Harness):**
- **Phase A: Definition:** \`planner\` fetches 1 issue -> \`designer\` generates **Detailed Mermaid User Flow** & High-Fidelity UI/UX Specification (via \`/impeccable\` and \`/nothing-design\`) -> \`planner\`+\`lead-dev\` refine & cache -> **USER APPROVAL**.
- **Phase B: Implementation:** \`developer\` builds code matching the **User Flow** and **DESIGN.md** standards -> \`tester\` writes/verifies tests.
- **Phase C: Review & QA (The Human Gate):** \`github-manager\` creates PR -> \`lead-dev\` reviews PR -> **SYSTEM PAUSE**. The agent MUST output manual testing steps for the user.
- **Phase D: Finalization:** (Triggered ONLY by user inputting "QA Passed") -> \`github-manager\` merges PR -> \`compound\`+\`auditor\` update the Documentation Brain -> System asks for permission to start the next issue.
<!-- END HITL HARNESS MANAGED BLOCK -->

## Mandatory Git Identity
All commits and GitHub operations MUST use the authorized Git identity for the project:
- **User:** [AUTHORIZED_USER_NAME]
- **Email:** [AUTHORIZED_USER_EMAIL]

### Zero-Trust Identity Verification
To prevent accidental pushes to incorrect accounts, all agents MUST:
1. **Explicitly scope** all repository creations and clones (e.g., \`gh repo create [USER]/[REPO]\`).
2. **Verify the active account** with \`gh auth status\` before any push or PR creation.
3. **Switch accounts** explicitly if the active user is not correct using \`gh auth switch --user [USER]\`.
4. **Audit remotes** frequently with \`git remote -v\`.

## Systemic Guardrails
- **No Direct Pushes to Main:** NEVER push changes directly to the \`main\` branch. All changes, including documentation and configuration updates, MUST be routed through a feature branch and a Pull Request. There are zero exceptions to this rule.
- **Agent Pre-flight:** Before using any \`run_shell_command\` that touches \`git\`, \`gh\`, or other CLIs, the agent MUST run a "status" command (\`gh auth status\`, \`git config user.name\`, etc.) to verify identity.
- **Issue Cache Mandate:** The issue cache MUST be stored at \`.gemini/cache/issues.cache\`. Use the \`.cache\` extension to ensure visibility to AI agents while bypassing default \`.json\` ignore rules.
- **Mermaid Documentation Mandate:** ALL diagrams (user flows, architecture, state machines, database schemas) MUST be generated using **Mermaid.js** syntax and stored within \`.md\` files in the \`docs/\` directory or root.
