<div style="text-align:center; padding: 20px 0;">
<span style="font-size:14px; color:#666666; font-weight:bold; letter-spacing:2px;">MODULE 13</span>

# <span style="color:#0D47A1;">Parallel Workflows & PR Automation with GitHub Copilot</span>

<hr style="border: 3px solid #1A73E8; width:80%;">
</div>

<table style="width:100%; border-collapse:collapse;">
<tr>
<td style="background:#E3F2FD; text-align:center; padding:10px; border:1px solid #BBDEFB; width:25%;"><span style="font-size:12px; color:#666;">Duration</span><br><strong style="color:#0D47A1;">45 min</strong></td>
<td style="background:#E3F2FD; text-align:center; padding:10px; border:1px solid #BBDEFB; width:25%;"><span style="font-size:12px; color:#666;">Format</span><br><strong style="color:#0D47A1;">Lecture + Demo</strong></td>
<td style="background:#E3F2FD; text-align:center; padding:10px; border:1px solid #BBDEFB; width:25%;"><span style="font-size:12px; color:#666;">Audience</span><br><strong style="color:#0D47A1;">React Developers</strong></td>
<td style="background:#E3F2FD; text-align:center; padding:10px; border:1px solid #BBDEFB; width:25%;"><span style="font-size:12px; color:#666;">Day / Position</span><br><strong style="color:#0D47A1;">Day 2 / Fifth</strong></td>
</tr>
</table>

---

## <span style="color:#1A73E8;">LEARNING OBJECTIVES</span>

By the end of this module, participants will be able to:

1. Run two independent React features in parallel using multiple VS Code windows and Copilot Chat sessions
2. Use git worktrees to maintain parallel branches without stashing or switching
3. Generate high-quality PR descriptions from diffs using Copilot
4. Write a reusable GitHub Actions workflow that runs quality gates automatically on every PR
5. Configure Copilot code review integration to automate first-pass PR review

---

## <span style="color:#1A73E8;">SESSION TIMING BREAKDOWN</span>

<table style="width:100%; border-collapse:collapse;">
<tr><td style="background:#00695C; color:white; padding:8px 14px; width:120px; font-weight:bold; font-size:13px;">0:00 – 0:10</td><td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Section 1: Parallel Copilot Sessions — Multiple VS Code Windows & Chat Tabs</td></tr>
<tr><td colspan="2" style="height:4px;"></td></tr>
<tr><td style="background:#00695C; color:white; padding:8px 14px; font-weight:bold; font-size:13px;">0:10 – 0:22</td><td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Section 2: Git Worktrees for Parallel React Feature Development</td></tr>
<tr><td colspan="2" style="height:4px;"></td></tr>
<tr><td style="background:#00695C; color:white; padding:8px 14px; font-weight:bold; font-size:13px;">0:22 – 0:32</td><td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Section 3: PR Automation — Generating Descriptions, Reviews & Changelogs</td></tr>
<tr><td colspan="2" style="height:4px;"></td></tr>
<tr><td style="background:#00695C; color:white; padding:8px 14px; font-weight:bold; font-size:13px;">0:32 – 0:43</td><td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Section 4: GitHub Actions — Automated Quality Gates on Every PR</td></tr>
<tr><td colspan="2" style="height:4px;"></td></tr>
<tr><td style="background:#00695C; color:white; padding:8px 14px; font-weight:bold; font-size:13px;">0:43 – 0:45</td><td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Wrap-Up: Team Workflow Reference</td></tr>
</table>

---

## <span style="color:#0D47A1;">1. Parallel Copilot Sessions — Multiple VS Code Windows & Chat Tabs</span>

A common misconception is that GitHub Copilot limits you to one active conversation at a time. In reality, you can run multiple independent Copilot Agent sessions simultaneously — in separate VS Code windows, or in separate Chat tabs within the same window. This dramatically increases throughput when working on multiple features.

### <span style="color:#0D47A1;">1.1  When to Parallelize</span>

Not every task benefits from parallelization. The key question is: **do the tasks depend on each other's output?**

