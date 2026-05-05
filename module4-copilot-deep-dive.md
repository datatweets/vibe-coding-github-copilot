<div style="text-align:center; padding: 20px 0;">

<span style="font-size:14px; color:#666666; font-weight:bold; letter-spacing:2px;">MODULE 4</span>

# <span style="color:#0D47A1;">GitHub Copilot Deep Dive: Chat, Agent Mode & VS Code Integration</span>

<hr style="border: 3px solid #1A73E8; width:80%;">

</div>

<table style="width:100%; border-collapse:collapse;">
<tr>
<td style="background:#E3F2FD; text-align:center; padding:10px; border:1px solid #BBDEFB; width:25%;"><span style="font-size:12px; color:#666;">Duration</span><br><strong style="color:#0D47A1;">45 min</strong></td>
<td style="background:#E3F2FD; text-align:center; padding:10px; border:1px solid #BBDEFB; width:25%;"><span style="font-size:12px; color:#666;">Format</span><br><strong style="color:#0D47A1;">Lecture + Demo</strong></td>
<td style="background:#E3F2FD; text-align:center; padding:10px; border:1px solid #BBDEFB; width:25%;"><span style="font-size:12px; color:#666;">Audience</span><br><strong style="color:#0D47A1;">React Developers</strong></td>
<td style="background:#E3F2FD; text-align:center; padding:10px; border:1px solid #BBDEFB; width:25%;"><span style="font-size:12px; color:#666;">Day / Position</span><br><strong style="color:#0D47A1;">Day 1 / Fourth</strong></td>
</tr>
</table>

---

## <span style="color:#1A73E8;">LEARNING OBJECTIVES</span>

By the end of this module, participants will be able to:

1. Navigate GitHub Copilot's three surfaces — inline completions, Inline Chat, and the Copilot Chat panel — and choose the right surface for each React development task
2. Use Copilot Chat's built-in slash commands (`/explain`, `/fix`, `/tests`, `/doc`) and context variables (`#file:`, `@workspace`, `#terminalLastCommand`) to give Copilot precise, relevant context
3. Work in Agent mode: request a plan before execution, review the task list, and accept or reject file changes in the Copilot Edits panel
4. Manage changes safely using the Copilot Edits accept/reject workflow, undo for inline suggestions, and git commits as a reliable safety net
5. Configure GitHub Copilot through VS Code settings, `.github/copilot-instructions.md`, and custom prompt files (`.github/prompts/`) to standardize team workflows

---

## <span style="color:#1A73E8;">SESSION TIMING BREAKDOWN</span>

<table style="width:100%; border-collapse:collapse;">
<tr><td style="background:#00695C; color:white; padding:8px 14px; width:120px; font-weight:bold; font-size:13px;">0:00 – 0:10</td><td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Section 1: VS Code-First Workflow — Copilot's Three Surfaces</td></tr>
<tr><td colspan="2" style="height:4px;"></td></tr>
<tr><td style="background:#00695C; color:white; padding:8px 14px; font-weight:bold; font-size:13px;">0:10 – 0:20</td><td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Section 2: Chat Commands & Context Variables — Your Precision Tools</td></tr>
<tr><td colspan="2" style="height:4px;"></td></tr>
<tr><td style="background:#00695C; color:white; padding:8px 14px; font-weight:bold; font-size:13px;">0:20 – 0:30</td><td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Section 3: Agent Mode — Multi-File Autonomous Development</td></tr>
<tr><td colspan="2" style="height:4px;"></td></tr>
<tr><td style="background:#00695C; color:white; padding:8px 14px; font-weight:bold; font-size:13px;">0:30 – 0:37</td><td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Section 4: Change Management — Copilot Edits, Undo, and Git Safety</td></tr>
<tr><td colspan="2" style="height:4px;"></td></tr>
<tr><td style="background:#00695C; color:white; padding:8px 14px; font-weight:bold; font-size:13px;">0:37 – 0:42</td><td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Section 5: Configuration — Settings, Instructions, and Custom Prompts</td></tr>
<tr><td colspan="2" style="height:4px;"></td></tr>
<tr><td style="background:#00695C; color:white; padding:8px 14px; font-weight:bold; font-size:13px;">0:42 – 0:45</td><td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Wrap-Up: Quick Reference & Transition to Module 5</td></tr>
</table>

---

<table style="width:100%; border-collapse:collapse;"><tr><td style="background:#00695C; color:white; padding:8px 16px; font-weight:bold;">0:00 – 0:10</td><td style="background:#E0F2F1; padding:8px 16px; color:#00695C; font-weight:bold; font-size:16px;">SECTION 1: VS Code-First Workflow — Copilot's Three Surfaces</td></tr></table>

## <span style="color:#0D47A1;">1. VS Code-First Workflow: Copilot's Three Surfaces</span>

### <span style="color:#0D47A1;">1.1  Why VS Code-First?</span>

GitHub Copilot was designed as a native VS Code tool. Unlike separate chat interfaces or browser-based AI assistants, Copilot lives where you write code — in your editor. This means it always has access to what you're looking at, what TypeScript is flagging, and what your terminal just output.

<table style="width:100%; border-collapse:collapse;">
<tr><td style="background:#0D47A1; color:white; padding:10px 12px; border:1px solid #BBDEFB; font-weight:bold;">VS Code Advantage</td><td style="background:#0D47A1; color:white; padding:10px 12px; border:1px solid #BBDEFB; font-weight:bold;">Why It Matters for React Developers</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><strong>TypeScript diagnostic integration</strong></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Type errors, missing imports, and ESLint violations are visible to Copilot — it can suggest fixes before you even ask</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><strong>Full project awareness</strong></td><td style="padding:10px 12px; border:1px solid #CCC;"><code>@workspace</code> lets Copilot search and reason across all project files — it knows your hooks, components, and types</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><strong>Terminal integration</strong></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><code>#terminalLastCommand</code> brings test output, build errors, and CLI results directly into Chat without copy-paste</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><strong>No context-switching</strong></td><td style="padding:10px 12px; border:1px solid #CCC;">Chat, edit, and review happen in the same window — your React component and the AI conversation are side by side</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><strong>Git integration</strong></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Copilot can generate commit messages, suggest PR descriptions, and understand git blame context</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><strong>Instructions file aware</strong></td><td style="padding:10px 12px; border:1px solid #CCC;">Automatically reads <code>.github/copilot-instructions.md</code> for every Chat session — your React standards are always in context</td></tr>
</table>

