<div style="text-align:center; padding: 20px 0;">
<span style="font-size:14px; color:#666666; font-weight:bold; letter-spacing:2px;">MODULE 10</span>

# <span style="color:#0D47A1;">Agents as Your Team: Foundations</span>

<hr style="border: 3px solid #1A73E8; width:80%;">
</div>

<table style="width:100%; border-collapse:collapse;">
<tr>
<td style="background:#E3F2FD; text-align:center; padding:10px; border:1px solid #BBDEFB; width:25%;"><span style="font-size:12px; color:#666;">Duration</span><br><strong style="color:#0D47A1;">45 min</strong></td>
<td style="background:#E3F2FD; text-align:center; padding:10px; border:1px solid #BBDEFB; width:25%;"><span style="font-size:12px; color:#666;">Format</span><br><strong style="color:#0D47A1;">Lecture + Demo</strong></td>
<td style="background:#E3F2FD; text-align:center; padding:10px; border:1px solid #BBDEFB; width:25%;"><span style="font-size:12px; color:#666;">Audience</span><br><strong style="color:#0D47A1;">React Developers</strong></td>
<td style="background:#E3F2FD; text-align:center; padding:10px; border:1px solid #BBDEFB; width:25%;"><span style="font-size:12px; color:#666;">Day / Position</span><br><strong style="color:#0D47A1;">Day 2 / Second</strong></td>
</tr>
</table>

---

## <span style="color:#1A73E8;">LEARNING OBJECTIVES</span>

1. Explain what Copilot Agent mode is and how it differs from standard Copilot chat and inline completions
2. Create reusable prompt files (`*.prompt.md`) and custom instruction files for specialized agent roles
3. Design a team of four specialized Copilot roles: planner, reviewer, implementer, tester — each with a scoped prompt file
4. Apply scope controls and safety guardrails: context variables, read-only prompts, model selection, confirmation gates
5. Orchestrate multi-step agent workflows using npm scripts, sequential prompt chaining, and human escalation gates
6. Use VS Code background tasks and the Copilot agent task queue for long-running autonomous work

---

<table style="width:100%; border-collapse:collapse;">
<tr><td style="background:#00695C; color:white; padding:8px 14px; width:120px; font-weight:bold; font-size:13px;">0:00 – 0:08</td><td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Section 1: What Are Agent Workflows?</td></tr>
<tr><td colspan="2" style="height:4px;"></td></tr>
<tr><td style="background:#00695C; color:white; padding:8px 14px; font-weight:bold; font-size:13px;">0:08 – 0:18</td><td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Section 2: Prompt Files & Custom Instructions — Copilot's Agent Configuration System</td></tr>
<tr><td colspan="2" style="height:4px;"></td></tr>
<tr><td style="background:#00695C; color:white; padding:8px 14px; font-weight:bold; font-size:13px;">0:18 – 0:28</td><td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Section 3: Guardrails, Scope & Safety in Agent Mode</td></tr>
<tr><td colspan="2" style="height:4px;"></td></tr>
<tr><td style="background:#00695C; color:white; padding:8px 14px; font-weight:bold; font-size:13px;">0:28 – 0:37</td><td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Section 4: Orchestrating Multi-Step Agent Workflows</td></tr>
<tr><td colspan="2" style="height:4px;"></td></tr>
<tr><td style="background:#00695C; color:white; padding:8px 14px; font-weight:bold; font-size:13px;">0:37 – 0:43</td><td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Section 5: VS Code Tasks & Practical Agent Patterns</td></tr>
<tr><td colspan="2" style="height:4px;"></td></tr>
<tr><td style="background:#00695C; color:white; padding:8px 14px; font-weight:bold; font-size:13px;">0:43 – 0:45</td><td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Wrap-Up: Quick Reference & Transition to Module 11</td></tr>
</table>

---

## <span style="color:#0D47A1;">1. What Are Agent Workflows?</span>

### <span style="color:#0D47A1;">1.1  From Single Prompt to Autonomous Team</span>

Yesterday's Copilot: you ask a question, you get an answer. Today's Copilot Agent mode: you describe a goal, Copilot plans the steps, executes them autonomously — reading files, running commands, writing code, looping until done.

