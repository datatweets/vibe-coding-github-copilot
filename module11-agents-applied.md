<div style="text-align:center; padding: 20px 0;">
<span style="font-size:14px; color:#666666; font-weight:bold; letter-spacing:2px;">MODULE 11</span>

# <span style="color:#0D47A1;">Copilot Agent Mode: Applied — Real-World React Workflows</span>

<hr style="border: 3px solid #1A73E8; width:80%;">
</div>

<table style="width:100%; border-collapse:collapse;">
<tr>
<td style="background:#E3F2FD; text-align:center; padding:10px; border:1px solid #BBDEFB; width:25%;"><span style="font-size:12px; color:#666;">Duration</span><br><strong style="color:#0D47A1;">45 min</strong></td>
<td style="background:#E3F2FD; text-align:center; padding:10px; border:1px solid #BBDEFB; width:25%;"><span style="font-size:12px; color:#666;">Format</span><br><strong style="color:#0D47A1;">Lecture + Demo</strong></td>
<td style="background:#E3F2FD; text-align:center; padding:10px; border:1px solid #BBDEFB; width:25%;"><span style="font-size:12px; color:#666;">Audience</span><br><strong style="color:#0D47A1;">React Developers</strong></td>
<td style="background:#E3F2FD; text-align:center; padding:10px; border:1px solid #BBDEFB; width:25%;"><span style="font-size:12px; color:#666;">Day / Position</span><br><strong style="color:#0D47A1;">Day 2 / Third</strong></td>
</tr>
</table>

---

## <span style="color:#1A73E8;">LEARNING OBJECTIVES</span>

By the end of this module, participants will be able to:

1. Use Copilot Agent mode to explore a React codebase and produce a structured analysis before writing a single line of code
2. Apply workspace context variables (`#codebase`, `#file`, `#selection`, `#terminalLastCommand`, `@workspace`) strategically to give Agent mode precise, scoped context
3. Execute the full Plan → Approve → Execute → Verify cycle for safe multi-file React refactoring
4. Apply concrete quality gates — TypeScript errors, Jest coverage delta, ESLint violations, accessibility checks — to validate every agent output
5. Explain optional MCP server integration (GitHub, browser) for environments where the required tools, tokens, and approvals are available

---

## <span style="color:#1A73E8;">SESSION TIMING BREAKDOWN</span>

<table style="width:100%; border-collapse:collapse;">
<tr><td style="background:#00695C; color:white; padding:8px 14px; width:120px; font-weight:bold; font-size:13px;">0:00 – 0:08</td><td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Section 1: Codebase Exploration — Observe Before You Act</td></tr>
<tr><td colspan="2" style="height:4px;"></td></tr>
<tr><td style="background:#00695C; color:white; padding:8px 14px; font-weight:bold; font-size:13px;">0:08 – 0:18</td><td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Section 2: Context Variables Deep Dive — Scope, Precision & Safety</td></tr>
<tr><td colspan="2" style="height:4px;"></td></tr>
<tr><td style="background:#00695C; color:white; padding:8px 14px; font-weight:bold; font-size:13px;">0:18 – 0:28</td><td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Section 3: The Plan → Approve → Execute Cycle</td></tr>
<tr><td colspan="2" style="height:4px;"></td></tr>
<tr><td style="background:#00695C; color:white; padding:8px 14px; font-weight:bold; font-size:13px;">0:28 – 0:37</td><td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Section 4: Safety Gates & Quality Metrics for Agent Output</td></tr>
<tr><td colspan="2" style="height:4px;"></td></tr>
<tr><td style="background:#00695C; color:white; padding:8px 14px; font-weight:bold; font-size:13px;">0:37 – 0:43</td><td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Section 5: Optional MCP Integration — Extending Copilot Beyond Local Files</td></tr>
<tr><td colspan="2" style="height:4px;"></td></tr>
<tr><td style="background:#00695C; color:white; padding:8px 14px; font-weight:bold; font-size:13px;">0:43 – 0:45</td><td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Wrap-Up: Quick Reference & Transition to Lab 2</td></tr>
</table>

