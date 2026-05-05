<div style="text-align:center; padding: 20px 0;">
<span style="font-size:14px; color:#666666; font-weight:bold; letter-spacing:2px;">MODULE 9</span>

# <span style="color:#0D47A1;">AIOps: CI/CD & Release Management with GitHub Copilot</span>

<hr style="border: 3px solid #1A73E8; width:80%;">
</div>

<table style="width:100%; border-collapse:collapse;">
<tr>
<td style="background:#E3F2FD; text-align:center; padding:10px; border:1px solid #BBDEFB; width:25%;"><span style="font-size:12px; color:#666;">Duration</span><br><strong style="color:#0D47A1;">45 min</strong></td>
<td style="background:#E3F2FD; text-align:center; padding:10px; border:1px solid #BBDEFB; width:25%;"><span style="font-size:12px; color:#666;">Format</span><br><strong style="color:#0D47A1;">Lecture + Demo</strong></td>
<td style="background:#E3F2FD; text-align:center; padding:10px; border:1px solid #BBDEFB; width:25%;"><span style="font-size:12px; color:#666;">Audience</span><br><strong style="color:#0D47A1;">React Developers</strong></td>
<td style="background:#E3F2FD; text-align:center; padding:10px; border:1px solid #BBDEFB; width:25%;"><span style="font-size:12px; color:#666;">Day / Position</span><br><strong style="color:#0D47A1;">Day 2 / First</strong></td>
</tr>
</table>

---

## <span style="color:#1A73E8;">LEARNING OBJECTIVES</span>

By the end of this module, you will be able to:

1. Design a GitHub Actions CI workflow that enforces TypeScript, ESLint, tests, coverage, build, and Storybook gates
2. Use GitHub Copilot Chat and the current standalone Copilot CLI to analyze CI failures safely
3. Generate release notes, PR summaries, and quality-check drafts from sanitized local git data
4. Configure Husky and lint-staged for pre-commit quality enforcement
5. Apply AIOps principles without giving AI unattended authority to change production code

---

## <span style="color:#1A73E8;">SESSION TIMING BREAKDOWN</span>

<table style="width:100%; border-collapse:collapse;">
<tr><td style="background:#00695C; color:white; padding:8px 14px; width:120px; font-weight:bold; font-size:13px;">0:00 – 0:10</td><td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Section 1: CI as the Backstop for AI-Assisted Development</td></tr>
<tr><td colspan="2" style="height:4px;"></td></tr>
<tr><td style="background:#00695C; color:white; padding:8px 14px; font-weight:bold; font-size:13px;">0:10 – 0:20</td><td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Section 2: AI-Assisted Failure Analysis Without Unattended AI Execution</td></tr>
<tr><td colspan="2" style="height:4px;"></td></tr>
<tr><td style="background:#00695C; color:white; padding:8px 14px; font-weight:bold; font-size:13px;">0:20 – 0:28</td><td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Section 3: Release Notes & PR Quality Drafts</td></tr>
<tr><td colspan="2" style="height:4px;"></td></tr>
<tr><td style="background:#00695C; color:white; padding:8px 14px; font-weight:bold; font-size:13px;">0:28 – 0:37</td><td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Section 4: Git Hooks & npm Scripts for Local Quality Gates</td></tr>
<tr><td colspan="2" style="height:4px;"></td></tr>
<tr><td style="background:#00695C; color:white; padding:8px 14px; font-weight:bold; font-size:13px;">0:37 – 0:43</td><td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Section 5: Complete CI Workflow for my-form-library</td></tr>
<tr><td colspan="2" style="height:4px;"></td></tr>
<tr><td style="background:#00695C; color:white; padding:8px 14px; font-weight:bold; font-size:13px;">0:43 – 0:45</td><td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Wrap-Up: Quick Reference & Transition to Module 10</td></tr>
</table>

---

<table style="width:100%; border-collapse:collapse;"><tr><td style="background:#00695C; color:white; padding:8px 16px; font-weight:bold;">0:00 – 0:10</td><td style="background:#E0F2F1; padding:8px 16px; color:#00695C; font-weight:bold; font-size:16px;">SECTION 1: CI as the Backstop for AI-Assisted Development</td></tr></table>

## <span style="color:#0D47A1;">1. CI as the Backstop for AI-Assisted Development</span>

### <span style="color:#0D47A1;">1.1  Welcome to Day 2</span>