### <span style="color:#0D47A1;">1.2  The Three Copilot Surfaces</span>

GitHub Copilot has three distinct surfaces, each optimized for a different task scope. Knowing which to use is one of the highest-leverage skills in this course.

<table style="width:100%; border-collapse:collapse;">
<tr><td style="background:#1A73E8; color:white; padding:10px 12px; border:1px solid #BBDEFB; font-weight:bold; width:22%;">Surface</td><td style="background:#1A73E8; color:white; padding:10px 12px; border:1px solid #BBDEFB; font-weight:bold; width:22%;">How to Open</td><td style="background:#1A73E8; color:white; padding:10px 12px; border:1px solid #BBDEFB; font-weight:bold; width:30%;">Best For</td><td style="background:#1A73E8; color:white; padding:10px 12px; border:1px solid #BBDEFB; font-weight:bold; width:26%;">Limitation</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><strong>Inline Completion</strong><br><em style="font-size:11px;">(ghost text)</em></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Appears automatically as you type</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Completing JSX props, finishing hook parameters, boilerplate repetition, import statements</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">No explicit chat — only what it can infer from your cursor context and open files</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><strong>Inline Chat</strong></td><td style="padding:10px 12px; border:1px solid #CCC;"><kbd>Ctrl+I</kbd> / <kbd>Cmd+I</kbd></td><td style="padding:10px 12px; border:1px solid #CCC;">Refactoring a specific function, adding a prop, fixing a single component bug, explaining a JSX block</td><td style="padding:10px 12px; border:1px solid #CCC;">Scoped to the active file — limited cross-file awareness</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><strong>Copilot Chat Panel</strong></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><kbd>Ctrl+Alt+I</kbd> / <kbd>Cmd+Alt+I</kbd></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Designing new hooks/components, debugging, architecture questions, generating tests with context, multi-turn conversations</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">In Chat mode (not Agent): you apply suggestions manually — Copilot doesn't edit files directly</td></tr>
</table>

<table style="width:100%; border-collapse:collapse;"><tr><td style="border-left:5px solid #1A73E8; background:#E3F2FD; padding:14px 18px;"><strong style="color:#0D47A1;">⭐ KEY POINT:</strong> <span style="color:#0D47A1;">Always start Copilot Chat from a project folder that has <code>.github/copilot-instructions.md</code> — this file loads automatically and ensures Copilot knows your React version, component standards, and testing conventions before you type your first message.</span></td></tr></table>

### <span style="color:#0D47A1;">1.3  Essential Keyboard Shortcuts</span>

<table style="width:100%; border-collapse:collapse;">
<tr><td style="background:#2E7D32; color:white; padding:10px 12px; border:1px solid #A5D6A7; font-weight:bold;">Shortcut</td><td style="background:#2E7D32; color:white; padding:10px 12px; border:1px solid #A5D6A7; font-weight:bold;">Action</td><td style="background:#2E7D32; color:white; padding:10px 12px; border:1px solid #A5D6A7; font-weight:bold;">When to Use</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><strong>Tab</strong></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Accept inline suggestion</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Ghost text looks correct — accept it</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><strong>Esc</strong></td><td style="padding:10px 12px; border:1px solid #CCC;">Dismiss inline suggestion</td><td style="padding:10px 12px; border:1px solid #CCC;">Ghost text is wrong — dismiss and keep typing your intent</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><strong>Alt+] / Option+]</strong></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Next inline suggestion</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Current suggestion isn't quite right — cycle to alternatives</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><strong>Alt+[ / Option+[</strong></td><td style="padding:10px 12px; border:1px solid #CCC;">Previous inline suggestion</td><td style="padding:10px 12px; border:1px solid #CCC;">Go back to an earlier suggestion option</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><strong>Ctrl+I / Cmd+I</strong></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Open Inline Chat</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Ask Copilot about or to modify the selected code block</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><strong>Ctrl+Alt+I / Cmd+Alt+I</strong></td><td style="padding:10px 12px; border:1px solid #CCC;">Open / focus Copilot Chat panel</td><td style="padding:10px 12px; border:1px solid #CCC;">Start a multi-turn conversation with context variables</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><strong>Ctrl+Z / Cmd+Z</strong></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Undo the last accepted suggestion</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Accepted a suggestion with Tab but it broke something — undo immediately</td></tr>
</table>

### <span style="color:#0D47A1;">1.4  Continuing and Managing Chat Sessions</span>

Copilot Chat is persistent — your conversation stays in the panel and accumulates context across messages. Manage it strategically:

<table style="width:100%; border-collapse:collapse;">
<tr><td style="background:#0D47A1; color:white; padding:10px 12px; border:1px solid #BBDEFB; font-weight:bold;">Action</td><td style="background:#0D47A1; color:white; padding:10px 12px; border:1px solid #BBDEFB; font-weight:bold;">How</td><td style="background:#0D47A1; color:white; padding:10px 12px; border:1px solid #BBDEFB; font-weight:bold;">When</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><strong>Continue current session</strong></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Just keep typing — Copilot Chat is persistent</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Same feature, related refinements</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><strong>Start a new chat</strong></td><td style="padding:10px 12px; border:1px solid #CCC;">Click <strong>+</strong> (New Chat) icon in the Chat panel toolbar</td><td style="padding:10px 12px; border:1px solid #CCC;">Switching to a completely different task; context is stale</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><strong>View chat history</strong></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Click the chat history icon in the Chat panel toolbar</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Resume a previous conversation from earlier in the day</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><strong>Ask workspace-wide question</strong></td><td style="padding:10px 12px; border:1px solid #CCC;">Start a new chat, prefix with <code>@workspace</code></td><td style="padding:10px 12px; border:1px solid #CCC;">Exploring unfamiliar codebases, finding where things are</td></tr>
</table>