---

## <span style="color:#0D47A1;">1. Codebase Exploration — Observe Before You Act</span>

The most common mistake developers make with Copilot Agent mode is giving it a task before it understands the codebase. An agent that doesn't know your component conventions, your hook patterns, or your test structure will generate technically correct code that completely ignores your existing standards.

**The rule: always make your first Agent prompt an observation prompt, not an action prompt.**

### <span style="color:#0D47A1;">1.1  The Repository Analysis Prompt</span>

When you open the `my-form-library` project, your first Agent mode prompt should look like this:

```text
@workspace Analyze this React component library. Tell me:
1. Project structure — what lives where (components, hooks, utils, stories, tests)
2. Tech stack — React version, TypeScript config, styling approach, Storybook setup
3. Component patterns — how are Props interfaces defined? Default exports vs named? Composition patterns?
4. Hook patterns — how are custom hooks named, structured, and co-located?
5. Testing patterns — how are tests organized? What queries are preferred (getByRole, getByLabelText)?
6. Which component currently has the lowest test coverage?
Output a summary to docs/repo-analysis.md
```

<table style="width:100%; border-collapse:collapse;"><tr><td style="border-left:5px solid #1A73E8; background:#E3F2FD; padding:14px 18px;"><strong style="color:#0D47A1;">⭐ KEY POINT:</strong> <span style="color:#0D47A1;">The <code>@workspace</code> variable gives the agent permission to explore all indexed files in your project. Combined with specific numbered questions, it produces a structured analysis rather than a vague summary. Always save the output to a file — you'll reference it in subsequent prompts.</span></td></tr></table>

### <span style="color:#0D47A1;">1.2  File Localization — Finding What Matters</span>

Before modifying a component, the agent needs to know everything that depends on it. A naive agent that doesn't do this can break imports across the project.

<table style="width:100%; border-collapse:collapse;">
<tr><td style="background:#00695C; color:white; padding:10px 12px; font-weight:bold;">Strategy</td><td style="background:#00695C; color:white; padding:10px 12px; font-weight:bold;">Context Variable / Tool</td><td style="background:#00695C; color:white; padding:10px 12px; font-weight:bold;">Example</td></tr>
<tr><td style="background:#E0F2F1; padding:10px 12px; border:1px solid #CCC;"><strong>By file pattern</strong></td><td style="background:#E0F2F1; padding:10px 12px; border:1px solid #CCC;"><code>#file:</code> with glob</td><td style="background:#E0F2F1; padding:10px 12px; border:1px solid #CCC;"><code>#file:src/components/TextInput*</code></td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><strong>By symbol usage</strong></td><td style="padding:10px 12px; border:1px solid #CCC;"><code>@workspace</code> + "find all"</td><td style="padding:10px 12px; border:1px solid #CCC;">"Find all files importing TextInputProps"</td></tr>
<tr><td style="background:#E0F2F1; padding:10px 12px; border:1px solid #CCC;"><strong>By test coverage</strong></td><td style="background:#E0F2F1; padding:10px 12px; border:1px solid #CCC;"><code>#terminalLastCommand</code></td><td style="background:#E0F2F1; padding:10px 12px; border:1px solid #CCC;">Run <code>npm test -- --coverage</code>, then use <code>#terminalLastCommand</code></td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><strong>By git history</strong></td><td style="padding:10px 12px; border:1px solid #CCC;">Terminal + <code>#terminalLastCommand</code></td><td style="padding:10px 12px; border:1px solid #CCC;"><code>git log --oneline -- src/components/Button.tsx</code></td></tr>
<tr><td style="background:#E0F2F1; padding:10px 12px; border:1px solid #CCC;"><strong>By type definition</strong></td><td style="background:#E0F2F1; padding:10px 12px; border:1px solid #CCC;"><code>@workspace</code></td><td style="background:#E0F2F1; padding:10px 12px; border:1px solid #CCC;">"Find every component using the <code>size</code> prop variant"</td></tr>
</table>