<table style="width:100%; border-collapse:collapse;">
<tr><td style="background:#2E7D32; color:white; padding:10px 12px; font-weight:bold; width:50%;">Parallelize These</td><td style="background:#C62828; color:white; padding:10px 12px; font-weight:bold; width:50%;">Keep Sequential</td></tr>
<tr><td style="background:#E8F5E9; padding:10px 12px; border:1px solid #CCC;">Two components with no shared types</td><td style="background:#FFEBEE; padding:10px 12px; border:1px solid #CCC;">Component + the hook it depends on</td></tr>
<tr><td style="background:#E8F5E9; padding:10px 12px; border:1px solid #CCC;">Adding Storybook stories while writing tests</td><td style="background:#FFEBEE; padding:10px 12px; border:1px solid #CCC;">Implementation + the tests for that implementation</td></tr>
<tr><td style="background:#E8F5E9; padding:10px 12px; border:1px solid #CCC;">Documentation while code is being written</td><td style="background:#FFEBEE; padding:10px 12px; border:1px solid #CCC;">A new type + the components that use it</td></tr>
<tr><td style="background:#E8F5E9; padding:10px 12px; border:1px solid #CCC;">Two independent bug fixes in separate files</td><td style="background:#FFEBEE; padding:10px 12px; border:1px solid #CCC;">Refactoring a shared utility + updating consumers</td></tr>
<tr><td style="background:#E8F5E9; padding:10px 12px; border:1px solid #CCC;">PR description while CI runs</td><td style="background:#FFEBEE; padding:10px 12px; border:1px solid #CCC;">Type migration across multiple interdependent files</td></tr>
</table>

### <span style="color:#0D47A1;">1.2  Multiple VS Code Windows — Full Isolation</span>

For completely independent features, the safest approach is opening the same repository in two VS Code windows. Each window has its own Copilot Agent session, its own chat history, and its own context. There is no cross-contamination between the two sessions.

**Setup:**
1. Open terminal: `code /path/to/my-form-library` — your main feature window
2. Open a second terminal: `code /path/to/my-form-library` — your second feature window
3. In each window, check out a different branch

**Example — two features running simultaneously:**

| Window 1 | Window 2 |
|---|---|
| Branch: `feature/date-picker` | Branch: `feature/color-picker` |
| Building `DatePicker` component | Building `ColorPicker` component |
| Agent focused on calendar logic | Agent focused on color swatch grid |
| Own git context and history | Own git context and history |

<table style="width:100%; border-collapse:collapse;"><tr><td style="border-left:5px solid #1A73E8; background:#E3F2FD; padding:14px 18px;"><strong style="color:#0D47A1;">⭐ KEY POINT:</strong> <span style="color:#0D47A1;">When you open a git repo in two VS Code windows, they share the same working directory. Changes made in Window 1 appear in Window 2 immediately on disk. This is fine if the branches are different — they modify different files. But do NOT let both windows edit the same file simultaneously — git cannot resolve that conflict automatically and you will lose work.</span></td></tr></table>

### <span style="color:#0D47A1;">1.3  Multiple Chat Tabs — Task Subdivision</span>

Within a single VS Code window, you can create multiple Copilot Chat tabs. Each tab maintains independent conversation history and context, but shares the same file system and workspace index.

**Use case: subdividing a large feature**

Instead of one chat doing everything for `DatePicker`, split tasks:

- **Tab 1 (Agent):** "Build the `DatePicker` component and its props interface"
- **Tab 2 (Agent):** "Write RTL tests for `DatePicker` based on the spec in docs/date-picker-spec.md"
- **Tab 3 (Chat):** "Review the Storybook stories for `DatePicker` I am writing in this file: #file:src/components/DatePicker.stories.tsx"

<table style="width:100%; border-collapse:collapse;"><tr><td style="border-left:5px solid #C62828; background:#FFEBEE; padding:14px 18px; border:1px solid #EF9A9A;"><strong style="color:#C62828;">⚠️ WARNING:</strong> <span style="color:#C62828;">If two Agent mode tabs are active simultaneously and both are writing to the same file, the last write wins and you will lose the other's changes. Only assign one Agent per file at a time. Use chat tabs for read-only operations (code review, explanation, planning) when they share files with an active agent.</span></td></tr></table>

---