<table style="width:100%; border-collapse:collapse;"><tr><td style="border-left:5px solid #1A73E8; background:#E3F2FD; padding:14px 18px;"><strong style="color:#0D47A1;">⭐ KEY POINT:</strong> <span style="color:#0D47A1;">Copilot Chat accumulates context with each message in a session. New Chat is your reset button — use it between unrelated tasks to prevent context from one feature confusing Copilot's suggestions for another. This maps directly to the context management practice from Module 3's "Context-Reset + Refine" pattern.</span></td></tr></table>

---

<table style="width:100%; border-collapse:collapse;"><tr><td style="background:#00695C; color:white; padding:8px 16px; font-weight:bold;">0:10 – 0:20</td><td style="background:#E0F2F1; padding:8px 16px; color:#00695C; font-weight:bold; font-size:16px;">SECTION 2: Chat Commands & Context Variables — Your Precision Tools</td></tr></table>

## <span style="color:#0D47A1;">2. Chat Commands & Context Variables: Your Precision Tools</span>

### <span style="color:#0D47A1;">2.1  Built-in Slash Commands</span>

Copilot Chat has built-in slash commands that trigger specialized behaviors. These are not sent to the AI as natural language — they're direct instructions to the Copilot application, just like CLI slash commands. Type `/` in the Chat input to see the full list.

<table style="width:100%; border-collapse:collapse;">
<tr><td style="background:#1A73E8; color:white; padding:10px 12px; border:1px solid #BBDEFB; font-weight:bold; width:18%;">Command</td><td style="background:#1A73E8; color:white; padding:10px 12px; border:1px solid #BBDEFB; font-weight:bold; width:40%;">What It Does</td><td style="background:#1A73E8; color:white; padding:10px 12px; border:1px solid #BBDEFB; font-weight:bold; width:42%;">React Example Usage</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><strong>/explain</strong></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Explains the selected code or a referenced file in plain English</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Select a complex <code>useReducer</code> implementation, press Ctrl+I, type <code>/explain</code></td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><strong>/fix</strong></td><td style="padding:10px 12px; border:1px solid #CCC;">Analyzes and fixes errors in selected code; integrates with VS Code Problems panel</td><td style="padding:10px 12px; border:1px solid #CCC;">Select the red-squiggled TypeScript error, press Ctrl+I, type <code>/fix</code></td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><strong>/tests</strong></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Generates unit tests for the selected code using the testing framework it detects in your project</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Select a hook or component, Ctrl+I → <code>/tests</code> to generate RTL tests automatically</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><strong>/doc</strong></td><td style="padding:10px 12px; border:1px solid #CCC;">Adds JSDoc comments to the selected function, component, or interface</td><td style="padding:10px 12px; border:1px solid #CCC;">Select an exported function, Ctrl+I → <code>/doc</code> to generate JSDoc with params and return type</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><strong>/new</strong></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Scaffolds new files, components, or project structures (Agent mode required)</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><code>/new React component named ProductCard with TypeScript props interface</code></td></tr>
</table>

<table style="width:100%; border-collapse:collapse;"><tr><td style="border-left:5px solid #1A73E8; background:#E3F2FD; padding:14px 18px;"><strong style="color:#0D47A1;">⭐ KEY POINT:</strong> <span style="color:#0D47A1;">The three most-used slash commands for daily React development are <strong>/fix</strong> (fastest path from TypeScript error to solution), <strong>/tests</strong> (generates RTL tests without writing test scaffolding manually), and <strong>/explain</strong> (understand unfamiliar code before modifying it). These three solve 80% of common React developer friction points.</span></td></tr></table>

### <span style="color:#0D47A1;">2.2  Context Variables — Giving Copilot the Right Information</span>

Context variables are the most powerful feature in Copilot Chat. They let you precisely control what information Copilot has before generating a response. Always be explicit — never assume Copilot "knows" something unless you've referenced it.

<table style="width:100%; border-collapse:collapse;">
<tr><td style="background:#0D47A1; color:white; padding:10px 12px; border:1px solid #BBDEFB; font-weight:bold; width:28%;">Context Variable</td><td style="background:#0D47A1; color:white; padding:10px 12px; border:1px solid #BBDEFB; font-weight:bold; width:35%;">What It Provides</td><td style="background:#0D47A1; color:white; padding:10px 12px; border:1px solid #BBDEFB; font-weight:bold; width:37%;">React Use Case</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><code><strong>#file:path/to/File.tsx</strong></code></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Full content of a specific file</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">"Review #file:src/hooks/useCart.ts and add error handling for network failures"</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><code><strong>@workspace</strong></code></td><td style="padding:10px 12px; border:1px solid #CCC;">Searches across ALL files in the project; Copilot finds relevant files itself</td><td style="padding:10px 12px; border:1px solid #CCC;">"@workspace where is the authentication logic currently handled?"</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><code><strong>#selection</strong></code></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Text currently selected in the active editor</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Select 3 lines of JSX → "Refactor #selection to extract it as a named component"</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><code><strong>#terminalLastCommand</strong></code></td><td style="padding:10px 12px; border:1px solid #CCC;">Output of the last command run in the VS Code terminal</td><td style="padding:10px 12px; border:1px solid #CCC;">Run <code>npm test</code>, see the failure → "Fix the test failures shown in #terminalLastCommand"</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><code><strong>#editor</strong></code></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Full content of the currently active editor tab</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">"Review #editor for missing ARIA attributes"</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><code><strong>@vscode</strong></code></td><td style="padding:10px 12px; border:1px solid #CCC;">VS Code state, settings, and available commands</td><td style="padding:10px 12px; border:1px solid #CCC;">"@vscode how do I configure the TypeScript path aliases for this project?"</td></tr>
</table>

**Context variable usage patterns in React development:**

