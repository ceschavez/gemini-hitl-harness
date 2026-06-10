# Human-In-The-Loop (HITL) Harness

A globally installable Gemini CLI skill that transforms a blank repository into a production-ready 4-Phase Human-in-the-Loop Agentic Engineering factory.

## Installation

```bash
git clone https://github.com/cesarchavezcal/gemini-hitl-harness ~/.agents/skills/hitl-harness
```

## Usage

Trigger the setup by typing:
```
/hitl-init
```

### What it does:
This skill scaffolds a robust Agentic Engineering workflow, including:
- **Docs Brain (`docs/` and root `.md` files):** Establishes the source of truth for your architecture, project requirements, and context.
- **Agent Definitions (`.gemini/agents/`):** Sets up specialized subagents (e.g., planner, designer, developer, github-manager, auditor, tester, compound) with distinct responsibilities and file access guardrails.
- **Husky Testing Gate (`.husky/`):** Configures pre-push hooks to ensure code doesn't leave the machine without tests passing, reinforcing local-first verification.

By using this harness, you ensure AI agents follow a strict "Zero-Proactivity Mandate", requiring explicit human approval before moving between the distinct phases: Context & Plan, Implement & Test, Audit & Compound, and Version Control.