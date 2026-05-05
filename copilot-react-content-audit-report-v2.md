# Copilot React Course Content Audit Report - Pass 2

Audit date: 2026-05-05  
Scope: current contents of `copilot-react/` after revisions  
Course files reviewed: 30 Markdown files, excluding prior audit artifact  
Prior audit artifact present: `copilot-react-content-audit-report.md`  
Total course lines reviewed: 12,000  
Fenced code blocks reviewed: 240

## Executive Summary

The course is materially improved from the earlier audit. The largest earlier gap, where Lab 1 built `Button`, `Input`, and `FormField` while later modules expected `TextInput`, `Select`, and `Checkbox`, has been partly corrected. Lab 1 now scaffolds `TextInput`, `Select`, and `Checkbox`, includes Storybook story stubs, and explicitly introduces `jest-axe`.

The course is still not fully ready as an end-to-end runnable GitHub Copilot curriculum. The remaining blockers are more specific:

1. Modules 11, 12, and 15 instructor notes still assume `RadioGroup` and `Textarea`, but Lab 1 does not scaffold them.
2. Module 12 now partly uses folder-based `PhoneInput` paths, but its test and story steps still use flat paths.
3. Modules 5 and 9 still teach the retired GitHub CLI Copilot extension (`gh extension install github/gh-copilot`, `gh copilot suggest`, `gh copilot explain`). Official GitHub docs now direct users to the standalone Copilot CLI.
4. Module 9 still presents Copilot CLI as an unattended CI analysis tool using `GITHUB_TOKEN`; this is not a reliable, documented GitHub Copilot workflow as written.
5. Two `json` code fences still contain non-JSON content and fail parsing.
6. Most learner modules still violate Markdown heading standards by using many H1 headings and jumping from H1 to H3.
7. Several command sequences are plausible examples but not guaranteed to run in the generated repo without additional package/config setup, especially Jest with Vite, Storybook, ESLint, and MCP sections.

Recommended status: improved, but revise again before delivery.

## Audit Method

I checked:

- Current file inventory and line counts.
- All learner modules and instructor notes, module by module.
- Markdown fence integrity.
- Heading hierarchy.
- JSON and bash fenced block validity.
- GitHub Copilot current tooling claims against official GitHub documentation.
- Lab-to-lab dependencies and generated repository state.
- Instructor-note assumptions against learner module outputs.
- Command sequences for plausibility and copy/paste safety.
- React/TypeScript/Jest/Storybook path consistency.

Automated validation results:

- Course files: 30 Markdown files.
- Total course lines: 12,000.
- Fenced code blocks: 240.
- Unclosed fenced code blocks: 0.
- Bash fenced blocks: 63, shell syntax parse passed.
- JSON fenced blocks: 5.
- JSON parse failures: 2.
- JSONC fenced blocks: 7.
- YAML fenced blocks: 10.
- YAML was manually reviewed. A local YAML parser was not available because Ruby/Psych is broken in this environment and PyYAML is not installed.

Code fence language distribution:

| Language tag | Count |
| --- | ---: |
| none | 124 |
| bash | 63 |
| markdown | 21 |
| yaml | 10 |
| jsonc | 7 |
| typescript | 6 |
| json | 5 |
| tsx | 3 |
| text | 1 |

## Official GitHub Copilot Spot Check

I checked current official GitHub documentation because Copilot CLI and prompt-file support change over time.

Official sources used:

- GitHub Copilot CLI install docs: https://docs.github.com/copilot/how-tos/set-up/install-copilot-cli
- GitHub Copilot CLI command reference: https://docs.github.com/en/copilot/reference/copilot-cli-reference/cli-command-reference
- GitHub Copilot in the command line docs: https://docs.github.com/en/copilot/using-github-copilot/using-github-copilot-in-the-command-line
- Repository custom instructions: https://docs.github.com/en/copilot/how-tos/configure-custom-instructions/add-repository-instructions
- Custom instructions support reference: https://docs.github.com/en/copilot/reference/custom-instructions-support

Current official-doc implications:

- The old GitHub CLI extension `github/gh-copilot` is marked as retired in GitHub docs.
- Current install path is the standalone Copilot CLI package, not `gh extension install github/gh-copilot`.
- Current npm package shown in docs is `@github/copilot`.
- Current CLI flow uses commands such as `copilot login` and `copilot`/`copilot -p`, not `gh copilot suggest`.
- `.github/copilot-instructions.md`, path-specific instruction files, prompt files, and `AGENTS.md` are supported surfaces, but IDE/version support details matter.

