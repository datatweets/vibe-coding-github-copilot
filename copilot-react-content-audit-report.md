# Copilot React Course Content Audit Report

Audit date: 2026-05-05  
Scope: all Markdown files in `copilot-react/`  
Files reviewed: 30 Markdown files, 11,956 total lines  
Code blocks reviewed: 238 fenced blocks

## Executive Summary

The course has a coherent high-level learning arc: safety and prompting, Copilot tooling, labs, quality gates, agent workflows, CI, production hardening, and a capstone sprint. However, it is not currently ready as a fully runnable end-to-end course, and it is not directly runnable in ChatGPT without a compatibility layer.

The most important blockers are:

1. Lab 1 creates a different component library than later modules assume.
2. Later labs depend on Storybook and `jest-axe`, but Lab 1 does not reliably install or configure them.
3. ChatGPT compatibility is missing: most hands-on prompts use Copilot-only syntax such as `@agent`, `@workspace`, `#file:`, `#terminalLastCommand`, and `/tests`.
4. Module 9 uses invalid or inconsistent Copilot CLI setup commands and treats Copilot CLI as a CI automation primitive in ways that are unlikely to work reliably.
5. Several code fences are mislabeled as `json`, `yaml`, or `tsx` even though they contain comments, prose, or prompt examples. That makes copied code fail validators.
6. Markdown structure is renderable, but it does not follow standard heading/accessibility conventions because most learner modules use many top-level `#` headings and jump from `#` to `###`.

Recommended status: revise before delivery.

## Audit Method

I checked:

- File inventory and module/instructor-note pairing.
- Heading hierarchy and Markdown fence integrity.
- Code fence languages and basic JSON/bash syntax validity.
- Course sequence, lab prerequisites, and later-module assumptions.
- GitHub Copilot, ChatGPT, and current tooling compatibility.
- Code and command plausibility for React, TypeScript, Jest, Storybook, GitHub Actions, and CI.
- Instructor notes against corresponding learner modules.

Automated checks found:

- 30 `.md` files present.
- 0 unclosed fenced code blocks.
- 238 fenced code blocks:
  - 124 have no language tag.
  - 61 are `bash`.
  - 21 are `markdown`.
  - 12 are `json`.
  - 10 are `yaml`.
  - 6 are `typescript`.
  - 4 are `tsx`.
- Bash fenced blocks passed shell parse checks.
- Multiple `json` fenced blocks are not valid JSON because they include JavaScript-style comments or are prompt prose.
- Local `tsc` is not installed in this environment, so TypeScript examples could not be compiled directly. Most TypeScript snippets are illustrative fragments rather than complete files.

## External Documentation Spot Check

I checked official GitHub documentation for current Copilot CLI and customization behavior because those product surfaces change frequently.

- GitHub's current Copilot CLI install docs show `npm install -g @github/copilot` and Node.js 22+ as the npm path, with `copilot login` in the CLI command reference.
- GitHub still has older docs for the GitHub CLI extension flow with `gh extension install github/gh-copilot` and `gh copilot explain/suggest`.
- There is no support in official docs for `npm install -g @github-copilot/cli` or `gh copilot auth` as used in Module 9.
- GitHub docs confirm `.github/copilot-instructions.md`, `.github/instructions/*.instructions.md`, `AGENTS.md`, and `.github/prompts/*.prompt.md` support, but prompt files are public preview and may require enabling workspace settings depending on IDE/version.

Sources:

- https://docs.github.com/copilot/how-tos/set-up/install-copilot-cli
- https://docs.github.com/en/copilot/reference/copilot-cli-reference/cli-command-reference
- https://docs.github.com/en/copilot/using-github-copilot/using-github-copilot-in-the-command-line
- https://docs.github.com/en/copilot/how-tos/configure-custom-instructions/add-repository-instructions
- https://docs.github.com/en/copilot/reference/custom-instructions-support

## Blocking Findings

### 1. Later Modules Assume Components Lab 1 Does Not Build

Severity: Critical  
Impact: Modules 11, 12, 15 cannot reliably run after Lab 1.

Lab 1 builds:

- `Button`
- `Input`
- `FormField`
- `useFormValidation`
- `validators`
- `formatters`

References:

- `module6-lab1-scaffold-tests.md:167-179`
- `module6-lab1-scaffold-tests.md:190-218`
- `module6-lab1-scaffold-tests.md:507-518`

Later modules assume the repo contains:

- `TextInput`
- `Select`
- `Checkbox`
- `RadioGroup`
- `Textarea`
- `PhoneInput`

References:

- `module11-instructor-notes.md:23`
- `module12-instructor-notes.md:23`
- `module15-instructor-notes.md:23`

Why this matters:

- Module 11 demos localize and edit `TextInput.tsx` and `Checkbox.tsx`, but these are never created in Lab 1.
- Module 12 uses `TextInput.tsx` as the canonical component pattern, but Lab 1 uses `Input/Input.tsx`.
- Module 15 assumes Lab 1 plus Lab 2 components all pass before the capstone.

Recommended fix:

- Either revise Lab 1 to scaffold the exact later component set (`TextInput`, `Select`, `Checkbox`, `RadioGroup`, `Textarea`) or revise Modules 11-15 to use `Button`, `Input`, and `FormField`.
- Choose one component directory convention and use it everywhere.

### 2. Storybook and jest-axe Are Required Later but Not Established Early

Severity: Critical  
Impact: Labs fail at quality gates and Storybook steps.

Lab 1 does not install or configure Storybook or `jest-axe`.

Later modules require them:

- `module10-agents-foundations.md:103` assumes Storybook is used for visual documentation.
- `module11-agents-applied.md:278-321` introduces `jest-axe` checks.
- `module12-lab2-component-pipeline.md:120-129` requires every component test to include `jest-axe` and every component to include stories.
- `module12-lab2-component-pipeline.md:290` runs `npx storybook build`.
- `module15-lab3-sprint.md:31`, `303-309`, and `519` require RTL, `jest-axe`, and Storybook.

Instructor notes partly patch this:

- `module12-instructor-notes.md:137` says `jest-axe` not installed is a common issue and gives an install command.

Why this matters:

- This turns a core lab requirement into an instructor rescue step.
- Students using ChatGPT or Copilot will receive inconsistent setup suggestions because the repo does not encode the expected toolchain.

Recommended fix:

- Add Storybook and `jest-axe` setup to Lab 1 or add a dedicated "Repo baseline upgrade" step before Module 11.
- Include exact install commands, setup file changes, scripts, and verification commands:
  - `npm install --save-dev jest-axe @types/jest-axe`
  - Storybook init command appropriate to the chosen framework.
  - `npm run storybook` or `npm run build-storybook` scripts.
  - Jest setup file extension for `toHaveNoViolations`.

### 3. ChatGPT Compatibility Is Not Defined

Severity: Critical  
Impact: The course is Copilot-runnable, not ChatGPT-runnable.

The content repeatedly uses Copilot-specific syntax:

- `@agent`
- `@workspace`
- `#file:path`
- `#terminalLastCommand`
- `#selection`
- `#codebase`
- `/tests`
- `/fix`
- `/explain`
- `/review`
- `/implement`

Examples:

- `module1-big-picture-safety-primer.md:705-712`
- `module5-automation-scripting.md:275-286`
- `module6-lab1-scaffold-tests.md:79-89`
- `module6-lab1-scaffold-tests.md:378-397`
- `module10-agents-foundations.md:372-378`
- `module11-agents-applied.md:61-69`
- `module12-lab2-component-pipeline.md:55-70`
- `module15-lab3-sprint.md:351-357`

Why this matters:

- ChatGPT does not interpret Copilot's `#file`, `#terminalLastCommand`, `@workspace`, or `/tests` syntax in a normal chat.
- ChatGPT can help if files are attached, a repo workspace is connected, or the user pastes command output, but the prompts need explicit alternatives.

Recommended fix:

Add a "ChatGPT/Codex equivalent" after every Copilot prompt pattern:

| Copilot syntax | ChatGPT/Codex equivalent |
| --- | --- |
| `@workspace Analyze...` | "Inspect the repository files available in this workspace. Start read-only and summarize the architecture." |
| `#file:src/App.tsx` | Attach or paste `src/App.tsx`, or say "Open `src/App.tsx` in the workspace and use it as context." |
| `#terminalLastCommand` | Paste the exact command and complete output, or ask the agent to run the command if it has terminal access. |
| `/tests` | "Generate tests for this file using Jest and React Testing Library. Put them in `<path>` and explain how to run them." |
| `.github/copilot-instructions.md` | For ChatGPT/Codex, add `AGENTS.md` at repo root, or paste the rules as system/project instructions. |

### 4. Module 9 Copilot CLI Commands Are Invalid or Inconsistent

Severity: Critical  
Impact: CI examples are not runnable as written.

Problems:

- `module9-aiops-cicd.md:73` installs `@github-copilot/cli`, which does not match GitHub's current npm package name.
- `module9-aiops-cicd.md:76` uses `gh copilot auth`, which is not in the official current Copilot CLI command reference.
- `module9-instructor-notes.md:10` repeats the invalid install/auth pattern.
- `module9-instructor-notes.md:154-155` repeats those commands in troubleshooting.
- Module 5 teaches the older `gh extension install github/gh-copilot` flow (`module5-automation-scripting.md:80-84`), while Module 9 switches to a different package name and auth flow without explaining the difference.

Why this matters:

- Students will fail setup in the CI module.
- Instructors will troubleshoot using invalid commands.
- The course conflates legacy `gh copilot` extension usage with the newer standalone `copilot` CLI.

Recommended fix:

- Pick one CLI path:
  - Legacy GitHub CLI extension path: `gh extension install github/gh-copilot`, then `gh copilot suggest/explain`.
  - Current standalone CLI path: `npm install -g @github/copilot`, then `copilot login`, `copilot`, or `copilot -p`.
- If teaching both, include a comparison table and explicitly mark Module 5 as legacy/interactive and Module 9 as standalone/non-interactive.
- Replace all `@github-copilot/cli` references.

### 5. Copilot-in-CI Pattern Is Overstated

Severity: High  
Impact: The AIOps module may teach unreliable automation.

Module 9 shows GitHub Actions running Copilot CLI to analyze PR diffs and test failures:

- `module9-aiops-cicd.md:57-87`
- `module9-aiops-cicd.md:106-124`
- `module9-aiops-cicd.md:162-187`
- `module9-aiops-cicd.md:276-331`

Problems:

- It assumes Copilot CLI can authenticate and run unattended in CI with `GH_TOKEN`.
- It pipes large logs/diffs into shell command arguments using `$(cat file)` or `$(tail ...)`, which can break on shell quoting, argument length limits, and sensitive content.
- It suggests generating shell fix scripts from CI output and running them locally (`module9-aiops-cicd.md:129-137`), which needs stronger safety gates.

Recommended fix:

- Reframe this module around CI collecting artifacts, then human-driven Copilot analysis in the IDE/CLI.
- If keeping programmatic CLI examples, use a documented non-interactive current CLI command, JSON/text output options if available, and explicit permission/auth requirements.
- Avoid `$(cat large-file)` inside prompt strings. Use file attachment/context mechanisms supported by the chosen tool or truncate and sanitize deliberately.

## High-Priority Findings

### 6. Component File Structure Is Inconsistent

Severity: High  
Impact: Agents will generate inconsistent imports, exports, tests, and stories.

Lab 1 uses folder-per-component:

- `src/components/Button/Button.tsx`
- `src/components/Input/Input.tsx`
- `src/components/FormField/FormField.tsx`

Module 12 prompt template uses flat component files:

- `src/components/${componentName}.tsx`
- `src/components/${componentName}.test.tsx`
- `src/components/${componentName}.stories.tsx`

References:

- `module6-lab1-scaffold-tests.md:167-179`
- `module12-lab2-component-pipeline.md:150-154`
- `module12-lab2-component-pipeline.md:246-297`
- `module15-lab3-sprint.md:120-132`

Recommended fix:

- Standardize on either:
  - `src/components/ComponentName/ComponentName.tsx`, or
  - `src/components/ComponentName.tsx`.
- Update every lab, prompt file, barrel export, test path, and Storybook path accordingly.

### 7. Multiple Code Blocks Are Mislabeled

Severity: High  
Impact: Copy/paste validation fails and syntax highlighting misleads students.

Examples:

- `module10-agents-foundations.md:388-403` is fenced as `json` but starts with `// package.json`.
- `module10-agents-foundations.md:537-576` is fenced as `json` but starts with `// .vscode/tasks.json`.
- `module11-agents-applied.md:361-375` is fenced as `json` but starts with `// .vscode/mcp.json`.
- `module4-copilot-deep-dive.md:436-443` is fenced as `json` but starts with `// .vscode/settings.json`.
- `module4-instructor-notes.md:186-190` is fenced as `json` but is only a JSON property fragment.
- `module5-automation-scripting.md:221-228` is fenced as `json` but is only commented prompt prose.
- `module9-aiops-cicd.md:228-239` is fenced as `json` but starts with `// package.json`.
- `module3-advanced-patterns.md:433-454` is fenced as `tsx` but contains prompt strings, not runnable TSX.

Recommended fix:

- Use `jsonc` for JSON-with-comments examples.
- Use `text` for prompt examples.
- Use `json` only for complete valid JSON.
- Use `yaml` only for complete YAML or clearly label fragments as `yaml` with comments explaining where they belong.