Yesterday you scaffolded a project, learned refactoring and debugging, and mastered AI-driven testing. Today we connect those habits to team infrastructure. The core idea is simple: **Copilot can help write code, but CI decides whether the code is acceptable.**

### <span style="color:#0D47A1;">1.2  Why We Do Not Let AI Run Unattended Fixes in CI</span>

GitHub Actions should gather evidence and enforce gates. Copilot should help humans interpret that evidence. Do not build a pipeline that lets AI generate arbitrary shell commands and run them automatically.

<table style="width:100%; border-collapse:collapse;">
<tr><td style="background:#0D47A1; color:white; padding:10px 12px; border:1px solid #BBDEFB; font-weight:bold;">Safe CI Responsibility</td><td style="background:#0D47A1; color:white; padding:10px 12px; border:1px solid #BBDEFB; font-weight:bold;">Human + Copilot Responsibility</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Run deterministic checks: lint, typecheck, tests, build</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Analyze failures and decide the fix</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;">Upload logs, coverage, and build artifacts</td><td style="padding:10px 12px; border:1px solid #CCC;">Summarize logs with Copilot Chat or Copilot CLI</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Block merges when gates fail</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Open a reviewed PR for any code change</td></tr>
</table>

<table style="width:100%; border-collapse:collapse;"><tr><td style="border-left:5px solid #C62828; background:#FFEBEE; padding:14px 18px; border:1px solid #EF9A9A;"><strong style="color:#C62828;">⚠️ SECURITY RULE:</strong> <span style="color:#C62828;">Never configure CI to execute AI-generated shell commands automatically. CI can collect logs and fail safely. Humans review Copilot's diagnosis and make code changes through normal pull requests.</span></td></tr></table>

### <span style="color:#0D47A1;">1.3  Current Copilot CLI Role</span>

The current GitHub Copilot CLI is useful for local, human-reviewed analysis:

```bash
# Install once on your development machine
npm install -g @github/copilot
copilot login

# Ask a one-shot question
copilot -p "Explain this Jest failure and suggest where to look first: [paste sanitized output]"
```

Use this locally or in a controlled instructor demo. Do not assume your CI runner can authenticate to Copilot or safely execute AI-generated changes.

---

<table style="width:100%; border-collapse:collapse;"><tr><td style="background:#00695C; color:white; padding:8px 16px; font-weight:bold;">0:10 – 0:20</td><td style="background:#E0F2F1; padding:8px 16px; color:#00695C; font-weight:bold; font-size:16px;">SECTION 2: AI-Assisted Failure Analysis Without Unattended AI Execution</td></tr></table>

## <span style="color:#0D47A1;">2. AI-Assisted Failure Analysis Without Unattended AI Execution</span>

### <span style="color:#0D47A1;">2.1  Capture Logs in CI</span>

Add log capture to your test job so the failed output is easy to inspect:

```yaml
# Add to your existing CI workflow
- name: Run Tests
  run: npm test -- --ci 2>&1 | tee test-output.txt

- name: Upload Test Output
  if: always()
  uses: actions/upload-artifact@v4
  with:
    name: test-output
    path: test-output.txt
```

### <span style="color:#0D47A1;">2.2  Analyze Failures Locally with Copilot</span>

After downloading the artifact or copying the relevant log section, ask Copilot for a diagnosis:

```bash
tail -150 test-output.txt > /tmp/test-failure-summary.txt
copilot -p "Analyze this Jest failure. Identify the failing tests, likely root cause, and the smallest safe fix. Do not suggest changing assertions unless the test is wrong: [paste sanitized failure summary from /tmp/test-failure-summary.txt]"
```

Or in Copilot Chat:

```text
The CI test job failed. Here is the exact command and the last 150 lines of output:

[paste sanitized output]

Diagnose:
1. Which test failed?
2. Is this likely product code, test setup, or flaky timing?
3. What file should I inspect first?
4. What is the smallest safe fix?
```

<table style="width:100%; border-collapse:collapse;"><tr><td style="border-left:5px solid #1A73E8; background:#E3F2FD; padding:14px 18px;"><strong style="color:#0D47A1;">⭐ KEY POINT:</strong> <span style="color:#0D47A1;">A good AIOps workflow does not remove the human review point. It makes the human review faster by gathering the right evidence and producing a first-pass diagnosis.</span></td></tr></table>

### <span style="color:#0D47A1;">2.3  AI-Assisted ESLint Fix Workflow</span>