This makes Modules 5 and 9 the highest-risk content from a GitHub Copilot accuracy standpoint.

## Critical Findings

### C1. Copilot CLI Content Uses Retired `gh-copilot` Extension

Severity: Critical  
Affected files:

- `module5-automation-scripting.md`
- `module5-instructor-notes.md`
- `module9-aiops-cicd.md`
- `module9-instructor-notes.md`

Evidence:

- `module5-automation-scripting.md:60-62` defines Copilot CLI as a GitHub CLI extension with `gh copilot suggest` and `gh copilot explain`.
- `module5-automation-scripting.md:80-84` installs and verifies `github/gh-copilot`.
- `module5-automation-scripting.md:98-132` teaches `gh copilot suggest` and `gh copilot explain`.
- `module5-automation-scripting.md:815-829` repeats the extension flow in the recap/quick reference.
- `module9-aiops-cicd.md:72-83` installs `github/gh-copilot` inside GitHub Actions and runs `gh copilot suggest`.
- `module9-instructor-notes.md:10` sets the same extension as a pre-session requirement.

Why this is a blocker:

- GitHub's official docs now identify the old `gh-copilot` extension as retired.
- Students following the course may install a retired path, hit unsupported behavior, or learn the wrong command surface.

Required fix:

- Rewrite Modules 5 and 9 around the current standalone Copilot CLI:
  - `npm install -g @github/copilot`
  - `copilot login`
  - `copilot`
  - `copilot -p "prompt here"` for non-interactive prompt mode if appropriate
- If you want to mention the retired `gh copilot` syntax, label it explicitly as historical/retired and remove it from runnable labs.

### C2. Module 9 Still Teaches Unreliable Copilot-in-CI Automation

Severity: Critical  
Affected files:

- `module9-aiops-cicd.md`
- `module9-instructor-notes.md`

Evidence:

- `module9-aiops-cicd.md:57-84` runs `gh copilot suggest` in GitHub Actions to review a PR diff.
- `module9-aiops-cicd.md:103-121` runs Copilot after test failure and posts a PR comment.
- `module9-aiops-cicd.md:127-134` asks Copilot to generate fix commands, then tells the learner to run `bash fix-commands.sh`.
- `module9-instructor-notes.md:20-38` frames Copilot CLI in CI as deterministic unattended pipeline automation.
- `module9-instructor-notes.md:34-38` states this works anywhere `gh` CLI is installed.

Why this is a blocker:

- Official docs do not support the exact retired-extension CI flow shown.
- The workflow assumes `GITHUB_TOKEN` grants the right Copilot auth for unattended AI execution. That claim needs official support or must be removed.
- Large prompt payloads are passed through shell command substitution:
  - `$(cat pr-diff.txt)`
  - `$(tail -150 test-output.txt)`
  - `$(cat lint-errors.json)`
- This is fragile because of quoting, size limits, untrusted content, and accidental secret leakage.
- `bash fix-commands.sh` from AI-generated shell output is too risky for a default student workflow, even with a "review first" note.

Required fix:

- Reframe Module 9 around standard GitHub Actions gates:
  - typecheck
  - lint
  - unit tests
  - coverage
  - build
  - Storybook build
  - audit/dependabot
- Move AI failure analysis to a manual or semi-manual workflow:
  - save logs as artifacts
  - open the failure in VS Code/Copilot Chat
  - paste sanitized output or use current supported CLI intentionally
- If you keep AI in CI, use only documented current CLI behavior and clearly list the required plan/license/auth model.

### C3. Lab 1 Still Does Not Produce All Components Required Later

Severity: Critical  
Affected files:

- `module6-lab1-scaffold-tests.md`
- `module11-instructor-notes.md`
- `module12-instructor-notes.md`
- `module15-instructor-notes.md`
- `module14-instructor-notes.md`

What Lab 1 now creates:

- `TextInput`
- `Select`
- `Checkbox`
- `useFormValidation`
- `validators`
- Storybook stubs
- `jest-axe` setup prompt

Evidence:

- `module6-lab1-scaffold-tests.md:167-188`
- `module6-lab1-scaffold-tests.md:193-226`
- `module6-lab1-scaffold-tests.md:549-561`

Later assumptions still include:

- `RadioGroup`
- `Textarea`

