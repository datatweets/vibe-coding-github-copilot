<div style="text-align:center; padding: 20px 0;">

<span style="font-size:14px; color:#666666; font-weight:bold; letter-spacing:2px;">MODULE 5</span>

# <span style="color:#0D47A1;">Automation & Scripting for React Teams — Copilot CLI, GitHub Actions & Bulk Workflows</span>

<hr style="border: 3px solid #1A73E8; width:80%;">

</div>

<table style="width:100%; border-collapse:collapse;">
<tr>
<td style="background:#E3F2FD; text-align:center; padding:10px; border:1px solid #BBDEFB; width:25%;"><span style="font-size:12px; color:#666;">Duration</span><br><strong style="color:#0D47A1;">45 min</strong></td>
<td style="background:#E3F2FD; text-align:center; padding:10px; border:1px solid #BBDEFB; width:25%;"><span style="font-size:12px; color:#666;">Format</span><br><strong style="color:#0D47A1;">Lecture + Demo</strong></td>
<td style="background:#E3F2FD; text-align:center; padding:10px; border:1px solid #BBDEFB; width:25%;"><span style="font-size:12px; color:#666;">Audience</span><br><strong style="color:#0D47A1;">React Developers</strong></td>
<td style="background:#E3F2FD; text-align:center; padding:10px; border:1px solid #BBDEFB; width:25%;"><span style="font-size:12px; color:#666;">Day / Position</span><br><strong style="color:#0D47A1;">Day 1 / Fifth</strong></td>
</tr>
</table>

---

## <span style="color:#1A73E8;">LEARNING OBJECTIVES</span>

By the end of this module, participants will be able to:

1. Use the standalone GitHub Copilot CLI (`copilot -p`) to get AI assistance directly in the terminal for shell commands, npm workflows, and git operations
2. Write, debug, and improve shell scripts and npm automation scripts with Copilot Chat, using `#file:` context to ground Copilot in your actual project
3. Generate GitHub Actions workflows for React CI/CD using Copilot — automated testing, coverage gates, bundle size monitoring, and PR quality checks
4. Run bulk React development tasks using Agent mode for large-scale changes across multiple files: prop additions, hook migrations, and test generation at scale
5. Design safe and reliable automation — secret management, controlled Agent mode scope, error handling patterns, and safe CI/CD integration

---

## <span style="color:#1A73E8;">SESSION TIMING BREAKDOWN</span>

<table style="width:100%; border-collapse:collapse;">
<tr><td style="background:#00695C; color:white; padding:8px 14px; width:120px; font-weight:bold; font-size:13px;">0:00 – 0:10</td><td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Section 1: GitHub Copilot CLI — AI-Assisted Terminal Work</td></tr>
<tr><td colspan="2" style="height:4px;"></td></tr>
<tr><td style="background:#00695C; color:white; padding:8px 14px; font-weight:bold; font-size:13px;">0:10 – 0:18</td><td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Section 2: Copilot-Assisted Script Writing — Shell, npm & YAML</td></tr>
<tr><td colspan="2" style="height:4px;"></td></tr>
<tr><td style="background:#00695C; color:white; padding:8px 14px; font-weight:bold; font-size:13px;">0:18 – 0:28</td><td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Section 3: GitHub Actions for React CI/CD</td></tr>
<tr><td colspan="2" style="height:4px;"></td></tr>
<tr><td style="background:#00695C; color:white; padding:8px 14px; font-weight:bold; font-size:13px;">0:28 – 0:36</td><td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Section 4: Agent Mode for Bulk React Workflows</td></tr>
<tr><td colspan="2" style="height:4px;"></td></tr>
<tr><td style="background:#00695C; color:white; padding:8px 14px; font-weight:bold; font-size:13px;">0:36 – 0:43</td><td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Section 5: Real-World Automation Recipes for React Teams</td></tr>
<tr><td colspan="2" style="height:4px;"></td></tr>
<tr><td style="background:#00695C; color:white; padding:8px 14px; font-weight:bold; font-size:13px;">0:43 – 0:45</td><td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Wrap-Up: Quick Reference & Transition to Lab 1</td></tr>
</table>

---

<table style="width:100%; border-collapse:collapse;"><tr><td style="background:#00695C; color:white; padding:8px 16px; font-weight:bold;">0:00 – 0:10</td><td style="background:#E0F2F1; padding:8px 16px; color:#00695C; font-weight:bold; font-size:16px;">SECTION 1: GitHub Copilot CLI — AI-Assisted Terminal Work</td></tr></table>

## <span style="color:#0D47A1;">1. GitHub Copilot CLI: AI-Assisted Terminal Work</span>

### <span style="color:#0D47A1;">1.1  What Is Copilot CLI?</span>

In Module 4, you used GitHub Copilot in VS Code — interactive, visual, conversation-based. The current GitHub Copilot CLI brings Copilot assistance into your terminal for the moments you're working with shell commands, npm scripts, git operations, and build tools — without switching windows.

Copilot CLI is a standalone command-line tool:
- **`copilot`** opens an interactive terminal assistant
- **`copilot -p "prompt"`** sends a one-shot prompt and prints the answer

This is the terminal developer's equivalent of asking Copilot Chat for command help, but it does not directly edit your source files. Treat the output as advice: read it, understand it, then run the command yourself if it is safe.