Use ESLint's deterministic output first, then ask Copilot to explain the pattern:

```bash
npm run lint -- --format json > lint-errors.json

copilot -p "This is ESLint JSON output from a React TypeScript project. Summarize the recurring violation categories and suggest a safe order to fix them. Do not write shell commands that modify files: [paste sanitized excerpt from lint-errors.json]"
```

Then fix in Copilot Chat or Agent mode with narrow scope:

```text
Fix the ESLint violations in src/components/TextInput/TextInput.tsx only.
Do not change behavior.
After the edit, show the ESLint command I should run.
```

---

<table style="width:100%; border-collapse:collapse;"><tr><td style="background:#00695C; color:white; padding:8px 16px; font-weight:bold;">0:20 – 0:28</td><td style="background:#E0F2F1; padding:8px 16px; color:#00695C; font-weight:bold; font-size:16px;">SECTION 3: Release Notes & PR Quality Drafts</td></tr></table>

## <span style="color:#0D47A1;">3. Release Notes & PR Quality Drafts</span>

### <span style="color:#0D47A1;">3.1  Draft Release Notes from Git History</span>

Generate the source data with Git, then use Copilot for the first draft:

```bash
git log --oneline v1.0.0..HEAD > /tmp/release-commits.txt
copilot -p "Draft release notes from these commits. Group by Features, Fixes, Breaking Changes, and Internal. Output Markdown only: [paste commit list from /tmp/release-commits.txt]" > RELEASE_NOTES_DRAFT.md
```

Review `RELEASE_NOTES_DRAFT.md` before publishing. Check for:

- Missing breaking changes
- Overstated features
- Internal implementation details that should not be public
- Incorrect issue or PR numbers

### <span style="color:#0D47A1;">3.2  Draft PR Quality Review</span>

```bash
git diff origin/main...HEAD --stat > /tmp/pr-stat.txt
git diff origin/main...HEAD -- src/ > /tmp/pr-src.diff

copilot -p "Review this PR diff for a React component library. Focus on missing tests, accessibility, TypeScript strictness, hardcoded values, and oversized changes. Output findings with file names and rationale: [paste git diff --stat and a sanitized excerpt from /tmp/pr-src.diff]" > /tmp/pr-quality-review.md
```

This is a **pre-review checklist**, not an automated approval.

<table style="width:100%; border-collapse:collapse;"><tr><td style="border-left:5px solid #1A73E8; background:#E3F2FD; padding:14px 18px;"><strong style="color:#0D47A1;">⭐ KEY POINT:</strong> <span style="color:#0D47A1;">Use Copilot to draft release and review text, then verify every claim. AI is good at grouping and summarizing; humans remain responsible for accuracy.</span></td></tr></table>

---

<table style="width:100%; border-collapse:collapse;"><tr><td style="background:#00695C; color:white; padding:8px 16px; font-weight:bold;">0:28 – 0:37</td><td style="background:#E0F2F1; padding:8px 16px; color:#00695C; font-weight:bold; font-size:16px;">SECTION 4: Git Hooks & npm Scripts for Quality Enforcement</td></tr></table>

## <span style="color:#0D47A1;">4. Git Hooks & npm Scripts for Quality Enforcement</span>

### <span style="color:#0D47A1;">4.1  Husky + lint-staged Setup</span>

The recommended approach for React/TypeScript projects is **Husky** (Git hook manager) + **lint-staged** (run linters on staged files only). Ask Copilot Agent to scaffold the setup:

```text
(Copilot Chat, Agent mode)
"Set up Husky and lint-staged in this project for a pre-commit hook
that runs ESLint and Prettier on staged TypeScript/TSX files.
Install the necessary packages and configure .husky/pre-commit
and the lint-staged config in package.json.
Do not change application source code."
```

Expected generated pieces:

```bash
# .husky/pre-commit
#!/usr/bin/env sh
. "$(dirname -- "$0")/_/husky.sh"

npx lint-staged
```

```jsonc
// package.json excerpt
{
  "scripts": {
    "prepare": "husky"
  },
  "lint-staged": {
    "src/**/*.{ts,tsx}": [
      "eslint --fix",
      "prettier --write"
    ]
  }
}
```

### <span style="color:#0D47A1;">4.2  Pre-Commit Hook Types</span>

