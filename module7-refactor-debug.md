<div style="text-align:center; padding: 20px 0;">
<span style="font-size:14px; color:#666666; font-weight:bold; letter-spacing:2px;">MODULE 7</span>

# <span style="color:#0D47A1;">Coding with GitHub Copilot: Refactor & Debug</span>

<hr style="border: 3px solid #1A73E8; width:80%;">
</div>

<table style="width:100%; border-collapse:collapse;">
<tr>
<td style="background:#E3F2FD; text-align:center; padding:10px; border:1px solid #BBDEFB; width:25%;"><span style="font-size:12px; color:#666;">Duration</span><br><strong style="color:#0D47A1;">45 min</strong></td>
<td style="background:#E3F2FD; text-align:center; padding:10px; border:1px solid #BBDEFB; width:25%;"><span style="font-size:12px; color:#666;">Format</span><br><strong style="color:#0D47A1;">Lecture + Demo</strong></td>
<td style="background:#E3F2FD; text-align:center; padding:10px; border:1px solid #BBDEFB; width:25%;"><span style="font-size:12px; color:#666;">Audience</span><br><strong style="color:#0D47A1;">React Developers</strong></td>
<td style="background:#E3F2FD; text-align:center; padding:10px; border:1px solid #BBDEFB; width:25%;"><span style="font-size:12px; color:#666;">Day / Position</span><br><strong style="color:#0D47A1;">Day 1 / Seventh</strong></td>
</tr>
</table>

---

## <span style="color:#1A73E8;">LEARNING OBJECTIVES</span>

1. Apply Copilot Chat and Agent prompting best practices for refactoring and debugging tasks
2. Refactor existing React/TypeScript code for testability using Copilot while maintaining minimal diffs
3. Auto-generate JSDoc comments, TypeScript type definitions, and inline documentation for existing codebases
4. Debug React and TypeScript errors by sharing error output with Copilot Chat using `#terminalLastCommand`
5. Use pre-refactor commits and Copilot Edits Discard to safely experiment with refactoring approaches
6. Apply the iterative refactor-test-commit cycle to incrementally improve component quality

---

## <span style="color:#1A73E8;">SESSION TIMING BREAKDOWN</span>

<table style="width:100%; border-collapse:collapse;">
<tr><td style="background:#00695C; color:white; padding:8px 14px; width:120px; font-weight:bold; font-size:13px;">0:00 – 0:08</td><td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Section 1: Prompting Best Practices for Refactoring</td></tr>
<tr><td colspan="2" style="height:4px;"></td></tr>
<tr><td style="background:#00695C; color:white; padding:8px 14px; font-weight:bold; font-size:13px;">0:08 – 0:18</td><td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Section 2: Refactoring for Testability with Minimal Diffs</td></tr>
<tr><td colspan="2" style="height:4px;"></td></tr>
<tr><td style="background:#00695C; color:white; padding:8px 14px; font-weight:bold; font-size:13px;">0:18 – 0:26</td><td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Section 3: Auto-Generating Documentation</td></tr>
<tr><td colspan="2" style="height:4px;"></td></tr>
<tr><td style="background:#00695C; color:white; padding:8px 14px; font-weight:bold; font-size:13px;">0:26 – 0:37</td><td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Section 4: Debugging from Error Output</td></tr>
<tr><td colspan="2" style="height:4px;"></td></tr>
<tr><td style="background:#00695C; color:white; padding:8px 14px; font-weight:bold; font-size:13px;">0:37 – 0:43</td><td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Section 5: Safe Experimentation with Checkpoints</td></tr>
<tr><td colspan="2" style="height:4px;"></td></tr>
<tr><td style="background:#00695C; color:white; padding:8px 14px; font-weight:bold; font-size:13px;">0:43 – 0:45</td><td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Wrap-Up: Quick Reference & Transition to Module 8</td></tr>
</table>

---

<table style="width:100%; border-collapse:collapse;"><tr><td style="background:#00695C; color:white; padding:8px 16px; font-weight:bold;">0:00 – 0:08</td><td style="background:#E0F2F1; padding:8px 16px; color:#00695C; font-weight:bold; font-size:16px;">SECTION 1: Prompting Best Practices for Refactoring</td></tr></table>

