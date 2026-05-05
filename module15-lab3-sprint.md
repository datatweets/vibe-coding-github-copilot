<div style="text-align:center; padding: 20px 0;">
<span style="font-size:14px; color:#666666; font-weight:bold; letter-spacing:2px;">MODULE 15 — LAB 3</span>

# <span style="color:#0D47A1;">Lab 3: Full Feature Sprint — Ship a Production-Ready React Feature</span>

<hr style="border: 3px solid #1A73E8; width:80%;">
</div>

<table style="width:100%; border-collapse:collapse;">
<tr>
<td style="background:#E3F2FD; text-align:center; padding:10px; border:1px solid #BBDEFB; width:20%;"><span style="font-size:12px; color:#666;">Duration</span><br><strong style="color:#0D47A1;">60 min</strong></td>
<td style="background:#E3F2FD; text-align:center; padding:10px; border:1px solid #BBDEFB; width:20%;"><span style="font-size:12px; color:#666;">Format</span><br><strong style="color:#0D47A1;">Hands-On Lab</strong></td>
<td style="background:#E3F2FD; text-align:center; padding:10px; border:1px solid #BBDEFB; width:20%;"><span style="font-size:12px; color:#666;">Track</span><br><strong style="color:#0D47A1;">Single Guided</strong></td>
<td style="background:#E3F2FD; text-align:center; padding:10px; border:1px solid #BBDEFB; width:20%;"><span style="font-size:12px; color:#666;">Project</span><br><strong style="color:#0D47A1;">my-form-library</strong></td>
<td style="background:#E3F2FD; text-align:center; padding:10px; border:1px solid #BBDEFB; width:20%;"><span style="font-size:12px; color:#666;">Day / Position</span><br><strong style="color:#0D47A1;">Day 2 / Final</strong></td>
</tr>
</table>

---

## <span style="color:#1A73E8;">What You'll Build</span>

In this capstone lab you will ship a `MultiFileUpload` component into `my-form-library` — using every workflow and tool from the course. This is a production-grade feature: real requirements, real quality gates, real PR.

**The component** accepts multiple files via drag-and-drop or file picker, validates file type and size, shows upload progress per file, handles error states, is fully keyboard and screen-reader accessible, and has complete test coverage.

**You will use:**
- Copilot Agent mode for planning, scaffolding, and implementation
- `.github/copilot-instructions.md` for project conventions
- `.github/prompts/` for a reusable feature scaffold prompt
- Quality gates: TypeScript, Jest + RTL + jest-axe, ESLint, coverage
- PR description generation from diff
- git worktrees (optional stretch — for a parallel experimental feature branch)

---

## <span style="color:#1A73E8;">PHASE TIMING OVERVIEW</span>

<table style="width:100%; border-collapse:collapse;">
<tr><td style="background:#00695C; color:white; padding:8px 14px; width:120px; font-weight:bold; font-size:13px;">0:00 – 0:08</td><td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Phase 1 — Decompose & Plan: Break the feature into shippable sub-tasks</td></tr>
<tr><td colspan="2" style="height:4px;"></td></tr>
<tr><td style="background:#00695C; color:white; padding:8px 14px; font-weight:bold; font-size:13px;">0:08 – 0:15</td><td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Phase 2 — Setup & Scaffold: File structure, types interface, custom hook skeleton</td></tr>
<tr><td colspan="2" style="height:4px;"></td></tr>
<tr><td style="background:#00695C; color:white; padding:8px 14px; font-weight:bold; font-size:13px;">0:15 – 0:35</td><td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Phase 3 — Core Sprint: Implement drag-and-drop, validation, progress state, accessibility</td></tr>
<tr><td colspan="2" style="height:4px;"></td></tr>
<tr><td style="background:#00695C; color:white; padding:8px 14px; font-weight:bold; font-size:13px;">0:35 – 0:45</td><td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Phase 4 — Test & Quality Gate: RTL + jest-axe tests, full quality gate run, fix failures</td></tr>
<tr><td colspan="2" style="height:4px;"></td></tr>
<tr><td style="background:#00695C; color:white; padding:8px 14px; font-weight:bold; font-size:13px;">0:45 – 0:53</td><td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Phase 5 — Refactor & Optimize: Error boundary, memoization, performance check</td></tr>
<tr><td colspan="2" style="height:4px;"></td></tr>
<tr><td style="background:#00695C; color:white; padding:8px 14px; font-weight:bold; font-size:13px;">0:53 – 1:00</td><td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Phase 6 — PR, Review & Ship: PR description, Copilot review, git diff final check</td></tr>
</table>