<table style="width:100%; border-collapse:collapse;">
<tr><td style="background:#0D47A1; color:white; padding:10px 12px; font-weight:bold;">Standard Copilot Chat</td><td style="background:#0D47A1; color:white; padding:10px 12px; font-weight:bold;">Copilot Agent Mode</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">One question → one answer</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">One goal → autonomous multi-step execution</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;">You manage the conversation flow</td><td style="padding:10px 12px; border:1px solid #CCC;">Copilot plans and self-manages steps</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Reads what you provide</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Explores the workspace (`#codebase`, terminal, tests)</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;">Suggests edits for one file</td><td style="padding:10px 12px; border:1px solid #CCC;">Edits multiple files, runs commands, validates results</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Stops after one response</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Loops: plan → execute → verify → revise → done</td></tr>
</table>

**Activate Agent mode:** In Copilot Chat, click the mode dropdown (shows "Ask" by default) and select **Agent**. Or type `/agent` at the start of your message.

### <span style="color:#0D47A1;">1.2  The Agent Team Model</span>

Instead of one generalist AI handling everything, structure your work across specialized roles — each with its own prompt, scope, and responsibility boundary.

<table style="width:100%; border-collapse:collapse;">
<tr><td style="background:#00695C; color:white; padding:10px 12px; font-weight:bold;">Role</td><td style="background:#00695C; color:white; padding:10px 12px; font-weight:bold;">Job</td><td style="background:#00695C; color:white; padding:10px 12px; font-weight:bold;">Context Variables Used</td><td style="background:#00695C; color:white; padding:10px 12px; font-weight:bold;">Writes Files?</td></tr>
<tr><td style="background:#E0F2F1; padding:10px 12px; border:1px solid #CCC;"><strong>Planner</strong></td><td style="background:#E0F2F1; padding:10px 12px; border:1px solid #CCC;">Explore codebase, produce implementation plan</td><td style="background:#E0F2F1; padding:10px 12px; border:1px solid #CCC;"><code>#codebase</code>, <code>@workspace</code></td><td style="background:#E0F2F1; padding:10px 12px; border:1px solid #CCC;">No — read only</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><strong>Reviewer</strong></td><td style="padding:10px 12px; border:1px solid #CCC;">Analyze PR diff for bugs, security, coverage</td><td style="padding:10px 12px; border:1px solid #CCC;"><code>#changes</code>, <code>#file</code></td><td style="padding:10px 12px; border:1px solid #CCC;">No — produces report</td></tr>
<tr><td style="background:#E0F2F1; padding:10px 12px; border:1px solid #CCC;"><strong>Implementer</strong></td><td style="background:#E0F2F1; padding:10px 12px; border:1px solid #CCC;">Write code per plan, run tests to verify</td><td style="background:#E0F2F1; padding:10px 12px; border:1px solid #CCC;"><code>#file</code>, <code>#codebase</code>, terminal</td><td style="background:#E0F2F1; padding:10px 12px; border:1px solid #CCC;">Yes — full edit</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><strong>Tester</strong></td><td style="padding:10px 12px; border:1px solid #CCC;">Generate tests, run Jest, report coverage gaps</td><td style="padding:10px 12px; border:1px solid #CCC;"><code>#file</code>, <code>#codebase</code>, terminal</td><td style="padding:10px 12px; border:1px solid #CCC;">Yes — test files only</td></tr>
</table>

<table style="width:100%; border-collapse:collapse;"><tr><td style="border-left:5px solid #1A73E8; background:#E3F2FD; padding:14px 18px;"><strong style="color:#0D47A1;">⭐ KEY POINT:</strong> <span style="color:#0D47A1;">Each role has a scoped context and a clear output artifact. The Planner produces a <code>PLAN.md</code>. The Reviewer produces a <code>REVIEW.md</code>. The Implementer writes code. The Tester writes tests. Separate roles = cleaner handoffs = more predictable outputs.</span></td></tr></table>

---

## <span style="color:#0D47A1;">2. Prompt Files & Custom Instructions — Copilot's Agent Configuration System</span>

### <span style="color:#0D47A1;">2.1  Three Configuration Layers</span>

GitHub Copilot's equivalent of named subagent configuration is a layered system:

<table style="width:100%; border-collapse:collapse;">
<tr><td style="background:#1A73E8; color:white; padding:10px 12px; font-weight:bold;">Layer</td><td style="background:#1A73E8; color:white; padding:10px 12px; font-weight:bold;">File Location</td><td style="background:#1A73E8; color:white; padding:10px 12px; font-weight:bold;">Scope</td><td style="background:#1A73E8; color:white; padding:10px 12px; font-weight:bold;">When It Applies</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><strong>Global instructions</strong></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><code>.github/copilot-instructions.md</code></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Entire repo</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Every Copilot interaction in this repo</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><strong>Path instructions</strong></td><td style="padding:10px 12px; border:1px solid #CCC;"><code>.github/instructions/*.instructions.md</code></td><td style="padding:10px 12px; border:1px solid #CCC;">File-path pattern</td><td style="padding:10px 12px; border:1px solid #CCC;">Only when editing matching files (set via <code>applyTo</code>)</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><strong>Reusable prompts</strong></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><code>.github/prompts/*.prompt.md</code></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">On-demand</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">When you invoke the prompt by name in Chat</td></tr>
</table>

### <span style="color:#0D47A1;">2.2  Global Instructions File</span>

This is always-on context for your entire repo. Think of it as the system prompt for every Copilot interaction.

```markdown
<!-- .github/copilot-instructions.md -->
# my-form-library — Copilot Instructions

## Project Context
React component library with TypeScript. Components live in `src/components/`.
Tests use Jest + React Testing Library. Storybook for visual documentation.

## Coding Standards
- TypeScript strict mode — no `any` types. Use `unknown` and narrow with type guards.
- Functional components only — no class components.
- Custom hooks go in `src/hooks/`. Utility functions in `src/utils/`.
- Every exported component requires a `*.stories.tsx` file.
- Export components from `src/index.ts` — named exports only, no default exports.

## Testing Standards
- Minimum 80% line coverage for all components in `src/components/`.
- Test user behavior, not implementation. Use `getByRole`, `getByLabelText`.
- Never use `getByTestId` unless there is no accessible alternative.

## What Copilot Should Never Do
- Never auto-push to `main`. Always suggest branch + PR workflow.
- Never remove existing tests to make coverage pass.
- Never introduce `any` to fix a TypeScript error — fix the type.
```

### <span style="color:#0D47A1;">2.3  Path-Specific Instruction Files</span>

Instruction files with `applyTo` frontmatter activate only when editing files in the matched path. This is how you create "specialist" behavior for specific parts of the codebase.

```markdown
<!-- .github/instructions/components.instructions.md -->
---
applyTo: "src/components/**"
---

## Component Development Rules

When creating or editing React components in `src/components/`:

1. **Accessibility first** — every interactive element needs ARIA labels.
   Use `aria-label`, `aria-describedby`, `role` attributes appropriately.
2. **Props interface** — define a `Props` interface above the component.
   Export it: `export interface ButtonProps { ... }`
3. **Error boundaries** — wrap async data-fetching components in an ErrorBoundary.
4. **No inline styles** — use CSS modules (`*.module.css`) or Tailwind classes.
5. **Storybook** — after creating a component, create `ComponentName.stories.tsx`
   with at least a `Default` and a `WithError` story.
```

```markdown
<!-- .github/instructions/tests.instructions.md -->
---
applyTo: "src/**/*.test.{ts,tsx}"
---

## Test Writing Rules

When writing or editing tests in this repo:

1. Arrange-Act-Assert structure — one assertion concept per test.
2. Wrap async operations in `waitFor()` from Testing Library.
3. Use `userEvent` over `fireEvent` for user interactions (closer to real browser).
4. Mock external modules in `__mocks__/` — never inline `jest.mock()` in test files.
5. Use descriptive test names: `it("shows error message when email is invalid")`.
```

### <span style="color:#0D47A1;">2.4  Reusable Prompt Files — Named Agent Roles</span>

Prompt files are the direct equivalent of named subagents. Each file defines a role, its mode, and its system prompt. Invoke them by typing `/` in Copilot Chat and selecting the prompt name.

If a prompt file does not appear in the `/` menu, use the same content manually: open the `.prompt.md` file, paste the prompt body into Copilot Chat, and replace any variables or placeholders yourself. Then verify the file is under `.github/prompts/`, ends in `.prompt.md`, and reload VS Code before trying the slash command again.

The `/plan`, `/review`, `/implement`, and `/test` commands in this module are not built-in Copilot commands. You create them below as team prompt files, and VS Code exposes each file name as a slash-command entry.

**The Planner — Read-Only Exploration:**

```markdown
<!-- .github/prompts/plan.prompt.md -->
---
mode: ask
description: Explore the codebase and produce a numbered implementation plan
             for a requested feature. Read-only — produces a plan document only.
---

You are a senior React architect performing codebase exploration.

Your job is to produce a concrete implementation plan — NOT to write code.

## Steps
1. Use `#codebase` to explore the relevant files and understand existing patterns.
2. Identify which files need to be created or modified.
3. Check `src/index.ts` for existing exports to avoid naming conflicts.
4. Review existing tests to understand what patterns are already established.