```text
# Debugging a TypeScript error with full file context
"The TypeScript error in #file:src/components/DataTable.tsx on line 47 says
'Type ProductFilter is not assignable to FilterState'. Explain why
and show me the fix."

# Cross-file consistency check
"Compare the API error handling in #file:src/hooks/useProducts.ts
and #file:src/hooks/useCart.ts — are they consistent?
If not, unify them to the pattern in useProducts.ts."

# Test failure from terminal output
"#terminalLastCommand shows 3 failing tests. Fix each failing test
in #file:src/components/ProductCard.test.tsx — don't change
the component itself, only the tests."

# Workspace-wide architecture question
"@workspace is there any component that calls fetch() directly
instead of using our API service layer in src/api/? List all occurrences."
```

### <span style="color:#0D47A1;">2.3  Custom Prompt Files — Your Team's Reusable Commands</span>

Just like `.claude/commands/` in a Claude Code project, GitHub Copilot supports reusable prompt files in `.github/prompts/`. These are Markdown files with `.prompt.md` extensions that become team-shared prompts — checked into git and shared automatically.

```markdown
<!-- .github/prompts/review-component.prompt.md -->
Review the React component at #file:${input:filePath} for:

1. TypeScript completeness — are all props typed, no `any`?
2. Accessibility — ARIA roles, keyboard navigation, screen-reader labels
3. Performance — unnecessary re-renders, missing useCallback/useMemo
4. Test coverage — are happy path, error state, and empty state tested?
5. copilot-instructions.md compliance — named export, functional component, Tailwind only

Provide a numbered list of issues sorted by severity (Critical / Warning / Suggestion).
```

```markdown
<!-- .github/prompts/add-tests.prompt.md -->
Generate RTL tests for #file:${input:componentPath}.

Rules:
- Use describe/it block structure
- Query with getByRole, getByLabelText, getByText only — no getByTestId
- Mock all API calls using MSW handlers in src/mocks/handlers.ts
- Cover: renders successfully, loading state, error state, user interaction
- Follow the test structure in #file:src/components/ProductCard.test.tsx
```

```bash
# To use a custom prompt file: In Copilot Chat, type:
> /review-component
# Then provide the file path when prompted
```

<table style="width:100%; border-collapse:collapse;"><tr><td style="border-left:5px solid #1A73E8; background:#E3F2FD; padding:14px 18px;"><strong style="color:#0D47A1;">⭐ KEY POINT:</strong> <span style="color:#0D47A1;">Custom prompt files are the team's shared slash commands. Instead of every developer writing the same "review this component against our standards" prompt from scratch, create it once in <code>.github/prompts/</code>, commit it, and every team member gets the same consistent, high-quality review — every time.</span></td></tr></table>

---

<table style="width:100%; border-collapse:collapse;"><tr><td style="background:#00695C; color:white; padding:8px 16px; font-weight:bold;">0:20 – 0:30</td><td style="background:#E0F2F1; padding:8px 16px; color:#00695C; font-weight:bold; font-size:16px;">SECTION 3: Agent Mode — Multi-File Autonomous Development</td></tr></table>

## <span style="color:#0D47A1;">3. Agent Mode: Multi-File Autonomous Development</span>

### <span style="color:#0D47A1;">3.1  What Is Agent Mode?</span>

Agent mode elevates Copilot Chat from a suggestion assistant to an autonomous Copilot that can:

- **Read** files across your entire project using `@workspace`
- **Write** and **edit** multiple files simultaneously
- **Execute** terminal commands (npm install, npm test, tsc --noEmit)
- **Create** new files and directory structures
- **Iterate** on its own output based on test results and TypeScript errors

This is the mode for multi-file React feature work — scaffolding entire features, large-scale refactors, and test generation across a whole component library.

<table style="width:100%; border-collapse:collapse;">
<tr><td style="background:#1A73E8; color:white; padding:10px 12px; border:1px solid #BBDEFB; font-weight:bold;">Chat Mode</td><td style="background:#1A73E8; color:white; padding:10px 12px; border:1px solid #BBDEFB; font-weight:bold;">Agent Mode</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Suggests code — you apply changes manually</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Writes, edits, and creates files autonomously</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;">One file at a time (with <code>#file:</code>)</td><td style="padding:10px 12px; border:1px solid #CCC;">Works across unlimited files in one session</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Can't run your tests or see their output</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Runs <code>npm test</code>, reads output, fixes failures</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;">Good for: design, Q&A, single file edits</td><td style="padding:10px 12px; border:1px solid #CCC;">Good for: feature scaffolding, refactors, test generation</td></tr>
</table>

### <span style="color:#0D47A1;">3.2  Starting an Agent Mode Session</span>

```text
1. Open Copilot Chat panel (Ctrl+Alt+I / Cmd+Alt+I)
2. In the Chat input, click the mode dropdown (bottom-left of input area)
3. Select "Agent" from the dropdown
4. The input prompt now shows "@agent" or an agent indicator
5. Type your multi-file task and press Enter
```

<table style="width:100%; border-collapse:collapse;"><tr><td style="border-left:5px solid #C62828; background:#FFEBEE; padding:14px 18px; border:1px solid #EF9A9A;"><strong style="color:#C62828;">⚠️ WARNING:</strong> <span style="color:#C62828;">Agent mode can modify many files at once. Always commit your current work to git before starting a significant Agent mode session. Commits are your safety net — see Section 4 for the full change management workflow.</span></td></tr></table>

### <span style="color:#0D47A1;">3.3  The Plan-Before-Execute Pattern</span>

For any Agent mode task touching three or more files, always request a plan first. This is the most important Agent mode best practice:

```text
# Step 1: Ask Agent to plan BEFORE it writes any code
"@agent I need to add a global notification system with a useNotification
hook and a NotificationBanner component. Before writing any code:

1. List every file you will create
2. List every file you will modify and describe each change
3. Identify any components that may be affected by this addition
4. Describe the state shape for the notification system

Wait for my approval before making any changes."

# [Review the plan — correct any misunderstandings]

# Step 2: Approve and start execution
"Approved. Proceed. After creating each file, show me what you wrote
before moving to the next file."
```