---

## <span style="color:#0D47A1;">PHASE 1 — Decompose & Plan</span>

**⏱ 0:00 – 0:08 (8 min)**

Before writing any code, use Copilot Agent mode to break the feature into a structured delivery plan. This is the most important discipline in the course: **think before you type.**

### Step 1.1 — Feature Analysis

In Agent mode, run this prompt:

```text
[PLAN ONLY — DO NOT CREATE OR EDIT ANY FILES]

I am building a MultiFileUpload component for my-form-library.
Analyze the existing codebase (#codebase) and produce a feature decomposition.

Feature requirements:
- Accept multiple files via drag-and-drop zone OR file picker button
- Validate: accepted file types (configurable via prop), max file size per file (configurable), max total files (configurable)
- Show each selected file as a list item with: filename, size, status icon, remove button
- Show upload progress per file (0–100%) — component accepts a progress map from parent
- Handle three file states: pending, uploading (with progress %), error (with message), success
- Keyboard accessible: drag zone is focusable and responds to Enter/Space, remove buttons are labeled
- Screen reader: live region announces when files are added or removed
- onChange fires with the current FileList every time files change
- onError fires with a list of validation errors when files fail validation
- Storybook stories for: empty state, files selected, file with error, all files succeeded

Produce:
1. A list of files to create with their purpose
2. A list of key decisions about the props interface (names, types)
3. A list of accessibility requirements with specific ARIA attributes
4. A list of test cases that will verify correct behavior
5. An estimated line count for each file

Do NOT generate any code yet.
```

### Step 1.2 — Review the Plan

Read the plan carefully. Before proceeding, verify:

- [ ] All files in the plan are new files in `src/components/MultiFileUpload/` and `src/hooks/` — the agent should not propose to modify any existing component
- [ ] The props interface plan includes: `onChange`, `onError`, `acceptedTypes`, `maxFileSize`, `maxFiles`, `uploadProgress`, `disabled`, `label`
- [ ] The plan includes an `aria-live` region for file announcements
- [ ] The test cases plan includes accessibility tests with `jest-axe`
- [ ] If any of the above is missing, add it to the plan in a follow-up prompt before proceeding

### Step 1.3 — Save the Plan

```text
Save the decomposition you just produced to docs/multifileupload-plan.md
Include the date and your name (or "AI assistant") as the author.
```

---

## <span style="color:#0D47A1;">PHASE 2 — Setup & Scaffold</span>

**⏱ 0:08 – 0:15 (7 min)**

Create the file structure and type interfaces before implementing any logic. Having clean types first ensures the implementation has a clear contract to fulfill.

### Step 2.1 — Create the File Structure

```text
Create the directory and file stubs for MultiFileUpload.
All files go in src/components/MultiFileUpload/ except the hook which goes in src/hooks/.

Files to create (stubs only — no implementation, just the skeleton with TypeScript types):
1. src/components/MultiFileUpload/MultiFileUpload.tsx — the main component, props interface, empty return
2. src/components/MultiFileUpload/MultiFileUpload.test.tsx — empty test file with imports only
3. src/components/MultiFileUpload/MultiFileUpload.stories.tsx — empty stories file with component meta
4. src/components/MultiFileUpload/FileListItem.tsx — sub-component stub for individual file rows
5. src/hooks/useFileValidation.ts — hook stub with the function signature only
6. src/components/MultiFileUpload/index.ts — barrel export: export { MultiFileUpload } from './MultiFileUpload'

After creating, add MultiFileUpload to src/index.ts barrel exports.
```

