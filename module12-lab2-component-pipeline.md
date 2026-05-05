<div style="text-align:center; padding: 20px 0;">
<span style="font-size:14px; color:#666666; font-weight:bold; letter-spacing:2px;">MODULE 12 — LAB 2</span>

# <span style="color:#0D47A1;">Lab 2: Full Agent Workflow — Plan, Build & Review a React Feature</span>

<hr style="border: 3px solid #1A73E8; width:80%;">
</div>

<table style="width:100%; border-collapse:collapse;">
<tr>
<td style="background:#E3F2FD; text-align:center; padding:10px; border:1px solid #BBDEFB; width:25%;"><span style="font-size:12px; color:#666;">Duration</span><br><strong style="color:#0D47A1;">45 min</strong></td>
<td style="background:#E3F2FD; text-align:center; padding:10px; border:1px solid #BBDEFB; width:25%;"><span style="font-size:12px; color:#666;">Format</span><br><strong style="color:#0D47A1;">Hands-On Lab</strong></td>
<td style="background:#E3F2FD; text-align:center; padding:10px; border:1px solid #BBDEFB; width:25%;"><span style="font-size:12px; color:#666;">Audience</span><br><strong style="color:#0D47A1;">React Developers</strong></td>
<td style="background:#E3F2FD; text-align:center; padding:10px; border:1px solid #BBDEFB; width:25%;"><span style="font-size:12px; color:#666;">Day / Position</span><br><strong style="color:#0D47A1;">Day 2 / Fourth</strong></td>
</tr>
</table>

---

## <span style="color:#1A73E8;">LAB OVERVIEW</span>

In this lab you will add a `PhoneInput` component to `my-form-library` using the full professional Agent mode workflow. You will go through every phase you learned in Modules 10 and 11 — observation, custom instructions, planning, executing, testing, and drafting a PR — all within a timed 45-minute sprint.

**Feature you are building:**

> A `PhoneInput` React component that accepts a phone number, auto-formats it as the user types (e.g., `(415) 555-1234`), validates the format, and exposes the same Props interface pattern as the other form components in `my-form-library`. Fully accessible, fully tested, Storybook story included.

---

## <span style="color:#1A73E8;">LAB TIMING BREAKDOWN</span>

<table style="width:100%; border-collapse:collapse;">
<tr><td style="background:#00695C; color:white; padding:8px 14px; width:120px; font-weight:bold; font-size:13px;">0:00 – 0:07</td><td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Exercise 1: Observe & Analyze the Repo (7 min)</td></tr>
<tr><td colspan="2" style="height:4px;"></td></tr>
<tr><td style="background:#00695C; color:white; padding:8px 14px; font-weight:bold; font-size:13px;">0:07 – 0:15</td><td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Exercise 2: Create Custom Instruction & Prompt Files (8 min)</td></tr>
<tr><td colspan="2" style="height:4px;"></td></tr>
<tr><td style="background:#00695C; color:white; padding:8px 14px; font-weight:bold; font-size:13px;">0:15 – 0:25</td><td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Exercise 3: Plan the PhoneInput Feature (10 min)</td></tr>
<tr><td colspan="2" style="height:4px;"></td></tr>
<tr><td style="background:#00695C; color:white; padding:8px 14px; font-weight:bold; font-size:13px;">0:25 – 0:40</td><td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Exercise 4: Implement, Test & Run Quality Gates (15 min)</td></tr>
<tr><td colspan="2" style="height:4px;"></td></tr>
<tr><td style="background:#00695C; color:white; padding:8px 14px; font-weight:bold; font-size:13px;">0:40 – 0:45</td><td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Exercise 5: Draft PR Description & Debrief (5 min)</td></tr>
</table>

---

## <span style="color:#0D47A1;">EXERCISE 1 — Observe & Analyze the Repo</span>
## <span style="color:#1A73E8;">⏱ 7 minutes (0:00 – 0:07)</span>

Before writing a single line of code, run a structured repository analysis. This gives the agent — and you — a complete picture of the existing patterns before introducing a new component.

### Step 1.1 — Run the analysis

Open Copilot Chat, switch to **Agent mode**, and run:

```text
@workspace Analyze the my-form-library project. Produce a structured analysis covering:
1. STRUCTURE — Where are components, hooks, types, stories, and test files?
2. TYPESCRIPT PATTERNS — How are Props interfaces defined? What naming convention is used (e.g., TextInputProps)?
3. STYLING — How is CSS applied? (CSS modules, inline styles, className with constants, etc.)
4. COMPONENT ANATOMY — Using TextInput.tsx as the reference, describe every section:
   - Props interface structure
   - Default prop values
   - ARIA attributes used
   - Error state implementation
   - How the label is associated with the input
5. TEST PATTERNS — How are components tested? What RTL queries are preferred?
6. STORYBOOK PATTERNS — How are stories structured? Where does the "WithError" variant appear?

Save this analysis to docs/repo-analysis.md
```

### Step 1.2 — Review and correct the analysis

Open `docs/repo-analysis.md` and read through it. Answer these questions:

- Is anything missing or wrong?
- Are there patterns the agent missed because they're in less common files?
- Does the component anatomy description match what you actually see in `TextInput.tsx`?

If anything is incorrect, add a manual correction at the bottom of the file in a **"Corrections"** section. This document is your source of truth for the next exercises.

<table style="width:100%; border-collapse:collapse;"><tr><td style="border-left:5px solid #2E7D32; background:#E8F5E9; padding:14px 18px;"><strong style="color:#2E7D32;">✅ CHECKPOINT 1:</strong> <span style="color:#2E7D32;"><code>docs/repo-analysis.md</code> exists, describes at least 5 patterns, and has been reviewed. You can describe the component anatomy from the analysis document without looking at the source code.</span></td></tr></table>

---

## <span style="color:#0D47A1;">EXERCISE 2 — Create Custom Instruction & Prompt Files</span>
## <span style="color:#1A73E8;">⏱ 8 minutes (0:07 – 0:15)</span>

You will create two files: one that tells Copilot how to behave in this project at all times, and one reusable prompt for generating new form components.

### Step 2.1 — Create `.github/copilot-instructions.md`

If this file already exists (from Lab 1), open it and verify it contains the following. If it doesn't exist, create it:

```markdown
# my-form-library — Copilot Instructions

## Project
TypeScript React component library. All components are form inputs.

## TypeScript
- strict: true is set in tsconfig.json
- Never use `any`, `as any`, or `// @ts-ignore`
- Props interfaces must be explicitly typed — no implicit object types
- All props must have JSDoc comments

## Component Pattern
Follow the structure in src/components/TextInput/TextInput.tsx:
- Named export of Props interface (e.g., PhoneInputProps)
- Default export of component
- Error state via errorMessage?: string prop
- Label associated with input via htmlFor/id pairing
- aria-describedby used to associate error message with input
- aria-invalid="true" set when errorMessage is defined

## Testing
- Use React Testing Library
- Prefer getByRole, getByLabelText, getByText over getByTestId
- Do NOT use data-testid unless there is no accessible alternative
- Every component test must include a jest-axe accessibility check
- Tests must NOT be modified to make a broken component pass

## ESLint
- 0 violations in src/
- If a rule must be suppressed, add a comment explaining why

## Storybook
- One story per component state (Default, WithError, WithPlaceholder, Disabled)
- Stories must compile and render without errors
```

### Step 2.2 — Create a reusable prompt file for new components

Create `.github/prompts/new-form-component.prompt.md`:

```markdown
---
mode: agent
description: Generate a new form input component for my-form-library
---

# New Form Component Generator

Read docs/repo-analysis.md before proceeding.
Follow the component patterns described in .github/copilot-instructions.md exactly.

## Task
Generate a complete new form component named `${componentName}`.

## Deliverables — Create ALL of these files:
1. `src/components/${componentName}/${componentName}.tsx` — the component
2. `src/components/${componentName}/${componentName}.test.tsx` — RTL + jest-axe tests
3. `src/components/${componentName}/${componentName}.stories.tsx` — Storybook stories
4. `src/components/${componentName}/index.ts` — folder-level barrel export
5. Update `src/index.ts` — export the new component and its Props type

## Requirements
- Props interface named `${componentName}Props`
- All standard form props: `id`, `label`, `value`, `onChange`, `errorMessage?`, `disabled?`, `placeholder?`
- Error state follows the TextInput pattern (aria-invalid, aria-describedby)
- Label uses htmlFor/id association
- Accessibility test using jest-axe
- Stories: Default, WithError, WithPlaceholder, Disabled