## <span style="color:#0D47A1;">1. Prompting Best Practices for Refactoring</span>

### <span style="color:#0D47A1;">1.1  The Refactoring Mindset</span>

Refactoring with GitHub Copilot is fundamentally different from writing new code. When you refactor, the code already works — your job is to make it better without breaking it. This requires precise prompts, explicit constraints, and a safety-first workflow.

<table style="width:100%; border-collapse:collapse;">
<tr><td style="background:#0D47A1; color:white; padding:10px 12px; border:1px solid #BBDEFB; font-weight:bold;">New Code Prompts</td><td style="background:#0D47A1; color:white; padding:10px 12px; border:1px solid #BBDEFB; font-weight:bold;">Refactoring Prompts</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Open-ended: describe what you want</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Constrained: specify what must NOT change</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;">Copilot has creative freedom</td><td style="padding:10px 12px; border:1px solid #CCC;">Copilot must preserve existing behavior</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">One prompt, one module</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Incremental: one refactoring step at a time</td></tr>
</table>

<table style="width:100%; border-collapse:collapse;"><tr><td style="border-left:5px solid #2E7D32; background:#E8F5E9; padding:14px 18px; border:1px solid #A5D6A7;"><strong style="color:#2E7D32;">✅ REFACTORING PROMPT RULES</strong><ul style="color:#333; margin:8px 0; padding-left:20px;"><li>Specify WHAT to change and WHAT to preserve</li><li>Request minimal diffs</li><li>One refactoring per prompt</li><li>Reference tests: "Ensure tests still pass"</li><li>Use <code>#file</code> references to point to the actual file in Copilot Chat</li><li>Ask for explanation: "Explain what you changed and why"</li></ul></td></tr></table>

### <span style="color:#0D47A1;">1.2  Prompt Templates</span>

```text
# Extract repeated render logic
(Copilot Chat, with #file:src/components/TextInput/TextInput.tsx open)
"Extract the helper/error message rendering from TextInput into an
internal FieldMessage component in the same file. Keep TextInputProps
unchanged. Ensure existing tests still pass."

# Rename with safety
"Rename the prop 'helperText' to 'hint' everywhere in
#file:src/components/TextInput/TextInput.tsx. Update the test file and
stories too. Keep backward compatibility only if existing tests require it."

# Reduce complexity
"Refactor validateField() in #file:src/utils/validators.ts to use
an array of validation rules and a loop instead of chained if-statements.
Keep the same ValidationResult return type and public signature."
```

---

<table style="width:100%; border-collapse:collapse;"><tr><td style="background:#00695C; color:white; padding:8px 16px; font-weight:bold;">0:08 – 0:18</td><td style="background:#E0F2F1; padding:8px 16px; color:#00695C; font-weight:bold; font-size:16px;">SECTION 2: Refactoring for Testability with Minimal Diffs</td></tr></table>

## <span style="color:#0D47A1;">2. Refactoring for Testability with Minimal Diffs</span>

### <span style="color:#0D47A1;">2.1  Common Testability Problems in React Components</span>

<table style="width:100%; border-collapse:collapse;">
<tr><td style="background:#00695C; color:white; padding:10px 12px; border:1px solid #80CBC4; font-weight:bold;">Problem</td><td style="background:#00695C; color:white; padding:10px 12px; border:1px solid #80CBC4; font-weight:bold;">Before</td><td style="background:#00695C; color:white; padding:10px 12px; border:1px solid #80CBC4; font-weight:bold;">After</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><strong>Does too much</strong></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">A legacy field component formats, validates, renders, and submits</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Split into component + custom hook + util</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><strong>Hidden dependency</strong></td><td style="padding:10px 12px; border:1px solid #CCC;">Reads from a global config object</td><td style="padding:10px 12px; border:1px solid #CCC;">Accept config via props or context</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><strong>Side effects inside render</strong></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Fetches data directly in the component body</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Extract to <code>useEffect</code> or custom hook; accept data as prop</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><strong>Hard-coded values</strong></td><td style="padding:10px 12px; border:1px solid #CCC;">Magic strings/numbers in JSX or validators</td><td style="padding:10px 12px; border:1px solid #CCC;">Extract to typed constants or configurable props</td></tr>
</table>

### <span style="color:#0D47A1;">2.2  The Refactor-Test-Commit Cycle</span>