## Output Format
Produce a `PLAN.md` file with:
- **Goal:** one-sentence summary
- **Files to create:** list with purpose
- **Files to modify:** list with what changes
- **Implementation steps:** numbered, actionable
- **Test cases to add:** list of describe/it structures
- **Risk flags:** anything that may break existing behavior

Do NOT write any implementation code. The Implementer will handle that.
```

**The Reviewer — Automated Code Review:**

```markdown
<!-- .github/prompts/review.prompt.md -->
---
mode: ask
description: Review changed files for bugs, TypeScript issues, accessibility
             violations, missing tests, and React best practices. Produces REVIEW.md.
---

You are a senior React code reviewer. You review diffs for quality and safety.

## Review Checklist
Run through every changed file and check:

**TypeScript**
- [ ] No `any` types introduced
- [ ] All function parameters and return values typed
- [ ] No type assertions (`as SomeType`) without a comment explaining why

**React**
- [ ] Hooks called at top level only (no conditional hooks)
- [ ] `useEffect` dependencies array is complete and correct
- [ ] Memoization (`useMemo`, `useCallback`) used only where measurably needed
- [ ] No prop drilling more than 2 levels deep (suggest Context or state management)

**Accessibility**
- [ ] Interactive elements have ARIA labels or accessible names
- [ ] Color is not the only indicator of state (add icons or text)
- [ ] Keyboard navigation works (focus management, tab order)

**Testing**
- [ ] New logic has corresponding tests
- [ ] Tests cover the error/edge case path, not just the happy path

## Output Format
Produce a `REVIEW.md` with findings grouped by file, severity (Critical / Warning / Suggestion).
```

**The Implementer — Focused Code Writing:**

```markdown
<!-- .github/prompts/implement.prompt.md -->
---
mode: agent
description: Implement a feature or fix using an existing PLAN.md as the blueprint.
             Runs tests after each file change to verify correctness.
---

You are a React TypeScript implementer. You write code that matches the plan exactly.

## Rules
1. Read `PLAN.md` first. Follow it precisely — do not improvise.
2. Create one file at a time. Run `npm test -- <filename>` after each.
3. If a test fails, fix the implementation — do not modify the test to make it pass.
4. All new TypeScript must have strict types. Run `npx tsc --noEmit` after completing all files.
5. Do not modify files not listed in the plan without flagging it as a deviation.
6. When complete, run `npm run lint && npm test -- --coverage` and report the results.

## Done Criteria
- All tests pass
- `tsc --noEmit` exits 0
- ESLint exits 0 with 0 warnings
- Coverage did not decrease from the baseline
```

**The Tester — Test-First Coverage:**

```markdown
<!-- .github/prompts/test.prompt.md -->
---
mode: agent
description: Generate comprehensive Jest + React Testing Library tests for a component
             or utility. Runs coverage and reports gaps. Never modifies implementation.
---

You are a React test engineer. Your only job is writing tests.

## Steps
1. Read the target file (`#file` reference).
2. Identify all exported functions, components, and edge cases.
3. Write tests in `<filename>.test.tsx` using Jest + React Testing Library.
4. Run `npm test -- --coverage <filename>` to check coverage.
5. If branch coverage is below 80%, add tests to cover the missing branches.
6. Report final coverage numbers and any branches that are genuinely untestable.

## Test Quality Rules
- Every `it()` block tests exactly one behavior.
- Use `userEvent.type()`, `userEvent.click()` — not `fireEvent`.
- Test what the user sees, not implementation details (no `.instance()`, no testing state).
- Every async interaction is wrapped in `await waitFor()` or `await screen.findBy*()`.