Evidence:

- `module11-instructor-notes.md:23` requires `TextInput, Select, Checkbox, RadioGroup, Textarea`.
- `module12-instructor-notes.md:23` repeats that requirement.
- `module15-instructor-notes.md:23` requires `TextInput, Select, Checkbox, RadioGroup, Textarea, PhoneInput`.
- `module14-instructor-notes.md:44` references `src/components/RadioGroup.tsx`.

Why this is a blocker:

- Students completing Lab 1 as written will not have `RadioGroup` or `Textarea`.
- Instructor demos and pre-lab checklists will fail or require hidden setup.

Required fix:

- Either add `RadioGroup` and `Textarea` to Lab 1 scaffolding and implementation, or remove them from later checklists and demos.
- If they are instructor-only demo artifacts, label them as instructor-prepared extra components and provide creation steps.

### C4. Module 12 Has Mixed Folder and Flat Paths for PhoneInput

Severity: Critical  
Affected file:

- `module12-lab2-component-pipeline.md`

Evidence:

- Prompt template uses folder convention:
  - `module12-lab2-component-pipeline.md:150-154`
  - `src/components/${componentName}/${componentName}.tsx`
- Component implementation step uses folder convention:
  - `module12-lab2-component-pipeline.md:245-249`
  - `src/components/PhoneInput/PhoneInput.tsx`
- Test step still uses flat path:
  - `module12-lab2-component-pipeline.md:261-270`
  - `src/components/PhoneInput.test.tsx`
- Story step still uses flat path:
  - `module12-lab2-component-pipeline.md:282-285`
  - `src/components/PhoneInput.stories.tsx`
- Expected diff says folder contains 3 files:
  - `module12-lab2-component-pipeline.md:328`

Why this is a blocker:

- Students and Copilot will create files in inconsistent locations.
- Barrel exports, Storybook discovery, test matching, and imports may fail.

Required fix:

- Change Step 4.2 to `src/components/PhoneInput/PhoneInput.test.tsx`.
- Change Step 4.3 to `src/components/PhoneInput/PhoneInput.stories.tsx`.
- Add `src/components/PhoneInput/index.ts` if the course standard is folder-per-component barrel exports.
- Update expected diff count accordingly.

### C5. Module 15 Adds JSX to an `.ts` Barrel File

Severity: Critical  
Affected file:

- `module15-lab3-sprint.md`

Evidence:

- `module15-lab3-sprint.md:376-388` says to add a JSX component export to `src/components/MultiFileUpload/index.ts`.

Why this is a blocker:

- A `.ts` file cannot contain JSX unless tooling is configured for it in a nonstandard way.
- The snippet also references `ErrorBoundary`, `MultiFileUploadProps`, and `MultiFileUpload` without showing imports.

Required fix:

- Use `index.tsx` for JSX, or create `SafeMultiFileUpload.tsx`.
- Keep `index.ts` as a pure barrel:
  - export from `./MultiFileUpload`
  - export from `./SafeMultiFileUpload`
- Add explicit imports in the example.

## High-Priority Findings

### H1. Storybook Setup Command May Be Outdated or Too Loose

Severity: High  
Affected file:

- `module6-lab1-scaffold-tests.md`

Evidence:

- `module6-lab1-scaffold-tests.md:253-261` uses `npx storybook@latest init --builder @storybook/builder-vite`.

Concern:

- Current Storybook React/Vite setup usually uses Storybook's detected framework integration. Depending on Storybook version, learners may get `@storybook/react-vite`, not just `@storybook/react` and `@storybook/builder-vite`.
- "Accept defaults" introduces nondeterminism in a timed lab.

Recommended fix:

- Pin the Storybook command and expected packages for the course version.
- Provide a known-good `.storybook/main.ts`.
- Add `build-storybook` script verification, not only `npm run storybook`.

### H2. Jest With Vite React TypeScript Is Under-Specified

Severity: High  
Affected files:

- `module6-lab1-scaffold-tests.md`
- `module6-instructor-notes.md`

Evidence:

- Lab 1 asks Copilot to add Jest but does not pin the transform stack:
  - `module6-lab1-scaffold-tests.md:183-188`
- It then anticipates `ts-jest` or `babel-jest` issues:
  - `module6-lab1-scaffold-tests.md:242-249`
- Instructor notes recommend installing `ts-jest`:
  - `module6-instructor-notes.md:89-95`
