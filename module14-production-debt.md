<div style="text-align:center; padding: 20px 0;">
<span style="font-size:14px; color:#666666; font-weight:bold; letter-spacing:2px;">MODULE 14</span>

# <span style="color:#0D47A1;">Production React Patterns & Technical Debt</span>

<hr style="border: 3px solid #1A73E8; width:80%;">
</div>

<table style="width:100%; border-collapse:collapse;">
<tr>
<td style="background:#E3F2FD; text-align:center; padding:10px; border:1px solid #BBDEFB; width:25%;"><span style="font-size:12px; color:#666;">Duration</span><br><strong style="color:#0D47A1;">45 min</strong></td>
<td style="background:#E3F2FD; text-align:center; padding:10px; border:1px solid #BBDEFB; width:25%;"><span style="font-size:12px; color:#666;">Format</span><br><strong style="color:#0D47A1;">Lecture + Demo</strong></td>
<td style="background:#E3F2FD; text-align:center; padding:10px; border:1px solid #BBDEFB; width:25%;"><span style="font-size:12px; color:#666;">Audience</span><br><strong style="color:#0D47A1;">React Developers</strong></td>
<td style="background:#E3F2FD; text-align:center; padding:10px; border:1px solid #BBDEFB; width:25%;"><span style="font-size:12px; color:#666;">Day / Position</span><br><strong style="color:#0D47A1;">Day 2 / Sixth</strong></td>
</tr>
</table>

---

## <span style="color:#1A73E8;">LEARNING OBJECTIVES</span>

By the end of this module, participants will be able to:

1. Add React Error Boundaries to a component library to provide graceful degradation
2. Identify and apply React performance optimizations (`useMemo`, `useCallback`, `React.memo`, `React.lazy`) with Copilot assistance
3. Configure ESLint and TypeScript strict mode rules to systematically surface code quality issues
4. Run dependency audits and interpret vulnerability reports with `npm audit`
5. Use Copilot to generate a structured technical debt inventory and prioritized refactor plan

---

## <span style="color:#1A73E8;">SESSION TIMING BREAKDOWN</span>

<table style="width:100%; border-collapse:collapse;">
<tr><td style="background:#00695C; color:white; padding:8px 14px; width:120px; font-weight:bold; font-size:13px;">0:00 – 0:09</td><td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Section 1: React Error Boundaries — Resilient Components</td></tr>
<tr><td colspan="2" style="height:4px;"></td></tr>
<tr><td style="background:#00695C; color:white; padding:8px 14px; font-weight:bold; font-size:13px;">0:09 – 0:22</td><td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Section 2: Performance Optimization — Memoization, Lazy Loading & Profiling</td></tr>
<tr><td colspan="2" style="height:4px;"></td></tr>
<tr><td style="background:#00695C; color:white; padding:8px 14px; font-weight:bold; font-size:13px;">0:22 – 0:31</td><td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Section 3: Code Quality — ESLint Rules, TypeScript Strict & Accessibility Linting</td></tr>
<tr><td colspan="2" style="height:4px;"></td></tr>
<tr><td style="background:#00695C; color:white; padding:8px 14px; font-weight:bold; font-size:13px;">0:31 – 0:38</td><td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Section 4: Dependency Management — npm audit, Security Patches & Dependabot</td></tr>
<tr><td colspan="2" style="height:4px;"></td></tr>
<tr><td style="background:#00695C; color:white; padding:8px 14px; font-weight:bold; font-size:13px;">0:38 – 0:45</td><td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Section 5: Technical Debt Inventory — Identify, Prioritize & Refactor Safely</td></tr>
</table>

---

## <span style="color:#0D47A1;">1. React Error Boundaries — Resilient Components</span>

A React Error Boundary is a class component that implements `componentDidCatch` and `getDerivedStateFromError`. It intercepts rendering errors in its child component tree, logs them, and renders a fallback UI instead of crashing the entire application.

### <span style="color:#0D47A1;">1.1  Why Error Boundaries Matter for Component Libraries</span>