Do NOT modify any implementation files. If a bug is found, report it — don't fix it.
```

<table style="width:100%; border-collapse:collapse;"><tr><td style="border-left:5px solid #1A73E8; background:#E3F2FD; padding:14px 18px;"><strong style="color:#0D47A1;">⭐ KEY POINT:</strong> <span style="color:#0D47A1;">Prompt files use YAML frontmatter (<code>mode</code>, <code>description</code>) just like any configuration system. The <code>description</code> field is shown in the Copilot Chat prompt picker — write it so any teammate can understand when to use this prompt without reading the full file.</span></td></tr></table>

---

## <span style="color:#0D47A1;">3. Guardrails, Scope & Safety in Agent Mode</span>

### <span style="color:#0D47A1;">3.1  Context Variables as Scope Control</span>

The context you give Agent mode determines what it can "see" and therefore what it can touch. This is your primary safety lever.

<table style="width:100%; border-collapse:collapse;">
<tr><td style="background:#1A73E8; color:white; padding:10px 12px; font-weight:bold;">Context Variable</td><td style="background:#1A73E8; color:white; padding:10px 12px; font-weight:bold;">What It Includes</td><td style="background:#1A73E8; color:white; padding:10px 12px; font-weight:bold;">Use For</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><code>#selection</code></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Currently highlighted code</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Narrowest scope — one function or block</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><code>#file</code></td><td style="padding:10px 12px; border:1px solid #CCC;">One specific file</td><td style="padding:10px 12px; border:1px solid #CCC;">Working on one component or utility</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><code>#changes</code></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">All uncommitted git changes</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Reviews, commit message generation</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><code>#codebase</code></td><td style="padding:10px 12px; border:1px solid #CCC;">Full workspace (indexed)</td><td style="padding:10px 12px; border:1px solid #CCC;">Architecture planning, cross-cutting changes</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><code>@workspace</code></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">All workspace files (semantic search)</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Finding related code across the repo</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><code>#terminalLastCommand</code></td><td style="padding:10px 12px; border:1px solid #CCC;">Last terminal output</td><td style="padding:10px 12px; border:1px solid #CCC;">Failure analysis, build error diagnosis</td></tr>
</table>

**Practical scoping rule:** Start narrow (`#file`), expand only if the agent needs more context. An agent that can see everything has the surface area to change everything.

### <span style="color:#0D47A1;">3.2  Agent Mode Confirmation Gates</span>

Agent mode shows a confirmation panel before executing terminal commands and before writing files. **Never click "Allow Always" for destructive commands.** Build the habit of reviewing before approving.

```text
# Copilot Agent mode will prompt:
# "I'd like to run: npm test -- --coverage"  → ✅ Safe: read-only analysis
# "I'd like to run: git push origin main"     → ❌ Review carefully  
# "I'd like to edit: src/index.ts"            → ✅ Review diff before accepting
# "I'd like to run: rm -rf node_modules"      → ❌ Reject — unnecessary destructive op
```

<table style="width:100%; border-collapse:collapse;"><tr><td style="border-left:5px solid #C62828; background:#FFEBEE; padding:14px 18px; border:1px solid #EF9A9A;"><strong style="color:#C62828;">⚠️ WARNING:</strong> <span style="color:#C62828;">The "Allow Always" option in Agent mode disables confirmation for a command pattern across the session. Only use it for known-safe, idempotent operations like <code>npm test</code> or <code>npx tsc --noEmit</code>. Never use "Allow Always" for commands that write to disk, push to remotes, or delete files.</span></td></tr></table>

### <span style="color:#0D47A1;">3.3  Model Selection for Task Complexity</span>

Copilot supports multiple models. Match the model to the cognitive demand of the task — not every task needs the most powerful model.

<table style="width:100%; border-collapse:collapse;">
<tr><td style="background:#0D47A1; color:white; padding:10px 12px; font-weight:bold;">Task</td><td style="background:#0D47A1; color:white; padding:10px 12px; font-weight:bold;">Recommended Model</td><td style="background:#0D47A1; color:white; padding:10px 12px; font-weight:bold;">Why</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Architectural planning, complex refactors, security analysis</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Claude Sonnet 4.5 / GPT-4o</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Deep reasoning, broad context</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;">Code review, feature implementation, test generation</td><td style="padding:10px 12px; border:1px solid #CCC;">Claude Sonnet / GPT-4o mini</td><td style="padding:10px 12px; border:1px solid #CCC;">Balanced quality + speed</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Rename symbols, format checks, simple completions</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Default (smallest available)</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Fast, low latency, token-efficient</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;">Multi-file architecture, design tradeoff analysis</td><td style="padding:10px 12px; border:1px solid #CCC;">o3 / o4-mini (reasoning models)</td><td style="padding:10px 12px; border:1px solid #CCC;">Chain-of-thought for complex decisions</td></tr>
</table>

Switch models in Copilot Chat via the model dropdown in the top-right of the Chat panel.

### <span style="color:#0D47A1;">3.4  Read-Only Prompt Patterns</span>

Some prompt files should be "safe to run without supervision" because they never write files. Enforce this in the prompt body:

```markdown
<!-- In plan.prompt.md and review.prompt.md system prompts: -->

IMPORTANT CONSTRAINTS:
- Do NOT create, edit, or delete any files.
- Do NOT run `git add`, `git commit`, or `git push`.
- Do NOT run `npm install` or modify `package.json`.
- Your ONLY output is a Markdown analysis document written to stdout.
- If you need to run a command, ask for permission first.
```