### 8. Markdown Heading Structure Does Not Follow Standard Accessibility Practice

Severity: High  
Impact: Generated table-of-contents, screen-reader navigation, and static site conversion degrade.

Most learner modules use many `#` headings for major sections and then jump to `###`.

Examples from automated scan:

- `module1-big-picture-safety-primer.md`: 31 H1 headings.
- `module2-prompting-fundamentals.md`: 22 H1 headings.
- `module3-advanced-patterns.md`: 33 H1 headings.
- `module5-automation-scripting.md`: 43 H1 headings.
- `module7-refactor-debug.md`: 24 H1 headings.
- `module13-parallel-pr.md`: 18 H1 headings.

Recommended fix:

- Use one H1 per file.
- Use H2 for major sections/exercises.
- Use H3 for subsections/steps.
- Avoid heading jumps.

### 9. Inline HTML Is Heavy and Sometimes Fragile

Severity: Medium/High  
Impact: Rendering varies across Markdown viewers and LMS platforms.

The files rely extensively on inline `<table>`, `<span>`, `<td style=...>`, and emoji callout blocks. This may render in VS Code preview but can fail or sanitize badly in some LMS, GitHub-rendered contexts, Notion imports, or static-site generators.

Concrete malformed HTML example:

- `module10-agents-foundations.md:312` has `style="padding:10px 12px; border:1px solid #CCC;feature"`.

Recommended fix:

- Replace repeated HTML callouts with standard Markdown blockquotes or a small set of portable callout shortcodes supported by the target publishing platform.
- If HTML tables must remain, run them through an HTML validator and remove malformed style fragments.

### 10. Course Transitions Contain Sequence Errors

Severity: Medium/High  
Impact: Instructor pacing and student expectations become confusing.

Examples:

- `module2-prompting-fundamentals.md:347` says students will write `copilot-instructions.md` during Module 4, but Module 3 already covers team `copilot-instructions.md` in depth.
- `module3-advanced-patterns.md:957` says Module 4 is a hands-on lab, but Module 4 is a tool deep dive.
- `module4-instructor-notes.md:214-217` says Module 5 is a lab, but Module 5 is Automation and Scripting; Lab 1 is Module 6.
- `module5-automation-scripting.md:846-853` correctly transitions to Module 6 Lab 1, so Module 4 notes should be corrected.

Recommended fix:

- Update all transitions after finalizing the module map.
- Add a one-page course dependency map at the top of the folder.

### 11. Safety Guidance Teaches Destructive Git Recovery Too Casually

Severity: Medium/High  
Impact: Students may lose uncommitted work.

Examples:

- `module4-instructor-notes.md:150-156` recommends `git reset --hard HEAD` as undo after agent sessions.
- `module7-instructor-notes.md:148` lists `git reset --hard HEAD`.
- `module6-lab1-scaffold-tests.md:537` says use `git checkout --` as undo.

The content often says "commit first", which helps, but the recovery commands should be wrapped in stronger warnings.

Recommended fix:

- Prefer:
  - `git status`
  - `git diff`
  - Copilot Edits Discard button
  - `git restore --source=HEAD -- <file>` for specific file recovery
  - `git stash push -u -m "before agent recovery"` before destructive recovery
- Keep `git reset --hard` only in an instructor-only warning box with exact prerequisites.

## Module-by-Module Findings

### Module 1: Big Picture & Safety Primer

Status: Mostly coherent, but not fully runnable.

Issues:

- Placeholder clone URL `https://github.com/your-org/vibe-coding-react.git` will fail unless replaced (`module1-big-picture-safety-primer.md:691-700`).
- Uses Copilot-only Chat prompts (`@workspace`, `/explain`, `#file`) without ChatGPT equivalents (`module1-big-picture-safety-primer.md:705-712`).
- Installation instructions should be checked against current VS Code/Copilot extension packaging; Copilot Chat may no longer require a separate extension in some VS Code setups (`module1-big-picture-safety-primer.md:625-634`).

Fixes:

- Replace placeholder repo URL with the real repository.
- Add a ChatGPT/Codex version of first interaction prompts.
- Add a setup verification checklist that includes the exact expected starter repo.

### Module 1 Instructor Notes

Status: Good facilitation structure.

Issues:

- Strongly Copilot-specific. If course must run on ChatGPT, add instructor fallback demos.
- Mentions duplication detection settings (`module1-instructor-notes.md:152`); verify current UI name before delivery.

### Module 2: Prompting Fundamentals

Status: Conceptually strong.

Issues:

- Timing/transition inconsistency around where `copilot-instructions.md` is created (`module2-prompting-fundamentals.md:347`, `946`).
- ChatGPT compatibility missing for `#file` and `@workspace` references.
- Several prompt examples assume Tailwind, React Router, React Query, Zustand, and Jest, but the lab repo later built from Vite does not establish all those dependencies (`module2-prompting-fundamentals.md:223-224`).

Fixes:

- Align stack examples with `my-form-library`.
- Add ChatGPT prompt equivalents.

### Module 2 Instructor Notes

Status: Useful and detailed.

Issues:

- Same stack-consistency issue as Module 2.
- No ChatGPT teaching path.

### Module 3: Advanced Patterns & Workflows

Status: Good prompting content with standards issues.

Issues:

- `module3-advanced-patterns.md:433-454` uses `tsx` for prompt prose.
- Module 3 transitions imply Module 4 is a hands-on lab (`module3-advanced-patterns.md:957`), but Module 4 is a Copilot deep dive.
- Extensive HTML and multiple H1 headings.

Fixes:

- Change prompt examples to `text`.
- Correct transition language.
- Normalize headings.

### Module 3 Instructor Notes

Status: Mostly coherent.

Issues:

- Transition language at `module3-instructor-notes.md:169` says Module 4 is where participants apply content in a hands-on lab. It should say Module 4 is tool fluency and Module 6 is Lab 1, unless Module 4 is redesigned.

### Module 4: Copilot Deep Dive

Status: Useful Copilot-specific tool module.

Issues:

- Several `json` code fences contain comments and are not valid JSON (`module4-copilot-deep-dive.md:436-456`).
- Uses `.github/prompts/` but does not clearly mention prompt-file enablement/preview status (`module4-copilot-deep-dive.md:170-203`).
- Strong Copilot syntax dependency; not ChatGPT-runnable.

Fixes:

- Use `jsonc` or remove comments.
- Add note that prompt files are public preview and may require enabling workspace setting depending on IDE/version.
- Add ChatGPT/Codex equivalents using `AGENTS.md` and explicit file attachments.

### Module 4 Instructor Notes

Status: Good demo guidance but has sequence and safety issues.

Issues:

- Says Module 5 is a lab, but Lab 1 is Module 6 (`module4-instructor-notes.md:214-217`).
- Recommends `git reset --hard HEAD` in Q&A (`module4-instructor-notes.md:150-156`).
- `module4-instructor-notes.md:186-190` is fenced as `json` but is a JSON fragment.

Fixes:

- Correct transition.
- Replace destructive recovery guidance with safer workflow.
- Change fence to `jsonc` or `text`.

### Module 5: Automation & Scripting

Status: Broad and useful, but cross-platform and CLI-currentness need work.

Issues:

- Uses legacy `gh copilot` extension flow (`module5-automation-scripting.md:80-84`) while Module 9 uses a different invalid flow.
- Unix-specific examples are presented as general React team automation:
  - `find`, `xargs`, `lsof`, `kill -9`
  - `ANALYZE=true` environment syntax in npm scripts, which fails on Windows without `cross-env`.
- `module5-automation-scripting.md:221-228` is fenced as `json` but is prompt prose.
- Several CI examples assume package scripts exist but the lab repo may not define them yet.

Fixes:

- Add macOS/Linux/Windows variants or use cross-platform Node scripts.
- Use `cross-env` where needed.
- Decide legacy vs current Copilot CLI path.
- Change prompt prose fences to `text`.

### Module 5 Instructor Notes

Status: Good instructor framing.

Issues:

- Same CLI/currentness issue.
- Module connections should account for Module 6 as the first lab.

### Module 6: Lab 1

Status: Needs correction before running.

Issues:

- Creates `Button`, `Input`, and `FormField`, but later modules assume `TextInput`, `Select`, `Checkbox`, `RadioGroup`, and `Textarea`.
- Adds Jest via agent prompt but does not pin exact dependency list or config expected to work with Vite React TS (`module6-lab1-scaffold-tests.md:181-185`, `221-238`).
- Does not add Storybook or `jest-axe`, which later modules require.
- Suggests path alias `"@/*" -> "src/*"` but does not show exact `tsconfig` syntax or bundler/Jest mapping.
- Tells students to approve `npm install` as safe (`module6-lab1-scaffold-tests.md:240`); network installs can still introduce supply-chain risk and should be reviewed.

Fixes:

- Make Lab 1 create the canonical component set used later.
- Add exact dependency and script setup.
- Add Storybook and `jest-axe` if they are required later.
- Include a final known-good `package.json`, `tsconfig`, and Jest/Storybook config reference.