<table style="width:100%; border-collapse:collapse;">
<tr><td style="background:#0D47A1; color:white; padding:10px 12px; border:1px solid #BBDEFB; font-weight:bold;">In VS Code (Module 4)</td><td style="background:#0D47A1; color:white; padding:10px 12px; border:1px solid #BBDEFB; font-weight:bold;">In the Terminal (Module 5)</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Ctrl+I → <code>/explain</code> on a TypeScript function</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><code>copilot -p "Explain this shell command: find src -name '*.tsx' -mtime -7"</code></td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;">Ctrl+I → <code>/fix</code> on a TypeScript error</td><td style="padding:10px 12px; border:1px solid #CCC;"><code>copilot -p "Suggest how to debug a failing Jest test in CI"</code></td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Copilot Chat panel for multi-turn conversation</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Copilot CLI for one-shot command generation or explanation</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;">Best for: code editing, architecture, testing tasks</td><td style="padding:10px 12px; border:1px solid #CCC;">Best for: shell commands, npm scripts, git operations, CI debugging</td></tr>
</table>

### <span style="color:#0D47A1;">1.2  Installation & Setup</span>

```bash
# Prerequisites: Node.js 22+ and a GitHub account with Copilot access
node --version

# Install the current standalone GitHub Copilot CLI
npm install -g @github/copilot

# Authenticate
copilot login

# Verify the CLI responds
copilot --help
```

<table style="width:100%; border-collapse:collapse;"><tr><td style="border-left:5px solid #C62828; background:#FFEBEE; padding:14px 18px; border:1px solid #EF9A9A;"><strong style="color:#C62828;">⚠️ VERSION NOTE:</strong> <span style="color:#C62828;">Older tutorials used a retired GitHub CLI extension for Copilot. Do not use that path for this course. Use the standalone <code>copilot</code> CLI shown above.</span></td></tr></table>

### <span style="color:#0D47A1;">1.3  `copilot -p` — Get Shell Command Help from Intent</span>

Describe what you want to accomplish in plain English; Copilot CLI returns a suggested approach. Review the response before running anything:

```bash
# React development scenarios
copilot -p "Suggest a macOS/Linux shell command to list TypeScript files modified in the last 3 days. Explain the command."

copilot -p "Suggest a safe command to find React components that use the useEffect hook. Explain any flags."

copilot -p "Suggest the npm command to check which packages have high or critical security vulnerabilities."

copilot -p "In a Jest project, how do I run only tests that match ProductCard?"

copilot -p "Suggest a git command that shows commits from the past week with author and changed files."

copilot -p "In a Vite React app, how can I build and inspect bundle chunk sizes?"

# Copilot CLI will:
# 1. Print a suggested command or explanation
# 2. Include caveats when the prompt is specific enough
# 3. Leave execution to you — review before running
```

<table style="width:100%; border-collapse:collapse;"><tr><td style="border-left:5px solid #1A73E8; background:#E3F2FD; padding:14px 18px;"><strong style="color:#0D47A1;">⭐ KEY POINT:</strong> <span style="color:#0D47A1;">Copilot CLI is command-line assistance, not a safety bypass. It can suggest commands that are valid but wrong for your project. Read the output, check paths, and avoid running commands that delete files, push to remotes, publish packages, or execute downloaded scripts unless you fully understand them.</span></td></tr></table>

### <span style="color:#0D47A1;">1.4  `copilot -p` — Understand Any Shell Command</span>

Paste any command you encounter in docs, Stack Overflow, or CI logs — Copilot CLI explains it in plain English:

```bash
# Common React/frontend commands that look cryptic
copilot -p "Explain this command and its risks: find . -name '*.test.tsx' | xargs grep -l 'act('"

copilot -p "Explain this command: ts-node --project tsconfig.scripts.json scripts/codegen.ts"

copilot -p "Explain this command: cross-env NODE_ENV=test jest --coverage --watchAll=false 2>&1 | tee coverage.log"

copilot -p "Explain this command: npx depcheck --ignores='@types/*,eslint-*'"

copilot -p "Explain this command and why it may be risky: lsof -ti:3000 | xargs kill -9"
```

### <span style="color:#0D47A1;">1.5  When to Use Copilot CLI vs. Copilot Chat</span>

<table style="width:100%; border-collapse:collapse;">
<tr><td style="background:#00695C; color:white; padding:10px 12px; border:1px solid #80CBC4; font-weight:bold;">Task</td><td style="background:#00695C; color:white; padding:10px 12px; border:1px solid #80CBC4; font-weight:bold;">Use</td><td style="background:#00695C; color:white; padding:10px 12px; border:1px solid #80CBC4; font-weight:bold;">Why</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><strong>Need a shell command</strong></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Copilot CLI with <code>copilot -p</code></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Stays in terminal, fast one-shot interaction</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><strong>Understand a cryptic command</strong></td><td style="padding:10px 12px; border:1px solid #CCC;">Copilot CLI with <code>copilot -p</code></td><td style="padding:10px 12px; border:1px solid #CCC;">Stays in terminal, targeted explanation</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><strong>Write or fix an npm script</strong></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Copilot Chat + <code>#file:package.json</code></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Needs context from your actual package.json</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><strong>Debug a CI failure</strong></td><td style="padding:10px 12px; border:1px solid #CCC;">Copilot Chat + <code>#terminalLastCommand</code></td><td style="background:white; padding:10px 12px; border:1px solid #CCC;">Needs the full output, multi-turn debugging</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><strong>Generate a GitHub Actions workflow</strong></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Copilot Chat (Agent mode)</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Writes the YAML file and creates the directory</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><strong>Bulk file operations across project</strong></td><td style="padding:10px 12px; border:1px solid #CCC;">Copilot Agent mode</td><td style="padding:10px 12px; border:1px solid #CCC;">Multi-file writing with self-correction</td></tr>
</table>

---

<table style="width:100%; border-collapse:collapse;"><tr><td style="background:#00695C; color:white; padding:8px 16px; font-weight:bold;">0:10 – 0:18</td><td style="background:#E0F2F1; padding:8px 16px; color:#00695C; font-weight:bold; font-size:16px;">SECTION 2: Copilot-Assisted Script Writing — Shell, npm & YAML</td></tr></table>