- Track A may substitute Vitest:
  - `module6-instructor-notes.md:98`
  - `module6-instructor-notes.md:196`

Why this matters:

- Vite's native testing ecosystem is Vitest.
- Jest can work, but for TypeScript + JSX + Vite aliases it needs explicit configuration.
- Leaving this to Copilot during a 45-minute lab makes the lab fragile.

Recommended fix:

- Choose Jest or Vitest for the course baseline.
- If using Jest, provide exact `devDependencies`, `jest.config.ts`, setup file, moduleNameMapper for `@/*`, and JSX transform settings.
- If using Vitest, update every command from `npx jest`/`npm test -- --coverage` to Vitest equivalents.

### H3. Two JSON Fences Still Fail Validation

Severity: High  
Affected files:

- `module4-instructor-notes.md`
- `module5-automation-scripting.md`

Evidence:

- `module4-instructor-notes.md:186-190` is fenced as `json` but contains only a property fragment:
  - `"editor.codeActionsOnSave": { ... }`
- `module5-automation-scripting.md:221-228` is fenced as `json` but contains JavaScript comments/prompt prose.

Required fix:

- For `module4-instructor-notes.md`, either wrap the fragment in braces or change the fence to `jsonc`/`text`.
- For `module5-automation-scripting.md`, change the fence to `text`.

### H4. Markdown Heading Structure Still Violates Standards

Severity: High  
Affected files:

- Most learner modules.

Examples:

- `module1-big-picture-safety-primer.md`: 31 H1 headings.
- `module5-automation-scripting.md`: 43 H1 headings.
- `module3-advanced-patterns.md`: 33 H1 headings.
- `module4-copilot-deep-dive.md`: 28 H1 headings.
- `module7-refactor-debug.md`: 24 H1 headings.
- `module2-prompting-fundamentals.md`: 22 H1 headings.
- `module10-agents-foundations.md`: 20 H1 headings.

Why this matters:

- Course files render visually, but they do not follow accessible Markdown structure.
- Table-of-contents generation and screen-reader navigation will be poor.

Required fix:

- One H1 per file.
- Major sections use H2.
- Subsections and steps use H3.
- Avoid H1 to H3 jumps.

### H5. Module 13 Instructor Notes Still Encourage Same-Repo Dual Window Setup

Severity: High  
Affected file:

- `module13-instructor-notes.md`

Evidence:

- `module13-instructor-notes.md:23-24` says two VS Code windows open for the same repo, one on `main`, one ready to switch to `feature/date-picker`.

Why this matters:

- Two windows pointing to the same working tree cannot safely represent two independent branches.
- Module 13 learner content correctly uses worktrees with `git worktree add -b` at `module13-parallel-pr.md:121-126`.

Required fix:

- Change instructor setup to:
  - one window for main worktree
  - one window for `../my-form-library-demo` worktree
- Avoid saying one same-repo window is on `main` and the other on a feature branch.

### H6. Module 14 Instructor Paths Do Not Match Folder Convention

Severity: High  
Affected file:

- `module14-instructor-notes.md`

Evidence:

- `module14-instructor-notes.md:42-44` references:
  - `src/components/Select.tsx`
  - `src/components/TextInput.tsx`
  - `src/components/RadioGroup.tsx`

Course convention after Lab 1:

- `src/components/Select/Select.tsx`
- `src/components/TextInput/TextInput.tsx`
- `src/components/Checkbox/Checkbox.tsx`

Required fix:

- Update paths to folder convention.
- Replace `RadioGroup` unless Lab 1 creates it.

### H7. Module 1 Still Uses Placeholder Repository URL

Severity: High  
Affected file:

- `module1-big-picture-safety-primer.md`

Evidence:

- `module1-big-picture-safety-primer.md:691-700` clones `https://github.com/your-org/vibe-coding-react.git`.

Why this matters:

- Students cannot run the first repository interaction without a real URL.

Required fix:

- Replace with real course repository URL.
- Or remove clone step and say "open the provided course repo".

### H8. Prompt Files Are Presented as Guaranteed Without IDE/Version Guardrails

Severity: High  
Affected files:

- `module4-copilot-deep-dive.md`
- `module10-agents-foundations.md`
- `module12-lab2-component-pipeline.md`

Evidence:

- `.github/prompts/*.prompt.md` is used throughout.
- `module10-instructor-notes.md:9-13` mentions Agent mode and prompt files but does not include fallback if prompt files are not recognized.

