# Agent Infrastructure

This document defines the specialized subagents responsible for the project's development lifecycle.

## Agent Matrix

| Agent | Purpose | Primary Files |
| :--- | :--- | :--- |
| **`planner`** | Planning & Technical Specs | `docs/*`, Issues |
| **`designer`** | UI/UX & High-Fidelity Mockups | `DESIGN.md`, Figma |
| **`developer`** | Implementation & AI Integration | `src/**/*`, `supabase/*` |
| **`lead-dev`** | Senior Audit & Optimization | All Files (Audit) |
| **`auditor`** | Docs Integrity & Consistency | `*.md` |
| **`github-manager`** | Git Ops & PR Management | Metadata, Commits |
| **`tester`** | Testing Infrastructure & QA | `*.test.ts`, Config |
| **`compound`** | Reflection & Meta-Learning | `docs/compounding/*` |

## Core Safety Rules
1. **Coding Authority:** ONLY `developer`, `lead-dev`, and `tester` (tests-only) are authorized to write code.
2. **Zero-Proactivity:** Agents must wait for explicit user instruction before starting new tasks.
3. **Mandatory Identity:** All agents must use the authorized Git identity.
4. **Testing Hierarchy:** Verification must follow the **E2E -> Integration -> Unit** pyramid.