## <span style="color:#0D47A1;">2. Copilot-Assisted Script Writing: Shell, npm & YAML</span>

### <span style="color:#0D47A1;">2.1  Writing Shell Scripts with Copilot Chat</span>

Copilot Chat is excellent at writing shell scripts when you provide the right context. The key: always include `#file:package.json` and any relevant config files so Copilot knows your project's real structure.

```bash
# Prompt pattern for shell script generation:
"Write a bash script that [goal].
Context: #file:package.json
Requirements:
- [specific behavior]
- [error handling expected]
- [output format expected]"
```

**Example: batch test cleanup script**

```text
"Write a bash script that finds all .test.tsx files in src/,
runs each one individually with jest --testPathPatterns, and
writes a summary of passing and failing tests to test-report.txt.
Context: #file:package.json
Requirements:
- Exit code 0 if all pass, 1 if any fail
- Show progress: 'Testing X/N...'
- Include test duration for each file"
```

**Copilot generates:**

```bash
#!/bin/bash
set -e

TEST_FILES=($(find src/ -name "*.test.tsx"))
TOTAL=${#TEST_FILES[@]}
PASS=0
FAIL=0
REPORT="test-report.txt"

echo "Running $TOTAL test files..." | tee "$REPORT"

for i in "${!TEST_FILES[@]}"; do
  FILE="${TEST_FILES[$i]}"
  echo -n "Testing $((i+1))/$TOTAL: $FILE ... " | tee -a "$REPORT"
  START=$(date +%s%N)

  if npx jest --testPathPatterns="$FILE" --silent 2>/dev/null; then
    ELAPSED=$(( ($(date +%s%N) - START) / 1000000 ))
    echo "PASS (${ELAPSED}ms)" | tee -a "$REPORT"
    ((PASS++))
  else
    ELAPSED=$(( ($(date +%s%N) - START) / 1000000 ))
    echo "FAIL (${ELAPSED}ms)" | tee -a "$REPORT"
    ((FAIL++))
  fi
done

echo "---" | tee -a "$REPORT"
echo "Results: $PASS passed, $FAIL failed" | tee -a "$REPORT"
[[ $FAIL -eq 0 ]] && exit 0 || exit 1
```

<table style="width:100%; border-collapse:collapse;"><tr><td style="border-left:5px solid #1A73E8; background:#E3F2FD; padding:14px 18px;"><strong style="color:#0D47A1;">⭐ KEY POINT:</strong> <span style="color:#0D47A1;">Always review Copilot-generated shell scripts before running them — especially those that write files, delete outputs, or call network resources. Scripts with <code>rm</code>, <code>curl</code>, or <code>git push</code> deserve a careful read. Copilot writes good shell scripts but may miss edge cases in your specific environment.</span></td></tr></table>

### <span style="color:#0D47A1;">2.2  Improving npm Scripts with Copilot</span>

Your `package.json` scripts section is an automation layer for your React project. Copilot Chat can generate, explain, and improve npm scripts — especially complex ones involving environment variables, conditions, and chaining:

```text
// Ask Copilot to improve this section:
// "#file:package.json — improve the scripts section to add:
// 1. A 'test:ci' script that runs jest in non-interactive mode with coverage
// 2. A 'build:analyze' script that builds and shows bundle composition
// 3. A 'lint:fix' script that runs eslint --fix and prettier --write
// 4. A 'precommit' script that runs type-check, lint, and unit tests"
```

**Copilot-generated scripts:**

```json
{
  "scripts": {
    "dev": "vite",
    "build": "tsc && vite build",
    "preview": "vite preview",
    "test": "jest",
    "test:ci": "jest --ci --coverage --coverageReporters=lcov --forceExit",
    "test:watch": "jest --watch",
    "build:analyze": "ANALYZE=true tsc && vite build",
    "lint": "eslint src --max-warnings 0",
    "lint:fix": "eslint src --fix && prettier --write 'src/**/*.{ts,tsx}'",
    "type-check": "tsc --noEmit",
    "precommit": "npm run type-check && npm run lint && npm run test:ci"
  }
}
```

### <span style="color:#0D47A1;">2.3  Debugging Failing npm Scripts with Copilot</span>

When an npm script fails in CI or locally, the `#terminalLastCommand` context variable makes Copilot Chat the fastest debugging tool:

```text
# After running: npm run build:analyze and seeing errors
"The build script failed with the output in #terminalLastCommand.
Context: #file:vite.config.ts #file:package.json
What is causing this error and how do I fix it?"
```

```text
# CI failure pattern — copy the relevant GitHub Actions log section
"The CI pipeline failed during the test:ci step. Here is the output:
[paste error output or reference #terminalLastCommand]

Context: #file:jest.config.ts #file:package.json
Diagnose and fix the test configuration issue."
```

### <span style="color:#0D47A1;">2.4  Generating GitHub Actions YAML with Copilot</span>

GitHub Actions workflows are notoriously verbose to write from scratch. Copilot Chat can generate complete, working YAML files. Use Agent mode so Copilot creates the file and directory in one step:

```text
"@agent Create a GitHub Actions workflow for this React project.
File: .github/workflows/ci.yml

The workflow should:
- Trigger on push to main and all pull_request events
- Use Node.js 20 on ubuntu-latest
- Cache node_modules using actions/cache with the package-lock.json hash as key
- Run steps: install, type-check (tsc --noEmit), lint (eslint), test with coverage (jest --ci --coverage)
- Fail the build if coverage drops below 80%
- Upload coverage reports as an artifact

Reference: #file:package.json for the exact npm script names."
```

**Copilot generates:**