This plan-first pattern prevents the most expensive Agent mode failure mode: Agent writes 8 files based on a misunderstanding of your intent, and you have to reject everything and start over.

### <span style="color:#0D47A1;">3.4  Agent Mode Workflow for React Features</span>

<table style="width:100%; border-collapse:collapse;">
<tr><td style="background:#00695C; color:white; padding:10px 12px; border:1px solid #80CBC4; font-weight:bold;">Step</td><td style="background:#00695C; color:white; padding:10px 12px; border:1px solid #80CBC4; font-weight:bold;">What Happens</td><td style="background:#00695C; color:white; padding:10px 12px; border:1px solid #80CBC4; font-weight:bold;">Your Role</td></tr>
<tr><td style="background:#E0F2F1; padding:10px 12px; border:1px solid #CCC;"><strong>1. Task description</strong></td><td style="background:#E0F2F1; padding:10px 12px; border:1px solid #CCC;">You describe the feature or task</td><td style="background:#E0F2F1; padding:10px 12px; border:1px solid #CCC;">Be specific — include the folder structure, React version, and any reference files</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><strong>2. Planning (if requested)</strong></td><td style="padding:10px 12px; border:1px solid #CCC;">Agent lists files it will touch and describes changes</td><td style="padding:10px 12px; border:1px solid #CCC;">Review the plan carefully — this is your best chance to redirect before any code is written</td></tr>
<tr><td style="background:#E0F2F1; padding:10px 12px; border:1px solid #CCC;"><strong>3. Execution</strong></td><td style="background:#E0F2F1; padding:10px 12px; border:1px solid #CCC;">Agent reads existing files, writes new ones, runs terminal commands</td><td style="background:#E0F2F1; padding:10px 12px; border:1px solid #CCC;">Watch the Copilot Edits panel — changes appear in real time</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><strong>4. Terminal permission</strong></td><td style="padding:10px 12px; border:1px solid #CCC;">Agent asks before running any terminal command</td><td style="padding:10px 12px; border:1px solid #CCC;">Review the command — approve safe ones (npm test, tsc), deny unexpected ones</td></tr>
<tr><td style="background:#E0F2F1; padding:10px 12px; border:1px solid #CCC;"><strong>5. Self-correction</strong></td><td style="background:#E0F2F1; padding:10px 12px; border:1px solid #CCC;">If tests fail or TypeScript errors appear, Agent iterates to fix them</td><td style="background:#E0F2F1; padding:10px 12px; border:1px solid #CCC;">Monitor — intervene if Agent is iterating in circles (stop and redirect)</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><strong>6. Review</strong></td><td style="padding:10px 12px; border:1px solid #CCC;">All changes appear in Copilot Edits for accept/reject</td><td style="padding:10px 12px; border:1px solid #CCC;">Review every changed file — accept good changes, reject others</td></tr>
</table>

**Effective Agent mode prompts for React feature development:**

```text
# New feature scaffold — explicit about structure and references
"@agent Scaffold a product search feature with these files:
- src/types/search.ts (SearchQuery, SearchResult interfaces)
- src/api/searchApi.ts (fetchProducts async function using fetchClient in #file:src/api/client.ts)
- src/hooks/useProductSearch.ts (React Query hook wrapping fetchProducts)
- src/components/SearchBar.tsx (controlled input component)
- src/components/SearchResults.tsx (renders a grid of ProductCard from #file:src/components/ProductCard.tsx)

Follow all standards in #file:.github/copilot-instructions.md"

# Large-scale refactor — with explicit safe constraint
"@agent Migrate all components in src/components/ from
using the old useStore hook to the new Zustand store in
#file:src/stores/appStore.ts.

Plan step 1: list every component that currently imports useStore.
Don't modify any files until I approve the list."

# Test generation with standards reference
"@agent Generate Jest + RTL tests for every component in
src/components/ that doesn't have a .test.tsx file.
Follow the test patterns in #file:src/components/ProductCard.test.tsx.
Use MSW for API mocking. Run npm test after each file and fix failures."
```

<table style="width:100%; border-collapse:collapse;"><tr><td style="border-left:5px solid #1A73E8; background:#E3F2FD; padding:14px 18px;"><strong style="color:#0D47A1;">⭐ KEY POINT:</strong> <span style="color:#0D47A1;">Agent mode's terminal execution is its killer feature for React development: Agent can run <code>npm test</code> after writing test files and fix failing tests on its own. This turns multi-file test generation from a 2-hour manual task into a 15-minute supervised session. Always review the final tests for correctness before committing.</span></td></tr></table>

---

<table style="width:100%; border-collapse:collapse;"><tr><td style="background:#00695C; color:white; padding:8px 16px; font-weight:bold;">0:30 – 0:37</td><td style="background:#E0F2F1; padding:8px 16px; color:#00695C; font-weight:bold; font-size:16px;">SECTION 4: Change Management — Copilot Edits, Undo, and Git Safety</td></tr></table>

## <span style="color:#0D47A1;">4. Change Management: Copilot Edits, Undo, and Git Safety</span>

### <span style="color:#0D47A1;">4.1  Copilot Edits — Your Change Review Interface</span>

When Agent mode (or a Copilot Edits session) modifies files, every change appears in the **Copilot Edits panel** — a dedicated diff view where you review and accept or reject changes file by file.