**Pre-modification localization prompt:**

```text
Before modifying the TextInput component:
1. Find every file that imports TextInput or TextInputProps
2. Find every test file that renders TextInput
3. Find every Storybook story that uses TextInput
4. Check if TextInput is exported from src/index.ts
List all findings. Do not modify any files yet.
```

<table style="width:100%; border-collapse:collapse;"><tr><td style="border-left:5px solid #1A73E8; background:#E3F2FD; padding:14px 18px;"><strong style="color:#0D47A1;">⭐ KEY POINT:</strong> <span style="color:#0D47A1;">Localization is a read-only safety step. Run it before every non-trivial change. The list it produces becomes your "blast radius" — you know exactly which files may need updating before the agent touches anything.</span></td></tr></table>

### <span style="color:#0D47A1;">1.3  Structured Pattern Recognition</span>

The agent's code quality depends entirely on how well it understands your existing patterns. Prompt it to extract and articulate the patterns it sees before following them.

```text
Look at src/components/Select/Select.tsx and Select.test.tsx.
Describe the exact pattern used for:
1. The Props interface — structure, naming, JSDoc comments
2. Error state handling — how is the error prop displayed?
3. Accessibility — which ARIA attributes are used and how?
4. Testing approach — how is the component rendered in tests? Which queries?
I will use these patterns as the standard for the next component I ask you to generate.
```

---

## <span style="color:#0D47A1;">2. Context Variables Deep Dive — Scope, Precision & Safety</span>

Context variables are the single most impactful lever you have for controlling agent quality. Using the wrong variable gives the agent too much (confused, slow, costly) or too little (generates wrong imports, misses your patterns) context.

### <span style="color:#0D47A1;">2.1  The Context Variable Hierarchy</span>

<table style="width:100%; border-collapse:collapse;">
<tr><td style="background:#1A73E8; color:white; padding:10px 12px; font-weight:bold; width:22%;">Variable</td><td style="background:#1A73E8; color:white; padding:10px 12px; font-weight:bold; width:25%;">Scope</td><td style="background:#1A73E8; color:white; padding:10px 12px; font-weight:bold; width:30%;">Best React Use Case</td><td style="background:#1A73E8; color:white; padding:10px 12px; font-weight:bold;">Warning</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><code>#selection</code></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Highlighted text only</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Explain a specific hook, refactor one JSX block, fix one function</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Agent has no file context — may generate incompatible imports</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><code>#file:path</code></td><td style="padding:10px 12px; border:1px solid #CCC;">One full file</td><td style="padding:10px 12px; border:1px solid #CCC;">Review a single component, add a prop, generate tests for one component</td><td style="padding:10px 12px; border:1px solid #CCC;">Agent doesn't see how the component is used elsewhere</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><code>#file:a #file:b</code></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Multiple named files</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Refactor component + its test together, update hook + hook test</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Manual — you must know which files are relevant</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><code>#codebase</code></td><td style="padding:10px 12px; border:1px solid #CCC;">Full repo (indexed)</td><td style="padding:10px 12px; border:1px solid #CCC;">Cross-cutting refactors, renaming types, accessibility audits</td><td style="padding:10px 12px; border:1px solid #CCC;">Slow on large repos; use only when cross-file awareness is needed</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><code>@workspace</code></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Full workspace (search)</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Answering architectural questions, finding files, planning work</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Read-only context — does not trigger agent edits</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><code>#terminalLastCommand</code></td><td style="padding:10px 12px; border:1px solid #CCC;">Last terminal output</td><td style="padding:10px 12px; border:1px solid #CCC;">Debug failing tests, fix build errors, respond to lint output</td><td style="padding:10px 12px; border:1px solid #CCC;">Only captures the most recent command — re-run if needed</td></tr>
</table>

### <span style="color:#0D47A1;">2.2  Combining Context Variables for Precision</span>

The most powerful prompts combine variables to give the agent exactly the right scope — nothing more, nothing less.

**Pattern: Component + Test + Instructions**