### Step 2.2 — Define the Props Interface

After file creation, review and finalize the props interface in `MultiFileUpload.tsx`:

```typescript
// What your MultiFileUploadProps should look like — review and adjust if needed
export interface UploadedFile {
  id: string;           // unique identifier, e.g. uuid or filename+timestamp
  file: File;
  status: 'pending' | 'uploading' | 'success' | 'error';
  errorMessage?: string;
}

export interface MultiFileUploadProps {
  label: string;
  value: UploadedFile[];           // controlled — current file list from parent
  onChange: (files: UploadedFile[]) => void;
  onError?: (errors: string[]) => void;
  uploadProgress?: Record<string, number>; // keyed by UploadedFile.id, 0–100
  acceptedTypes?: string[];         // e.g. ['image/png', 'application/pdf']
  maxFileSize?: number;             // bytes, e.g. 5 * 1024 * 1024 = 5MB
  maxFiles?: number;                // e.g. 10
  disabled?: boolean;
  errorMessage?: string;            // external error (e.g. from server)
}
```

If the generated interface differs from the above, prompt: `Update the MultiFileUploadProps interface to match [the specific difference].`

<table style="width:100%; border-collapse:collapse;"><tr><td style="border-left:5px solid #2E7D32; background:#E8F5E9; padding:14px 18px;"><strong style="color:#2E7D32;">✅ CHECKPOINT 1:</strong> <span style="color:#2E7D32;">All 6 files exist. TypeScript compiles clean with <code>npx tsc --noEmit</code>. src/index.ts exports MultiFileUpload. You have NOT written any implementation logic yet.</span></td></tr></table>

---

## <span style="color:#0D47A1;">PHASE 3 — Core Sprint</span>

**⏱ 0:15 – 0:35 (20 min)**

Implement one focused piece at a time. Review each before moving to the next.

### Step 3.1 — Implement useFileValidation

```text
Implement the useFileValidation hook in src/hooks/useFileValidation.ts.

This hook takes:
- files: File[] — the files to validate
- options: { acceptedTypes?: string[], maxFileSize?: number, maxFiles?: number, existingCount?: number }

It returns:
- validFiles: File[] — files that passed all validations
- errors: string[] — human-readable error messages for files that failed

Validation rules:
1. If acceptedTypes is provided and not empty, reject files whose type is not in the list
   Error: `"filename.pdf" is not an accepted file type. Accepted: image/png, image/jpeg`
2. If maxFileSize is provided, reject files larger than the limit
   Error: `"filename.pdf" exceeds the maximum file size of 5MB`
3. If maxFiles is provided, reject files that would push total (existingCount + new) over the limit
   Error: `You can upload a maximum of 10 files. 3 files were not added.`

Validations should all run and all errors collected — do not short-circuit on first error.
Add full TypeScript types. No any.
```

### Step 3.2 — Implement FileListItem

```text
Implement the FileListItem sub-component in src/components/MultiFileUpload/FileListItem.tsx

Props:
- file: UploadedFile
- progress?: number  (0–100, only shown when status is 'uploading')
- onRemove: (id: string) => void
- disabled?: boolean

Requirements:
1. Show filename and formatted file size (e.g. "2.4 MB")
2. Show status icon: spinner for pending/uploading, checkmark for success, X for error
3. Show progress bar when status is 'uploading' (aria-valuenow, aria-valuemin, aria-valuemax, role="progressbar")
4. Show errorMessage text when status is 'error'
5. Remove button: accessible label "Remove filename.pdf", disabled when component is disabled
6. The entire list item has role="listitem"

No useState — this is a pure display component controlled entirely by props.
```

### Step 3.3 — Implement Drag-and-Drop and File Selection Logic