<table style="width:100%; border-collapse:collapse;">
<tr><td style="background:#2E7D32; color:white; padding:10px 12px; border:1px solid #A5D6A7; font-weight:bold;">Feature</td><td style="background:#2E7D32; color:white; padding:10px 12px; border:1px solid #A5D6A7; font-weight:bold;">How It Works</td></tr>
<tr><td style="background:#E8F5E9; padding:10px 12px; border:1px solid #CCC;"><strong>File-level review</strong></td><td style="background:#E8F5E9; padding:10px 12px; border:1px solid #CCC;">Each modified file shows as a diff — green for additions, red for removals — in the Copilot Edits panel</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><strong>Accept / Reject per file</strong></td><td style="padding:10px 12px; border:1px solid #CCC;">Click ✓ (Accept) or ✗ (Reject) per file independently — accept the good files, reject the problematic ones</td></tr>
<tr><td style="background:#E8F5E9; padding:10px 12px; border:1px solid #CCC;"><strong>Accept All / Reject All</strong></td><td style="background:#E8F5E9; padding:10px 12px; border:1px solid #CCC;">Bulk action buttons at the top of the Copilot Edits panel — use "Accept All" only after reviewing each file</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><strong>Live updates</strong></td><td style="padding:10px 12px; border:1px solid #CCC;">As Agent writes files, they appear in Copilot Edits in real time — you can review while Agent is still working</td></tr>
<tr><td style="background:#E8F5E9; padding:10px 12px; border:1px solid #CCC;"><strong>VS Code Problems integration</strong></td><td style="background:#E8F5E9; padding:10px 12px; border:1px solid #CCC;">TypeScript errors and ESLint warnings from accepted changes appear in the Problems panel immediately</td></tr>
</table>

<table style="width:100%; border-collapse:collapse;"><tr><td style="border-left:5px solid #C62828; background:#FFEBEE; padding:14px 18px; border:1px solid #EF9A9A;"><strong style="color:#C62828;">⚠️ WARNING:</strong> <span style="color:#C62828;">Never click "Accept All" without reading the diffs first — especially in Agent mode sessions that touched many files. Agent mode occasionally modifies files you didn't ask it to. Review every file before accepting, particularly test files and configuration files.</span></td></tr></table>

### <span style="color:#0D47A1;">4.2  Undo for Inline Suggestions</span>

For inline completions accepted with Tab, the undo experience is simpler:

```text
# In editor — after accepting an inline suggestion with Tab:
Ctrl+Z / Cmd+Z  →  Undoes the accepted suggestion (standard editor undo)

# This works immediately after accepting, or can be applied
# multiple times to step back through several accepted suggestions.

# Best practice: Review the suggestion before pressing Tab.
# The Alt+] / Option+] shortcut lets you cycle through alternatives
# without accepting any — find the right one BEFORE pressing Tab.
```

### <span style="color:#0D47A1;">4.3  Change Management Strategies</span>

<table style="width:100%; border-collapse:collapse;">
<tr><td style="background:#00695C; color:white; padding:10px 12px; border:1px solid #80CBC4; font-weight:bold;">Scenario</td><td style="background:#00695C; color:white; padding:10px 12px; border:1px solid #80CBC4; font-weight:bold;">Action</td><td style="background:#00695C; color:white; padding:10px 12px; border:1px solid #80CBC4; font-weight:bold;">Why</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><strong>Agent's overall approach was wrong</strong></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Reject All in Copilot Edits, then start new chat with corrected task description</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Full reset — don't iterate on a wrong foundation</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><strong>Some files good, some wrong</strong></td><td style="padding:10px 12px; border:1px solid #CCC;">Accept correct files individually, reject the problematic ones, refine only the rejected files in a follow-up prompt</td><td style="padding:10px 12px; border:1px solid #CCC;">Keep good work, fix targeted issues</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><strong>Want to try an alternative approach</strong></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Reject All, start new chat, describe the alternative approach explicitly</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Clean slate for the new direction</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><strong>Accepted changes with TypeScript errors</strong></td><td style="padding:10px 12px; border:1px solid #CCC;">Open Problems panel, select all errors, use Ctrl+I → <code>/fix</code> on each affected file</td><td style="padding:10px 12px; border:1px solid #CCC;">Fix type errors before they cascade into other files</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><strong>Agent changed files you didn't ask it to</strong></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Use <code>git diff</code> to review all changes, use <code>git restore path/to/file</code> to restore individual files</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Git is the true safety net — review everything</td></tr>
</table>

### <span style="color:#0D47A1;">4.4  Git as Your Primary Safety Net</span>

Unlike systems with built-in automatic checkpointing, GitHub Copilot's safety net is git. Make it routine:

```bash
# BEFORE any significant Agent mode session:
git add -A && git commit -m "WIP: checkpoint before Copilot Agent session"

# or use a feature branch:
git checkout -b feature/add-search-copilot-session

# AFTER reviewing and accepting Agent mode changes:
git diff --staged                  # Review exactly what changed
npm test                           # Confirm tests still pass
tsc --noEmit                       # Confirm no TypeScript errors
git add -A && git commit -m "feat: add product search (Copilot-assisted)"
```

<table style="width:100%; border-collapse:collapse;"><tr><td style="border-left:5px solid #2E7D32; background:#E8F5E9; padding:14px 18px; border:1px solid #A5D6A7;"><strong style="color:#2E7D32;">✅ PRE-AGENT MODE CHECKLIST</strong><ul style="color:#333; margin:8px 0; padding-left:20px;"><li>git commit or stash any current WIP work</li><li>Confirm you're on a feature branch, not <code>main</code></li><li>For sessions touching 3+ files: request a plan first ("list all files before writing")</li><li>For sessions with test execution: verify npm test passes before starting</li><li>After Agent completes: review Copilot Edits diffs before Accept All</li><li>After accepting: run <code>npm test</code> and <code>tsc --noEmit</code> before committing</li></ul></td></tr></table>

<table style="width:100%; border-collapse:collapse;"><tr><td style="border-left:5px solid #1A73E8; background:#E3F2FD; padding:14px 18px;"><strong style="color:#0D47A1;">⭐ KEY POINT:</strong> <span style="color:#0D47A1;">The Copilot Edits accept/reject workflow combined with git commits gives you two layers of protection. Copilot Edits for immediate "is this the right approach?" decisions. Git for "I accepted everything and it broke things" recovery. Always have both layers in place before significant Agent sessions.</span></td></tr></table>

---

<table style="width:100%; border-collapse:collapse;"><tr><td style="background:#00695C; color:white; padding:8px 16px; font-weight:bold;">0:37 – 0:42</td><td style="background:#E0F2F1; padding:8px 16px; color:#00695C; font-weight:bold; font-size:16px;">SECTION 5: Configuration — Settings, Instructions, and Custom Prompts</td></tr></table>