Without error boundaries, a single prop-type mismatch or unexpected `undefined` value in one component can crash the entire React tree. For a production form library, this means a user filling out a form loses all their progress because one field had an edge case bug.

<table style="width:100%; border-collapse:collapse;">
<tr><td style="background:#1A73E8; color:white; padding:10px 12px; font-weight:bold; width:50%;">Without Error Boundary</td><td style="background:#1A73E8; color:white; padding:10px 12px; font-weight:bold; width:50%;">With Error Boundary</td></tr>
<tr><td style="background:#FFEBEE; padding:10px 12px; border:1px solid #CCC;">One broken component → entire page blank</td><td style="background:#E8F5E9; padding:10px 12px; border:1px solid #CCC;">One broken component → graceful fallback UI</td></tr>
<tr><td style="background:#FFEBEE; padding:10px 12px; border:1px solid #CCC;">Error only surfaced in browser console</td><td style="background:#E8F5E9; padding:10px 12px; border:1px solid #CCC;">Error captured and sent to monitoring (Sentry, etc.)</td></tr>
<tr><td style="background:#FFEBEE; padding:10px 12px; border:1px solid #CCC;">User data lost — form resets on crash</td><td style="background:#E8F5E9; padding:10px 12px; border:1px solid #CCC;">Rest of form still functional; only broken field shows fallback</td></tr>
</table>

### <span style="color:#0D47A1;">1.2  Generating a Reusable Error Boundary</span>

Ask Copilot to generate a flexible Error Boundary component:

```text
Create a reusable ErrorBoundary component for my-form-library.

Requirements:
1. TypeScript class component that implements getDerivedStateFromError and componentDidCatch
2. Props:
   - children: ReactNode
   - fallback: ReactNode | ((error: Error, resetError: () => void) => ReactNode) — supports both static and render-prop fallbacks
   - onError?: (error: Error, errorInfo: ErrorInfo) => void — optional error reporting callback
3. Exposes a reset() method that clears the error state so the child tree rerenders
4. The component should be placed in src/components/ErrorBoundary.tsx
5. Export an ErrorBoundaryProps interface
6. Add a simple default fallback if no fallback prop is provided

Also create src/components/ErrorBoundary.test.tsx with:
- Test that renders children when no error
- Test that renders fallback UI when child throws
- Test that calls onError callback with the error
- Test that renders render-prop fallback with error and resetError arguments
```

This `ErrorBoundary` is a required artifact for Module 15. Lab 3 wraps `MultiFileUpload` in a safe export that imports this component.

### <span style="color:#0D47A1;">1.3  Wrapping Form Components with Error Boundaries</span>

For a form library, the right granularity is usually one Error Boundary per field group or section — not one per field (too many) and not one for the entire form (too coarse).

```tsx
// Recommended pattern for my-form-library consumers
<ErrorBoundary
  fallback={(error, reset) => (
    <div role="alert">
      <p>This field encountered an error. <button onClick={reset}>Retry</button></p>
    </div>
  )}
  onError={(error) => trackingService.captureException(error)}
>
  <PhoneInput value={phone} onChange={setPhone} />
</ErrorBoundary>
```

---

## <span style="color:#0D47A1;">2. Performance Optimization — Memoization, Lazy Loading & Profiling</span>

React performance issues in component libraries almost always fall into one of three categories: unnecessary re-renders, expensive recalculations, and large bundle size. Copilot can identify which category you're in and help apply the right fix.

### <span style="color:#0D47A1;">2.1  The Right Optimization Mindset</span>

<table style="width:100%; border-collapse:collapse;"><tr><td style="border-left:5px solid #C62828; background:#FFEBEE; padding:14px 18px; border:1px solid #EF9A9A;"><strong style="color:#C62828;">⚠️ WARNING — Don't Optimize Prematurely:</strong> <span style="color:#C62828;">Adding <code>useMemo</code>, <code>useCallback</code>, and <code>React.memo</code> to every component by default introduces its own overhead (memory cost, additional comparisons, harder-to-read code). Profile first, then optimize. Ask Copilot to identify hot spots before applying memoization broadly.</span></td></tr></table>

**Ask Copilot to identify optimization candidates:**