Why this matters:

- Copilot prompt-file support depends on current IDE support and settings.

Recommended fix:

- Add a fallback for every prompt-file exercise:
  - "If `/plan` does not autocomplete, open `.github/prompts/plan.prompt.md`, copy its contents into Chat, and run it manually."
- Include a setup check for prompt file recognition.

## Medium-Priority Findings

### M1. Unlabeled Code Fences Are Overused

Severity: Medium  
Evidence:

- 124 fenced blocks have no language tag.

Why this matters:

- Prompt examples, directory trees, and expected output should be explicitly tagged as `text`.
- Code snippets should be tagged with actual languages.

Recommended fix:

- Use `text` for prompts and expected terminal output.
- Use `bash` only for actual shell commands.
- Use `jsonc` for JSON-with-comments.
- Use `markdown` only for content intended to be written into `.md` files.

### M2. Commands Use Deprecated or Version-Sensitive Flags

Severity: Medium  
Examples:

- `npx eslint src/ --ext .tsx,.ts` appears in multiple modules. With newer ESLint flat config setups, `--ext` may be unnecessary or invalid depending on configuration.
- `npm test -- --testPathPattern PhoneInput` may vary between Jest versions and scripts. Newer Jest prefers `--testPathPatterns`.
- Storybook commands vary between versions.

Recommended fix:

- Pin tool versions in Lab 1.
- Provide package scripts and use those scripts everywhere:
  - `npm run typecheck`
  - `npm run lint`
  - `npm run test:coverage`
  - `npm run build-storybook`

### M3. Some Safety Guidance Still Normalizes Risky Commands

Severity: Medium  
Evidence:

- `module6-instructor-notes.md:20` uses `rm -rf test-check`.
- `module5-automation-scripting.md:132` uses `lsof -ti:3000 | xargs kill -9` as an explanation example.
- `module5-automation-scripting.md:134` runs AI-generated `fix-commands.sh`.
- `module5-instructor-notes.md:146` still says `git checkout -- filename`, while other files have moved to `git restore`.

Recommended fix:

- Add explicit "demo cleanup only" warnings around destructive commands.
- Prefer `git restore <file>` consistently.
- Do not include `kill -9` as a beginner-facing example unless the safety discussion is the point.

### M4. Instructor Notes Are Not Fully Standardized

Severity: Medium  
Evidence:

- Some instructor notes have styled headers and course metadata, others start plainly.
- Several instructor files do not include Day/Position metadata.
- Heading hierarchy differs widely across instructor notes.

Recommended fix:

- Standardize instructor-note template:
  - module title
  - prerequisites
  - demo setup
  - section-by-section facilitation
  - common issues
  - timing cuts
  - transition

### M5. Inline HTML Is Still Heavy

Severity: Medium  
Evidence:

- All modules rely heavily on styled HTML tables and callout boxes.

Why this matters:

- This renders in many Markdown viewers but can be stripped by LMS systems or static-site pipelines.

Recommended fix:

- If the target publishing environment supports raw HTML, keep it.
- Otherwise convert callouts to Markdown blockquotes and tables to Markdown tables where possible.

## Module-by-Module Review

### Module 1 - Big Picture & Safety Primer

Status: Mostly coherent, still not fully runnable.

Issues:

- Placeholder repo URL remains at `module1-big-picture-safety-primer.md:691-700`.
- Copilot Chat installation instructions still separate Copilot and Copilot Chat extensions at `module1-big-picture-safety-primer.md:613-634`; this may vary by current VS Code/Copilot packaging.
- Uses `@workspace`, `#file`, and `/explain`, which are GitHub Copilot-specific. This is acceptable for this pass because the user asked for GitHub Copilot runnable content.

Fix:

- Replace placeholder repo URL.
- Add a "if Copilot Chat is already bundled" note.

### Module 1 Instructor Notes

Status: Coherent.

Issues:

- Duplication detection and UI labels may need current product verification.
- No major content blocker.

### Module 2 - Prompting Fundamentals

Status: Conceptually coherent.

Issues:

- Examples include broader app stack assumptions, such as Tailwind, React Router, React Query, and Zustand, while the course lab repo is a form component library.
- Many H1 headings.

Fix:

- Keep broad examples if intentional, but clearly separate "dashboard example" from the course repo.
- Normalize heading levels.

### Module 2 Instructor Notes