## <span style="color:#0D47A1;">5. Configuration: Settings, Instructions, and Custom Prompts</span>

### <span style="color:#0D47A1;">5.1  VS Code Settings Hierarchy for Copilot</span>

GitHub Copilot's behavior is configured through VS Code's standard settings system, which has three layers (lowest → highest priority):

<table style="width:100%; border-collapse:collapse;">
<tr><td style="background:#0D47A1; color:white; padding:10px 12px; border:1px solid #BBDEFB; font-weight:bold;">Settings Level</td><td style="background:#0D47A1; color:white; padding:10px 12px; border:1px solid #BBDEFB; font-weight:bold;">Location &  Purpose</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><strong>1. User Settings (global)</strong></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><em>File → Preferences → Settings → User tab</em> — your personal preferences across all projects. Enable/disable features, set inline suggestion delay, etc.</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><strong>2. Workspace Settings</strong></td><td style="padding:10px 12px; border:1px solid #CCC;"><em>.vscode/settings.json</em> — project-level settings committed to git. Team-shared Copilot configuration, language-level enable/disable.</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><strong>3. Folder Settings</strong></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">In multi-root workspaces, per-folder overrides for specific sub-projects within a monorepo.</td></tr>
</table>

**Useful `.vscode/settings.json` configuration for React projects:**

```json
{
  "github.copilot.enable": {
    "*": true,
    "markdown": false,
    "plaintext": false
  },
  "github.copilot.chat.agent.autoFix": true,
  "github.copilot.chat.generateTests.codeLens": true,
  "editor.inlineSuggest.enabled": true,
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": "explicit",
    "source.organizeImports": "explicit"
  }
}
```

The `editor.codeActionsOnSave` block is your quality gate equivalent: ESLint auto-fix and import organization run automatically every time you save — including when Copilot writes a file in Agent mode that you've accepted.

### <span style="color:#0D47A1;">5.2  The Project Configuration Hierarchy</span>

Beyond VS Code settings, Copilot uses a `.github/` folder structure for project-level AI configuration:

<table style="width:100%; border-collapse:collapse;">
<tr><td style="background:#1A73E8; color:white; padding:10px 12px; border:1px solid #BBDEFB; font-weight:bold;">File / Location</td><td style="background:#1A73E8; color:white; padding:10px 12px; border:1px solid #BBDEFB; font-weight:bold;">Purpose</td><td style="background:#1A73E8; color:white; padding:10px 12px; border:1px solid #BBDEFB; font-weight:bold;">Scope</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><code>.github/copilot-instructions.md</code></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Global project instructions — always injected into every Copilot Chat session for this repo</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">All files, all sessions</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><code>.github/instructions/*.instructions.md</code></td><td style="padding:10px 12px; border:1px solid #CCC;">Scoped instructions with <code>applyTo:</code> glob frontmatter — injected only for matching files</td><td style="padding:10px 12px; border:1px solid #CCC;">Files matching the glob</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><code>.github/prompts/*.prompt.md</code></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Reusable prompt templates — invoked on-demand as custom slash commands in Copilot Chat</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Manual invocation</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><code>.vscode/settings.json</code></td><td style="padding:10px 12px; border:1px solid #CCC;">VS Code / Copilot feature flags and behavior settings — committed to git for team consistency</td><td style="padding:10px 12px; border:1px solid #CCC;">VS Code behavior</td></tr>
</table>