### Module 6 Instructor Notes

Status: Helpful, but depends on corrected Lab 1.

Issues:

- Includes `rm -rf test-check` (`module6-instructor-notes.md:20`) without broader destructive-command warning.
- Focuses on Button while later modules expect TextInput/Checkbox/etc.

### Module 7: Refactor & Debug

Status: Coherent, but short and highly Copilot-specific.

Issues:

- Uses `git checkout --` as a normal workflow (`module7-refactor-debug.md:226`, `239`, `250`).
- Prompt examples depend on paths and files not guaranteed by corrected Lab 1 unless aligned.

Fixes:

- Replace with `git restore` guidance plus `git status` checks.
- Align file names with the canonical component set.

### Module 7 Instructor Notes

Status: Good facilitation.

Issues:

- `git reset --hard HEAD` appears as an option (`module7-instructor-notes.md:148`).
- Debug demos assume `#terminalLastCommand`; add ChatGPT fallback.

### Module 8: AI Quality Assurance

Status: Conceptually coherent.

Issues:

- Prompt blocks are mostly unlabeled and not directly runnable.
- Property-based testing and mutation testing are introduced, but dependencies/tooling (`fast-check`, mutation framework) are not installed in the lab repo.
- `BICEP` is introduced clearly, but it is a custom heuristic; consider defining it as a course-specific testing heuristic to avoid confusion with unrelated Bicep infrastructure tooling.

Fixes:

- Add install/setup commands for optional tools or mark them as conceptual.
- Add ChatGPT prompt equivalents.

### Module 8 Instructor Notes

Status: Good.

Issues:

- Depends on `#terminalLastCommand`.
- The flaky test example lacks imports by design, but if copied into code it is incomplete.

### Module 9: AIOps / CI/CD

Status: Needs major rewrite.

Issues:

- Invalid CLI package/auth commands (`module9-aiops-cicd.md:73-76`, `module9-instructor-notes.md:10`).
- CI uses Copilot CLI as an unattended reviewer/fixer without reliable documented setup.
- `gh copilot suggest` prompts receive large file contents through command substitution.
- JSON fence at `module9-aiops-cicd.md:228-239` is invalid JSON due comment line.
- Instructor note points to `github.com/actions/copilot` as future ecosystem (`module9-instructor-notes.md:175-176`); this should be verified or removed.

Fixes:

- Rewrite around standard GitHub Actions quality gates first.
- Move AI analysis to "optional/manual assistant workflow" unless using documented non-interactive current CLI.
- Replace invalid CLI commands.

### Module 10: Agents Foundations

Status: Good conceptual bridge.

Issues:

- Malformed inline HTML at `module10-agents-foundations.md:312`.
- JSON fences with comments at `module10-agents-foundations.md:388-403` and `537-576`.
- Prompt files/custom instructions need current preview/enablement notes.
- Custom slash commands like `/plan`, `/implement`, `/test`, `/review` are course-defined prompt files, but the learner may think they are built-in Copilot commands.

Fixes:

- Fix HTML.
- Use `jsonc` fences.
- Explicitly state which slash commands are custom prompt files created by the course.

### Module 10 Instructor Notes

Status: Good.

Issues:

- `module10-instructor-notes.md:106` says switch to Claude Sonnet. In a GitHub Copilot React course, mention this as a model option only if the Copilot UI exposes it in the target environment; otherwise generalize to "a stronger reasoning model".
- Mentions Copilot Workspace in `module10-instructor-notes.md:211`; verify product naming/status before delivery.

### Module 11: Agents Applied

Status: Good workflow design, but depends on missing repo features.

Issues:

- Requires `TextInput`, `Select`, `Checkbox`, stories, and `jest-axe`, none guaranteed by Lab 1.
- `.vscode/mcp.json` examples are fenced as JSON but include comments (`module11-agents-applied.md:361-375`, `399-410`).
- MCP server setup uses `npx -y` and external packages; this requires network and authentication that are not covered enough for a lab.
- The `jest-axe` TypeScript snippet is incomplete if copied into a new file because `render`, `Checkbox`, and test globals/imports are assumed (`module11-agents-applied.md:312-324`).

Fixes:

- Add prerequisites or move MCP to optional advanced section.
- Provide complete example test file or mark snippet as partial.
- Align component names with Lab 1.

### Module 11 Instructor Notes

Status: Strong facilitation, but not runnable until Lab 1 is fixed.

Issues:

- Pre-session checklist assumes components that Lab 1 does not create (`module11-instructor-notes.md:23`).
- `@workspace` and `#file` demos need ChatGPT equivalents.

### Module 12: Lab 2

Status: Good workflow lab design, but blocked by prerequisites.

Issues:

- Assumes `TextInput.tsx` exists and is canonical (`module12-lab2-component-pipeline.md:58-60`, `78`, `108`).
- Uses flat file paths for `PhoneInput` while Lab 1 uses component directories (`module12-lab2-component-pipeline.md:150-154`, `246-297`).
- Requires Storybook and `jest-axe`, but these are not set up by Lab 1 (`module12-lab2-component-pipeline.md:120-129`, `290`, `379`).
- Says diff should include exactly four files (`module12-lab2-component-pipeline.md:328`), but a folder-based component convention, index barrel, Storybook setup, test setup, or CSS file may legitimately change that.

Fixes:

- Align component pattern and paths.
- Add pre-lab setup for Storybook and `jest-axe`.
- Replace "exactly 4 files" with "expected files only; no unrelated existing components changed".

### Module 12 Instructor Notes

Status: Good if prerequisites are fixed.

Issues:

- Pre-lab checklist assumes missing components (`module12-instructor-notes.md:23`).
- Common issues include `jest-axe` not installed, which should be resolved before the lab (`module12-instructor-notes.md:137`).

### Module 13: Parallel Workflows & PR Automation

Status: Useful, but some Git guidance needs precision.

Issues:

- `git worktree add ../my-form-library-datepicker feature/date-picker` fails if `feature/date-picker` does not already exist (`module13-parallel-pr.md:121-124`). Use `git worktree add -b feature/date-picker ../my-form-library-datepicker`.
- Opening two VS Code windows on the same working directory is described as useful for parallel work (`module13-parallel-pr.md:70-83`), but two windows cannot be on different branches if they point to the same working tree. The warning acknowledges shared files, but the safer default should be worktrees.
- CI workflow includes Storybook build, but Storybook may not exist unless earlier fixed (`module13-parallel-pr.md:288`).

Fixes:

- Teach same-directory multi-window only for read-only or non-overlapping review.
- Teach worktrees as the default for write parallelism.
- Use `git worktree add -b`.

### Module 13 Instructor Notes

Status: Good.

Issues:

- Demo worktree command also omits `-b` (`module13-instructor-notes.md:26`, `65`).
- Requires PhoneInput branch from Lab 2; ensure Lab 2 creates consistent branch guidance.

### Module 14: Production Debt

Status: Strong production-oriented content.

Issues:

- Snippets are partial and not standalone; they need imports/context if used as code (`module14-production-debt.md:140-189`).
- ErrorBoundary component is introduced here, then Module 15 assumes it exists. Make the expected deliverable explicit.
- `npx eslint src/ --ext .tsx,.ts --max-warnings 0` may not match ESLint flat config conventions in newer ESLint versions (`module14-production-debt.md:279`).

Fixes:

- Mark snippets as partial or provide complete examples.
- Add a final "Module 14 required artifact" checklist including `ErrorBoundary`.
- Align ESLint commands with the actual generated config.

### Module 14 Instructor Notes

Status: Good.

Issues:

- Requires deliberate repo mutation before class. Add a reset script or branch instructions so instructors can return to clean state.
- Intentional issues reference `Select.tsx` and `TextInput.tsx`, again depending on missing Lab 1 components (`module14-instructor-notes.md:42-43`).

### Module 15: Lab 3 Sprint

Status: Good capstone concept, but too dependent on unresolved earlier issues.

Issues:

- Pre-lab assumptions include missing components and `ErrorBoundary` (`module15-instructor-notes.md:23-24`).
- `MultiFileUploadProps.value?` is optional while the lab says the component is controlled; optional `value` can lead to controlled/uncontrolled ambiguity (`module15-lab3-sprint.md:148-151`).
- Drag-and-drop zone uses `div role="button"` and hidden file input. This can be accessible if implemented carefully, but a real `<button>` or `<label>` pattern may be more robust (`module15-lab3-sprint.md:226-231`).
- Accepted file types are validated but the prompt does not explicitly require passing `accept` to the file input (`module15-lab3-sprint.md:187-193`, `223-231`).
- Storybook and `jest-axe` dependencies still depend on earlier setup.
- 45 minutes is tight for a production-ready multi-file upload with tests, error boundary, Storybook, PR writeup, and quality gates.

Fixes:

- Make `value: UploadedFile[]` required if controlled is mandatory.
- Add `accept={acceptedTypes?.join(',')}` requirement.
- Consider splitting implementation and hardening into two phases or extending the lab.