Status: Good.

Issues:

- Same stack drift as Module 2.
- No runnable blocker.

### Module 3 - Advanced Patterns

Status: Strong conceptual module.

Issues:

- Many H1 headings.
- Some prompt examples remain in unlabeled fences.
- Transition language should be checked against the final course sequence.

Fix:

- Normalize headings and label prompt blocks as `text`.

### Module 3 Instructor Notes

Status: Good.

Issues:

- Instructor metadata is less standardized than later notes.

### Module 4 - Copilot Deep Dive

Status: Useful Copilot-specific module.

Issues:

- Requires current prompt-file support but does not provide fallback if `/review-component` does not appear.
- Uses team-shared prompt files as if universally available.
- Many H1 headings.

Fix:

- Add IDE/version check and manual fallback for prompt files.

### Module 4 Instructor Notes

Status: Good, but has one code-fence problem.

Issues:

- `module4-instructor-notes.md:186-190` is not complete JSON.

Fix:

- Wrap it as:
  - `{ "editor.codeActionsOnSave": { ... } }`
- Or mark it as `jsonc`/`text` and call it a fragment.

### Module 5 - Automation & Scripting

Status: Needs major CLI rewrite.

Issues:

- Teaches retired `gh-copilot` extension.
- Uses shell-specific commands heavily.
- `module5-automation-scripting.md:221-228` is invalid JSON fence.
- Some examples are Unix/macOS-specific but not labeled as such.

Fix:

- Rewrite around current Copilot CLI.
- Label shell examples by platform.
- Convert invalid JSON fence to `text`.

### Module 5 Instructor Notes

Status: Needs CLI update.

Issues:

- Uses retired `gh copilot` examples.
- Still mentions `git checkout -- filename`.

Fix:

- Update to current Copilot CLI.
- Prefer `git restore`.

### Module 6 - Lab 1

Status: Much improved, but still risky.

Improvements:

- Now scaffolds `TextInput`, `Select`, and `Checkbox`.
- Adds `.stories.tsx` files.
- Adds `jest-axe`.
- Adds Storybook initialization.
- Uses `git restore` instead of `git checkout --` in the learner module.

Remaining issues:

- Does not create `RadioGroup` and `Textarea`, which later instructor notes still require.
- Jest setup is still left partly to Copilot and may fail in Vite.
- Storybook init command should be pinned and verified.
- `npx storybook@latest init --builder @storybook/builder-vite` may not produce the exact package/config expected by later modules.
- The lab is now very dense for 45 minutes: Vite init, Git, instructions, scaffold, Jest config, Storybook init, component generation, tests, coverage, lint, and recap.

Fix:

- Add `RadioGroup` and `Textarea` or remove them later.
- Provide known-good config files.
- Consider extending Lab 1 or moving Storybook setup to pre-lab.

### Module 6 Instructor Notes

Status: Aligned better than before, but needs cleanup.

Issues:

- `rm -rf test-check` appears at `module6-instructor-notes.md:20`.
- Jest/Vitest optionality may confuse instructors if the learner path is Jest-only.

Fix:

- Add cleanup warning.
- Pick one test runner for baseline.

### Module 7 - Refactor & Debug

Status: Coherent.

Issues:

- Uses `FormField` paths in examples, but Lab 1 no longer builds `FormField`.
- Example command: `npm test -- --testPathPattern=FormField` at `module7-refactor-debug.md:166`.

Fix:

- Replace `FormField` examples with `TextInput`, `Select`, or `Checkbox`.

### Module 7 Instructor Notes

Status: Mostly coherent.

Issues:

- Demo references validators and `#terminalLastCommand`, which fits Lab 1.
- No major blocker besides path alignment if examples mention old components.

### Module 8 - AI Quality Assurance

Status: Coherent conceptually.

Issues:

- `fast-check` is introduced, but learner module does not include explicit install steps; instructor notes do (`module8-instructor-notes.md:122`).
- Mutation testing remains conceptual unless tooling is provided.

Fix:

- In learner module, mark property/mutation testing as optional unless dependencies are installed.

### Module 8 Instructor Notes

Status: Good.

Issues:

- Pre-session setup requires `fast-check`; ensure learner module matches.

### Module 9 - AIOps / CI/CD

Status: Major rewrite still required.

Issues:

- Retired `gh-copilot` extension.
- Unreliable Copilot-in-CI automation.
- Risky AI-generated fix script workflow.
- Uses shell command substitution for large inputs.