## <span style="color:#0D47A1;">2. Git Worktrees for Parallel React Feature Development</span>

Git worktrees solve the hardest problem with parallel feature development: being forced to switch branches on your main working directory. With worktrees, each branch lives in its own directory, each with its own `node_modules` install and its own Copilot session.

### <span style="color:#0D47A1;">2.1  Why Worktrees Beat Branch Switching</span>

<table style="width:100%; border-collapse:collapse;">
<tr><td style="background:#1A73E8; color:white; padding:10px 12px; font-weight:bold;">Pain with `git checkout`</td><td style="background:#1A73E8; color:white; padding:10px 12px; font-weight:bold;">Solution with `git worktree`</td></tr>
<tr><td style="background:#FFEBEE; padding:10px 12px; border:1px solid #CCC;">Must stash WIP before switching to a hotfix branch</td><td style="background:#E8F5E9; padding:10px 12px; border:1px solid #CCC;">Both branches live in different directories simultaneously</td></tr>
<tr><td style="background:#FFEBEE; padding:10px 12px; border:1px solid #CCC;">Copilot loses conversation context when you switch branches</td><td style="background:#E8F5E9; padding:10px 12px; border:1px solid #CCC;">Each worktree has its own VS Code window and Copilot chat</td></tr>
<tr><td style="background:#FFEBEE; padding:10px 12px; border:1px solid #CCC;">Dev server restarts every time you switch</td><td style="background:#E8F5E9; padding:10px 12px; border:1px solid #CCC;">Both dev servers can run simultaneously on different ports</td></tr>
<tr><td style="background:#FFEBEE; padding:10px 12px; border:1px solid #CCC;">node_modules rebuild after switching TypeScript configurations</td><td style="background:#E8F5E9; padding:10px 12px; border:1px solid #CCC;">Each worktree has its own node_modules</td></tr>
</table>

### <span style="color:#0D47A1;">2.2  Setting Up Worktrees for my-form-library</span>

```bash
# From the main repo root
cd ~/Projects/my-form-library   # Your main repo directory

# Create a worktree for a second parallel feature
git worktree add -b feature/date-picker ../my-form-library-datepicker

# Install dependencies in the new worktree
cd ../my-form-library-datepicker
npm install

# Open the worktree in a new VS Code window
code .
```

Now you have two independent working copies:

```text
~/Projects/
  my-form-library/               # main branch or feature/phone-input
    node_modules/
    src/
  my-form-library-datepicker/    # feature/date-picker
    node_modules/
    src/
```

Both share the same `.git` directory — commits, history, and remote tracking are fully synchronized.

### <span style="color:#0D47A1;">2.3  Worktree Workflow for Component Development</span>

**Starting parallel work on two components:**

```bash
# Terminal 1 — Working on PhoneInput
cd ~/Projects/my-form-library
git checkout -b feature/phone-input
# Agent session in this window focused on PhoneInput

# Terminal 2 — Working on DatePicker simultaneously
cd ~/Projects/my-form-library-datepicker
git checkout -b feature/date-picker
# Agent session in this window focused on DatePicker

# When DatePicker is ready to review, check PhoneInput branch first:
cd ~/Projects/my-form-library
git log --oneline feature/date-picker  # Works across both worktrees!
```

<table style="width:100%; border-collapse:collapse;"><tr><td style="border-left:5px solid #1A73E8; background:#E3F2FD; padding:14px 18px;"><strong style="color:#0D47A1;">⭐ KEY POINT:</strong> <span style="color:#0D47A1;">Git commands run from any worktree directory see the same repository. <code>git log feature/date-picker</code> works even if you're in the <code>my-form-library</code> directory. You don't need to switch directories to check the status of another branch.</span></td></tr></table>

### <span style="color:#0D47A1;">2.4  Cleaning Up Worktrees</span>

```bash
# When done with a worktree
git worktree remove ../my-form-library-datepicker

# Or if the directory has been manually deleted
git worktree prune

# List all active worktrees
git worktree list
```

---

## <span style="color:#0D47A1;">3. PR Automation — Generating Descriptions, Reviews & Changelogs</span>

High-quality PRs are essential for team collaboration — but writing good PR descriptions takes time. Copilot can generate first-draft PR descriptions, review code against team conventions, and flag issues before human review begins.