---

## <span style="color:#0D47A1;">4. Orchestrating Multi-Step Agent Workflows</span>

### <span style="color:#0D47A1;">4.1  Sequential Prompt Chaining</span>

Agent workflows chain prompt files: each role completes its task and produces an artifact that becomes the input for the next role.

```text
User: "/plan Add a date-picker component to my-form-library"
  → Copilot (Planner prompt) explores codebase → produces PLAN.md

User: "/implement" (with PLAN.md in context via #file:PLAN.md)
  → Copilot (Implementer prompt) reads PLAN.md → writes DatePicker.tsx + DatePicker.test.tsx

User: "/test #file:src/components/DatePicker.tsx"
  → Copilot (Tester prompt) reads component → runs coverage → adds missing tests

User: "/review #changes"
  → Copilot (Reviewer prompt) reads all diffs → produces REVIEW.md
```

**Key principle:** Each handoff uses a file artifact. `PLAN.md` → implementation input. `REVIEW.md` → PR description. Never chain by "remembering" — always write the artifact to disk and reference it explicitly.

### <span style="color:#0D47A1;">4.2  npm Scripts as Workflow Orchestrators</span>

Wrap multi-step agent workflows in npm scripts so the entire team can run them consistently:

```jsonc
// package.json — agent workflow scripts
{
  "scripts": {
    "agent:review": "echo 'Open Copilot Chat → run /review with #changes'",
    "agent:fullcheck": "npm run lint && npm run typecheck && npm test -- --coverage",
    "agent:prepare-pr": "npm run agent:fullcheck && gh pr create --draft --title 'Draft: ' --body-file REVIEW.md",

    "lint": "eslint src/ --max-warnings 0",
    "typecheck": "tsc --noEmit",
    "test": "jest",
    "test:coverage": "jest --coverage --coverageThreshold='{\"global\":{\"lines\":80}}'",
    "storybook": "storybook dev -p 6006"
  }
}
```

**Pre-flight check before invoking Implementer:**

```bash
#!/bin/bash
# scripts/pre-implement.sh
# Run before invoking the Implementer prompt to ensure a clean baseline.

set -e

echo "=== Pre-implementation check ==="
echo "1. TypeScript..."
npx tsc --noEmit

echo "2. Lint..."
npm run lint

echo "3. Tests..."
npm test -- --ci --passWithNoTests

echo "4. Checking for PLAN.md..."
if [ ! -f "PLAN.md" ]; then
  echo "ERROR: PLAN.md not found. Run /plan first."
  exit 1
fi

echo "✅ Baseline clean. Safe to run /implement"
```

Run it before every implementation session:

```bash
chmod +x scripts/pre-implement.sh
bash scripts/pre-implement.sh
```

### <span style="color:#0D47A1;">4.3  Loop Exit Criteria & Retry Patterns</span>

Agent mode can get stuck in loops. Define explicit done criteria in every agent prompt so Copilot knows when to stop.

```markdown
<!-- In implement.prompt.md — add explicit exit criteria: -->

## Exit Criteria (STOP when ALL of these are true)
- [ ] `npx tsc --noEmit` exits 0
- [ ] `npm run lint` exits 0
- [ ] `npm test -- --ci` exits 0
- [ ] All files in PLAN.md have been created or modified

## Retry Limit
If tests still fail after 3 fix attempts on the same file, STOP and report:
- What was tried
- What the current error is
- What human input is needed

Do NOT loop more than 3 times on any single failing test.
```

**Human escalation gate in CI:**

```yaml
# .github/workflows/agent-implement.yml
name: AI Implementation Gate

on:
  pull_request:
    paths: ['src/**']

jobs:
  validate-ai-work:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with: { node-version: '20', cache: 'npm' }
      - run: npm ci
      - name: Type check
        run: npx tsc --noEmit
      - name: Lint (zero warnings)
        run: npm run lint
      - name: Tests with coverage
        run: npm test -- --ci --coverage --coverageThreshold='{"global":{"lines":80}}'
      - name: Block if PLAN.md still in repo
        run: |
          if [ -f "PLAN.md" ]; then
            echo "::error::PLAN.md found in PR. Remove it before merging."
            exit 1
          fi
```

<table style="width:100%; border-collapse:collapse;"><tr><td style="border-left:5px solid #1A73E8; background:#E3F2FD; padding:14px 18px;"><strong style="color:#0D47A1;">⭐ KEY POINT:</strong> <span style="color:#0D47A1;">CI is your final safety net — it validates agent-produced code the same way it validates human-written code. An agent workflow that skips CI is unacceptably risky. The CI gate is non-negotiable.</span></td></tr></table>