```text
Implement the drag-and-drop zone and file selection in MultiFileUpload.tsx.

The drop zone element must:
- Be a div with role="button", tabIndex={0}, aria-label="Upload files. Drag and drop or press Enter to browse."
- Respond to: onClick (open file picker), onKeyDown (Enter and Space open file picker),
  onDragEnter, onDragOver, onDragLeave, onDrop
- Apply a visual "drag active" CSS class (use inline style or className) when a drag is in progress over it
- Connect to a hidden <input type="file" multiple> element via a ref

When files are selected (via drop or file picker input):
1. Run them through useFileValidation
2. If there are errors, call props.onError with the error list
3. Add the validFiles to the current list as UploadedFile objects with status 'pending'
4. Call props.onChange with the updated file list

Include the FileListItem list:
- Wrap in <ul aria-label="Selected files" role="list">
- Render one <FileListItem> per file in props.value
- Pass uploadProgress[file.id] as progress if available

Include an aria-live="polite" div that announces:
- "2 files added. 5 files selected." when files are added
- "filename.pdf removed. 4 files selected." when a file is removed
```

### Step 3.4 — Wire removeFile and Finalize the Component

```text
Complete MultiFileUpload.tsx:

1. Implement handleRemove(id: string):
   - Filter out the file with the matching id from props.value
   - Call props.onChange with the updated list
   - Update the aria-live announcement text

2. Wire handleRemove to FileListItem onRemove prop

3. Add the disabled state:
   - When props.disabled is true: drop zone has aria-disabled="true" and ignores drag/click events
   - All FileListItem remove buttons are disabled

4. Add the external errorMessage display:
   - If props.errorMessage is provided, render it below the drop zone
   - The error div has role="alert" and id that the drop zone references via aria-describedby

5. Export the component as both named and default export
```

<table style="width:100%; border-collapse:collapse;"><tr><td style="border-left:5px solid #2E7D32; background:#E8F5E9; padding:14px 18px;"><strong style="color:#2E7D32;">✅ CHECKPOINT 2:</strong> <span style="color:#2E7D32;">The component renders without errors. TypeScript compiles clean. The file picker opens when you click or press Enter on the drop zone. Files added via the picker appear in the list. The remove button works. Run: <code>npx tsc --noEmit</code> — zero errors.</span></td></tr></table>

---

## <span style="color:#0D47A1;">PHASE 4 — Test & Quality Gate</span>

**⏱ 0:35 – 0:45 (10 min)**

Now that the implementation exists, write tests that verify its behavior from the user's perspective.

### Step 4.1 — Generate Tests for useFileValidation

```text
Write Jest unit tests for src/hooks/useFileValidation.ts.
Test the hook using @testing-library/react-hooks or renderHook from @testing-library/react.

Required test cases:
1. Returns all files as valid when no options are provided
2. Rejects a file with wrong type when acceptedTypes is configured
3. Rejects a file exceeding maxFileSize
4. Rejects files that exceed maxFiles when combined with existingCount
5. Returns multiple errors in a single call when multiple files fail different validations
6. Does NOT reject valid files when mixed with invalid ones

Add descriptive test names. Use describe() blocks to group by scenario.
```

### Step 4.2 — Generate Tests for MultiFileUpload

```text
Write RTL tests for src/components/MultiFileUpload/MultiFileUpload.test.tsx.
Use @testing-library/react, @testing-library/user-event, and jest-axe.

Required test cases:

ACCESSIBILITY:
1. jest-axe: no accessibility violations in the empty state
2. jest-axe: no accessibility violations when files are loaded with mixed statuses
3. Drop zone has role="button" and is keyboard focusable
4. Drop zone announces state changes via aria-live region

INTERACTION:
5. Clicking the drop zone opens the file picker (hint: mock the hidden input click)
6. Pressing Enter on the drop zone opens the file picker
7. Pressing Space on the drop zone opens the file picker
8. Dropping a valid file calls onChange with a pending UploadedFile
9. Dropping an invalid file (wrong type) calls onError with an error message
10. Clicking remove button calls onChange with the file removed
11. Remove button is labeled with the filename (aria-label check)

UPLOAD PROGRESS:
12. When status is 'uploading', a progress bar appears with correct aria attributes
13. When uploadProgress prop provides a value, progress bar reflects it

DISABLED STATE:
14. When disabled=true, drop zone has aria-disabled="true"
15. When disabled=true, clicking the drop zone does NOT open the file picker
```