```text
#file:src/components/Select/Select.tsx
#file:src/components/TextInput/TextInput.tsx

Review these components for React performance issues.
Identify:
1. Functions created on every render that are passed as props to child components (useCallback candidates)
2. Expensive computations performed on every render (useMemo candidates)
3. Components that render frequently with the same props (React.memo candidates)
4. Any effects that run on every render due to missing or incorrect dependency arrays

For each issue found, explain:
- What the problem is
- Why it causes unnecessary work
- The specific code change needed to fix it
- A note if the optimization is marginal (not worth the complexity cost)
```

### <span style="color:#0D47A1;">2.2  useMemo — Caching Expensive Computations</span>

Use `useMemo` when a value is expensive to compute AND depends on specific inputs that change rarely:

```typescript
// Before: formatOptions runs on every render even if options haven't changed
const formattedOptions = formatOptions(rawOptions, locale, sortBy);

// After: only recalculates when rawOptions, locale, or sortBy change
const formattedOptions = useMemo(
  () => formatOptions(rawOptions, locale, sortBy),
  [rawOptions, locale, sortBy]
);
```

**When to use:** Sort/filter operations on lists, computed display values from complex transformations, derived data shared between multiple renders.

**When NOT to use:** Simple string concatenation, arithmetic, or any operation that takes < 0.1ms regardless of input size.

### <span style="color:#0D47A1;">2.3  useCallback — Stable Function References</span>

Use `useCallback` when a function is passed as a prop to a memoized child component. Without it, `React.memo` is useless because the function reference changes on every parent render:

```typescript
// Without useCallback: handleChange is a new function reference every render
// → React.memo on the child component never prevents re-renders
const handleChange = (value: string) => {
  setValue(value);
  props.onChange?.(value);
};

// With useCallback: same function reference as long as props.onChange doesn't change
const handleChange = useCallback((value: string) => {
  setValue(value);
  props.onChange?.(value);
}, [props.onChange]);
```

### <span style="color:#0D47A1;">2.4  React.lazy — Code Splitting</span>

For large components that are not needed immediately (modal dialogs, date pickers, rich text editors), use `React.lazy` to split them into separate bundles loaded only when needed:

```typescript
// Without lazy: SelectionModal code is in the initial bundle
import { SelectionModal } from './SelectionModal';

// With lazy: SelectionModal is loaded only when rendered for the first time
const SelectionModal = React.lazy(() => import('./SelectionModal'));

// Wrap with Suspense to handle the loading state
<Suspense fallback={<div role="progressbar" aria-label="Loading...">Loading...</div>}>
  {isOpen && <SelectionModal />}
</Suspense>
```

### <span style="color:#0D47A1;">2.5  React Profiler — Finding Real Bottlenecks</span>

Never guess at performance issues. Use the React DevTools Profiler to record actual render behavior:

**With Copilot's help:**

```text
I profiled my-form-library's Select component in React DevTools.
The flamegraph shows that Select re-renders 47ms after every keystroke in
the search input, even when the options list hasn't changed.

The component receives these props: options, value, onChange, isSearchable, placeholder.

Analyze what is likely causing the unexpected re-renders and suggest the minimal
set of changes to fix it. Show the code changes needed.
```

<table style="width:100%; border-collapse:collapse;"><tr><td style="border-left:5px solid #1A73E8; background:#E3F2FD; padding:14px 18px;"><strong style="color:#0D47A1;">⭐ KEY POINT:</strong> <span style="color:#0D47A1;">Paste profiler output, error messages, or performance traces directly into Copilot Chat. The more specific the signal you provide, the more precise the optimization suggestion. "My component is slow" is a poor prompt. "My component re-renders 47ms on every keystroke" is a great prompt.</span></td></tr></table>

---

## <span style="color:#0D47A1;">3. Code Quality — ESLint Rules, TypeScript Strict & Accessibility Linting</span>

A production component library needs systematic quality enforcement — not just "this code looks fine to me." ESLint and TypeScript strict mode encode team decisions as automated rules that run on every file change.