### <span style="color:#0D47A1;">4.4  Committing Agent Work Safely</span>

Agent mode produces real file changes. Follow the same discipline as any other change:

```bash
# After Implementer prompt completes:

# 1. Review every changed file before adding
git diff src/

# 2. Stage selectively — not git add .
git add src/components/DatePicker.tsx
git add src/components/DatePicker.test.tsx
git add src/components/DatePicker.stories.tsx

# 3. Write a clear commit message attributing AI assistance
git commit -m "feat(forms): add DatePicker component

- Implements controlled date input with validation
- Accessibility: ARIA labels, keyboard navigation, role=spinbutton
- Tests: 14 cases, 89% branch coverage

Co-authored-by: GitHub Copilot <copilot@github.com>"

# 4. Open a PR — never push direct to main
git push origin feat/date-picker
gh pr create --title "feat(forms): DatePicker component" \
  --body-file REVIEW.md \
  --label "ai-assisted"
```

Using the `ai-assisted` label on PRs creates a searchable history of AI-generated work. This is useful for audits, training, and understanding where agent patterns work well.

---

## <span style="color:#0D47A1;">5. VS Code Tasks & Practical Agent Patterns</span>

### <span style="color:#0D47A1;">5.1  VS Code Tasks for Background Agent Work</span>

Long-running agent workflows (scanning the full codebase, running full test suites) should run as VS Code background tasks — not blocking your editor session.

```jsonc
// .vscode/tasks.json
{
  "version": "2.0.0",
  "tasks": [
    {
      "label": "Watch: TypeScript",
      "type": "npm",
      "script": "typecheck:watch",
      "isBackground": true,
      "group": "build",
      "presentation": { "panel": "dedicated", "reveal": "never" },
      "problemMatcher": "$tsc-watch"
    },
    {
      "label": "Watch: Tests",
      "type": "npm",
      "script": "test:watch",
      "isBackground": true,
      "group": "test",
      "presentation": { "panel": "dedicated", "reveal": "never" }
    },
    {
      "label": "Agent: Pre-Implement Check",
      "type": "shell",
      "command": "bash scripts/pre-implement.sh",
      "group": "test",
      "presentation": { "panel": "shared", "reveal": "always" },
      "problemMatcher": []
    },
    {
      "label": "Agent: Full Validation",
      "type": "npm",
      "script": "agent:fullcheck",
      "group": "test",
      "presentation": { "panel": "shared", "reveal": "always" }
    }
  ]
}
```

**Run a background task:** `Cmd+Shift+P` → `Tasks: Run Task` → select task. The task runs in a dedicated terminal panel and does not block your current editor window.

**Add package.json watch scripts:**

```json
{
  "scripts": {
    "typecheck:watch": "tsc --noEmit --watch",
    "test:watch": "jest --watch"
  }
}
```

With both watch tasks running in background, you get real-time feedback on TypeScript errors and test failures while Agent mode is writing code.

### <span style="color:#0D47A1;">5.2  Practical Workflow Patterns</span>

<table style="width:100%; border-collapse:collapse;">
<tr><td style="background:#2E7D32; color:white; padding:10px 12px; font-weight:bold;">Pattern</td><td style="background:#2E7D32; color:white; padding:10px 12px; font-weight:bold;">Prompt Sequence</td><td style="background:#2E7D32; color:white; padding:10px 12px; font-weight:bold;">Gate at Each Step</td></tr>
<tr><td style="background:#E8F5E9; padding:10px 12px; border:1px solid #CCC;"><strong>New Feature</strong></td><td style="background:#E8F5E9; padding:10px 12px; border:1px solid #CCC;">/plan → review PLAN.md → /implement → /test → /review → PR</td><td style="background:#E8F5E9; padding:10px 12px; border:1px solid #CCC;">Human approves plan before implementation begins</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><strong>Bug Fix</strong></td><td style="padding:10px 12px; border:1px solid #CCC;">/review #changes → /implement → /test</td><td style="padding:10px 12px; border:1px solid #CCC;">Review diagnosis before applying fix</td></tr>
<tr><td style="background:#E8F5E9; padding:10px 12px; border:1px solid #CCC;"><strong>Accessibility Audit</strong></td><td style="background:#E8F5E9; padding:10px 12px; border:1px solid #CCC;">/review with accessibility prompt → /implement targeted fixes</td><td style="background:#E8F5E9; padding:10px 12px; border:1px solid #CCC;">Run axe-core after each fix</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><strong>Test Coverage Push</strong></td><td style="padding:10px 12px; border:1px solid #CCC;">/test #file for each uncovered file</td><td style="padding:10px 12px; border:1px solid #CCC;">Verify coverage delta with each batch</td></tr>
<tr><td style="background:#E8F5E9; padding:10px 12px; border:1px solid #CCC;"><strong>Dependency Upgrade</strong></td><td style="background:#E8F5E9; padding:10px 12px; border:1px solid #CCC;">/plan (impact analysis) → /implement (update + fix breakage) → full test run</td><td style="background:#E8F5E9; padding:10px 12px; border:1px solid #CCC;">Human reviews breaking change summary before proceeding</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><strong>PR Review Assist</strong></td><td style="padding:10px 12px; border:1px solid #CCC;">/review #changes</td><td style="padding:10px 12px; border:1px solid #CCC;">Human makes final call — Copilot surfaces, human decides</td></tr>
</table>