### Step 4.3 — Full Quality Gate

Run all quality gates in sequence. Fix any failures using `#terminalLastCommand`:

```bash
# Step 1: TypeScript
npx tsc --noEmit

# Step 2: ESLint
npm run lint --max-warnings 0

# Step 3: Tests with coverage
npm test -- --ci --coverage

# Step 4: Library build
npm run build
```

If any command fails, use this recovery pattern in Copilot:

```text
#terminalLastCommand

This quality gate failed. Identify the root cause and fix it.
Do NOT change test assertions to make tests pass — fix the component or hook.
Show the specific diff needed to resolve the failure.
```

<table style="width:100%; border-collapse:collapse;"><tr><td style="border-left:5px solid #2E7D32; background:#E8F5E9; padding:14px 18px;"><strong style="color:#2E7D32;">✅ CHECKPOINT 3:</strong> <span style="color:#2E7D32;">All 4 quality gates pass. Coverage report shows MultiFileUpload and useFileValidation at ≥ 85% line coverage. Zero ESLint warnings. Zero TypeScript errors. Library builds successfully.</span></td></tr></table>

---

## <span style="color:#0D47A1;">PHASE 5 — Refactor & Optimize</span>

**⏱ 0:45 – 0:53 (8 min)**

With tests as your safety net, make targeted improvements before shipping.

### Step 5.1 — Add Error Boundary

Ask Copilot:

```text
Wrap MultiFileUpload in an ErrorBoundary without putting JSX in a `.ts` file.

Rather than having consumers wrap manually every time, create a wrapped export:

Create `src/components/MultiFileUpload/SafeMultiFileUpload.tsx`:
```

```tsx
import { ErrorBoundary } from '../ErrorBoundary';
import { MultiFileUpload, type MultiFileUploadProps } from './MultiFileUpload';

export function SafeMultiFileUpload(props: MultiFileUploadProps) {
  return (
  <ErrorBoundary
    fallback={(error) => (
      <div role="alert" style={{ padding: '12px', border: '1px solid #EF9A9A', borderRadius: '4px' }}>
        <strong>File upload encountered an error.</strong>
        <p style={{ margin: '4px 0 0', fontSize: '14px', color: '#555' }}>{error.message}</p>
      </div>
    )}
  >
    <MultiFileUpload {...props} />
  </ErrorBoundary>
  );
}
```

Then ask Copilot:

```text
Then update `src/components/MultiFileUpload/index.ts` to export from `./SafeMultiFileUpload`.

Export both MultiFileUpload (raw) and SafeMultiFileUpload (with boundary) from src/index.ts.
```

### Step 5.2 — Memoize Event Handlers

```text
#file:src/components/MultiFileUpload/MultiFileUpload.tsx

Review this component for unnecessary re-renders.

Identify any callback functions (handleDrop, handleRemove, handleFileChange, etc.)
that are created on every render and are passed as props to FileListItem.

For each one, apply useCallback with the correct dependency array.

Show the exact diff. Do not add useCallback where it provides no benefit
(e.g., handlers that are not passed to memoized children).
```

### Step 5.3 — Storybook Stories

```text
Create Storybook stories in MultiFileUpload.stories.tsx.

Required stories:
1. Default — empty state, no files selected
2. WithFiles — 3 files loaded: one pending, one uploading (50%), one success
3. WithError — one file with status 'error' and an errorMessage
4. AllSucceeded — 3 files all with status 'success'
5. Disabled — component with disabled=true and 2 files loaded
6. WithValidationConfig — configured with acceptedTypes: ['image/png', 'image/jpeg'], maxFileSize: 2MB, maxFiles: 5

Use CSF3 format. Include args tables for all props.
Add a play() function to the Default story that simulates opening the file picker.
```

---

## <span style="color:#0D47A1;">PHASE 6 — PR, Review & Ship</span>

**⏱ 0:53 – 1:00 (7 min)**

The feature is complete. Ship it with a PR that shows your work clearly.

### Step 6.1 — Generate the PR Description