<table style="width:100%; border-collapse:collapse;"><tr><td style="border-left:5px solid #1A73E8; background:#E3F2FD; padding:14px 18px;"><strong style="color:#0D47A1;">⭐ KEY POINT:</strong> <span style="color:#0D47A1;">For TI-size teams: put team-agreed React standards in <code>.github/copilot-instructions.md</code> (committed to git, applies to everyone). Put personal style preferences in VS Code User Settings (not in the repo). Put quality gates in <code>.vscode/settings.json</code> (committed to git, applies to every developer's save-on-file). This gives you consistency everywhere that matters, and individual customization where it's harmless.</span></td></tr></table>

### <span style="color:#0D47A1;">5.3  Quality Gate Hooks with ESLint and TypeScript</span>

The equivalent of Claude Code's PostToolUse hooks — running a linter automatically every time code is written — is VS Code's `editor.codeActionsOnSave` combined with a CI check:

```jsonc
// .vscode/settings.json — runs on every file save (including Agent-accepted files)
{
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": "explicit"
  }
}
```

```jsonc
// package.json — lint-staged runs ESLint + TypeScript on git pre-commit
{
  "scripts": {
    "lint": "eslint src --max-warnings 0",
    "type-check": "tsc --noEmit"
  },
  "lint-staged": {
    "src/**/*.{ts,tsx}": ["eslint --fix", "tsc-files --noEmit"]
  }
}
```

**Together, this means:**
1. Every file save → ESLint auto-fix (catches style issues immediately)
2. Every `git commit` → ESLint + TypeScript check (blocks committing broken code)
3. Agent mode → writes files → files are saved → ESLint fires on each save automatically

<table style="width:100%; border-collapse:collapse;"><tr><td style="border-left:5px solid #2E7D32; background:#E8F5E9; padding:14px 18px; border:1px solid #A5D6A7;"><strong style="color:#2E7D32;">✅ COPILOT CONFIGURATION CHECKLIST FOR REACT PROJECTS</strong><ul style="color:#333; margin:8px 0; padding-left:20px;"><li><strong>CREATED:</strong> <code>.github/copilot-instructions.md</code> with React standards (see Module 3, Section 5)</li><li><strong>CREATED:</strong> <code>.vscode/settings.json</code> with ESLint on-save and Copilot feature flags</li><li><strong>CREATED:</strong> <code>.github/prompts/review-component.prompt.md</code> for team standard reviews</li><li><strong>CONFIGURED:</strong> lint-staged for pre-commit ESLint + TypeScript checks</li><li><strong>COMMITTED:</strong> All <code>.github/</code> and <code>.vscode/</code> files to git and pushed to the team repo</li><li><strong>VERIFIED:</strong> New team member clones repo, opens in VS Code — Copilot Chat immediately has correct standards</li></ul></td></tr></table>

---

<table style="width:100%; border-collapse:collapse;"><tr><td style="background:#00695C; color:white; padding:8px 16px; font-weight:bold;">0:42 – 0:45</td><td style="background:#E0F2F1; padding:8px 16px; color:#00695C; font-weight:bold; font-size:16px;">WRAP-UP: Quick Reference & Transition to Module 5</td></tr></table>

## <span style="color:#0D47A1;">6. Quick Reference & Transition</span>

## <span style="color:#1A73E8;">MODULE 4 RECAP</span>

- ✅ **Three surfaces:** inline completion for boilerplate, Inline Chat (`Ctrl+I`) for file-scoped edits, Copilot Chat panel for multi-turn conversations and architecture. New Chat is your context-reset button.
- ✅ **Slash commands:** `/explain` to understand before modifying, `/fix` for TypeScript errors, `/tests` for instant RTL test generation, `/doc` for JSDoc, `/new` for file scaffolding.
- ✅ **Context variables:** `#file:` to include specific files, `@workspace` for project-wide search, `#terminalLastCommand` to bring in test output, `#selection` for selected code.
- ✅ **Agent mode:** the autonomous multi-file surface. Always plan before executing ("list all files before writing"). Terminal commands require your explicit approval.
- ✅ **Change management:** Copilot Edits panel for accept/reject per file. `Ctrl+Z` for inline undo. Git commits are your safety net — commit before every significant Agent session.
- ✅ **Configuration:** `.github/copilot-instructions.md` for team AI standards, `.github/prompts/` for custom prompt files, `.vscode/settings.json` for behavior and quality gates.

---

## <span style="color:#1A73E8;">QUICK REFERENCE CARD</span>

<table style="width:100%; border-collapse:collapse;">
<tr><td style="background:#2E7D32; color:white; padding:10px 12px; border:1px solid #A5D6A7; font-weight:bold;">Feature</td><td style="background:#2E7D32; color:white; padding:10px 12px; border:1px solid #A5D6A7; font-weight:bold;">Shortcut / Command</td><td style="background:#2E7D32; color:white; padding:10px 12px; border:1px solid #A5D6A7; font-weight:bold;">What It Does</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><strong>Open Chat panel</strong></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><kbd>Ctrl+Alt+I</kbd> / <kbd>Cmd+Alt+I</kbd></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Focus Copilot Chat panel</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><strong>Open Inline Chat</strong></td><td style="padding:10px 12px; border:1px solid #CCC;"><kbd>Ctrl+I</kbd> / <kbd>Cmd+I</kbd></td><td style="padding:10px 12px; border:1px solid #CCC;">Ask/edit in current file at cursor</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><strong>Accept inline suggestion</strong></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><kbd>Tab</kbd></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Accept ghost text completion</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><strong>Dismiss suggestion</strong></td><td style="padding:10px 12px; border:1px solid #CCC;"><kbd>Esc</kbd></td><td style="padding:10px 12px; border:1px solid #CCC;">Reject and clear ghost text</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><strong>Next suggestion</strong></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><kbd>Alt+]</kbd> / <kbd>Option+]</kbd></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Cycle to next inline suggestion alternative</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><strong>Undo accepted suggestion</strong></td><td style="padding:10px 12px; border:1px solid #CCC;"><kbd>Ctrl+Z</kbd> / <kbd>Cmd+Z</kbd></td><td style="padding:10px 12px; border:1px solid #CCC;">Undo last accepted inline completion</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><strong>New Chat</strong></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Click <strong>+</strong> in Chat panel toolbar</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Reset context for a new task</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><strong>Explain code</strong></td><td style="padding:10px 12px; border:1px solid #CCC;">Select code → Ctrl+I → <code>/explain</code></td><td style="padding:10px 12px; border:1px solid #CCC;">Get plain English explanation of selection</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><strong>Fix error</strong></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Select error → Ctrl+I → <code>/fix</code></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Fix TypeScript / ESLint error in selection</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><strong>Generate tests</strong></td><td style="padding:10px 12px; border:1px solid #CCC;">Select code → Ctrl+I → <code>/tests</code></td><td style="padding:10px 12px; border:1px solid #CCC;">Generate RTL / Jest tests for selection</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><strong>Add JSDoc</strong></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Select function → Ctrl+I → <code>/doc</code></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Generate JSDoc documentation comment</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><strong>Reference file</strong></td><td style="padding:10px 12px; border:1px solid #CCC;"><code>#file:path/to/Component.tsx</code></td><td style="padding:10px 12px; border:1px solid #CCC;">Include full file in Chat context</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><strong>Workspace search</strong></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><code>@workspace [question]</code></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Search across all project files</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><strong>Include terminal output</strong></td><td style="padding:10px 12px; border:1px solid #CCC;"><code>#terminalLastCommand</code></td><td style="padding:10px 12px; border:1px solid #CCC;">Bring last terminal output into Chat</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><strong>Agent mode</strong></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Chat dropdown → Agent</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Autonomous multi-file editing with terminal access</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><strong>Accept/Reject changes</strong></td><td style="padding:10px 12px; border:1px solid #CCC;">Copilot Edits panel → ✓ or ✗</td><td style="padding:10px 12px; border:1px solid #CCC;">Review and selectively accept Agent-made changes</td></tr>
</table>

---

## <span style="color:#1A73E8;">TRANSITION TO MODULE 5</span>

You now know how to drive GitHub Copilot — the three surfaces, the commands, the change management workflow, and the configuration system. In Module 5, we'll cover **automation and scripting**: using Copilot to write and improve automation scripts, GitHub Actions workflows, and repetitive React boilerplate generation — the tasks where AI-assisted coding produces the most measurable time savings for React teams.

---

<div style="text-align:center; padding:20px; color:#666; font-size:12px;">
Vibe Coding with GitHub Copilot | React Developer Track<br>
Module 4 — GitHub Copilot Deep Dive: Chat, Agent Mode & VS Code Integration
</div>