```text
#file:src/components/Checkbox.tsx
#file:src/components/Checkbox.test.tsx
#file:.github/copilot-instructions.md

The Checkbox component is missing:
1. An `indeterminate` state (the HTML `indeterminate` DOM property)
2. A keyboard handler for Space key to toggle
Add both. Follow the existing Props interface pattern and RTL test style.
```

**Pattern: Terminal output → targeted fix**

```text
#terminalLastCommand

Three tests in Checkbox.test.tsx are failing.
Without changing the test assertions, fix the component code only.
Explain what caused each failure before fixing it.
```

**Pattern: Workspace search → targeted action**

```text
@workspace Find every component in src/components/ that uses the 
`data-testid` attribute. List them. Then explain which ones 
have accessible alternatives we should migrate to instead.
```

### <span style="color:#0D47A1;">2.3  The Context Size Trap</span>

More context is not always better. Giving an agent the entire `#codebase` for a single-component task creates three problems:

<table style="width:100%; border-collapse:collapse;">
<tr><td style="background:#C62828; color:white; padding:10px 12px; font-weight:bold;">Problem</td><td style="background:#C62828; color:white; padding:10px 12px; font-weight:bold;">Symptom</td><td style="background:#C62828; color:white; padding:10px 12px; font-weight:bold;">Correct Scope</td></tr>
<tr><td style="background:#FFEBEE; padding:10px 12px; border:1px solid #CCC;"><strong>Noise confusion</strong></td><td style="background:#FFEBEE; padding:10px 12px; border:1px solid #CCC;">Agent uses patterns from unrelated files</td><td style="background:#FFEBEE; padding:10px 12px; border:1px solid #CCC;"><code>#file:</code> specific files</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><strong>Slow responses</strong></td><td style="padding:10px 12px; border:1px solid #CCC;">30+ seconds per response</td><td style="padding:10px 12px; border:1px solid #CCC;"><code>#file:</code> or <code>#selection</code></td></tr>
<tr><td style="background:#FFEBEE; padding:10px 12px; border:1px solid #CCC;"><strong>Over-reach</strong></td><td style="background:#FFEBEE; padding:10px 12px; border:1px solid #CCC;">Agent edits files you didn't intend to change</td><td style="background:#FFEBEE; padding:10px 12px; border:1px solid #CCC;">Explicit file list in prompt</td></tr>
</table>

<table style="width:100%; border-collapse:collapse;"><tr><td style="border-left:5px solid #C62828; background:#FFEBEE; padding:14px 18px; border:1px solid #EF9A9A;"><strong style="color:#C62828;">⚠️ WARNING:</strong> <span style="color:#C62828;">If you use <code>#codebase</code> and the agent starts modifying files you didn't mention, use the Copilot Edits "Keep" / "Undo" controls immediately. Always review the file change list in the Copilot Edits panel before clicking "Accept All".</span></td></tr></table>

---

## <span style="color:#0D47A1;">3. The Plan → Approve → Execute Cycle</span>

Every non-trivial agent task should go through three gates before a single file is written. This is the discipline that separates professional AI-assisted development from pure vibe coding.

### <span style="color:#0D47A1;">3.1  Phase 1: Plan (Read-Only)</span>

In Agent mode, ask the agent to plan only — not execute. Use explicit language:

```text
[PLAN ONLY — DO NOT EDIT ANY FILES]

I want to add an `errorMessage` prop to all form components in src/components/ 
(TextInput, Select, Checkbox, RadioGroup, Textarea).

For each component:
1. What is the current Props interface?
2. What changes are needed to add errorMessage support?
3. Which files need updating (component + test + story + index.ts)?
4. Are there any shared types that should be updated in src/types.ts instead?
5. What is the correct implementation order to avoid circular dependencies?

Output a numbered implementation plan. Do not write any code yet.
```

**Why this works:** The `[PLAN ONLY]` instruction creates a contractual boundary between thinking and acting. The agent maps the full blast radius before touching anything.

### <span style="color:#0D47A1;">3.2  Phase 2: Approve or Refine the Plan</span>