<table style="width:100%; border-collapse:collapse;">
<tr><td style="background:#2E7D32; color:white; padding:10px 12px; border:1px solid #A5D6A7; font-weight:bold;">Step</td><td style="background:#2E7D32; color:white; padding:10px 12px; border:1px solid #A5D6A7; font-weight:bold;">What to Do</td></tr>
<tr><td style="background:#E8F5E9; padding:10px 12px; border:1px solid #CCC;"><strong>1. Baseline</strong></td><td style="background:#E8F5E9; padding:10px 12px; border:1px solid #CCC;">Run tests: all must pass before refactoring — <code>npm test</code></td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><strong>2. Checkpoint</strong></td><td style="padding:10px 12px; border:1px solid #CCC;">Commit: <code>git commit -am "pre-refactor baseline"</code></td></tr>
<tr><td style="background:#E8F5E9; padding:10px 12px; border:1px solid #CCC;"><strong>3. Refactor</strong></td><td style="background:#E8F5E9; padding:10px 12px; border:1px solid #CCC;">Ask Copilot to make ONE refactoring change</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><strong>4. Test</strong></td><td style="padding:10px 12px; border:1px solid #CCC;">Run tests immediately: <code>npm test</code></td></tr>
<tr><td style="background:#E8F5E9; padding:10px 12px; border:1px solid #CCC;"><strong>5. Review</strong></td><td style="background:#E8F5E9; padding:10px 12px; border:1px solid #CCC;">Check diff: <code>git diff</code> in terminal, or view Copilot Edits diff panel</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><strong>6. Fix or Revert</strong></td><td style="padding:10px 12px; border:1px solid #CCC;">Tests fail → ask Copilot to fix. Still failing → <code>git restore &lt;file&gt;</code> or Copilot Edits Discard</td></tr>
<tr><td style="background:#E8F5E9; padding:10px 12px; border:1px solid #CCC;"><strong>7. Commit</strong></td><td style="background:#E8F5E9; padding:10px 12px; border:1px solid #CCC;">Tests pass → commit with descriptive message</td></tr>
</table>

<table style="width:100%; border-collapse:collapse;"><tr><td style="border-left:5px solid #1A73E8; background:#E3F2FD; padding:14px 18px;"><strong style="color:#0D47A1;">⭐ KEY POINT:</strong> <span style="color:#0D47A1;">After extracting form state logic into <code>useFormValidation()</code>, you can test it with plain <code>renderHook()</code> calls — no DOM, no component mounting required. Components like <code>TextInput</code> then need only focused integration tests for labels, values, and error display. Separate logic from rendering.</span></td></tr></table>

---

<table style="width:100%; border-collapse:collapse;"><tr><td style="background:#00695C; color:white; padding:8px 16px; font-weight:bold;">0:18 – 0:26</td><td style="background:#E0F2F1; padding:8px 16px; color:#00695C; font-weight:bold; font-size:16px;">SECTION 3: Auto-Generating Documentation</td></tr></table>

## <span style="color:#0D47A1;">3. Auto-Generating JSDoc, TypeScript Types & Documentation</span>

```text
# Add JSDoc to the entire component library:
(Copilot Chat, Agent mode)
"Add JSDoc comments to all exported functions and components in
src/utils/ and src/hooks/. Skip those that already have JSDoc.
Use @param, @returns, and @example tags."

# Add or tighten TypeScript types:
(Copilot Chat, with #file:src/hooks/useFormValidation.ts open)
"Review all function signatures in this file. Add explicit return
types wherever they are inferred. Replace any 'any' types with
proper TypeScript interfaces."

# Audit generated documentation:
(Copilot Chat)
"Review all JSDoc in #file:src/utils/validators.ts. Check that
@param descriptions match actual parameter behavior. Fix any
inaccuracies and flag any missing @example blocks."
```

<table style="width:100%; border-collapse:collapse;"><tr><td style="border-left:5px solid #1A73E8; background:#E3F2FD; padding:14px 18px;"><strong style="color:#0D47A1;">⭐ KEY POINT:</strong> <span style="color:#0D47A1;">Generate documentation AFTER code is stable, not during initial development. JSDoc added too early means double work on every refactor. Sweet spot: right before code review or before publishing the component to a shared library.</span></td></tr></table>