```yaml
name: CI

on:
  push:
    branches: [main]
  pull_request:

jobs:
  ci:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: Set up Node.js
        uses: actions/setup-node@v4
        with:
          node-version: '20'

      - name: Cache dependencies
        uses: actions/cache@v4
        with:
          path: node_modules
          key: ${{ runner.os }}-node-${{ hashFiles('package-lock.json') }}
          restore-keys: ${{ runner.os }}-node-

      - name: Install dependencies
        run: npm ci

      - name: Type check
        run: npm run type-check

      - name: Lint
        run: npm run lint

      - name: Test with coverage
        run: npm run test:ci

      - name: Check coverage threshold
        run: |
          COVERAGE=$(cat coverage/coverage-summary.json | \
            jq '.total.lines.pct')
          echo "Coverage: $COVERAGE%"
          if (( $(echo "$COVERAGE < 80" | bc -l) )); then
            echo "Coverage below 80% threshold"
            exit 1
          fi

      - name: Upload coverage
        if: always()
        uses: actions/upload-artifact@v4
        with:
          name: coverage-report
          path: coverage/
```

<table style="width:100%; border-collapse:collapse;"><tr><td style="border-left:5px solid #1A73E8; background:#E3F2FD; padding:14px 18px;"><strong style="color:#0D47A1;">⭐ KEY POINT:</strong> <span style="color:#0D47A1;">Always provide your real <code>package.json</code> as context when asking Copilot to generate GitHub Actions YAML. Without it, Copilot guesses at your npm script names and Node version. With <code>#file:package.json</code>, it uses your exact scripts, detects your testing framework, and generates a workflow that actually runs on your project.</span></td></tr></table>

---

<table style="width:100%; border-collapse:collapse;"><tr><td style="background:#00695C; color:white; padding:8px 16px; font-weight:bold;">0:18 – 0:28</td><td style="background:#E0F2F1; padding:8px 16px; color:#00695C; font-weight:bold; font-size:16px;">SECTION 3: GitHub Actions for React CI/CD</td></tr></table>

## <span style="color:#0D47A1;">3. GitHub Actions for React CI/CD</span>

### <span style="color:#0D47A1;">3.1  The React CI/CD Pipeline Pattern</span>

A mature React team CI/CD pipeline has multiple automated quality gates. Copilot can generate workflows for each layer:

<table style="width:100%; border-collapse:collapse;">
<tr><td style="background:#1A73E8; color:white; padding:10px 12px; border:1px solid #BBDEFB; font-weight:bold;">Gate</td><td style="background:#1A73E8; color:white; padding:10px 12px; border:1px solid #BBDEFB; font-weight:bold;">What It Checks</td><td style="background:#1A73E8; color:white; padding:10px 12px; border:1px solid #BBDEFB; font-weight:bold;">Copilot Prompt</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><strong>Type safety</strong></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><code>tsc --noEmit</code> — no TypeScript errors in the build</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">"Add a TypeScript check step to #file:.github/workflows/ci.yml"</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><strong>Code style</strong></td><td style="padding:10px 12px; border:1px solid #CCC;">ESLint + Prettier — no lint errors or formatting violations</td><td style="padding:10px 12px; border:1px solid #CCC;">"Generate an ESLint step that fails on warnings (--max-warnings 0)"</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><strong>Test coverage</strong></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Jest with coverage threshold — minimum line/branch/function coverage</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">"Add coverage enforcement at 80% threshold using jest --coverage"</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><strong>Bundle size</strong></td><td style="padding:10px 12px; border:1px solid #CCC;">Vite/webpack build — bundle doesn't exceed size budget</td><td style="padding:10px 12px; border:1px solid #CCC;">"Generate a bundle size check that fails if main chunk exceeds 250KB"</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><strong>Dependency audit</strong></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><code>npm audit --audit-level high</code> — no high/critical CVEs</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">"Add an npm audit step that blocks on high severity vulnerabilities"</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><strong>Accessibility</strong></td><td style="padding:10px 12px; border:1px solid #CCC;">axe-core / Playwright — no accessibility violations in key routes</td><td style="padding:10px 12px; border:1px solid #CCC;">"Generate a Playwright accessibility check for the login and home pages"</td></tr>
</table>

### <span style="color:#0D47A1;">3.2  Automated PR Review Workflow</span>

Use the GitHub CLI (`gh`) in CI to post Copilot-generated review summaries as PR comments. This gives every PR an automated first-pass review:

```yaml
# .github/workflows/pr-review.yml
name: PR Review

on:
  pull_request:
    types: [opened, synchronize]

jobs:
  review:
    runs-on: ubuntu-latest
    permissions:
      pull-requests: write
      contents: read

    steps:
      - uses: actions/checkout@v4
        with:
          fetch-depth: 0

      - name: Get PR diff summary
        id: diff
        run: |
          # Summarize changed files and line counts
          DIFF_STATS=$(git diff origin/${{ github.base_ref }}...HEAD \
            --stat --no-color)
          echo "stats<<EOF" >> $GITHUB_OUTPUT
          echo "$DIFF_STATS" >> $GITHUB_OUTPUT
          echo "EOF" >> $GITHUB_OUTPUT

      - name: Post review reminder checklist
        uses: actions/github-script@v7
        with:
          script: |
            const stats = `${{ steps.diff.outputs.stats }}`;
            const body = `## Automated Review Checklist

            **Changed files:**
            \`\`\`
            ${stats}
            \`\`\`

            Before approving, verify:
            - [ ] TypeScript types are correct (CI type-check passed)
            - [ ] Tests cover new code paths (CI coverage gate passed)
            - [ ] No accessibility regressions in changed components
            - [ ] Bundle size impact is acceptable
            - [ ] No hardcoded values — use constants/env vars

            *CI gates run automatically. This checklist is for human review.*`;

            github.rest.issues.createComment({
              issue_number: context.issue.number,
              owner: context.repo.owner,
              repo: context.repo.repo,
              body
            });