Review the plan the agent produces. Ask yourself:

<table style="width:100%; border-collapse:collapse;">
<tr><td style="background:#2E7D32; color:white; padding:10px 12px; font-weight:bold; width:50%;">Green Light Questions</td><td style="background:#C62828; color:white; padding:10px 12px; font-weight:bold; width:50%;">Red Flag Questions</td></tr>
<tr><td style="background:#E8F5E9; padding:10px 12px; border:1px solid #CCC;">Does the plan match my intent exactly?</td><td style="background:#FFEBEE; padding:10px 12px; border:1px solid #CCC;">Is the agent planning to touch files I didn't mention?</td></tr>
<tr><td style="background:#E8F5E9; padding:10px 12px; border:1px solid #CCC;">Is the implementation order sensible?</td><td style="background:#FFEBEE; padding:10px 12px; border:1px solid #CCC;">Is the plan missing any files I know are affected?</td></tr>
<tr><td style="background:#E8F5E9; padding:10px 12px; border:1px solid #CCC;">Are the proposed changes minimal and focused?</td><td style="background:#FFEBEE; padding:10px 12px; border:1px solid #CCC;">Is the scope larger than expected? Why?</td></tr>
<tr><td style="background:#E8F5E9; padding:10px 12px; border:1px solid #CCC;">Does the plan account for tests and stories?</td><td style="background:#FFEBEE; padding:10px 12px; border:1px solid #CCC;">Is the agent proposing a refactor when I asked for an addition?</td></tr>
</table>

If the plan has red flags, reply with corrections before approving:

```text
Correction on the plan:
- Step 3: Do NOT update src/types.ts. Define errorMessage directly in each component's Props interface.
- Add Step 4b: After each component is updated, update its Storybook story to show the error state.
- Remove: You mentioned updating FormContext — that is out of scope for this task.
Revised plan accepted. Proceed with execution.
```

### <span style="color:#0D47A1;">3.3  Phase 3: Execute (File by File)</span>

Once the plan is approved, execute it incrementally — one file at a time, with verification after each:

```text
Implement Step 1 only: add errorMessage to TextInput.tsx and TextInput.test.tsx.
After writing both files, output the Jest test command to verify just those tests.
```

After each step:
1. Review the Copilot Edits diff panel — read every line changed
2. Run the specific tests: `npm test -- TextInput`
3. Check TypeScript: `npx tsc --noEmit`
4. Accept or reject individual file changes in the Edits panel

### <span style="color:#0D47A1;">3.4  Phase 4: Verify the Full Cycle</span>

After all steps are implemented, run a full verification:

```bash
# Full test suite with coverage
npm test -- --coverage

# TypeScript strict check across all files
npx tsc --noEmit

# ESLint across changed files
npm run lint

# Verify only intended files changed
git diff --name-only
```

<table style="width:100%; border-collapse:collapse;"><tr><td style="border-left:5px solid #1A73E8; background:#E3F2FD; padding:14px 18px;"><strong style="color:#0D47A1;">⭐ KEY POINT:</strong> <span style="color:#0D47A1;">The git diff check is the most underused verification step. Run <code>git diff --name-only</code> before accepting any agent batch. If you see files in the diff that were not in the plan, reject those specific changes in the Copilot Edits panel before accepting the rest.</span></td></tr></table>

---

## <span style="color:#0D47A1;">4. Safety Gates & Quality Metrics for Agent Output</span>

Agent-generated React code passes "it works" far more often than it passes "it's production-ready." Quality gates catch the gap.

### <span style="color:#0D47A1;">4.1  The React Quality Gate Stack</span>