## Extra requirements for this component
${extraRequirements}
```

<table style="width:100%; border-collapse:collapse;"><tr><td style="border-left:5px solid #1A73E8; background:#E3F2FD; padding:14px 18px;"><strong style="color:#0D47A1;">⭐ NOTE:</strong> <span style="color:#0D47A1;">The <code>${componentName}</code> and <code>${extraRequirements}</code> placeholders work like template variables. When you use this prompt file, VS Code will ask you to fill them in. This makes the prompt file reusable for any future component.</span></td></tr></table>

If the prompt file does not appear in the `/` menu or VS Code does not prompt for variables, open `.github/prompts/new-form-component.prompt.md`, paste the body into Copilot Chat manually, and replace `${componentName}` and `${extraRequirements}` yourself before sending.

<table style="width:100%; border-collapse:collapse;"><tr><td style="border-left:5px solid #2E7D32; background:#E8F5E9; padding:14px 18px;"><strong style="color:#2E7D32;">✅ CHECKPOINT 2:</strong> <span style="color:#2E7D32;"><code>.github/copilot-instructions.md</code> and <code>.github/prompts/new-form-component.prompt.md</code> both exist. Read them both. Do they fully capture the patterns you documented in Exercise 1?</span></td></tr></table>

---

## <span style="color:#0D47A1;">EXERCISE 3 — Plan the PhoneInput Feature</span>
## <span style="color:#1A73E8;">⏱ 10 minutes (0:15 – 0:25)</span>

Before writing any implementation code, use Agent mode to produce a detailed implementation plan. This is your approval gate — you review and correct the plan before any file is touched.

### Step 3.1 — Run the planning prompt

```text
[PLAN ONLY — DO NOT EDIT ANY FILES]

Using docs/repo-analysis.md and .github/copilot-instructions.md as references, 
plan the implementation of a PhoneInput component with the following behavior:

BEHAVIOR:
- Accepts a phone number as a string value (controlled component)
- Auto-formats as the user types: digits are formatted as (XXX) XXX-XXXX
- Only allows digit input — non-digit keystrokes are swallowed
- onChange fires with the raw digit string (not the formatted display value)
- Validates that the number is exactly 10 digits when the field loses focus
- Shows errorMessage from parent (for external validation) OR an internal 
  format error if the user types less than 10 digits and blurs
- Placeholder: "(555) 555-5555" by default

PLAN REQUIREMENTS:
1. List every file that needs to be created or modified
2. Describe the PhoneInputProps interface (all fields, all types)
3. Describe the formatting logic (step by step — no code yet)
4. Describe the validation logic
5. Describe what each test should assert
6. Describe what each Storybook story should show
7. Identify any edge cases to handle

Output the plan clearly. Do not write any implementation code.
```

### Step 3.2 — Review the plan

Evaluate the plan against this checklist before approving:

<table style="width:100%; border-collapse:collapse;">
<tr><td style="background:#1A73E8; color:white; padding:8px 12px; font-weight:bold; width:70%;">Plan Check</td><td style="background:#1A73E8; color:white; padding:8px 12px; font-weight:bold;">Status</td></tr>
<tr><td style="background:#E3F2FD; padding:8px 12px; border:1px solid #CCC;">Plan lists: component file + test file + story file + index.ts update</td><td style="background:#E3F2FD; padding:8px 12px; border:1px solid #CCC;">[ ] ✓ / [ ] ✗</td></tr>
<tr><td style="padding:8px 12px; border:1px solid #CCC;">Props interface includes: id, label, value, onChange, errorMessage?, disabled?, placeholder?</td><td style="padding:8px 12px; border:1px solid #CCC;">[ ] ✓ / [ ] ✗</td></tr>
<tr><td style="background:#E3F2FD; padding:8px 12px; border:1px solid #CCC;">Formatting logic handles: empty input, 1-3 digits, 4-6 digits, 7-10 digits, 10+ digits (capped)</td><td style="background:#E3F2FD; padding:8px 12px; border:1px solid #CCC;">[ ] ✓ / [ ] ✗</td></tr>
<tr><td style="padding:8px 12px; border:1px solid #CCC;">Validation correctly fires only on blur (not on every keystroke)</td><td style="padding:8px 12px; border:1px solid #CCC;">[ ] ✓ / [ ] ✗</td></tr>
<tr><td style="background:#E3F2FD; padding:8px 12px; border:1px solid #CCC;">Tests include an axe accessibility check</td><td style="background:#E3F2FD; padding:8px 12px; border:1px solid #CCC;">[ ] ✓ / [ ] ✗</td></tr>
<tr><td style="padding:8px 12px; border:1px solid #CCC;">onChange fires with raw digits, not formatted value</td><td style="padding:8px 12px; border:1px solid #CCC;">[ ] ✓ / [ ] ✗</td></tr>
<tr><td style="background:#E3F2FD; padding:8px 12px; border:1px solid #CCC;">Stories: Default, WithError, WithPlaceholder, Disabled, WithPrefilledValue</td><td style="background:#E3F2FD; padding:8px 12px; border:1px solid #CCC;">[ ] ✓ / [ ] ✗</td></tr>
</table>

### Step 3.3 — Correct and approve the plan

If any items above are missing, tell the agent before approving:

```text
Corrections to the plan:
- [list any specific corrections here]
Plan is now approved. Proceed with implementation, one file at a time. Start with PhoneInput.tsx.
```

<table style="width:100%; border-collapse:collapse;"><tr><td style="border-left:5px solid #2E7D32; background:#E8F5E9; padding:14px 18px;"><strong style="color:#2E7D32;">✅ CHECKPOINT 3:</strong> <span style="color:#2E7D32;">You have reviewed the plan against the checklist above. All items are checked or you have provided explicit corrections. You have typed "Plan is now approved. Proceed with implementation." into the Agent mode chat.</span></td></tr></table>

---

## <span style="color:#0D47A1;">EXERCISE 4 — Implement, Test & Run Quality Gates</span>
## <span style="color:#1A73E8;">⏱ 15 minutes (0:25 – 0:40)</span>

Now you implement the plan — but still under control. Request one file at a time and run quality gates after each.

### Step 4.1 — Implement the component

```text
Implement Step 1 only: create `src/components/PhoneInput/PhoneInput.tsx`.
Follow the plan exactly and the patterns in .github/copilot-instructions.md.
After writing the file, show me the TypeScript check command to run.
Do not create any other files yet.
```

**After the agent writes the file:**
```bash
npx tsc --noEmit
```

Check for TypeScript errors. If any exist, paste them into the agent using `#terminalLastCommand` and ask for a fix.