Fix:

- Rewrite as described in C1 and C2.

### Module 9 Instructor Notes

Status: Needs major rewrite.

Issues:

- Pre-session setup and demo script depend on retired extension.
- Claims about org license/GITHUB_TOKEN need verification or removal.

Fix:

- Update to current CLI or remove unattended AI CI claims.

### Module 10 - Agents Foundations

Status: Mostly coherent.

Improvements:

- Malformed HTML from prior report appears fixed.
- JSON-with-comments examples now mostly use `jsonc`.

Issues:

- Custom slash commands `/plan`, `/implement`, `/test`, `/review` may be mistaken for built-in commands.
- Prompt-file support still needs fallback.
- Contains several git commit/PR commands that assume a real GitHub repo and branch.

Fix:

- Add "these are custom prompt files you create in this module" before first slash-command table.
- Add fallback manual invocation.

### Module 10 Instructor Notes

Status: Good.

Issues:

- `module10-instructor-notes.md:9` says Agent mode requires Copilot extension v1.230+. Verify exact version before delivery.
- Uses model-specific teaching language. Keep if target Copilot tenant exposes those model choices.

### Module 11 - Agents Applied

Status: Mostly coherent, but depends on missing components and optional MCP setup.

Improvements:

- `jest-axe` snippet now includes imports.

Issues:

- Instructor notes require `RadioGroup` and `Textarea`.
- MCP setup uses external `npx` packages and GitHub tokens. This is advanced and network/auth-dependent.
- `@workspace`, `#file`, `#terminalLastCommand` examples are Copilot-specific, which is fine for this pass, but learners need exact UI setup.

Fix:

- Move MCP sections to optional/advanced unless the environment is guaranteed.
- Align component list with Lab 1.

### Module 11 Instructor Notes

Status: Good but blocked by component mismatch.

Issues:

- `module11-instructor-notes.md:23` still requires missing `RadioGroup` and `Textarea`.
- Pre-session setup assumes `.vscode/mcp.json` and `GITHUB_TOKEN`.

Fix:

- Update component list or Lab 1.
- Mark MCP setup optional.

### Module 12 - Lab 2

Status: Good workflow design, but path bug blocks clean execution.

Issues:

- Mixed folder/flat `PhoneInput` paths as described in C4.
- Pre-lab instructor notes still require `RadioGroup` and `Textarea`.
- `npx storybook build --quiet 2>&1 | tail -20` is shell/platform-specific.

Fix:

- Fix `PhoneInput` paths.
- Use package script `npm run build-storybook`.
- Align prerequisites.

### Module 12 Instructor Notes

Status: Useful, but prerequisite mismatch remains.

Issues:

- `module12-instructor-notes.md:23` still requires missing components.
- `module12-instructor-notes.md:137` still treats missing `jest-axe` as common issue even though Lab 1 now installs it. This should become a pre-check failure, not a common surprise.

### Module 13 - Parallel PR

Status: Improved.

Improvements:

- Worktree command now uses `git worktree add -b` in learner content.

Issues:

- Instructor setup still describes two windows pointing at the same repo as if they can be on different branches.
- CI examples assume Storybook script names and package scripts exist.

Fix:

- Update instructor setup to use two worktrees.
- Use canonical package scripts.

### Module 13 Instructor Notes

Status: Needs setup correction.

Issues:

- Same-repo dual-window setup at `module13-instructor-notes.md:23-24`.

### Module 14 - Production Debt

Status: Strong conceptual production module.

Issues:

- Instructor notes use flat paths and missing `RadioGroup`.
- `ErrorBoundary` is created in Module 14, but Module 15 depends on it. Make that dependency explicit in learner recap.
- Strict TypeScript is intentionally not enabled for demo in notes, but previous modules often assume strict mode. This is a course-state contradiction unless handled as a staged demo branch.

Fix:

- Use a dedicated instructor demo branch with intentional debt.
- Update file paths.
- Explicitly mark `ErrorBoundary` as a required artifact for Lab 3.

### Module 14 Instructor Notes

Status: Good concept, but path/component mismatch.

Issues:

- `module14-instructor-notes.md:42-44` paths are inconsistent with Lab 1.
- `RadioGroup` missing.

### Module 15 - Lab 3

Status: Good capstone design, but one TypeScript/JSX blocker.

Improvements:

- `MultiFileUploadProps.value` is now required, which fixes the prior controlled/uncontrolled API concern.

Issues:

- JSX in `index.ts` at `module15-lab3-sprint.md:376-388`.
- Lab still assumes `ErrorBoundary` is available from Module 14.
- 45 minutes remains tight for the full feature, tests, accessibility, Storybook, PR write-up, and quality gates.

Fix:

- Move safe wrapper to `.tsx`.
- Add imports.
- Make ErrorBoundary dependency explicit.
- Consider making Storybook interaction story optional.

### Module 15 Instructor Notes

Status: Good, but prerequisites need alignment.

Issues:

- Still requires `RadioGroup` and `Textarea` at `module15-instructor-notes.md:23`.
- Opening says there are "no step-by-step prompts", while learner module still has many step prompts.

Fix:

- Align wording: "less prescriptive prompts" rather than "no step-by-step prompts".

## Current Runnable Path Assessment

### Can a student run the course end to end today?

Not reliably.

The likely failure points are:

1. Module 1 placeholder repository URL.
2. Lab 1 Jest/Storybook setup variability.
3. Later modules expecting `RadioGroup` and `Textarea`.
4. Module 7 references `FormField`, which Lab 1 no longer creates.
5. Module 12 path mismatch for `PhoneInput` tests and stories.
6. Modules 5 and 9 retired Copilot CLI command surface.
7. Module 15 JSX in `.ts`.

### Can a student use it with GitHub Copilot after targeted fixes?

Yes. The course structure is sound once the remaining path/tooling issues are fixed.

## Recommended Remediation Plan

### Immediate Fixes

1. Replace all retired `gh copilot` CLI content with current standalone Copilot CLI content.
2. Remove or rewrite Copilot-in-CI unattended automation in Module 9.
3. Decide whether Lab 1 creates `RadioGroup` and `Textarea`.
4. Fix Module 12 `PhoneInput` test/story paths.
5. Fix Module 15 `SafeMultiFileUpload` file extension/imports.
6. Replace Module 1 placeholder repository URL.
7. Convert the two invalid `json` fences.

### Next Pass Fixes

1. Normalize heading hierarchy.
2. Pin course tool versions.
3. Provide known-good generated repo baseline files:
   - `package.json`
   - `jest.config.ts` or `vitest.config.ts`
   - `.storybook/main.ts`
   - `tsconfig.json`
   - `eslint.config.js`
4. Add prompt-file fallback instructions.
5. Standardize instructor notes.
6. Replace platform-specific shell snippets or label them.

## Acceptance Criteria for the Next Revision

The content is ready when:

- Lab 1 produces every component expected by Modules 7, 11, 12, 14, and 15.
- `npm install` works from a clean Lab 1 repo.
- `npx tsc --noEmit` passes after Lab 1.
- `npm test -- --coverage` passes after Lab 1.
- `npm run build-storybook` passes after Lab 1.
- Module 12 creates all `PhoneInput` files in one consistent folder structure.
- Module 15 does not put JSX in `.ts` files.
- Modules 5 and 9 use current official GitHub Copilot CLI commands.
- Module 9 does not claim unsupported unattended Copilot CI behavior.
- Every `json` fence parses as JSON.
- Each module has one H1 heading.
- Instructor notes and learner modules refer to the same components, paths, commands, and prerequisites.

## Quick Checklist

- [ ] Rewrite Module 5 CLI section for current `@github/copilot` CLI.
- [ ] Rewrite Module 9 AIOps section to avoid retired `gh-copilot`.
- [ ] Remove unsupported `GITHUB_TOKEN` Copilot-in-CI claims or cite official support.
- [ ] Decide on `RadioGroup` and `Textarea`; add them to Lab 1 or remove from later modules.
- [ ] Replace `FormField` examples in Module 7.
- [ ] Fix Module 12 `PhoneInput.test.tsx` path.
- [ ] Fix Module 12 `PhoneInput.stories.tsx` path.
- [ ] Add `PhoneInput/index.ts` if folder barrels are standard.
- [ ] Fix Module 15 `SafeMultiFileUpload` JSX in `.ts`.
- [ ] Replace Module 1 placeholder repository URL.
- [ ] Convert invalid JSON fences in Module 4 instructor notes and Module 5.
- [ ] Pin Jest/Storybook/ESLint setup.
- [ ] Normalize headings.
- [ ] Add prompt-file fallback instructions.