<table style="width:100%; border-collapse:collapse;">
<tr><td style="background:#C62828; color:white; padding:10px 12px; font-weight:bold; width:25%;">Gate</td><td style="background:#C62828; color:white; padding:10px 12px; font-weight:bold; width:30%;">Command</td><td style="background:#C62828; color:white; padding:10px 12px; font-weight:bold; width:20%;">Threshold</td><td style="background:#C62828; color:white; padding:10px 12px; font-weight:bold;">What It Catches</td></tr>
<tr><td style="background:#FFEBEE; padding:10px 12px; border:1px solid #CCC;"><strong>TypeScript compiler</strong></td><td style="background:#FFEBEE; padding:10px 12px; border:1px solid #CCC;"><code>npx tsc --noEmit</code></td><td style="background:#FFEBEE; padding:10px 12px; border:1px solid #CCC;">0 errors</td><td style="background:#FFEBEE; padding:10px 12px; border:1px solid #CCC;">Type mismatches, missing props, unsafe `any` usage</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><strong>Jest test suite</strong></td><td style="padding:10px 12px; border:1px solid #CCC;"><code>npm test -- --ci</code></td><td style="padding:10px 12px; border:1px solid #CCC;">100% pass</td><td style="padding:10px 12px; border:1px solid #CCC;">Behavior regressions, broken renders, hook errors</td></tr>
<tr><td style="background:#FFEBEE; padding:10px 12px; border:1px solid #CCC;"><strong>Coverage delta</strong></td><td style="background:#FFEBEE; padding:10px 12px; border:1px solid #CCC;"><code>npm test -- --coverage</code></td><td style="background:#FFEBEE; padding:10px 12px; border:1px solid #CCC;">Same or higher</td><td style="background:#FFEBEE; padding:10px 12px; border:1px solid #CCC;">New code added without corresponding tests</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><strong>ESLint</strong></td><td style="padding:10px 12px; border:1px solid #CCC;"><code>npm run lint</code></td><td style="padding:10px 12px; border:1px solid #CCC;">0 new violations</td><td style="padding:10px 12px; border:1px solid #CCC;">Unused vars, missing hook deps, React rules violations</td></tr>
<tr><td style="background:#FFEBEE; padding:10px 12px; border:1px solid #CCC;"><strong>Accessibility (axe)</strong></td><td style="background:#FFEBEE; padding:10px 12px; border:1px solid #CCC;"><code>jest-axe</code> in tests</td><td style="background:#FFEBEE; padding:10px 12px; border:1px solid #CCC;">0 violations</td><td style="background:#FFEBEE; padding:10px 12px; border:1px solid #CCC;">Missing ARIA labels, invalid role usage, color contrast</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><strong>Diff size</strong></td><td style="padding:10px 12px; border:1px solid #CCC;"><code>git diff --stat</code></td><td style="padding:10px 12px; border:1px solid #CCC;">< 200 lines</td><td style="padding:10px 12px; border:1px solid #CCC;">Agent over-reach — unexpectedly large changes</td></tr>
</table>

### <span style="color:#0D47A1;">4.2  Using Terminal Output as a Feedback Loop</span>

When a quality gate fails, feed the output back to the agent using `#terminalLastCommand`. This creates a tight correction loop:

```bash
# Step 1: Run the gate
npm test -- --ci
# Tests fail. Don't fix it yourself.

# Step 2: Feed the failure to the agent
```

```text
#terminalLastCommand

Two tests in Checkbox.test.tsx are failing. 
Look at the test assertions and the current Checkbox.tsx implementation.
Identify the root cause — do NOT rewrite the tests.
Fix only the component code to make both tests pass.
After fixing, tell me what the underlying issue was.
```

<table style="width:100%; border-collapse:collapse;"><tr><td style="border-left:5px solid #1A73E8; background:#E3F2FD; padding:14px 18px;"><strong style="color:#0D47A1;">⭐ KEY POINT:</strong> <span style="color:#0D47A1;">Adding "do NOT rewrite the tests" is essential. Without this instruction, agents will sometimes change test assertions to match broken behavior rather than fixing the actual bug. Your tests describe the contract — they should not be changed to accommodate bad code.</span></td></tr></table>

### <span style="color:#0D47A1;">4.3  Accessibility as a First-Class Quality Gate</span>

React components that don't pass accessibility checks are not production-ready. Add `jest-axe` to your test suite and include it in agent verification prompts.