### <span style="color:#0D47A1;">3.1  TypeScript Strict Mode</span>

`strict: true` in `tsconfig.json` enables a set of compiler checks that catch common bugs at compile time:

```text
Review my-form-library's tsconfig.json and check if TypeScript strict mode
is fully enabled.

If it's not, generate the diff needed to enable these TypeScript compiler options:
- strict: true (enables: noImplicitAny, strictNullChecks, strictFunctionTypes, etc.)
- noUncheckedIndexedAccess: true
- exactOptionalPropertyTypes: true
- noImplicitReturns: true
- noFallthroughCasesInSwitch: true

After enabling, identify which files in src/components/ likely need changes to
satisfy the new strictness requirements. For each file, list what TypeScript
errors would be reported and how to fix them.
```

### <span style="color:#0D47A1;">3.2  ESLint Configuration for a Component Library</span>

Ask Copilot to audit and strengthen your ESLint configuration:

```text
#file:eslint.config.js (or .eslintrc.json)

Review this ESLint config for my-form-library.
It's a TypeScript React component library.

Add or recommend the following rules and explain the rationale for each:
1. @typescript-eslint/no-explicit-any: error — force proper typing
2. @typescript-eslint/explicit-function-return-type: warn — improve readability
3. react/prop-types: off — we use TypeScript interfaces instead
4. react-hooks/rules-of-hooks: error — catch hook violations
5. react-hooks/exhaustive-deps: warn — catch missing hook dependencies
6. jsx-a11y/label-has-associated-control: error — enforce label accessibility
7. jsx-a11y/aria-roles: error — catch invalid ARIA role usage
8. complexity: ["warn", { max: 10 }] — flag overly complex functions
9. max-lines-per-function: ["warn", { max: 60 }] — keep functions focused

For each rule, show the exact config object to add to the ESLint file.
```

### <span style="color:#0D47A1;">3.3  Accessibility Linting with eslint-plugin-jsx-a11y</span>

`eslint-plugin-jsx-a11y` catches accessibility violations at lint time — before tests run and before a human reviewer sees the code:

```bash
npm install --save-dev eslint-plugin-jsx-a11y
```

**The most valuable a11y rules for a form library:**

<table style="width:100%; border-collapse:collapse;">
<tr><td style="background:#1A73E8; color:white; padding:10px 12px; font-weight:bold; width:40%;">Rule</td><td style="background:#1A73E8; color:white; padding:10px 12px; font-weight:bold;">What It Catches</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><code>label-has-associated-control</code></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Labels without a matching input id or htmlFor attribute</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><code>interactive-supports-focus</code></td><td style="padding:10px 12px; border:1px solid #CCC;">Clickable elements that are not focusable with keyboard</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><code>no-autofocus</code></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Autofocus attributes that break screen reader flow</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC;"><code>aria-props</code></td><td style="padding:10px 12px; border:1px solid #CCC;">Misspelled or invalid ARIA attribute names</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><code>role-has-required-aria-props</code></td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">ARIA roles used without their required companion attributes</td></tr>
</table>