```

### <span style="color:#0D47A1;">3.3  Bundle Size Monitor</span>

Track React bundle size across PRs with a Copilot-generated workflow:

```yaml
# .github/workflows/bundle-size.yml
name: Bundle Size

on:
  pull_request:

jobs:
  bundle:
    runs-on: ubuntu-latest
    permissions:
      pull-requests: write

    steps:
      - uses: actions/checkout@v4

      - uses: actions/setup-node@v4
        with:
          node-version: '20'

      - run: npm ci

      - name: Build and measure
        id: build
        run: |
          npm run build
          # Sum all JS chunks
          TOTAL=$(find dist/assets -name "*.js" \
            -exec wc -c {} + | tail -1 | awk '{print $1}')
          TOTAL_KB=$(( TOTAL / 1024 ))
          echo "total_kb=$TOTAL_KB" >> $GITHUB_OUTPUT
          echo "Bundle size: ${TOTAL_KB}KB"

      - name: Fail if over budget
        run: |
          BUDGET=500
          ACTUAL=${{ steps.build.outputs.total_kb }}
          if [ "$ACTUAL" -gt "$BUDGET" ]; then
            echo "Bundle size ${ACTUAL}KB exceeds budget of ${BUDGET}KB"
            exit 1
          fi
          echo "Bundle size ${ACTUAL}KB is within budget"
```

### <span style="color:#0D47A1;">3.4  GitHub Actions Debugging with Copilot</span>

When a GitHub Actions workflow fails, paste the error log into Copilot Chat:

```text
# Pattern for debugging Actions failures:

"The GitHub Actions step 'Test with coverage' failed.
Here is the relevant log output:
[paste the last 50 lines of the Actions log]

Context: #file:.github/workflows/ci.yml #file:jest.config.ts

Diagnose the failure and provide the exact fix."
```

```text
# Common React CI failure patterns to ask Copilot about:

"I'm getting 'Error: Cannot find module @/components/Button'
in CI but not locally. Context: #file:jest.config.ts
#file:tsconfig.json
Why does this happen in CI only and how do I fix it?"

"Our jest --coverage is passing locally but the
GitHub Actions step exits with code 1.
Context: #file:jest.config.ts #terminalLastCommand
What is different about CI that could cause this?"
```

<table style="width:100%; border-collapse:collapse;"><tr><td style="border-left:5px solid #C62828; background:#FFEBEE; padding:14px 18px; border:1px solid #EF9A9A;"><strong style="color:#C62828;">⚠️ WARNING:</strong> <span style="color:#C62828;">Never paste real secrets, API keys, or environment variable values into Copilot Chat — even in a private conversation. Use placeholder names like <code>${{ secrets.API_KEY }}</code> in your prompts. Copilot Chat logs are subject to GitHub's data practices; keep credentials out of conversations entirely.</span></td></tr></table>

---

<table style="width:100%; border-collapse:collapse;"><tr><td style="background:#00695C; color:white; padding:8px 16px; font-weight:bold;">0:28 – 0:36</td><td style="background:#E0F2F1; padding:8px 16px; color:#00695C; font-weight:bold; font-size:16px;">SECTION 4: Agent Mode for Bulk React Workflows</td></tr></table>

## <span style="color:#0D47A1;">4. Agent Mode for Bulk React Workflows</span>

### <span style="color:#0D47A1;">4.1  Agent Mode as a Bulk Processing Engine</span>

In Module 4, you used Agent mode for single-feature development. For automation work, Agent mode serves a different role: **bulk operations across many files**. Instead of writing a shell script that processes files, you describe the transformation and let Agent do the multi-file work autonomously.

<table style="width:100%; border-collapse:collapse;">
<tr><td style="background:#1A73E8; color:white; padding:10px 12px; border:1px solid #BBDEFB; font-weight:bold;">Task Type</td><td style="background:#1A73E8; color:white; padding:10px 12px; border:1px solid #BBDEFB; font-weight:bold;">Script Approach</td><td style="background:#1A73E8; color:white; padding:10px 12px; border:1px solid #BBDEFB; font-weight:bold;">Agent Mode Approach</td><td style="background:#1A73E8; color:white; padding:10px 12px; border:1px solid #BBDEFB; font-weight:bold;">Better Option</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><strong>Rename a prop across 20 components</strong></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">sed/grep replace script</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Agent finds usages, updates correctly including types</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Agent (handles TypeScript types too)</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><strong>Add JSDoc to 30 exported functions</strong></td><td style="padding:10px 12px; border:1px solid #CCC;">Complex AST transform</td><td style="padding:10px 12px; border:1px solid #CCC;">Agent reads each function, generates meaningful docs</td><td style="padding:10px 12px; border:1px solid #CCC;">Agent (content-aware, not mechanical)</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><strong>Generate tests for 15 components</strong></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Template-based test scaffold</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Agent reads each component, generates meaningful tests</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Agent (understands component logic)</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><strong>Bump a version number in all package files</strong></td><td style="padding:10px 12px; border:1px solid #CCC;">sed replace script (1 line)</td><td style="padding:10px 12px; border:1px solid #CCC;">Overkill for trivial mechanical changes</td><td style="padding:10px 12px; border:1px solid #CCC;">Script (mechanical, no intelligence needed)</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><strong>Delete files matching a pattern</strong></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><code>find . -name "*.bak" -delete</code></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Unnecessary — trivial shell command</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Script (or Copilot CLI suggest)</td></tr>
</table>

### <span style="color:#0D47A1;">4.2  Bulk Prompt Patterns for Agent Mode</span>

**Pattern: Migrate a hook across all component usages**

```text
"@agent Migrate all components in src/components/ from using the
deprecated useUserStore hook to the new useAuthStore hook from
#file:src/stores/authStore.ts.