**Adding axe to an existing test:**

```typescript
// Checkbox.test.tsx — add to every component test file
import { render } from '@testing-library/react';
import '@testing-library/jest-dom';
import { axe, toHaveNoViolations } from 'jest-axe';
import { Checkbox } from '../Checkbox/Checkbox';

expect.extend(toHaveNoViolations);

it('has no accessibility violations', async () => {
  const { container } = render(
    <Checkbox id="test-cb" label="Accept terms" onChange={() => {}} />
  );
  const results = await axe(container);
  expect(results).toHaveNoViolations();
});
```

**Agent prompt to add axe to all component tests:**

```text
#codebase
Add a jest-axe accessibility violation test to every test file in 
src/components/*.test.tsx that doesn't already have one.
For each component, use a minimal but valid render (all required props).
Do not change any existing test assertions.
```

### <span style="color:#0D47A1;">4.4  TypeScript Strictness — Rejecting Agent Shortcuts</span>

Agents will sometimes introduce `any` types to avoid a complex TypeScript error. This is never acceptable in a component library. Use these prompts to enforce strictness:

```text
#file:src/components/Select/Select.tsx
TypeScript is showing: "Type 'string | undefined' is not assignable to type 'string'"
Do NOT use `as string` or `any` to fix this.
Fix the actual type narrowing. Explain the correct approach first, then implement it.
```

<table style="width:100%; border-collapse:collapse;"><tr><td style="border-left:5px solid #C62828; background:#FFEBEE; padding:14px 18px; border:1px solid #EF9A9A;"><strong style="color:#C62828;">⚠️ WARNING:</strong> <span style="color:#C62828;">If you see <code>as any</code>, <code>// @ts-ignore</code>, or <code>// eslint-disable</code> in agent-generated code, stop and reject the change. These are escape hatches that defeat the purpose of TypeScript and ESLint. Prompt the agent to fix the underlying type issue instead.</span></td></tr></table>

---

## <span style="color:#0D47A1;">5. Optional MCP Integration — Extending Copilot Beyond Local Files</span>

MCP (Model Context Protocol) is an open standard that lets external services connect to Copilot Agent mode. Instead of only working with local files, the agent can query GitHub, fetch browser pages, access databases, or call APIs — all within the VS Code interface.

This section is optional/advanced. Run it live only if your workshop environment has VS Code MCP support enabled, network access to install the server packages, and a read-only GitHub token or demo repository approved for class use. Otherwise, review the configuration and security model without running the tools.

### <span style="color:#0D47A1;">5.1  The GitHub MCP Server</span>

The GitHub MCP server gives Copilot Agent direct access to your repository's issues, PRs, and code — without leaving VS Code.

**Setup in VS Code:**

```jsonc
// .vscode/mcp.json
{
  "servers": {
    "github": {
      "type": "stdio",
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"],
      "env": {
        "GITHUB_TOKEN": "${env:GITHUB_TOKEN}"
      }
    }
  }
}
```

**Using GitHub MCP in agent prompts:**

```text
Using the GitHub MCP server:
1. List all open issues labeled "accessibility" in this repository
2. For each issue, find the related component file in src/components/
3. Create a prioritized fix plan: which issues can be fixed with a single 
   ARIA attribute addition vs. which require structural changes?
```

```text
Using the GitHub MCP server, review PR #47:
1. Summarize the changes
2. Check if there are any missing test files for new components added
3. Check if the TypeScript types are consistent with the existing Props interfaces
4. Output a structured review to docs/pr-47-review.md
```

### <span style="color:#0D47A1;">5.2  The Browser MCP Server (Playwright)</span>

The Playwright MCP server gives Copilot the ability to open a browser, navigate your running Storybook, and verify visual or interactive behavior.

```jsonc
// .vscode/mcp.json — add to existing servers
{
  "servers": {
    "playwright": {
      "type": "stdio",
      "command": "npx",
      "args": ["-y", "@playwright/mcp@latest"]
    }
  }
}
```

**Using browser MCP for component verification:**