### <span style="color:#0D47A1;">3.1  Generating a PR Description from Git Diff</span>

After completing a feature branch, generate the PR description using the actual diff:

```bash
# Get the diff against main
git diff main...HEAD > /tmp/pr-diff.patch
```

Then in Copilot Chat:

```text
#file:/tmp/pr-diff.patch

Generate a professional GitHub pull request description for this diff.

Structure it as:
## Summary
[1–3 sentence non-technical description of what changed and why]

## Changes
[Bulleted list of files changed and what changed in each]

## Testing
[Describe what tests were added and what they verify]

## Accessibility
[Describe any accessibility features added or verified]

## Breaking Changes
[Any changes to the public component API — prop renames, removed props, changed types]

## Screenshots / Demo
[Note: screenshots to be added by the developer before submitting]

Format for GitHub Markdown.
```

### <span style="color:#0D47A1;">3.2  Automated Code Review with Copilot</span>

Before requesting human review, run a Copilot pre-review to catch obvious issues:

```text
#file:src/components/PhoneInput/PhoneInput.tsx
#file:src/components/PhoneInput/PhoneInput.test.tsx
#file:.github/copilot-instructions.md

Perform a code review of PhoneInput.tsx and PhoneInput.test.tsx.
Check specifically for:
1. TypeScript violations — any, type assertions, missing return types
2. Props interface completeness — any missing props compared to other form components?
3. Accessibility — ARIA attributes, label association, keyboard navigation
4. Test coverage — are there behavior paths in the component not covered by tests?
5. Pattern consistency — does this component follow the conventions in copilot-instructions.md?

For each issue found, specify:
- File and approximate line
- Severity: Critical / Warning / Suggestion
- What the problem is
- How to fix it

Output as a numbered list.
```

<table style="width:100%; border-collapse:collapse;"><tr><td style="border-left:5px solid #1A73E8; background:#E3F2FD; padding:14px 18px;"><strong style="color:#0D47A1;">⭐ KEY POINT:</strong> <span style="color:#0D47A1;">The pre-review prompt gives you a list of issues to address before a human reviewer even sees the PR. In practice, this reduces human review round-trips by 50–70% for team members using it consistently. Save the review output, fix the issues, then note in the PR description: "Pre-reviewed with Copilot — see docs/pr-pre-review.md for initial findings and how they were resolved."</span></td></tr></table>

### <span style="color:#0D47A1;">3.3  Changelog Generation</span>

For a component library, maintaining a `CHANGELOG.md` is essential for consumers. Copilot can keep it updated:

```text
#file:CHANGELOG.md
#file:src/components/PhoneInput/PhoneInput.tsx
#file:src/components/PhoneInput/PhoneInput.stories.tsx

Add a new entry to CHANGELOG.md for the PhoneInput component addition.
Use the existing entry format in the file (Keep a Changelog format).
The version is 1.3.0 (minor version bump — new feature, no breaking changes).
```

---

## <span style="color:#0D47A1;">4. GitHub Actions — Automated Quality Gates on Every PR</span>

Copilot can write and maintain GitHub Actions workflows. Instead of relying on developers to remember to run quality gates locally, encode them in CI so they run automatically on every PR — and block merges when they fail.

### <span style="color:#0D47A1;">4.1  The Component Library CI Workflow</span>

This is the standard CI workflow for `my-form-library`. Ask Copilot to generate it:

```text
Generate a GitHub Actions workflow file for my-form-library.
The workflow should run on:
- Every push to main
- Every pull_request targeting main

The workflow should have the following jobs (in order):
1. lint: run ESLint on src/ with --max-warnings 0
2. typecheck: run `npx tsc --noEmit` — fail if any errors
3. test: run `npm test -- --ci --coverage` — fail if any test fails or coverage drops below threshold
4. build: run `npm run build` — fail if the library build fails
5. storybook-build: run `npx storybook build` — fail if stories don't compile

Additional requirements:
- Cache node_modules using actions/cache with the package-lock.json hash as the key
- jobs.test should upload the coverage report as an artifact
- jobs.test should add a coverage summary comment to the PR using a step with github-actions-coverage-report or similar
- All jobs should specify: runs-on: ubuntu-latest, Node.js version 20

Output the workflow as .github/workflows/ci.yml
```