### Step 4.2 — Implement the tests

```text
Implement Step 2: create src/components/PhoneInput/PhoneInput.test.tsx.
Tests must cover:
1. Renders with a label associated to the input (getByLabelText)
2. Typing 4155551234 formats the display as "(415) 555-1234"
3. onChange fires with raw "4155551234", not the formatted version
4. Blurring with fewer than 10 digits shows the internal error message
5. External errorMessage prop is displayed when provided
6. aria-invalid is true when an error is shown
7. jest-axe accessibility check passes
```

**After the agent writes the test file:**
```bash
npm test -- PhoneInput
```

<table style="width:100%; border-collapse:collapse;"><tr><td style="border-left:5px solid #C62828; background:#FFEBEE; padding:14px 18px; border:1px solid #EF9A9A;"><strong style="color:#C62828;">⚠️ IF TESTS FAIL:</strong> <span style="color:#C62828;">Run <code>#terminalLastCommand</code> → "Fix the component code to make these tests pass. Do not change the test assertions." If the agent wants to change a test assertion, explain that the assertion is the contract — reject the edit and ask again.</span></td></tr></table>

### Step 4.3 — Implement Storybook stories

```text
Implement Step 3: create src/components/PhoneInput/PhoneInput.stories.tsx.
Stories needed: Default, WithError, WithPlaceholder, Disabled, WithPrefilledValue.
WithPrefilledValue: pass value="4155551234" to show a pre-formatted number.
```

Verify stories compile:
```bash
npx storybook build --quiet 2>&1 | tail -20
```
Or if Storybook dev server is running, navigate to the PhoneInput stories.

### Step 4.4 — Update the barrel export

```text
Implement Step 4: create src/components/PhoneInput/index.ts, then update src/index.ts to export PhoneInput and PhoneInputProps.
Follow the same pattern as the existing component exports.
Show me the diff before making the change.
```

Review the diff in the Copilot Edits panel — it should be a minimal 1-2 line addition.

### Step 4.5 — Run the full quality gate suite

```bash
# 1. TypeScript strict check
npx tsc --noEmit

# 2. Full test suite with coverage
npm test -- --coverage

# 3. ESLint
npm run lint

# 4. Verify diff scope
git diff --name-only
```

**Expected results:**