### Module 15 Instructor Notes

Status: Useful capstone facilitation.

Issues:

- Pre-lab checklist is blocked by previous course state issues.
- "No step-by-step prompts" framing conflicts slightly with the learner module, which does contain step prompts. Clarify that prompts are less prescriptive than earlier labs, not absent.

## ChatGPT-Runnable Conversion Requirements

To make this folder runnable on ChatGPT/Codex, add a short compatibility box to each module and lab.

Required patterns:

1. Repository context:
   - Copilot: `@workspace Analyze this project...`
   - ChatGPT/Codex: "Inspect the repository in the current workspace. Do not edit files yet. Produce `docs/repo-analysis.md`."

2. File context:
   - Copilot: `#file:src/components/TextInput.tsx`
   - ChatGPT/Codex: "Open `src/components/TextInput.tsx` and use it as context. If you cannot access files, ask me to paste it."

3. Terminal output:
   - Copilot: `#terminalLastCommand`
   - ChatGPT/Codex: "Here is the command and full output: ... Diagnose and propose the minimal fix."

4. Custom instructions:
   - Copilot: `.github/copilot-instructions.md`
   - ChatGPT/Codex: `AGENTS.md` plus optional `.github/copilot-instructions.md` if teaching both tools.

5. Slash commands:
   - Copilot: `/tests`, `/review`, `/implement`
   - ChatGPT/Codex: plain prompts such as "Generate tests", "Review the diff", "Implement only step 1".

6. Tool execution:
   - Copilot: Agent mode confirmation panel.
   - ChatGPT/Codex: ask the coding agent to run `npm test`, `npx tsc --noEmit`, etc., then review command output.

## Recommended Remediation Plan

### Phase 1: Fix the Course Backbone

1. Define the canonical `my-form-library` target state after Lab 1.
2. Update Lab 1 to create the exact components later modules use.
3. Add Storybook and `jest-axe` setup before Module 11.
4. Choose one component file structure and apply it across Modules 6, 11, 12, 14, and 15.
5. Add a starter repo URL or remove clone steps that point at placeholders.

### Phase 2: Fix Tooling Accuracy

1. Decide which Copilot CLI path is taught.
2. Rewrite Module 9 using verified current commands.
3. Mark Copilot prompt files and CLI features as preview where appropriate.
4. Add ChatGPT/Codex alternatives for all Copilot-specific syntax.

### Phase 3: Fix Code/Markdown Standards

1. Normalize headings to one H1 per file.
2. Convert invalid `json` fences to `jsonc` or `text`.
3. Convert prompt prose fences to `text`.
4. Fix malformed inline HTML and reduce HTML table dependency.
5. Add complete config examples for Jest, Storybook, ESLint, and path aliases.

### Phase 4: Instructor Delivery Hardening

1. Add pre-session repo setup scripts or checkpoints for each lab.
2. Add "known good final state" file trees after Labs 1 and 2.
3. Replace casual destructive Git recovery with safer alternatives.
4. Add time-box fallback paths for labs when students fall behind.

## Suggested Acceptance Criteria After Revision

The course should be considered ready when:

- A fresh student can run Module 6 from an empty folder and finish with the exact repo state expected by Modules 11, 12, and 15.
- `npm install`, `npm test -- --coverage`, `npx tsc --noEmit`, `npx eslint src --max-warnings 0`, and Storybook build all work in the generated repo.
- Every code fence labeled `json` parses as JSON.
- Every prompt example is labeled `text` unless it is actual code.
- Every Copilot-only prompt has a ChatGPT/Codex equivalent.
- Instructor notes reference the same components, paths, dependencies, and timings as the learner modules.
- Module 9 commands match the selected current Copilot CLI flow.

## Quick Issue Checklist

- [ ] Replace placeholder repo URL in Module 1.
- [ ] Fix Module 3/4/5 transition language.
- [ ] Decide Lab 1 component set and update all later references.
- [ ] Add Storybook setup.
- [ ] Add `jest-axe` setup.
- [ ] Standardize component directory convention.
- [ ] Replace invalid Module 9 CLI commands.
- [ ] Rewrite Copilot-in-CI examples or mark them optional/manual.
- [ ] Add ChatGPT/Codex prompt equivalents.
- [ ] Normalize Markdown headings.
- [ ] Convert invalid JSON fences.
- [ ] Fix malformed HTML in Module 10.
- [ ] Replace unsafe Git recovery guidance.
- [ ] Add final repo state checklists after each lab.