Step 1: List every component that currently imports useUserStore.
Wait for my approval before making changes."

# [After approving the list:]

"Proceed. For each file:
1. Replace the useUserStore import with useAuthStore
2. Update the destructured values to match the new store shape in #file:src/stores/authStore.ts
3. Fix any TypeScript errors caused by the changed property names
4. Run tsc --noEmit after each file to confirm no errors"
```

**Pattern: Add accessibility attributes to all form components**

```text
"@agent Review all components in src/components/forms/ for
missing ARIA attributes. Focus on:
- <input> elements without aria-label or aria-labelledby
- <button> elements without accessible name
- <select> elements missing aria-describedby for error messages

Step 1: List every file in src/components/forms/ and describe
which ARIA attributes are missing. Wait for my approval."

# [After reviewing the list and approving:]
"Fix only the Critical issues you listed. Don't touch
components listed as Passing."
```

**Pattern: Generate tests for all untested components**

```text
"@agent Find every .tsx component file in src/components/ that
does not have a corresponding .test.tsx file.

Step 1: List all component files missing test files.
Do not write any code yet."

# [After reviewing and approving:]
"Generate RTL tests for the first 5 files on the list.
Follow the test structure in #file:src/components/TextInput/TextInput.test.tsx.
After writing each test file, run: npx jest [filename] --no-coverage
and fix any failures before moving to the next file."
```

<table style="width:100%; border-collapse:collapse;"><tr><td style="border-left:5px solid #1A73E8; background:#E3F2FD; padding:14px 18px;"><strong style="color:#0D47A1;">⭐ KEY POINT:</strong> <span style="color:#0D47A1;">For bulk Agent mode sessions, always split into two steps: (1) <em>plan</em> — "list every X affected" and wait for approval, (2) <em>execute</em> — "proceed with the list." This two-step pattern prevents Agent from modifying 20 files based on a misunderstanding of your intent. The plan step is free; the Reject All recovery is not.</span></td></tr></table>

### <span style="color:#0D47A1;">4.3  Safety Patterns for Bulk Agent Sessions</span>

<table style="width:100%; border-collapse:collapse;"><tr><td style="border-left:5px solid #2E7D32; background:#E8F5E9; padding:14px 18px; border:1px solid #A5D6A7;"><strong style="color:#2E7D32;">✅ BULK AGENT MODE SAFETY CHECKLIST</strong><ul style="color:#333; margin:8px 0; padding-left:20px;"><li><strong>Before starting:</strong> <code>git add -A && git commit -m "WIP: before bulk Agent session"</code></li><li><strong>Before starting:</strong> Create a dedicated branch: <code>git checkout -b refactor/bulk-session-name</code></li><li><strong>First Agent message:</strong> Always ask Agent to list affected files before making changes</li><li><strong>Batch size:</strong> Do no more than 10 files per Agent session — split large changes into batches</li><li><strong>Between batches:</strong> Run <code>npm test</code> and <code>tsc --noEmit</code> to catch errors before they accumulate</li><li><strong>After each batch:</strong> Review the Copilot Edits diffs file-by-file before Accept All</li><li><strong>After completing all batches:</strong> <code>git diff HEAD</code> to review the totality of changes — then <code>npm test</code> for a full suite run</li></ul></td></tr></table>

### <span style="color:#0D47A1;">4.4  Limiting Agent Mode Scope</span>

Just as you can constrain `--allowedTools` in Claude Code's headless mode, you can constrain Agent mode scope through prompt boundaries:

```text
# Explicit file scope constraint
"@agent Work ONLY on files within src/components/forms/.
Do not modify any file outside this directory."

# Explicit operation constraint
"@agent Add JSDoc comments ONLY. Do not change any logic,
refactor any code, or modify any TypeScript types."

# Explicit preservation constraint
"@agent You may add new tests to the test files but must not
modify the component implementation files. If you find a bug
in a component while writing its tests, document it as a
TODO comment in the test file instead of fixing it."
```

<table style="width:100%; border-collapse:collapse;"><tr><td style="border-left:5px solid #C62828; background:#FFEBEE; padding:14px 18px; border:1px solid #EF9A9A;"><strong style="color:#C62828;">⚠️ WARNING:</strong> <span style="color:#C62828;">Agent mode will sometimes modify files outside the stated scope if it determines that doing so is necessary to make the primary task work. This is why the pre-session git commit is non-negotiable — you can always <code>git diff HEAD</code> to see every changed file and <code>git restore path/to/unexpected-file</code> to restore anything Agent touched that you didn't want modified.</span></td></tr></table>

---

<table style="width:100%; border-collapse:collapse;"><tr><td style="background:#00695C; color:white; padding:8px 16px; font-weight:bold;">0:36 – 0:43</td><td style="background:#E0F2F1; padding:8px 16px; color:#00695C; font-weight:bold; font-size:16px;">SECTION 5: Real-World Automation Recipes for React Teams</td></tr></table>

## <span style="color:#0D47A1;">5. Real-World Automation Recipes for React Teams</span>

Complete, copy-paste-ready automation recipes for daily React development. Each recipe combines Copilot Chat prompts, npm scripts, and GitHub Actions patterns.

### <span style="color:#0D47A1;">5.1  Recipe: Automated PR Description Generation</span>

Use the `gh` CLI to generate a Copilot-informed PR description from the diff:

```bash
#!/bin/bash
# generate-pr-description.sh
# Usage: ./generate-pr-description.sh <PR-number>

PR=$1
BRANCH=$(git branch --show-current)