<table style="width:100%; border-collapse:collapse;"><tr><td style="border-left:5px solid #C62828; background:#FFEBEE; padding:14px 18px; border:1px solid #EF9A9A;"><strong style="color:#C62828;">⚠️ WARNING:</strong> <span style="color:#C62828;">Copilot generates JSDoc based on code analysis but can make mistakes with complex business logic. Always review parameter descriptions for accuracy. A wrong <code>@param</code> description is worse than no JSDoc at all — it actively misleads future developers.</span></td></tr></table>

---

<table style="width:100%; border-collapse:collapse;"><tr><td style="background:#00695C; color:white; padding:8px 16px; font-weight:bold;">0:26 – 0:37</td><td style="background:#E0F2F1; padding:8px 16px; color:#00695C; font-weight:bold; font-size:16px;">SECTION 4: Debugging from Error Output</td></tr></table>

## <span style="color:#0D47A1;">4. Debugging from Error Output: Share Context, Get Fix</span>

### <span style="color:#0D47A1;">4.1  Debug Prompt Quality Levels</span>

<table style="width:100%; border-collapse:collapse;">
<tr><td style="background:#C62828; color:white; padding:10px 12px; border:1px solid #EF9A9A; font-weight:bold;">Quality</td><td style="background:#C62828; color:white; padding:10px 12px; border:1px solid #EF9A9A; font-weight:bold;">Example</td></tr>
<tr><td style="background:#FFEBEE; padding:10px 12px; border:1px solid #CCC;"><strong>Bad: vague</strong></td><td style="background:#FFEBEE; padding:10px 12px; border:1px solid #CCC;">"My component doesn't work. Fix it."</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><strong>Better: error only</strong></td><td style="padding:10px 12px; border:1px solid #CCC;">"I'm getting 'Cannot read properties of undefined'. Fix it."</td></tr>
<tr><td style="background:#FFEBEE; padding:10px 12px; border:1px solid #CCC;"><strong>Good: error + context</strong></td><td style="background:#FFEBEE; padding:10px 12px; border:1px solid #CCC;">"Running <code>npm test</code> gives this: [full Jest output + stack trace]. Started failing after yesterday's refactor."</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><strong>Best: full context</strong></td><td style="padding:10px 12px; border:1px solid #CCC;">"This test fails when passed an empty array. Fix without changing the component's props interface. Re-run tests after."</td></tr>
</table>

### <span style="color:#0D47A1;">4.2  Paste-and-Fix Workflow with Copilot Chat</span>

```text
# Step 1: Run the failing test
npm test -- TextInput --verbose

# Step 2: Share the error in Copilot Chat using #terminalLastCommand:
(Copilot Chat)
"#terminalLastCommand — this test fails with:
  ● TextInput › renders error state
    TypeError: Cannot read properties of undefined (reading 'message')
The test renders <TextInput id="email" label="Email" value="" onChange={handleChange} errorMessage={undefined} />.
Fix the null guard without changing the component's props type."

# Step 3: Copilot locates the undefined access, diagnoses, proposes fix

# Step 4: Apply fix, run test again
npm test -- TextInput --verbose
```

<table style="width:100%; border-collapse:collapse;"><tr><td style="border-left:5px solid #1A73E8; background:#E3F2FD; padding:14px 18px;"><strong style="color:#0D47A1;">⭐ KEY POINT:</strong> <span style="color:#0D47A1;">Always include: (1) the full Jest failure output, (2) the command that triggered it, (3) what you expected, (4) constraints on the fix. Use <code>#terminalLastCommand</code> in Copilot Chat to automatically attach the most recent terminal output without copy-pasting.</span></td></tr></table>

### <span style="color:#0D47A1;">4.3  Advanced: Add Console Logs for Hard Bugs</span>

```text
# Ask Copilot to add diagnostic logging:
(Copilot Chat, with the failing hook file open)
"Add console.debug logs to validateForm() in
#file:src/utils/validators.ts. Log each field's result
and the final combined result."

# Run the test, paste the log output back:
(Copilot Chat)
"The logs show 3 fields valid but validateForm returns false.
Find the logic error — do not change the function signature."

# After fixing, remove debug logging:
(Copilot Chat)
"Remove all console.debug calls from validateForm() in
#file:src/utils/validators.ts."
```