```bash
# Commit everything first
git add -A
git commit -m "feat: add MultiFileUpload component with drag-and-drop, validation, and a11y"

# Generate the diff
git diff main...HEAD > /tmp/multifileupload-pr.patch
```

Then in Copilot Chat:

```text
#file:/tmp/multifileupload-pr.patch

Generate a production-quality GitHub pull request description for this feature.

Structure:
## Summary
## What's Included (file list with one-line descriptions)
## Component API (key props table: name | type | description)
## Accessibility Features
## Test Coverage (what is tested and what coverage was achieved)
## Breaking Changes (none expected — new component)
## Testing Locally (commands to run)
```

### Step 6.2 — Copilot Pre-Review

```text
#file:src/components/MultiFileUpload/MultiFileUpload.tsx
#file:src/hooks/useFileValidation.ts
#file:src/components/MultiFileUpload/MultiFileUpload.test.tsx
#file:.github/copilot-instructions.md

Perform a code review of this feature before human review.

Check for:
1. TypeScript strictness — any `any`, type assertions, missing return types
2. Accessibility completeness — ARIA attributes, keyboard support, live regions
3. Test completeness — behavior paths covered, edge cases missing
4. Pattern consistency with copilot-instructions.md conventions
5. Security — any use of dangerouslySetInnerHTML or unvalidated user data rendered as HTML

Output as a numbered list with: File, Line (approx), Severity (Critical/Warning/Suggestion), Issue, Fix.
```

**Fix any Critical or Warning items before submitting.** Suggestions can be deferred.

### Step 6.3 — Final Git Diff Review

```bash
# One last look at everything going into this PR
git diff main...HEAD --stat

# Check the total size is reasonable (a new component: 15–25 files changed is normal)
git diff main...HEAD --name-only
```

<table style="width:100%; border-collapse:collapse;"><tr><td style="border-left:5px solid #2E7D32; background:#E8F5E9; padding:14px 18px;"><strong style="color:#2E7D32;">✅ CHECKPOINT 4 — FINAL:</strong> <span style="color:#2E7D32;">All quality gates pass. PR description generated and reviewed. Copilot pre-review complete with zero Critical issues. Git diff shows only expected files. The branch is ready to merge. Congratulations — you have shipped a production-ready React feature.</span></td></tr></table>

---

## <span style="color:#1A73E8;">Stretch Goals (If You Finish Early)</span>

If you complete the full lab before time is up:

<table style="width:100%; border-collapse:collapse;">
<tr><td style="background:#1A73E8; color:white; padding:10px 12px; font-weight:bold; width:40%;">Stretch Goal</td><td style="background:#1A73E8; color:white; padding:10px 12px; font-weight:bold;">What to Do</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><strong>Git Worktree:</strong> Experimental variant</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Create a worktree branch to experiment with a "paste from clipboard" feature that accepts image/png from clipboard paste events (onPaste handler). Keep it isolated from the main feature.</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><strong>Changelog:</strong> Update CHANGELOG.md</td><td style="padding:10px 12px; border:1px solid #CCC;">Ask Copilot to add a 2.0.0 entry to CHANGELOG.md for MultiFileUpload as a major feature addition.</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><strong>Tech Debt:</strong> Run the debt audit</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Run the debt audit prompt from Module 14 against the full codebase including your new feature. How does MultiFileUpload score?</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><strong>Dependabot:</strong> Add configuration</td><td style="padding:10px 12px; border:1px solid #CCC;">Create <code>.github/dependabot.yml</code> as shown in Module 14. Add CI badge to README.md.</td></tr>
</table>

---

## <span style="color:#1A73E8;">QUICK REFERENCE — Full Quality Gate Commands</span>

```bash
npx tsc --noEmit                                  # TypeScript check
npm run lint --max-warnings 0   # ESLint
npm test -- --ci --coverage                       # Tests + coverage
npm run build                                     # Library build
npx storybook build                               # Stories compile check
```

**Recovery prompt pattern (paste into Copilot after any failure):**
```text
#terminalLastCommand
This quality gate failed. Fix the root cause. Do not change test assertions.
Show me the minimal diff to resolve this failure.
```