# Get the diff summary
DIFF_STAT=$(git diff origin/main...HEAD --stat --no-color)
CHANGED_FILES=$(git diff origin/main...HEAD --name-only)

# In Copilot Chat, use this prompt (with your diff content):
cat <<EOF
Generate a GitHub PR description for this branch.

Changed files:
$DIFF_STAT

Requirements for the description:
- Title: "[Component/Feature] Short description of what changed"
- ## Summary section: 2-3 sentences on what and why
- ## Changes section: bullet list of key changes
- ## Testing section: what was tested and how
- ## Screenshots section: placeholder if any UI changed

Follow the PR template in #file:.github/pull_request_template.md if it exists.
EOF
```

### <span style="color:#0D47A1;">5.2  Recipe: Pre-Commit Quality Gate Script</span>

A comprehensive local pre-commit check (complement to lint-staged, for developers who want feedback before committing):

```bash
#!/bin/bash
# scripts/pre-commit-check.sh
# Run manually before important commits:
# chmod +x scripts/pre-commit-check.sh && ./scripts/pre-commit-check.sh

set -e

echo "=== Pre-Commit Quality Check ==="

echo "[1/4] TypeScript type check..."
if ! npm run type-check; then
  echo "FAIL: TypeScript errors found. Fix before committing."
  exit 1
fi
echo "PASS: No TypeScript errors"

echo "[2/4] ESLint..."
if ! npm run lint; then
  echo "FAIL: ESLint violations found."
  echo "Run 'npm run lint:fix' to auto-fix many issues."
  exit 1
fi
echo "PASS: No ESLint errors"

echo "[3/4] Unit tests..."
if ! npm run test:ci -- --passWithNoTests; then
  echo "FAIL: Tests failing."
  exit 1
fi
echo "PASS: All tests pass"

echo "[4/4] Build check..."
if ! npm run build 2>/dev/null; then
  echo "FAIL: Build failed."
  exit 1
fi
echo "PASS: Build succeeds"

echo ""
echo "All checks passed. Ready to commit."
```

### <span style="color:#0D47A1;">5.3  Recipe: Coverage Report Generator</span>

After running tests with coverage, use Copilot Chat to interpret the coverage data and generate a readable summary:

```bash
#!/bin/bash
# scripts/coverage-summary.sh

# Run tests with JSON coverage
npm run test:ci -- --coverageReporters=json-summary 2>/dev/null

# Display summary
echo "=== Coverage Summary ==="
if [ -f coverage/coverage-summary.json ]; then
  cat coverage/coverage-summary.json | jq '{
    lines: .total.lines,
    branches: .total.branches,
    functions: .total.functions,
    statements: .total.statements
  }'

  # Check thresholds
  LINES=$(cat coverage/coverage-summary.json | jq '.total.lines.pct')
  echo ""
  if (( $(echo "$LINES < 80" | bc -l) )); then
    echo "Coverage is below 80% threshold ($LINES%). Consider adding tests."
    exit 1
  else
    echo "Coverage: $LINES% (above 80% threshold)"
  fi
fi
```

**Copilot Chat prompt to interpret coverage results:**

```text
"Coverage fell from 84% to 76% after this PR. Here are the
uncovered lines from the coverage report:
[paste coverage/coverage-summary.json relevant section]

Context: #file:src/hooks/useCheckout.ts

Which code paths are most important to test? Suggest the
3 most valuable tests to add to bring coverage back above 80%."
```

### <span style="color:#0D47A1;">5.4  Recipe: Batch Component Documentation</span>

Use Agent mode to add JSDoc to all exported components and hooks missing documentation:

```bash
# In Copilot Chat (Agent mode):
```

```text
"@agent Find all exported functions and components in src/ that
are missing JSDoc comments. Generate JSDoc for each one.

Rules:
- Components: document props interface, component purpose, and basic usage example
- Hooks: document parameters, return value shape, and a usage example
- Do NOT add JSDoc to internal helper functions (not exported)
- Do NOT modify any logic — documentation additions only

Step 1: List the top 10 files with the most undocumented exports.
Wait for approval before writing any docs."
```

### <span style="color:#0D47A1;">5.5  Recipe: Dependency Audit with Copilot Analysis</span>

```bash
#!/bin/bash
# scripts/audit-deps.sh

echo "=== Dependency Security Audit ==="

# Run npm audit and capture output
AUDIT=$(npm audit --json 2>/dev/null)

HIGH=$(echo "$AUDIT" | jq '.metadata.vulnerabilities.high // 0')
CRITICAL=$(echo "$AUDIT" | jq '.metadata.vulnerabilities.critical // 0')

echo "Critical: $CRITICAL"
echo "High: $HIGH"

if [ "$CRITICAL" -gt 0 ] || [ "$HIGH" -gt 0 ]; then
  echo ""
  echo "Vulnerabilities found. Use this Copilot prompt to plan fixes:"
  echo ""
  echo '---'
  npm audit 2>/dev/null | head -60
  echo '---'
  echo ""
  echo "Paste the above into Copilot Chat with:"
  echo '"Review the npm audit output above and suggest the safest"'
  echo '"upgrade path for each high/critical vulnerability."'
  echo '"Context: #file:package.json"'
  exit 1
fi