```text
Using the Playwright browser tool:
1. Navigate to http://localhost:6006 (Storybook)
2. Open the TextInput/WithError story
3. Take a screenshot and describe what you see
4. Check if the error message text is visible and styled correctly
5. Verify the input has aria-invalid="true" in the DOM
```

### <span style="color:#0D47A1;">5.3  MCP Security Model</span>

<table style="width:100%; border-collapse:collapse;">
<tr><td style="background:#2E7D32; color:white; padding:10px 12px; font-weight:bold; width:50%;">Safe MCP Patterns</td><td style="background:#C62828; color:white; padding:10px 12px; font-weight:bold; width:50%;">Risky MCP Patterns</td></tr>
<tr><td style="background:#E8F5E9; padding:10px 12px; border:1px solid #CCC;">Read-only GitHub access (issues, PRs, code)</td><td style="background:#FFEBEE; padding:10px 12px; border:1px solid #CCC;">GitHub tokens with push/merge permissions in MCP</td></tr>
<tr><td style="background:#E8F5E9; padding:10px 12px; border:1px solid #CCC;">Browser MCP pointing to localhost only</td><td style="background:#FFEBEE; padding:10px 12px; border:1px solid #CCC;">Browser MCP with no URL restrictions</td></tr>
<tr><td style="background:#E8F5E9; padding:10px 12px; border:1px solid #CCC;">MCP servers defined in per-project `.vscode/mcp.json`</td><td style="background:#FFEBEE; padding:10px 12px; border:1px solid #CCC;">MCP servers globally configured with production credentials</td></tr>
<tr><td style="background:#E8F5E9; padding:10px 12px; border:1px solid #CCC;">Confirmation gates enabled (VS Code setting)</td><td style="background:#FFEBEE; padding:10px 12px; border:1px solid #CCC;">Auto-approving all MCP tool calls without review</td></tr>
</table>

<table style="width:100%; border-collapse:collapse;"><tr><td style="border-left:5px solid #1A73E8; background:#E3F2FD; padding:14px 18px;"><strong style="color:#0D47A1;">⭐ KEY POINT:</strong> <span style="color:#0D47A1;">Always use environment variables (<code>${env:GITHUB_TOKEN}</code>) for credentials in <code>mcp.json</code>. Never commit tokens directly. Add <code>.vscode/mcp.json</code> to <code>.gitignore</code> if it contains any environment-specific configuration, or use a <code>mcp.json.example</code> template with placeholder values that is committed instead.</span></td></tr></table>

---

## <span style="color:#1A73E8;">WRAP-UP: Quick Reference</span>

<table style="width:100%; border-collapse:collapse;">
<tr><td style="background:#0D47A1; color:white; padding:10px 12px; font-weight:bold; width:40%;">Situation</td><td style="background:#0D47A1; color:white; padding:10px 12px; font-weight:bold;">Best Approach</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><strong>Opening an unfamiliar codebase</strong></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><code>@workspace</code> analysis prompt first — save output to docs/</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><strong>Before any component modification</strong></td><td style="padding:10px 12px; border:1px solid #CCC;">File localization prompt — map the blast radius</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><strong>Multi-file refactoring</strong></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">[PLAN ONLY] → review → approve → execute one file at a time</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><strong>Tests failing after agent edit</strong></td><td style="padding:10px 12px; border:1px solid #CCC;"><code>#terminalLastCommand</code> → "fix component, not tests"</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><strong>Agent introduces <code>any</code> type</strong></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Reject immediately — prompt for correct type narrowing</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><strong>External systems (GitHub, browser)</strong></td><td style="padding:10px 12px; border:1px solid #CCC;">MCP servers — configure per-project, use env vars for tokens</td></tr>
</table>

**Transition to Lab 2:** In the next module you will apply everything from Modules 10 and 11 in a structured 45-minute lab. You will run the full Plan → Approve → Execute cycle on a real feature addition to `my-form-library` — creating a `PhoneInput` component from scratch using Agent mode with custom prompt files and quality gates.