<table style="width:100%; border-collapse:collapse;"><tr><td style="background:#F3E5F5; padding:14px 18px; border:1px solid #CE93D8;"><strong style="color:#6A1B9A;">🎯 INSTRUCTOR NOTE</strong><br><em style="color:#6A1B9A;">Live demo: Introduce a bug into the Lab 1 project (change <code>&gt;</code> to <code>&gt;=</code> in a validator boundary check). Run <code>npm test</code>, show the failure. Share the Jest output in Copilot Chat with <code>#terminalLastCommand</code>. Watch Copilot locate the line, explain the off-by-one, fix it. Run tests to confirm. Most impactful demo in the module.</em></td></tr></table>

---

<table style="width:100%; border-collapse:collapse;"><tr><td style="background:#00695C; color:white; padding:8px 16px; font-weight:bold;">0:37 – 0:43</td><td style="background:#E0F2F1; padding:8px 16px; color:#00695C; font-weight:bold; font-size:16px;">SECTION 5: Safe Experimentation with Checkpoints</td></tr></table>

## <span style="color:#0D47A1;">5. Safe Experimentation with Checkpoints</span>

### <span style="color:#0D47A1;">5.1  Try Two Approaches</span>

```bash
# Commit baseline
git commit -am "checkpoint: before refactoring validateForm"

# Try Approach A — extract helper functions
(Copilot Chat)
"Refactor validateForm() in #file:src/utils/validators.ts to
use extracted helper functions, one per field type."

npm test

# Not happy with the result? Revert and try Approach B
git restore src/utils/validators.ts

# Try Approach B — use a rules array
(Copilot Chat)
"Refactor validateForm() in #file:src/utils/validators.ts to
use a VALIDATION_RULES array and a single reduce() call."

npm test

# Compare and keep the winner
git diff
```

<table style="width:100%; border-collapse:collapse;"><tr><td style="border-left:5px solid #1A73E8; background:#E3F2FD; padding:14px 18px;"><strong style="color:#0D47A1;">⭐ KEY POINT:</strong> <span style="color:#0D47A1;">The checkpoint → try → revert → try again workflow is the #1 refactoring productivity technique. Instead of debating which approach is better in the abstract, try both in minutes. <code>git restore &lt;file&gt;</code> makes experimentation cost nearly zero. You can also use Copilot Edits "Discard" to revert individual files without touching git.</span></td></tr></table>

---

## <span style="color:#1A73E8;">MODULE 7 RECAP</span>

- ✅ **Refactoring prompts:** constrained — specify what to change AND what to preserve. One per prompt.
- ✅ **Testability:** extract logic out of components into hooks and utils. Accept dependencies via props/context, not globals. Split large components.
- ✅ **Documentation:** generate AFTER code is stable. JSDoc with `@param`/`@returns`/`@example`, no `any` types.
- ✅ **Debugging:** share full Jest output with `#terminalLastCommand`. Include the command, expected behavior, and fix constraints.
- ✅ **Advanced debugging:** add `console.debug` logs, run tests, paste output back for iterative diagnosis.
- ✅ **Safe experimentation:** commit first, try approaches with `git restore <file>` or Copilot Edits Discard, compare `git diff`, keep winner.

## <span style="color:#1A73E8;">TRANSITION TO MODULE 8</span>

Module 8 (AI-Driven Quality Assurance) takes testing to the next level — coverage prompts, edge case generation, fixtures/mocks, flaky test triage, and property-based testing. Builds directly on the refactor-test-commit cycle you practiced here.

<table style="width:100%; border-collapse:collapse;"><tr><td style="background:#F3E5F5; padding:14px 18px; border:1px solid #CE93D8;"><strong style="color:#6A1B9A;">🎯 INSTRUCTOR NOTE</strong><br><em style="color:#6A1B9A;">Ask: "What's the most important thing to do BEFORE starting any refactoring?" Answer: commit to git. If someone says "run your tests first" — also correct. Green tests + baseline commit = the full safety net. Emphasize both.</em></td></tr></table>

---

<div style="text-align:center; padding:20px; color:#666; font-size:12px;">
<strong>React Developer Track | Vibe Coding with GitHub Copilot</strong>
</div>
