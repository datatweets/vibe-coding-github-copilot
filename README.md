# Vibe Coding with GitHub Copilot — React Developer Course

A two-day intensive course teaching React developers how to use GitHub Copilot effectively and safely in professional workflows. The course progresses from prompting fundamentals to Agent mode, CI/CD automation, and production-ready feature sprints across 15 modules and 3 hands-on labs.

---

## Prerequisites

- Node.js 18+, npm, Git, VS Code
- GitHub account with an active GitHub Copilot subscription
- Working knowledge of React and TypeScript (intermediate level)

---

## Course Structure

### Day 1 — Foundations & First Lab (8 modules, ~7 hours)

| # | Module | Duration | Format |
|---|--------|----------|--------|
| 1 | **Big Picture & Safety Primer** — What vibe coding is, where Copilot fits in the React SDLC, AI strengths/limitations, privacy and IP checklist, Copilot installation and first interaction | 45–60 min | Lecture + Demo |
| 2 | **Prompting Fundamentals** — Persistent instructions vs. task prompts, zero/one/few-shot patterns, Chain-of-Thought reasoning, prompt hygiene and context packing | 45 min | Lecture + Demo |
| 3 | **Advanced Patterns & Workflows** — Problem decomposition, ReAct framework, output style control, iterative refinement, building team `copilot-instructions.md` | 45 min | Lecture + Demo |
| 4 | **GitHub Copilot Deep Dive** — Inline completions, Inline Chat, Chat panel, slash commands, context variables, Agent mode, Copilot Edits, configuration files | 45 min | Lecture + Demo |
| 5 | **Automation & Scripting** — Copilot CLI, shell scripts, npm automation, GitHub Actions for React CI/CD, bulk Agent mode workflows, safe automation design | 45 min | Lecture + Demo |
| 6 | **Lab 1: Scaffold a React Component Library & First Tests** — Vite + TypeScript setup, scaffold `TextInput`/`Select`/`Checkbox` components with Storybook and jest-axe, RTL tests, git workflow | 45 min | **Hands-On Lab** |
| 7 | **Refactor & Debug** — Prompting for refactoring vs. new code, testability refactors, JSDoc generation, debugging with `#terminalLastCommand`, safe experimentation with `git restore` | 45 min | Lecture + Demo |
| 8 | **AI-Driven Quality Assurance** — Coverage-driven test design, BICEP edge case framework, Jest mocks, flaky test diagnosis, property-based testing concepts | 45 min | Lecture + Demo |

### Day 2 — Agents, CI/CD & Production (7 modules, ~6 hours)

| # | Module | Duration | Format |
|---|--------|----------|--------|
| 9 | **AIOps: CI/CD & Release Management** — CI as AI backstop, failure analysis, release note generation, Husky + lint-staged, complete CI workflow design | 45 min | Lecture + Demo |
| 10 | **Agents as Your Team: Foundations** — Agent mode vs. chat, reusable prompt files, four specialized agent roles (planner/reviewer/implementer/tester), scope controls, multi-step orchestration | 45 min | Lecture + Demo |
| 11 | **Agent Mode Applied** — Codebase exploration before action, context variables deep dive, Plan → Approve → Execute cycle, quality gates (TypeScript/ESLint/jest-axe), optional MCP integration | 45 min | Lecture + Demo |
| 12 | **Lab 2: Full Agent Workflow — Plan, Build & Review** — Observe repo, create custom prompt files, plan and implement `PhoneInput` component, run quality gates, draft PR description | 45 min | **Hands-On Lab** |
| 13 | **Parallel Workflows & PR Automation** — Parallel Copilot sessions, git worktrees, Copilot-generated PR descriptions, GitHub Actions quality gates, automated code review | 45 min | Lecture + Demo |
| 14 | **Production React Patterns & Technical Debt** — Error Boundaries, `useMemo`/`useCallback`/`React.memo`/`React.lazy`, ESLint strict mode, `npm audit`, technical debt inventory | 45 min | Lecture + Demo |
| 15 | **Lab 3: Full Feature Sprint** — Decompose `MultiFileUpload` into sub-tasks, scaffold types and hooks, implement drag-and-drop + validation + accessibility, RTL + jest-axe, Error Boundaries, ship via PR | 60 min | **Hands-On Lab** |

---

## Labs Summary

| Lab | Module | Deliverable |
|-----|--------|-------------|
| Lab 1 | 6 | `my-form-library` — `TextInput`, `Select`, `Checkbox` components with Storybook stories, RTL tests, jest-axe, and `copilot-instructions.md` |
| Lab 2 | 12 | `PhoneInput` component added to the library using the full Agent mode Plan → Approve → Execute workflow |
| Lab 3 | 15 | `MultiFileUpload` feature shipped production-ready — drag-and-drop, validation, accessibility, Error Boundary, PR submitted |

---

## Repository Contents

Each module has a student-facing content file and an instructor notes companion:

```
module{N}-{slug}.md            # Student content
module{N}-instructor-notes.md  # Facilitator guide, demo scripts, timing, FAQs
```

---

## Key Tools & Technologies

- **GitHub Copilot** (VS Code extension) — inline completions, Chat, Agent mode, Copilot Edits
- **Vite + React + TypeScript** — project scaffold used across all labs
- **React Testing Library + Jest** — test suite with jest-axe for accessibility
- **Storybook** — component documentation and visual testing
- **Husky + lint-staged** — pre-commit quality gates
- **GitHub Actions** — CI/CD workflows covering test, lint, coverage, and build gates
- **gh CLI** — PR creation and Copilot CLI integration