<table style="width:100%; border-collapse:collapse;">
<tr><td style="background:#2E7D32; color:white; padding:8px 12px; font-weight:bold; width:35%;">Gate</td><td style="background:#2E7D32; color:white; padding:8px 12px; font-weight:bold;">Expected Output</td></tr>
<tr><td style="background:#E8F5E9; padding:8px 12px; border:1px solid #CCC;">TypeScript</td><td style="background:#E8F5E9; padding:8px 12px; border:1px solid #CCC;">0 errors</td></tr>
<tr><td style="padding:8px 12px; border:1px solid #CCC;">Jest</td><td style="padding:8px 12px; border:1px solid #CCC;">All tests pass, including 7 new PhoneInput tests</td></tr>
<tr><td style="background:#E8F5E9; padding:8px 12px; border:1px solid #CCC;">Coverage</td><td style="background:#E8F5E9; padding:8px 12px; border:1px solid #CCC;">Overall coverage same or higher than before Lab 2</td></tr>
<tr><td style="padding:8px 12px; border:1px solid #CCC;">ESLint</td><td style="padding:8px 12px; border:1px solid #CCC;">0 new violations</td></tr>
<tr><td style="background:#E8F5E9; padding:8px 12px; border:1px solid #CCC;">Git diff --name-only</td><td style="background:#E8F5E9; padding:8px 12px; border:1px solid #CCC;">Only expected files changed: <code>src/components/PhoneInput/</code> (4 files) and <code>src/index.ts</code></td></tr>
</table>

If any gate fails, fix it before proceeding to Exercise 5.

<table style="width:100%; border-collapse:collapse;"><tr><td style="border-left:5px solid #2E7D32; background:#E8F5E9; padding:14px 18px;"><strong style="color:#2E7D32;">✅ CHECKPOINT 4:</strong> <span style="color:#2E7D32;">All 5 quality gates above pass. The git diff contains only the expected files (<code>src/components/PhoneInput/</code> and <code>src/index.ts</code>). You have not manually edited any file — all changes were made through Agent mode with explicit prompts.</span></td></tr></table>

---

## <span style="color:#0D47A1;">EXERCISE 5 — Draft PR Description & Debrief</span>
## <span style="color:#1A73E8;">⏱ 5 minutes (0:40 – 0:45)</span>

### Step 5.1 — Generate a PR description

```text
Generate a pull request description for the PhoneInput component I just built.
Include:
1. Summary: what was added and why
2. Changes: list of files changed and what changed in each
3. Testing: how the feature was tested and what the tests cover
4. Accessibility: what accessibility features are included and how they were verified
5. How to review: what a reviewer should check in the code

Format as a Markdown document suitable for a GitHub PR body.
Save to docs/pr-phone-input.md
```

### Step 5.2 — Debrief

Reflect on the lab by answering these questions in the chat (or write your answers):

1. At which stage did the agent produce output that required correction?
2. Which quality gate caught the most issues?
3. What would have happened if you had skipped the planning step and gone straight to "implement PhoneInput"?
4. How does having `docs/repo-analysis.md` and `.github/copilot-instructions.md` in place change the quality of agent output?

<table style="width:100%; border-collapse:collapse;"><tr><td style="border-left:5px solid #2E7D32; background:#E8F5E9; padding:14px 18px;"><strong style="color:#2E7D32;">✅ LAB 2 COMPLETE:</strong> <span style="color:#2E7D32;">You have run the full professional Agent mode workflow end-to-end: observation → custom instructions → planning → implementation one file at a time → quality gates → PR documentation. This is the complete cycle you will use for every significant feature going forward.</span></td></tr></table>

---

## <span style="color:#1A73E8;">LAB REFERENCE — Key Commands</span>

```bash
# Quality gate commands
npx tsc --noEmit                              # TypeScript strict check
npm test -- PhoneInput      # Run only PhoneInput tests
npm test -- --coverage                        # Full suite + coverage report
npm run lint               # Lint all source files
git diff --name-only                          # Check scope of changes

# Storybook verification
npx storybook build --quiet                   # Build stories (catches compile errors)
```

<table style="width:100%; border-collapse:collapse;">
<tr><td style="background:#0D47A1; color:white; padding:10px 12px; font-weight:bold;">Situation</td><td style="background:#0D47A1; color:white; padding:10px 12px; font-weight:bold;">Recovery Action</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Agent edits wrong files</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Reject those files in Copilot Edits panel. Add explicit file list to next prompt.</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;">Tests fail, agent wants to change assertions</td><td style="padding:10px 12px; border:1px solid #CCC;">Reject edit. Say "Fix the component, not the test. The test assertion is the contract."</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Agent uses `any` type</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Reject. Say "No `any` types. Fix the underlying type error with proper TypeScript."</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;">Coverage drops after new code</td><td style="padding:10px 12px; border:1px solid #CCC;">"The coverage dropped. What new code paths are untested? Add tests for them."</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Storybook build fails</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><code>#terminalLastCommand</code> → "Fix the Storybook story compilation error."</td></tr>
</table>