<table style="width:100%; border-collapse:collapse;">
<tr><td style="background:#0D47A1; color:white; padding:10px 12px; border:1px solid #BBDEFB; font-weight:bold;">Hook</td><td style="background:#0D47A1; color:white; padding:10px 12px; border:1px solid #BBDEFB; font-weight:bold;">Use For</td><td style="background:#0D47A1; color:white; padding:10px 12px; border:1px solid #BBDEFB; font-weight:bold;">Keep It Fast?</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><code>pre-commit</code></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Lint/format staged files</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Yes — under 10 seconds if possible</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><code>pre-push</code></td><td style="padding:10px 12px; border:1px solid #CCC;">Full tests or build before pushing</td><td style="padding:10px 12px; border:1px solid #CCC;">Medium — acceptable if under 1-2 minutes</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><code>commit-msg</code></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Conventional Commits format</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Yes — string validation only</td></tr>
</table>

### <span style="color:#0D47A1;">4.3  AI-Assisted Commit Message Guidance</span>

Do not call AI from a commit hook. Hooks should be deterministic and fast. If a commit message fails validation, print examples and let the developer ask Copilot manually:

```bash
# .husky/commit-msg
#!/usr/bin/env sh

COMMIT_MSG_FILE=$1
COMMIT_MSG=$(cat "$COMMIT_MSG_FILE")

if ! echo "$COMMIT_MSG" | grep -Eq '^(feat|fix|docs|style|refactor|test|chore)(\(.+\))?: .+'; then
  echo "Commit message must follow Conventional Commits."
  echo "Examples:"
  echo "  feat(text-input): add error state"
  echo "  fix(select): preserve keyboard focus"
  echo ""
  echo "Tip: run this manually if you want a draft:"
  echo "  git diff --cached --stat"
  echo "  copilot -p 'Suggest a Conventional Commit message for this staged diff summary: ...'"
  exit 1
fi
```

---

<table style="width:100%; border-collapse:collapse;"><tr><td style="background:#00695C; color:white; padding:8px 16px; font-weight:bold;">0:37 – 0:43</td><td style="background:#E0F2F1; padding:8px 16px; color:#00695C; font-weight:bold; font-size:16px;">SECTION 5: Complete CI Workflow for my-form-library</td></tr></table>

## <span style="color:#0D47A1;">5. Complete CI Workflow for my-form-library</span>

This is the CI workflow the course project should have before the capstone lab:

```yaml
# .github/workflows/ci.yml
name: CI

on:
  push:
    branches: [main, develop]
  pull_request:
    branches: [main]

jobs:
  quality:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - uses: actions/setup-node@v4
        with:
          node-version: '20'
          cache: 'npm'

      - name: Install dependencies
        run: npm ci

      - name: TypeScript
        run: npx tsc --noEmit

      - name: ESLint
        run: npm run lint

      - name: Unit tests with coverage
        run: npm test -- --ci --coverage

      - name: Library build
        run: npm run build

      - name: Storybook build
        run: npm run build-storybook

      - name: Upload coverage
        if: always()
        uses: actions/upload-artifact@v4
        with:
          name: coverage
          path: coverage/
```

If a project uses different script names, ask Copilot Chat to adapt the workflow with `#file:package.json` in context.

<table style="width:100%; border-collapse:collapse;"><tr><td style="border-left:5px solid #2E7D32; background:#E8F5E9; padding:14px 18px;"><strong style="color:#2E7D32;">✅ CI CHECKPOINT:</strong> <span style="color:#2E7D32;">The workflow should fail if TypeScript, ESLint, unit tests, coverage, build, or Storybook compilation fails. It should not run AI-generated fix commands automatically.</span></td></tr></table>

---

## <span style="color:#1A73E8;">MODULE 9 RECAP</span>

- ✅ **CI gates:** use deterministic checks as the team backstop for Copilot-generated code
- ✅ **Failure analysis:** collect logs in CI, then use Copilot Chat or `copilot -p` locally to diagnose
- ✅ **Release notes:** draft from git history, then review for accuracy before publishing
- ✅ **Git hooks:** use deterministic local hooks for fast feedback
- ✅ **Security boundary:** never let AI-generated commands run unattended in CI

## <span style="color:#1A73E8;">TRANSITION TO MODULE 10</span>

Now that CI can enforce quality gates, Module 10 moves into agent workflows. The rule carries forward: agents can plan and implement, but the project must have deterministic checks that validate every change.

---

Module 9 — AIOps: CI/CD & Release Management with GitHub Copilot