<table style="width:100%; border-collapse:collapse;"><tr><td style="border-left:5px solid #2E7D32; background:#E8F5E9; padding:14px 18px;"><strong style="color:#2E7D32;">✅ CHECKPOINT:</strong> <span style="color:#2E7D32;">After enabling all ESLint rules, run: <code>npm run lint --max-warnings 0</code>. If this passes with zero warnings, your codebase meets the quality gate. Add this command to your CI pipeline (it's already in the GitHub Actions workflow from Module 13).</span></td></tr></table>

---

## <span style="color:#0D47A1;">4. Dependency Management — npm audit, Security Patches & Dependabot</span>

Component libraries introduce dependencies that consumers inherit. A vulnerable dependency in your library is a vulnerability in every project that installs it. Dependency management is not optional.

### <span style="color:#0D47A1;">4.1  Running npm audit</span>

```bash
# Check for vulnerabilities
npm audit

# See vulnerabilities with full detail
npm audit --json | head -200

# Auto-fix safe patches (minor/patch version bumps)
npm audit fix

# Show what --force would do without doing it
npm audit fix --dry-run --force
```

**Reading the audit output:**

<table style="width:100%; border-collapse:collapse;">
<tr><td style="background:#1A73E8; color:white; padding:10px 12px; font-weight:bold; width:20%;">Severity</td><td style="background:#1A73E8; color:white; padding:10px 12px; font-weight:bold; width:40%;">Meaning</td><td style="background:#1A73E8; color:white; padding:10px 12px; font-weight:bold;">Action</td></tr>
<tr><td style="background:#FFEBEE; padding:10px 12px; border:1px solid #CCC; font-weight:bold; color:#C62828;">Critical</td><td style="background:#FFEBEE; padding:10px 12px; border:1px solid #CCC;">Remote code execution or data exfiltration possible</td><td style="background:#FFEBEE; padding:10px 12px; border:1px solid #CCC;">Fix immediately — block PR merge if CI detects this</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC; font-weight:bold; color:#E65100;">High</td><td style="padding:10px 12px; border:1px solid #CCC;">Significant security impact likely</td><td style="padding:10px 12px; border:1px solid #CCC;">Fix before next sprint — include in current sprint if possible</td></tr>
<tr><td style="background:#FFF9C4; padding:10px 12px; border:1px solid #CCC;">Moderate</td><td style="background:#FFF9C4; padding:10px 12px; border:1px solid #CCC;">Limited or conditional security impact</td><td style="background:#FFF9C4; padding:10px 12px; border:1px solid #CCC;">Schedule in backlog — address within 30–60 days</td></tr>
<tr><td style="background:#E8F5E9; padding:10px 12px; border:1px solid #CCC;">Low</td><td style="background:#E8F5E9; padding:10px 12px; border:1px solid #CCC;">Minimal security impact</td><td style="background:#E8F5E9; padding:10px 12px; border:1px solid #CCC;">Address during routine dependency updates</td></tr>
</table>

### <span style="color:#0D47A1;">4.2  Using Copilot to Interpret audit Output</span>

```bash
# Export the raw audit report
npm audit --json > /tmp/audit.json
```

Then in Copilot Chat:

```text
#file:/tmp/audit.json

Analyze this npm audit output for my-form-library.
This is a React TypeScript component library.

For each vulnerability:
1. Is it in a production dependency or devDependency?
2. Would a consumer of the library be exposed to this vulnerability?
3. What is the safe upgrade path? (version to upgrade to)
4. Does upgrading have any breaking API changes we need to handle?

Prioritize your recommendations by: Critical > High > Moderate > Low.
Ignore vulnerabilities only in devDependencies if they cannot affect library consumers.
```

### <span style="color:#0D47A1;">4.3  Dependabot Configuration</span>

Enable automatic dependency update PRs via Dependabot:

```yaml
# .github/dependabot.yml
version: 2
updates:
  - package-ecosystem: "npm"
    directory: "/"
    schedule:
      interval: "weekly"
      day: "monday"
      time: "09:00"
    groups:
      devDependencies:
        patterns:
          - "@types/*"
          - "eslint*"
          - "jest*"
          - "@testing-library/*"
          - "typescript"
        update-types:
          - "minor"
          - "patch"
    ignore:
      - dependency-name: "react"
        update-types: ["version-update:semver-major"]
      - dependency-name: "react-dom"
        update-types: ["version-update:semver-major"]
```

<table style="width:100%; border-collapse:collapse;"><tr><td style="border-left:5px solid #1A73E8; background:#E3F2FD; padding:14px 18px;"><strong style="color:#0D47A1;">⭐ KEY POINT:</strong> <span style="color:#0D47A1;">Dependabot groups related packages (all @types/* together, all eslint plugins together) so you get one PR for a group of related updates instead of 15 individual PRs. Each Dependabot PR runs your CI pipeline automatically — if tests pass, you can merge in seconds. This eliminates dependency drift, the silent accumulation of unpatched vulnerabilities over months.</span></td></tr></table>

---

## <span style="color:#0D47A1;">5. Technical Debt Inventory — Identify, Prioritize & Refactor Safely</span>

Technical debt is not just messy code — it's any decision that slows down future change. Copilot can systematically identify technical debt across a codebase and generate a prioritized refactor plan.

### <span style="color:#0D47A1;">5.1  Running a Technical Debt Audit</span>

```text
#codebase

Perform a technical debt audit of my-form-library's src/ directory.
Organize findings into four categories:

1. RELIABILITY DEBT — Code that is likely to break under edge cases
   (missing null checks, implicit type coercions, unhandled promise rejections)

2. MAINTAINABILITY DEBT — Code that is difficult to change safely
   (functions over 50 lines, components with more than 5 responsibilities,
   prop drilling more than 3 levels deep, magic numbers without named constants)

3. CONSISTENCY DEBT — Code that doesn't follow team conventions
   (inconsistent prop naming, mixed styling approaches, some components
   with stories and some without, varying test patterns)

4. SECURITY DEBT — Code patterns that could be exploited
   (dangerouslySetInnerHTML, insecure direct dependencies, untrusted
   data rendered without sanitization)

For each issue found:
- File and approximate line range
- Brief description of the problem
- Estimated effort to fix: XS / S / M / L
- Priority: P1 (critical path) / P2 (should fix this quarter) / P3 (nice to have)

Output as a structured list.
```

### <span style="color:#0D47A1;">5.2  Safe Refactoring with Copilot</span>

Before refactoring, establish the safety net — tests that will tell you if the refactor broke something:

```text
#file:src/components/Select/Select.tsx

I want to refactor the filtering logic in the Select component to improve
readability. The filterOptions function at line 45 is 80 lines long and
handles three different cases (substring match, starts-with, exact match).

Before I refactor:
1. What test cases must exist to ensure the refactor doesn't change behavior?
2. Which of these tests are currently missing from Select.test.tsx?
3. Write the missing tests first, then show the refactored filterOptions function
   split into three smaller, named functions.

Approach: Write tests first, then refactor. Do NOT change behavior.
```

### <span style="color:#0D47A1;">5.3  The Refactor Workflow</span>

<table style="width:100%; border-collapse:collapse;">
<tr><td style="background:#1A73E8; color:white; padding:10px 12px; font-weight:bold; width:60px; text-align:center;">Step</td><td style="background:#1A73E8; color:white; padding:10px 12px; font-weight:bold;">Action</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC; text-align:center; font-weight:bold;">1</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><strong>Identify:</strong> Run the debt audit prompt → get list of issues → prioritize by P1/P2</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC; text-align:center; font-weight:bold;">2</td><td style="padding:10px 12px; border:1px solid #CCC;"><strong>Test coverage:</strong> Before touching the code, verify tests cover existing behavior. Add missing tests first.</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC; text-align:center; font-weight:bold;">3</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><strong>Refactor in isolation:</strong> One component at a time. Use <code>[PLAN ONLY]</code> to preview the changes before applying.</td></tr>
<tr><td style="padding:10px 12px; border:1px solid #CCC; text-align:center; font-weight:bold;">4</td><td style="padding:10px 12px; border:1px solid #CCC;"><strong>Quality gate:</strong> <code>npm test</code> + <code>npx tsc --noEmit</code> + <code>npm run lint</code> — all must pass.</td></tr>
<tr><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC; text-align:center; font-weight:bold;">5</td><td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><strong>PR:</strong> Separate refactor PRs from feature PRs. A reviewer should be able to verify "no behavior changed" without reading the full diff.</td></tr>
</table>

<table style="width:100%; border-collapse:collapse;"><tr><td style="border-left:5px solid #1A73E8; background:#E3F2FD; padding:14px 18px;"><strong style="color:#0D47A1;">⭐ KEY POINT:</strong> <span style="color:#0D47A1;">The refactor workflow above is identical whether you're doing it manually or with Copilot. Copilot doesn't change the discipline — it accelerates it. The discipline is: identify → test → change → verify → ship. With Copilot, the "identify" and "change" steps take seconds instead of hours. The "test" and "verify" steps are non-negotiable regardless of how fast the code changes.</span></td></tr></table>