echo "No high or critical vulnerabilities found."
```

<table style="width:100%; border-collapse:collapse;"><tr><td style="border-left:5px solid #1A73E8; background:#E3F2FD; padding:14px 18px;"><strong style="color:#0D47A1;">⭐ KEY POINT:</strong> <span style="color:#0D47A1;">These recipes are templates, not finished products. The real value comes from adapting them to your team's exact workflow — your coverage threshold, your PR template, your component naming conventions. Change the thresholds, the file patterns, and the Copilot prompt content. The pattern stays the same: automate the data gathering, use Copilot for the intelligence layer.</span></td></tr></table>

---

<table style="width:100%; border-collapse:collapse;"><tr><td style="background:#00695C; color:white; padding:8px 16px; font-weight:bold;">0:43 – 0:45</td><td style="background:#E0F2F1; padding:8px 16px; color:#00695C; font-weight:bold; font-size:16px;">WRAP-UP: Quick Reference & Transition to Lab 1</td></tr></table>

## <span style="color:#0D47A1;">6. Quick Reference & Transition</span>

## <span style="color:#1A73E8;">MODULE 5 RECAP</span>

- ✅ **Copilot CLI:** use the standalone `copilot` command for terminal assistance. Install with `npm install -g @github/copilot`, authenticate with `copilot login`, and use `copilot -p "..."` for one-shot prompts.
- ✅ **Script writing:** Use Copilot Chat with `#file:package.json` context to generate and improve npm scripts and shell scripts. Use `#terminalLastCommand` to debug script failures.
- ✅ **GitHub Actions:** Copilot can generate complete CI/CD YAML files. Provide `#file:package.json` context so it uses your real script names and Node version.
- ✅ **Bulk Agent mode:** Use Agent for content-aware bulk operations (prop renames, JSDoc, test generation). Use scripts for mechanical transformations (version bumps, file deletes). Always plan before executing.
- ✅ **Safety:** Commit before bulk sessions. Limit scope with explicit prompt boundaries. Never paste secrets into Copilot Chat.

---

## <span style="color:#1A73E8;">QUICK REFERENCE CARD</span>

<table style="width:100%; border-collapse:collapse;">
<tr><td style="background:#2E7D32; color:white; padding:10px 12px; border:1px solid #A5D6A7; font-weight:bold;">Feature</td><td style="background:#2E7D32; color:white; padding:10px 12px; border:1px solid #A5D6A7; font-weight:bold;">Command / Prompt</td><td style="background:#2E7D32; color:white; padding:10px 12px; border:1px solid #A5D6A7; font-weight:bold;">Notes</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><strong>Install Copilot CLI</strong></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><code>npm install -g @github/copilot</code></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Requires Node.js 22+ and Copilot access</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><strong>Authenticate</strong></td><td style="padding:10px 12px; border:1px solid #CCC;"><code>copilot login</code></td><td style="padding:10px 12px; border:1px solid #CCC;">Opens GitHub authentication flow</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><strong>Ask for command help</strong></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><code>copilot -p "Suggest a safe command to ..."</code></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Review output before running anything</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><strong>Generate npm script</strong></td><td style="padding:10px 12px; border:1px solid #CCC;">Chat: "Add a [goal] script to #file:package.json"</td><td style="padding:10px 12px; border:1px solid #CCC;">Always include #file:package.json context</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><strong>Generate CI workflow</strong></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Agent: "@agent Create .github/workflows/ci.yml … #file:package.json"</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Agent creates the file and directory</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><strong>Debug script failure</strong></td><td style="padding:10px 12px; border:1px solid #CCC;">Chat: "Fix the error in #terminalLastCommand. #file:jest.config.ts"</td><td style="padding:10px 12px; border:1px solid #CCC;">#terminalLastCommand provides the exact error output</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><strong>Bulk rename prop</strong></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Agent: "@agent List all usages of [propName] then rename it"</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Plan step first; commit before session</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><strong>Bulk add JSDoc</strong></td><td style="padding:10px 12px; border:1px solid #CCC;">Agent: "@agent List exported functions missing JSDoc, then add docs only"</td><td style="padding:10px 12px; border:1px solid #CCC;">Explicit "docs only" constraint prevents logic changes</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><strong>Generate tests at scale</strong></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Agent: "@agent List components missing .test.tsx, then generate in batches of 5"</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">10-file batches max; run npm test between batches</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><strong>Safety: pre-session commit</strong></td><td style="padding:10px 12px; border:1px solid #CCC;"><code>git add -A && git commit -m "WIP: before bulk session"</code></td><td style="padding:10px 12px; border:1px solid #CCC;">Your recovery point for bulk Agent work</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><strong>Safety: scope constraint</strong></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">"Work ONLY on files within src/components/forms/"</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Explicit scope in prompt limits Agent's range</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><strong>Safety: secret handling</strong></td><td style="padding:10px 12px; border:1px solid #CCC;">Never paste real secrets — use <code>${{ secrets.NAME }}</code> placeholders</td><td style="padding:10px 12px; border:1px solid #CCC;">In prompts, YAML, and code shared with Copilot</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><strong>Verify bulk changes</strong></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><code>git diff HEAD</code> → <code>npm test</code> → <code>tsc --noEmit</code></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Validate the full scope of changes before committing</td></tr>
</table>

---

## <span style="color:#1A73E8;">TRANSITION TO MODULE 6: LAB 1</span>

You now know how to drive GitHub Copilot across every surface — from inline completions to Chat, Agent mode, Copilot CLI, and CI/CD automation. In Module 6 (Lab 1), you'll put these skills to work hands-on: scaffold a React feature from scratch using Agent mode, write tests with `/tests`, generate a CI workflow, and run a bulk documentation pass on an existing component library.

**Lab 1 will use everything from Modules 1–5:**
- Module 1's safety practices (commit before Agent sessions, review before Accept All)
- Module 2's prompting patterns (persona, output format, context)
- Module 3's advanced techniques (custom prompt files, context-reset strategy)
- Module 4's surface selection (right tool for each subtask)
- Module 5's automation patterns (npm scripts, CI workflow, bulk Agent mode)

---

<div style="text-align:center; padding:20px; color:#666; font-size:12px;">
Vibe Coding with GitHub Copilot | React Developer Track<br>
Module 5 — Automation & Scripting for React Teams
</div>