**The generated workflow should look like this structure:**

```yaml
name: CI

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  lint:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: '20'
          cache: 'npm'
      - run: npm ci
      - run: npm run lint --max-warnings 0

  typecheck:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: '20'
          cache: 'npm'
      - run: npm ci
      - run: npx tsc --noEmit

  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: '20'
          cache: 'npm'
      - run: npm ci
      - run: npm test -- --ci --coverage
      - uses: actions/upload-artifact@v4
        with:
          name: coverage-report
          path: coverage/

  build:
    runs-on: ubuntu-latest
    needs: [lint, typecheck, test]
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: '20'
          cache: 'npm'
      - run: npm ci
      - run: npm run build
```

### <span style="color:#0D47A1;">4.2  Coverage Enforcement</span>

Add a coverage threshold to `jest.config.ts` that CI will enforce:

```text
Add Jest coverage thresholds to jest.config.ts.
Set the following minimum thresholds:
- branches: 80
- functions: 80
- lines: 85
- statements: 85

If coverage falls below these thresholds, `npm test` should exit with a non-zero code (causing CI to fail).
Use the coverageThreshold configuration key in the Jest config.
```

<table style="width:100%; border-collapse:collapse;"><tr><td style="border-left:5px solid #1A73E8; background:#E3F2FD; padding:14px 18px;"><strong style="color:#0D47A1;">⭐ KEY POINT:</strong> <span style="color:#0D47A1;">Coverage thresholds are a forcing function, not a guarantee of quality. A component can have 100% line coverage with tests that assert nothing meaningful. Coverage gates prevent obvious neglect — they don't replace thoughtful test design. Use them alongside the manual test review practices from Lab 2.</span></td></tr></table>

### <span style="color:#0D47A1;">4.3  Copilot Code Review in GitHub (Enterprise)</span>

For organizations using GitHub Copilot Enterprise, automated code review can be enabled directly on GitHub:

**Setting → Repository → Code Review → Enable Copilot Code Review**

When enabled, Copilot automatically posts a review comment on every PR with:
- Summary of what changed
- Potential bugs or issues detected
- Questions for the reviewer to consider
- Suggestions for improvement

You can also configure it to block merge if Copilot finds critical issues. This creates a two-layer review: Copilot first (automated), then human (focused review on the issues Copilot couldn't catch).

```text
#file:.github/copilot-review-instructions.md (create this file)
Instructions for Copilot code review on PRs to my-form-library:

Focus on:
1. TypeScript strictness — flag any `any`, type assertions, or `ts-ignore`
2. Accessibility — check for missing ARIA labels, invalid role usage, missing keyboard handlers
3. Test coverage — check if new component code has corresponding tests
4. Props API consistency — check if new components match the existing Props interface pattern
5. Storybook — check if new components have stories for all their states

Skip:
- Minor style preferences already handled by ESLint/Prettier
- Performance micro-optimizations unless there's a clear render loop issue
```

---

## <span style="color:#1A73E8;">WRAP-UP: Team Workflow Reference</span>

<table style="width:100%; border-collapse:collapse;">
<tr><td style="background:#0D47A1; color:white; padding:10px 12px; font-weight:bold;">Workflow Step</td><td style="background:#0D47A1; color:white; padding:10px 12px; font-weight:bold;">Tool / Approach</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Two independent features simultaneously</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Git worktrees + two VS Code windows + two Agent sessions</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;">Same feature, multiple parallel tasks</td><td style="padding:10px 12px; border:1px solid #CCC;">Multiple Copilot Chat tabs — one agent per file target</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">PR description</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><code>git diff main...HEAD</code> → Copilot structured description prompt</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;">Pre-human code review</td><td style="padding:10px 12px; border:1px solid #CCC;">Copilot code review prompt with explicit checklist</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Automated quality gates</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">GitHub Actions: lint → typecheck → test → build → storybook-build</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;">Merge protection</td><td style="padding:10px 12px; border:1px solid #CCC;">Branch protection rules: require CI pass + 1 human reviewer</td></tr>
</table>