### <span style="color:#0D47A1;">5.3  When NOT to Use Agent Mode</span>

Agent mode is powerful but not always the right tool:

<table style="width:100%; border-collapse:collapse;">
<tr><td style="background:#C62828; color:white; padding:10px 12px; font-weight:bold;">Situation</td><td style="background:#C62828; color:white; padding:10px 12px; font-weight:bold;">Use Instead</td></tr>
<tr><td style="background:#FFEBEE; padding:10px 12px; border:1px solid #CCC;">Simple single-line completion (variable name, function signature)</td><td style="background:#FFEBEE; padding:10px 12px; border:1px solid #CCC;">Inline completion (Tab to accept)</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;">Explaining what a function does</td><td style="padding:10px 12px; border:1px solid #CCC;">Ask mode in Copilot Chat (`/ask`)</td></tr>
<tr><td style="background:#FFEBEE; padding:10px 12px; border:1px solid #CCC;">Editing one specific block of code</td><td style="background:#FFEBEE; padding:10px 12px; border:1px solid #CCC;">Inline chat (`Cmd+I` on a selection)</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;">Tasks that require external APIs, cloud auth, or secrets</td><td style="padding:10px 12px; border:1px solid #CCC;">Human — agent mode doesn't manage credentials</td></tr>
<tr><td style="background:#FFEBEE; padding:10px 12px; border:1px solid #CCC;">Architectural decisions that affect multiple teams</td><td style="background:#FFEBEE; padding:10px 12px; border:1px solid #CCC;">Human-led design review with Copilot as advisor</td></tr>
</table>

---

## <span style="color:#1A73E8;">MODULE 10 RECAP</span>

- ✅ **Agent mode:** Copilot moves from single-answer to multi-step autonomous execution — plan → execute → verify → iterate
- ✅ **Three config layers:** global instructions → path instructions → reusable prompt files
- ✅ **Four specialist roles:** Planner (read-only), Reviewer (read-only), Implementer (full edit), Tester (test files only)
- ✅ **Scope controls:** use `#file` and `#changes` before reaching for `#codebase` — narrow context = safer agents
- ✅ **Confirmation gates:** never "Allow Always" for commands that write to remotes or delete files
- ✅ **Exit criteria:** define done criteria and retry limits in every agent prompt — prevent infinite loops
- ✅ **VS Code Tasks:** run watch tasks in background so TypeScript and test feedback is always live
- ✅ **CI is the backstop:** agent-produced code goes through the same CI pipeline as human-produced code — no exceptions

## <span style="color:#1A73E8;">TRANSITION TO MODULE 11</span>

Module 11 (Agents for Software Development: Applied) puts these foundations to work on real scenarios: repository-level codebase exploration, intelligent file localization, the Plan-Execute-Review cycle end-to-end, MCP server integration, and measuring agent reliability with concrete metrics.

<table style="width:100%; border-collapse:collapse;"><tr><td style="background:#F3E5F5; padding:14px 18px; border:1px solid #CE93D8;"><strong style="color:#6A1B9A;">🎯 INSTRUCTOR NOTE</strong><br><em style="color:#6A1B9A;">Ask: "What's the first prompt file you'd create for your team — planner, reviewer, tester, or something else entirely?" Common answers: code reviewer (immediate ROI), accessibility auditor (pain point), Storybook story generator (repetitive task). These answers prime Lab 2 in Module 12: students build their own prompt file suite.</em></td></tr></table>

---

<div style="text-align:center; padding:20px; color:#666; font-size:12px;">
<strong>Vibe Coding with GitHub Copilot | React Developer Track</strong>
</div>
