<div style="text-align:center; padding: 20px 0;">

<span style="font-size:14px; color:#666666; font-weight:bold; letter-spacing:2px;">MODULE 2</span>

# <span style="color:#0D47A1;">Prompting Techniques: Fundamentals</span>

<hr style="border: 3px solid #1A73E8; width:80%;">

</div>

<table style="width:100%; border-collapse:collapse;">
<tr>
<td style="background:#E3F2FD; text-align:center; padding:10px; border:1px solid #BBDEFB; width:25%;">
<span style="font-size:12px; color:#666;">Duration</span><br><strong style="color:#0D47A1;">45 min</strong>
</td>
<td style="background:#E3F2FD; text-align:center; padding:10px; border:1px solid #BBDEFB; width:25%;">
<span style="font-size:12px; color:#666;">Format</span><br><strong style="color:#0D47A1;">Lecture + Demo</strong>
</td>
<td style="background:#E3F2FD; text-align:center; padding:10px; border:1px solid #BBDEFB; width:25%;">
<span style="font-size:12px; color:#666;">Audience</span><br><strong style="color:#0D47A1;">React Developers</strong>
</td>
<td style="background:#E3F2FD; text-align:center; padding:10px; border:1px solid #BBDEFB; width:25%;">
<span style="font-size:12px; color:#666;">Day / Position</span><br><strong style="color:#0D47A1;">Day 1 / Second</strong>
</td>
</tr>
</table>

---

## <span style="color:#1A73E8;">LEARNING OBJECTIVES</span>

By the end of this module, participants will be able to:

1. Distinguish between persistent instructions and task prompts in GitHub Copilot and explain when to use each
2. Apply zero-shot, one-shot, and few-shot prompting patterns to generate React code with predictable quality
3. Use Chain-of-Thought (CoT) reasoning to guide GitHub Copilot through complex, multi-step React tasks
4. Practice prompt hygiene: effective context packing with `#file:` and `@workspace` references, snippet safety, and context management
5. Complete a live prompting exercise building a real-world React feature using every technique learned in this module

---

## <span style="color:#1A73E8;">SESSION TIMING BREAKDOWN</span>

<table style="width:100%; border-collapse:collapse;">
<tr>
<td style="background:#00695C; color:white; padding:8px 14px; width:120px; font-weight:bold; font-size:13px;">0:00 – 0:08</td>
<td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Section 1: The Language of AI — Why Prompting Matters</td>
</tr>
<tr><td colspan="2" style="height:4px;"></td></tr>
<tr>
<td style="background:#00695C; color:white; padding:8px 14px; font-weight:bold; font-size:13px;">0:08 – 0:18</td>
<td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Section 2: Persistent Instructions vs. Task Prompts</td>
</tr>
<tr><td colspan="2" style="height:4px;"></td></tr>
<tr>
<td style="background:#00695C; color:white; padding:8px 14px; font-weight:bold; font-size:13px;">0:18 – 0:28</td>
<td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Section 3: Zero-Shot, One-Shot & Few-Shot Patterns</td>
</tr>
<tr><td colspan="2" style="height:4px;"></td></tr>
<tr>
<td style="background:#00695C; color:white; padding:8px 14px; font-weight:bold; font-size:13px;">0:28 – 0:38</td>
<td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Section 4: Chain-of-Thought Reasoning</td>
</tr>
<tr><td colspan="2" style="height:4px;"></td></tr>
<tr>
<td style="background:#00695C; color:white; padding:8px 14px; font-weight:bold; font-size:13px;">0:38 – 0:43</td>
<td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Section 5: Prompt Hygiene — Context, References & Safety</td>
</tr>
<tr><td colspan="2" style="height:4px;"></td></tr>
<tr>
<td style="background:#00695C; color:white; padding:8px 14px; font-weight:bold; font-size:13px;">0:43 – 0:45</td>
<td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Wrap-Up: Live Demo & Transition to Module 3</td>
</tr>
</table>

---

<table style="width:100%; border-collapse:collapse;">
<tr>
<td style="background:#00695C; color:white; padding:8px 16px; font-weight:bold;">0:00 – 0:08</td>
<td style="background:#E0F2F1; padding:8px 16px; color:#00695C; font-weight:bold; font-size:16px;">SECTION 1: The Language of AI — Why Prompting Matters</td>
</tr>
</table>

## <span style="color:#0D47A1;">1. The Language of AI — Why Prompting Matters</span>

### <span style="color:#0D47A1;">1.1  What Is a Prompt?</span>

A prompt is the natural language instruction you give to an AI model. In GitHub Copilot, every message you type in the Chat panel, every inline edit request (`Ctrl+I`), and even the comments you write before typing a component — all of these are prompts. The quality of your prompt directly determines the quality of the React code Copilot generates.

<table style="width:100%; border-collapse:collapse;">
<tr>
<td style="border-left:5px solid #1A73E8; background:#E3F2FD; padding:16px 20px;">
<em style="color:#0D47A1; font-size:15px;">"Prompt engineering is to AI-assisted coding what requirements gathering is to software engineering. Garbage in, garbage out. Precise in, precise out."</em>
</td>
</tr>
</table>

Think of it this way: in traditional React development, you translate a design spec into JSX and TypeScript. In AI-assisted development, you translate that spec into an effective prompt, and Copilot translates the prompt into code. Your prompting skill is now the critical bottleneck in your productivity.

### <span style="color:#0D47A1;">1.2  The Prompt → Response Loop</span>

Every interaction with GitHub Copilot follows this cycle:

<table style="width:100%; border-collapse:collapse;">
<tr>
<th style="background:#1A73E8; color:white; padding:8px 12px; text-align:left;">Step</th>
<th style="background:#1A73E8; color:white; padding:8px 12px; text-align:left;">What Happens</th>
<th style="background:#1A73E8; color:white; padding:8px 12px; text-align:left;">Your Responsibility</th>
</tr>
<tr>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;"><strong>1. Context</strong></td>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;">Copilot reads your open files, <code>copilot-instructions.md</code>, and any <code>#file:</code> or <code>@workspace</code> references you've provided</td>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;">Ensure Copilot has the right context — reference the relevant component files, not the whole repo</td>
</tr>
<tr>
<td style="padding:8px 12px; border:1px solid #ccc;"><strong>2. Prompt</strong></td>
<td style="padding:8px 12px; border:1px solid #ccc;">You type a natural language instruction in Chat, inline prompt, or as a code comment</td>
<td style="padding:8px 12px; border:1px solid #ccc;">Be specific, structured, and include constraints — especially around TypeScript types and React patterns</td>
</tr>
<tr>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;"><strong>3. Processing</strong></td>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;">Copilot plans an approach and generates code, a component, hook, or test</td>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;">Understand that Copilot may interpret component requirements differently than you intend</td>
</tr>
<tr>
<td style="padding:8px 12px; border:1px solid #ccc;"><strong>4. Output</strong></td>
<td style="padding:8px 12px; border:1px solid #ccc;">Copilot presents inline completions, a Chat reply, or an Agent-mode diff across multiple files</td>
<td style="padding:8px 12px; border:1px solid #ccc;">Review every output. Accept, reject, or refine before committing anything.</td>
</tr>
<tr>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;"><strong>5. Iteration</strong></td>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;">You refine: correct mistakes, add detail, redirect the approach in a follow-up message</td>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;">Use the conversation history to iteratively improve the React output</td>
</tr>
</table>

<table style="width:100%; border-collapse:collapse;">
<tr>
<td style="border-left:5px solid #1A73E8; background:#E3F2FD; padding:14px 18px;">
<strong style="color:#0D47A1;">⭐ KEY POINT:</strong> <span style="color:#0D47A1;">Prompting is iterative, not one-shot. The best React components come from starting with a clear prompt, reviewing the output, and refining through 2–3 follow-up messages. Don't expect a complete, production-ready component on the first try.</span>
</td>
</tr>
</table>

### <span style="color:#0D47A1;">1.3  The Anatomy of an Effective Prompt (React)</span>

Every effective Chat prompt for GitHub Copilot contains some or all of these elements:

<table style="width:100%; border-collapse:collapse;">
<tr>
<th style="background:#1A73E8; color:white; padding:8px 12px; text-align:left;">Element</th>
<th style="background:#1A73E8; color:white; padding:8px 12px; text-align:left;">React Example</th>
</tr>
<tr>
<td style="background:#E3F2FD; padding:8px 12px; border:1px solid #ccc;"><strong>Role / Context</strong></td>
<td style="background:#E3F2FD; padding:8px 12px; border:1px solid #ccc;">"I'm building a React 18 + TypeScript dashboard app using Tailwind CSS and React Router v6..."</td>
</tr>
<tr>
<td style="padding:8px 12px; border:1px solid #ccc;"><strong>Specific Task</strong></td>
<td style="padding:8px 12px; border:1px solid #ccc;">"Create a reusable <code>DataTable</code> component that accepts generic row data and a column config array..."</td>
</tr>
<tr>
<td style="background:#E3F2FD; padding:8px 12px; border:1px solid #ccc;"><strong>Constraints</strong></td>
<td style="background:#E3F2FD; padding:8px 12px; border:1px solid #ccc;">"Use TypeScript generics, Tailwind for styling, support keyboard navigation, emit <code>onRowClick</code>..."</td>
</tr>
<tr>
<td style="padding:8px 12px; border:1px solid #ccc;"><strong>Output Format</strong></td>
<td style="padding:8px 12px; border:1px solid #ccc;">"Named export. Props interface above the component. Include a JSDoc comment on the component."</td>
</tr>
<tr>
<td style="background:#E3F2FD; padding:8px 12px; border:1px solid #ccc;"><strong>Examples (optional)</strong></td>
<td style="background:#E3F2FD; padding:8px 12px; border:1px solid #ccc;">"Usage: <code>&lt;DataTable&lt;User&gt; rows={users} columns={userColumns} onRowClick={handleSelect} /&gt;</code>"</td>
</tr>
<tr>
<td style="padding:8px 12px; border:1px solid #ccc;"><strong>Negative Constraints</strong></td>
<td style="padding:8px 12px; border:1px solid #ccc;">"Do NOT use any third-party table library. Do NOT use inline styles."</td>
</tr>
</table>

---

<table style="width:100%; border-collapse:collapse;">
<tr>
<td style="background:#00695C; color:white; padding:8px 16px; font-weight:bold;">0:08 – 0:18</td>
<td style="background:#E0F2F1; padding:8px 16px; color:#00695C; font-weight:bold; font-size:16px;">SECTION 2: Persistent Instructions vs. Task Prompts</td>
</tr>
</table>

## <span style="color:#0D47A1;">2. Persistent Instructions vs. Task Prompts</span>

In GitHub Copilot, there are two fundamentally different levels of prompting that work together. Understanding the distinction is essential for consistent, high-quality React code generation.

### <span style="color:#0D47A1;">2.1  Persistent Instructions: Global Context</span>

Persistent instructions set Copilot's "personality," constraints, and global behavior for your entire project. In GitHub Copilot, the primary mechanism for this is the **`.github/copilot-instructions.md`** file:

<table style="width:100%; border-collapse:collapse;">
<tr>
<th style="background:#00695C; color:white; padding:8px 12px; text-align:left;">Instruction Source</th>
<th style="background:#00695C; color:white; padding:8px 12px; text-align:left;">How It Works</th>
</tr>
<tr>
<td style="background:#E0F2F1; padding:8px 12px; border:1px solid #ccc;"><strong>.github/copilot-instructions.md</strong></td>
<td style="background:#E0F2F1; padding:8px 12px; border:1px solid #ccc;">Automatically applied to every Copilot Chat interaction in the repository. Defines your React stack, coding conventions, component standards, and safety guardrails.</td>
</tr>
<tr>
<td style="padding:8px 12px; border:1px solid #ccc;"><strong>VS Code Personal Instructions</strong></td>
<td style="padding:8px 12px; border:1px solid #ccc;">User-level defaults that apply across all your projects. Set in VS Code Settings → GitHub Copilot → Chat → Personal Instructions. Great for personal style preferences.</td>
</tr>
<tr>
<td style="background:#E0F2F1; padding:8px 12px; border:1px solid #ccc;"><strong>Custom Instructions (per chat)</strong></td>
<td style="background:#E0F2F1; padding:8px 12px; border:1px solid #ccc;">In Agent mode, you can add additional instructions at the start of a specific task. Useful for scoping a single session to a specific module or feature.</td>
</tr>
</table>

Here's an example `copilot-instructions.md` that acts as a persistent prompt for a React project:

```markdown
# GitHub Copilot Instructions

## Project
React 18 + TypeScript 5 application. Stack: Vite, React Router v6,
React Query v5, Zustand, Tailwind CSS, Jest, React Testing Library.

## Component Standards
- Functional components with hooks only — no class components
- Named exports for all components: `export function MyComponent`
- TypeScript prop interface defined immediately above each component
- All props interfaces named `[ComponentName]Props`
- Prefer composition over inheritance; extract custom hooks for shared logic

## Styling
- Use Tailwind utility classes only — no inline styles, no CSS modules
- Use `clsx` for conditional class logic
- Follow the design token variables in `src/styles/tokens.css`

## Testing
- Jest + React Testing Library for all component and hook tests
- Test behavior via `getByRole` and `getByText`, not implementation details
- Every component test must include at least one `axe` accessibility check
- Co-locate test files: `Button.tsx` → `Button.test.tsx`

## Safety
- NEVER suggest `dangerouslySetInnerHTML` with unsanitized input
- NEVER hardcode API endpoint URLs — use the `API_BASE_URL` env variable
- Always use mock data from `/src/mocks/` for development and tests
```

<table style="width:100%; border-collapse:collapse;">
<tr>
<td style="border-left:5px solid #1A73E8; background:#E3F2FD; padding:14px 18px;">
<strong style="color:#0D47A1;">⭐ KEY POINT:</strong> <span style="color:#0D47A1;"><code>copilot-instructions.md</code> is the single most powerful Copilot configuration tool. It is applied automatically to every Chat interaction, so Copilot will consistently use your stack, your naming patterns, and your testing conventions without you repeating them in every prompt. It lives in your repo and is version-controlled alongside your code.</span>
</td>
</tr>
</table>

### <span style="color:#0D47A1;">2.2  Task Prompts: Single Interactions</span>

A task prompt is what you type in the Copilot Chat panel, in an inline prompt (`Ctrl+I`), or as a comment that triggers an inline completion. It is a specific request for a specific action:

<table style="width:100%; border-collapse:collapse;">
<tr>
<th style="background:#0D47A1; color:white; padding:8px 12px; text-align:left;">Task Prompt Type</th>
<th style="background:#0D47A1; color:white; padding:8px 12px; text-align:left;">React Example</th>
<th style="background:#0D47A1; color:white; padding:8px 12px; text-align:left;">When to Use</th>
</tr>
<tr>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;"><strong>Direct instruction</strong></td>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;">"Create a <code>useDebounce</code> hook that delays state updates by a configurable interval"</td>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;">Simple, well-defined hooks or components with clear output</td>
</tr>
<tr>
<td style="padding:8px 12px; border:1px solid #ccc;"><strong>Question</strong></td>
<td style="padding:8px 12px; border:1px solid #ccc;">"What does the <code>useCartStore</code> hook do and where is it used in this app?"</td>
<td style="padding:8px 12px; border:1px solid #ccc;">Understanding existing code, exploring component relationships</td>
</tr>
<tr>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;"><strong>Modification</strong></td>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;">"Add loading, error, and empty states to the <code>ProductList</code> component"</td>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;">Extending or refactoring an existing component</td>
</tr>
<tr>
<td style="padding:8px 12px; border:1px solid #ccc;"><strong>Multi-step</strong></td>
<td style="padding:8px 12px; border:1px solid #ccc;">"Create a modal, a form inside it, hook it up to the submit handler, and add tests"</td>
<td style="padding:8px 12px; border:1px solid #ccc;">Sequential feature work — better handled via Agent mode</td>
</tr>
<tr>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;"><strong>Debugging</strong></td>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;">"Here's the console error: [paste error]. Why is this happening in my <code>useEffect</code>?"</td>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;">Paste errors or warnings directly for diagnosis</td>
</tr>
<tr>
<td style="padding:8px 12px; border:1px solid #ccc;"><strong>Review</strong></td>
<td style="padding:8px 12px; border:1px solid #ccc;">"Review this component for accessibility issues, unnecessary re-renders, and missing error boundaries"</td>
<td style="padding:8px 12px; border:1px solid #ccc;">Pre-commit code quality checks</td>
</tr>
</table>

### <span style="color:#0D47A1;">2.3  How Persistent Instructions and Task Prompts Work Together</span>

The persistent instructions (`copilot-instructions.md`) set the rules; the task prompt provides the specific request. Copilot combines both automatically:

```tsx
// Your copilot-instructions.md says:
//   - use functional components with named exports
//   - use TypeScript prop interfaces named [Component]Props
//   - use Tailwind classes only, no inline styles
//   - include at least one accessibility attribute

// Your task prompt in Chat:
// "Create a Badge component that shows a count with a color variant"

// Copilot automatically produces (applying instructions):
interface BadgeProps {
  count: number;
  variant: 'primary' | 'success' | 'warning' | 'danger';
  label?: string; // for screen readers
}

export function Badge({ count, variant, label }: BadgeProps) {
  const variantClasses = {
    primary: 'bg-blue-100 text-blue-800',
    success: 'bg-green-100 text-green-800',
    warning: 'bg-yellow-100 text-yellow-800',
    danger: 'bg-red-100 text-red-800',
  };

  return (
    <span
      className={`inline-flex items-center rounded-full px-2.5 py-0.5 text-xs font-medium ${variantClasses[variant]}`}
      aria-label={label ?? `${count} items`}
    >
      {count}
    </span>
  );
}
// ✅ Named export, prop interface, Tailwind only, aria-label — all from instructions
```

<table style="width:100%; border-collapse:collapse;">
<tr>
<td style="background:#F3E5F5; padding:14px 18px; border:1px solid #CE93D8;">
<strong style="color:#6A1B9A;">💬 QUICK CHECK (1 minute)</strong><br>
<em style="color:#6A1B9A;">• Think about your current React project. What are 3 rules you'd put in a <code>copilot-instructions.md</code> file?</em><br>
<em style="color:#6A1B9A;">• Examples: component patterns, naming conventions, CSS approach, state management library, testing requirements, forbidden patterns</em><br>
<em style="color:#6A1B9A;">• We'll write your own <code>copilot-instructions.md</code> during the Module 4 deep-dive</em>
</td>
</tr>
</table>

---

<table style="width:100%; border-collapse:collapse;">
<tr>
<td style="background:#00695C; color:white; padding:8px 16px; font-weight:bold;">0:18 – 0:28</td>
<td style="background:#E0F2F1; padding:8px 16px; color:#00695C; font-weight:bold; font-size:16px;">SECTION 3: Zero-Shot, One-Shot & Few-Shot Patterns</td>
</tr>
</table>

## <span style="color:#0D47A1;">3. Zero-Shot, One-Shot & Few-Shot Patterns</span>

These are the foundational prompting patterns used across all AI systems. They describe how many examples you provide to Copilot before making your request.

### <span style="color:#0D47A1;">3.1  Zero-Shot Prompting</span>

Give Copilot a direct instruction with no examples. Copilot relies entirely on its training and your `copilot-instructions.md` to understand what you want.

**Example — Zero-Shot:**

```text
Create a React hook called useLocalStorage that syncs a state
value to localStorage. Accept a key string and an initial value.
Use TypeScript generics. Handle JSON parse errors gracefully.
```

<table style="width:100%; border-collapse:collapse;">
<tr>
<th style="background:#2E7D32; color:white; padding:8px 12px; text-align:left;">When to Use Zero-Shot</th>
<th style="background:#2E7D32; color:white; padding:8px 12px; text-align:left;">When to Avoid Zero-Shot</th>
</tr>
<tr>
<td style="background:#E8F5E9; padding:8px 12px; border:1px solid #ccc;"><strong>Standard React hooks or components</strong></td>
<td style="background:#E8F5E9; padding:8px 12px; border:1px solid #ccc;">Tasks requiring a specific component API shape</td>
</tr>
<tr>
<td style="padding:8px 12px; border:1px solid #ccc;"><strong>Well-known UI patterns</strong></td>
<td style="padding:8px 12px; border:1px solid #ccc;">Components that must match your design system exactly</td>
</tr>
<tr>
<td style="background:#E8F5E9; padding:8px 12px; border:1px solid #ccc;"><strong>Utility functions with clear intent</strong></td>
<td style="background:#E8F5E9; padding:8px 12px; border:1px solid #ccc;">When you need exact prop naming or JSX structure</td>
</tr>
<tr>
<td style="padding:8px 12px; border:1px solid #ccc;"><strong>Quick prototyping</strong></td>
<td style="padding:8px 12px; border:1px solid #ccc;">Complex multi-component feature flows</td>
</tr>
</table>

### <span style="color:#0D47A1;">3.2  One-Shot Prompting</span>

Provide one example of the desired component or hook pattern before your actual request. This dramatically improves consistency when building a family of related components.

**Example — One-Shot:**

```text
I need form field components that follow this pattern:

// Example (already implemented):
interface TextFieldProps {
  label: string;
  name: string;
  value: string;
  onChange: (value: string) => void;
  error?: string;
  required?: boolean;
}

export function TextField({ label, name, value, onChange, error, required }: TextFieldProps) {
  return (
    <div className="flex flex-col gap-1">
      <label htmlFor={name} className="text-sm font-medium text-gray-700">
        {label} {required && <span className="text-red-500">*</span>}
      </label>
      <input
        id={name}
        name={name}
        value={value}
        onChange={(e) => onChange(e.target.value)}
        className={`rounded-md border px-3 py-2 text-sm focus:outline-none focus:ring-2 focus:ring-blue-500 ${error ? 'border-red-500' : 'border-gray-300'}`}
        aria-describedby={error ? `${name}-error` : undefined}
      />
      {error && <p id={`${name}-error`} className="text-xs text-red-500">{error}</p>}
    </div>
  );
}

Now create similar components for:
1. SelectField (dropdown, accepts an options array)
2. CheckboxField (single checkbox with label)
3. TextareaField (multiline input with rows prop)
```

<table style="width:100%; border-collapse:collapse;">
<tr>
<td style="border-left:5px solid #1A73E8; background:#E3F2FD; padding:14px 18px;">
<strong style="color:#0D47A1;">⭐ KEY POINT:</strong> <span style="color:#0D47A1;">One-shot prompting is the sweet spot for React component families. A single example communicates your preferred props interface shape, Tailwind class patterns, accessibility approach, and error handling more precisely than any written description could.</span>
</td>
</tr>
</table>

### <span style="color:#0D47A1;">3.3  Few-Shot Prompting</span>

Provide 2–5 examples to establish a clear pattern. Especially useful when building a design system — you want every component to follow a highly specific and consistent structure.

**Example — Few-Shot:**

```text
Map these design spec descriptions to Tailwind variant class strings.
Follow the exact format shown:

Input: "Primary action button, default size"
Output: { base: "rounded-md font-medium focus:outline-none focus:ring-2", variant: "bg-blue-600 text-white hover:bg-blue-700 focus:ring-blue-500", size: "px-4 py-2 text-sm" }

Input: "Destructive action button, small size"
Output: { base: "rounded-md font-medium focus:outline-none focus:ring-2", variant: "bg-red-600 text-white hover:bg-red-700 focus:ring-red-500", size: "px-3 py-1.5 text-xs" }

Input: "Ghost button (transparent background), default size"
Output: { base: "rounded-md font-medium focus:outline-none focus:ring-2", variant: "bg-transparent text-gray-700 hover:bg-gray-100 focus:ring-gray-400", size: "px-4 py-2 text-sm" }

Now produce the class strings for:
"Secondary outlined button, large size"
"Success button, default size"
"Link-style button (no background or border), default size"
```

### <span style="color:#0D47A1;">3.4  Choosing the Right Pattern</span>

<table style="width:100%; border-collapse:collapse;">
<tr>
<th style="background:#0D47A1; color:white; padding:8px 12px; text-align:left;">Pattern</th>
<th style="background:#0D47A1; color:white; padding:8px 12px; text-align:left;"># Examples</th>
<th style="background:#0D47A1; color:white; padding:8px 12px; text-align:left;">Best For</th>
</tr>
<tr>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;"><strong>Zero-Shot</strong></td>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;">0</td>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;">Standard hooks, utility functions, simple prototyping, well-known React patterns</td>
</tr>
<tr>
<td style="padding:8px 12px; border:1px solid #ccc;"><strong>One-Shot</strong></td>
<td style="padding:8px 12px; border:1px solid #ccc;">1</td>
<td style="padding:8px 12px; border:1px solid #ccc;">Establishing component API shape, prop naming, Tailwind class style, test structure</td>
</tr>
<tr>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;"><strong>Few-Shot</strong></td>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;">2–5</td>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;">Design system components, complex data transformations, domain-specific prop mapping</td>
</tr>
</table>

<table style="width:100%; border-collapse:collapse;">
<tr>
<td style="border-left:5px solid #C62828; background:#FFEBEE; padding:14px 18px;">
<strong style="color:#C62828;">⚠️ WARNING:</strong> <span style="color:#C62828;">More examples are not always better. Beyond 5 examples, you risk filling Copilot's context with samples at the expense of actual task context. If you need more than 5 examples to communicate your intent, move those patterns into your <code>copilot-instructions.md</code> instead — that way they apply to every interaction without consuming prompt space.</span>
</td>
</tr>
</table>

---

<table style="width:100%; border-collapse:collapse;">
<tr>
<td style="background:#00695C; color:white; padding:8px 16px; font-weight:bold;">0:28 – 0:38</td>
<td style="background:#E0F2F1; padding:8px 16px; color:#00695C; font-weight:bold; font-size:16px;">SECTION 4: Chain-of-Thought Reasoning</td>
</tr>
</table>

## <span style="color:#0D47A1;">4. Chain-of-Thought Reasoning</span>

Chain-of-Thought (CoT) prompting asks Copilot to reason step-by-step before generating code. This is the single most effective technique for complex React tasks that require planning — such as multi-component features, state management decisions, or full-page refactors.

### <span style="color:#0D47A1;">4.1  What Is Chain-of-Thought?</span>

Instead of asking Copilot to jump directly to a component, you ask it to think through the architecture first. This mirrors how experienced React engineers approach complex tasks: design the component API before writing JSX.

<table style="width:100%; border-collapse:collapse;">
<tr>
<th style="background:#0D47A1; color:white; padding:8px 12px; text-align:left;">Without CoT (Direct)</th>
<th style="background:#0D47A1; color:white; padding:8px 12px; text-align:left;">With CoT (Step-by-Step)</th>
</tr>
<tr>
<td style="background:#E3F2FD; padding:8px 12px; border:1px solid #ccc;"><strong>"Build the checkout flow"</strong></td>
<td style="background:#E3F2FD; padding:8px 12px; border:1px solid #ccc;">"Before writing any code, outline the components needed for a checkout flow: list each component, its props, what state it owns, and how they communicate. Then implement step by step."</td>
</tr>
<tr>
<td style="padding:8px 12px; border:1px solid #ccc;">Copilot jumps to code immediately</td>
<td style="padding:8px 12px; border:1px solid #ccc;">Copilot plans the component tree, then codes with clear intent</td>
</tr>
<tr>
<td style="background:#E3F2FD; padding:8px 12px; border:1px solid #ccc;">May miss async states, error boundaries, or loading skeletons</td>
<td style="background:#E3F2FD; padding:8px 12px; border:1px solid #ccc;">More likely to account for all UI states during the planning phase</td>
</tr>
<tr>
<td style="padding:8px 12px; border:1px solid #ccc;">Often produces large monolithic components</td>
<td style="padding:8px 12px; border:1px solid #ccc;">Produces well-decomposed, individually testable components and hooks</td>
</tr>
</table>

### <span style="color:#0D47A1;">4.2  CoT Prompting Techniques for GitHub Copilot</span>

**Technique 1: Explicit Step-by-Step**

```text
I need to build a multi-step user registration form in React.
Before writing any code, please:
1. List the steps/pages in the wizard (e.g., Account Info, Profile, Confirmation)
2. Identify the components you'll create and the props each needs
3. Describe how form state will be managed across steps
4. Note any edge cases (validation per step, going back, submission errors)
5. Then implement Step 1 as the first component
```

**Technique 2: "Think Before You Code"**

```text
Think step by step about how to architect a React feature that:
- Shows a filterable list of products fetched from an API
- Allows users to add items to a cart (persisted in localStorage)
- Shows a live cart summary in a sidebar

Explain your component structure and state management approach first,
then write the code.
```

**Technique 3: Agent Mode Planning**

Copilot's Agent mode is the closest equivalent to a "plan and execute" workflow. Use it for multi-file feature work:

```text
# In Copilot Chat, switch to Agent mode:
# Click the mode selector in the Chat panel → select "Agent"

# Then describe the full feature:
"I need a complete dark mode feature for this React app.
Before making any changes, describe every file you plan to
modify and what you will change in each one. Wait for my
approval before starting."

# Agent mode will:
# 1. Explore the codebase to understand the current setup
# 2. Propose a plan listing every file to be touched
# 3. Wait for you to confirm before making edits
# 4. Execute the changes file by file

# This is your safety net for multi-file changes.
```

<table style="width:100%; border-collapse:collapse;">
<tr>
<td style="border-left:5px solid #1A73E8; background:#E3F2FD; padding:14px 18px;">
<strong style="color:#0D47A1;">⭐ KEY POINT:</strong> <span style="color:#0D47A1;">Agent mode with an explicit "plan first, wait for approval" instruction is your safety net for any React change that touches more than 2–3 files. Review the plan, add your feedback, and only then tell Copilot to proceed. This prevents cascading unintended edits in a large component tree.</span>
</td>
</tr>
</table>

### <span style="color:#0D47A1;">4.3  Structured Thinking for Complex React Decisions</span>

For complex architectural decisions — like choosing between local state, Context, and a state management library — ask Copilot to reason through trade-offs explicitly before making a recommendation:

<table style="width:100%; border-collapse:collapse;">
<tr>
<th style="background:#1A73E8; color:white; padding:8px 12px; text-align:left;">Use Case</th>
<th style="background:#1A73E8; color:white; padding:8px 12px; text-align:left;">Why Structured Thinking Helps</th>
</tr>
<tr>
<td style="background:#E3F2FD; padding:8px 12px; border:1px solid #ccc;"><strong>State management decisions</strong></td>
<td style="background:#E3F2FD; padding:8px 12px; border:1px solid #ccc;">Copilot evaluates <code>useState</code> vs. Context vs. Zustand trade-offs for your specific use case before committing to an approach</td>
</tr>
<tr>
<td style="padding:8px 12px; border:1px solid #ccc;"><strong>Component decomposition</strong></td>
<td style="background:#E3F2FD; padding:8px 12px; border:1px solid #ccc;">Identifies natural split points in a large component before generating new files</td>
</tr>
<tr>
<td style="background:#E3F2FD; padding:8px 12px; border:1px solid #ccc;"><strong>Performance optimization</strong></td>
<td style="background:#E3F2FD; padding:8px 12px; border:1px solid #ccc;">Reasons about re-render causes before suggesting <code>memo</code>, <code>useCallback</code>, or <code>useMemo</code> — avoids premature optimization</td>
</tr>
<tr>
<td style="padding:8px 12px; border:1px solid #ccc;"><strong>Data fetching strategy</strong></td>
<td style="padding:8px 12px; border:1px solid #ccc;">Weighs React Query vs. SWR vs. <code>useEffect</code> for your caching and revalidation requirements</td>
</tr>
<tr>
<td style="background:#E3F2FD; padding:8px 12px; border:1px solid #ccc;"><strong>Test strategy design</strong></td>
<td style="background:#E3F2FD; padding:8px 12px; border:1px solid #ccc;">Plans which interactions to test, which to mock, and what the coverage strategy should be before writing a single test</td>
</tr>
</table>

```text
# Example — structured thinking prompt for state management:

"We're building a shopping cart feature. Before implementing,
think step by step about state management:
1. What state needs to be shared across how many components?
2. Does this state need to persist across page reloads?
3. What are the read/write patterns?
4. Evaluate: useState + prop drilling, Context + useReducer, or Zustand
5. Recommend one approach with justification for this specific case"
```

### <span style="color:#0D47A1;">4.4  When NOT to Use CoT</span>

CoT is not always necessary. For simple React tasks, it adds overhead without benefit:

- Creating a simple presentational component with clear specs — use zero-shot
- Adding a prop to an existing component — inline prompt (`Ctrl+I`) is faster
- Generating tests for a component that already exists — use `/tests` slash command
- Adding JSDoc to existing functions — direct instruction or inline prompt

<table style="width:100%; border-collapse:collapse;">
<tr>
<td style="border-left:5px solid #1A73E8; background:#E3F2FD; padding:14px 18px;">
<strong style="color:#0D47A1;">⭐ KEY POINT:</strong> <span style="color:#0D47A1;">Use CoT for React tasks where you would need to sketch an architecture diagram or write pseudocode before you started coding. If the task is mechanical or well-defined (add a prop, fix a bug, generate a test), skip CoT and use direct prompting for speed.</span>
</td>
</tr>
</table>

---

<table style="width:100%; border-collapse:collapse;">
<tr>
<td style="background:#00695C; color:white; padding:8px 16px; font-weight:bold;">0:38 – 0:43</td>
<td style="background:#E0F2F1; padding:8px 16px; color:#00695C; font-weight:bold; font-size:16px;">SECTION 5: Prompt Hygiene — Context, References & Safety</td>
</tr>
</table>

## <span style="color:#0D47A1;">5. Prompt Hygiene: Context, References & Safety</span>

Even with great prompting patterns, poor context management will degrade results. This section covers the practical skills that separate effective Copilot users from frustrated ones.

### <span style="color:#0D47A1;">5.1  Context References in Copilot Chat</span>

GitHub Copilot's reference system lets you precisely control what files and workspace context Copilot sees for a given prompt:

<table style="width:100%; border-collapse:collapse;">
<tr>
<th style="background:#1A73E8; color:white; padding:8px 12px; text-align:left;">Reference</th>
<th style="background:#1A73E8; color:white; padding:8px 12px; text-align:left;">What It Does</th>
</tr>
<tr>
<td style="background:#E3F2FD; padding:8px 12px; border:1px solid #ccc;"><strong>@workspace</strong></td>
<td style="background:#E3F2FD; padding:8px 12px; border:1px solid #ccc;">Gives Copilot awareness of the entire project structure. Use for questions about architecture or when the task spans many files.</td>
</tr>
<tr>
<td style="padding:8px 12px; border:1px solid #ccc;"><strong>#file:path/to/Component.tsx</strong></td>
<td style="padding:8px 12px; border:1px solid #ccc;">Include a specific file in Copilot's context for this prompt. Most precise and token-efficient.</td>
</tr>
<tr>
<td style="background:#E3F2FD; padding:8px 12px; border:1px solid #ccc;"><strong>#selection</strong></td>
<td style="background:#E3F2FD; padding:8px 12px; border:1px solid #ccc;">Reference only the currently selected code in the editor. Ideal for scoped questions or refactors.</td>
</tr>
<tr>
<td style="padding:8px 12px; border:1px solid #ccc;"><strong>#editor</strong></td>
<td style="padding:8px 12px; border:1px solid #ccc;">Reference the full content of the currently active editor tab.</td>
</tr>
<tr>
<td style="background:#E3F2FD; padding:8px 12px; border:1px solid #ccc;"><strong>#terminalLastCommand</strong></td>
<td style="background:#E3F2FD; padding:8px 12px; border:1px solid #ccc;">Include the last terminal command and its output. Useful for debugging failed builds or test runs.</td>
</tr>
<tr>
<td style="padding:8px 12px; border:1px solid #ccc;"><strong>Drag & Drop</strong></td>
<td style="padding:8px 12px; border:1px solid #ccc;">Drag a file from the VS Code Explorer into the Copilot Chat input to attach it as context. Works for images too.</td>
</tr>
</table>

**Effective reference usage in React projects:**

```text
# BAD: Vague prompt with no context
"Fix the bug in the cart"

# GOOD: Specific prompt with precise file reference
"There's a stale state bug in #file:src/hooks/useCart.ts — the
cart total doesn't update when quantity changes. Here's the
console output: #terminalLastCommand"

# GOOD: Cross-file refactor with explicit references
"Refactor #file:src/components/ProductCard.tsx to use the same
loading skeleton pattern as #file:src/components/UserCard.tsx"

# GOOD: Architecture question with workspace context
"@workspace Where is user authentication state currently managed,
and is it consistent across the app?"
```

### <span style="color:#0D47A1;">5.2  Managing Copilot's Context</span>

Copilot Chat has a limited context window per conversation. When conversations grow long, context management becomes critical:

<table style="width:100%; border-collapse:collapse;">
<tr>
<th style="background:#00695C; color:white; padding:8px 12px; text-align:left;">Technique</th>
<th style="background:#00695C; color:white; padding:8px 12px; text-align:left;">How</th>
<th style="background:#00695C; color:white; padding:8px 12px; text-align:left;">When to Use</th>
</tr>
<tr>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;"><strong>New Chat</strong></td>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;">Click "New Chat" (+ icon) in the Chat panel</td>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;">Switching to a completely different task. Clears all conversation history.</td>
</tr>
<tr>
<td style="padding:8px 12px; border:1px solid #ccc;"><strong>Focused <code>#file:</code> refs</strong></td>
<td style="padding:8px 12px; border:1px solid #ccc;">Reference only the specific files relevant to the current prompt</td>
<td style="padding:8px 12px; border:1px solid #ccc;">Every prompt — avoid using <code>@workspace</code> for narrow, file-specific tasks</td>
</tr>
<tr>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;"><strong>Task-scoped chats</strong></td>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;">Start a new Chat per feature or module, not one giant session</td>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;">Long working sessions with multiple unrelated tasks</td>
</tr>
<tr>
<td style="padding:8px 12px; border:1px solid #ccc;"><strong>Inline Chat (<kbd>Ctrl+I</kbd>)</strong></td>
<td style="padding:8px 12px; border:1px solid #ccc;">Use inline prompts for single-component edits instead of Chat</td>
<td style="padding:8px 12px; border:1px solid #ccc;">When the edit is scoped to the active file — faster and lighter than Chat</td>
</tr>
</table>

<table style="width:100%; border-collapse:collapse;">
<tr>
<td style="border-left:5px solid #1A73E8; background:#E3F2FD; padding:14px 18px;">
<strong style="color:#0D47A1;">⭐ KEY POINT:</strong> <span style="color:#0D47A1;">Start a new Copilot Chat for each distinct feature or debugging session. A dedicated chat keeps context clean and focused. Long, unfocused conversations cause Copilot to lose track of earlier decisions — the same symptom as a context window filling up.</span>
</td>
</tr>
</table>

### <span style="color:#0D47A1;">5.3  Snippet Safety: What to Include in Prompts</span>

When pasting code into Copilot Chat, follow these rules:

<table style="width:100%; border-collapse:collapse;">
<tr>
<td style="background:#E8F5E9; padding:14px 18px; border:1px solid #A5D6A7;">
<strong style="color:#2E7D32;">✅ SNIPPET SAFETY RULES</strong><br>
<em style="color:#333;">• DO paste console errors and React error boundary stack traces verbatim — Copilot needs the exact error</em><br>
<em style="color:#333;">• DO include the relevant component's TypeScript interface and JSX for context</em><br>
<em style="color:#333;">• DO include failed test output so Copilot can see what assertion is breaking</em><br>
<em style="color:#333;">• DO NOT paste entire page-level components when only a specific hook is relevant — use <code>#file:</code> instead</em><br>
<em style="color:#333;">• DO NOT include API keys, environment variables, auth tokens, or backend URLs in prompts</em><br>
<em style="color:#333;">• DO NOT paste real user data or PII, even as example data — use fake/generated data</em><br>
<em style="color:#333;">• SANITIZE proprietary component or feature names before pasting: use generic names like <code>FeatureWidget</code> instead of <code>AcmeCorpQ4RevenueCalculator</code></em>
</td>
</tr>
</table>

### <span style="color:#0D47A1;">5.4  Common Prompt Anti-Patterns (React Context)</span>

<table style="width:100%; border-collapse:collapse;">
<tr>
<th style="background:#C62828; color:white; padding:8px 12px; text-align:left;">Anti-Pattern</th>
<th style="background:#C62828; color:white; padding:8px 12px; text-align:left;">Better Alternative</th>
</tr>
<tr>
<td style="background:#FFEBEE; padding:8px 12px; border:1px solid #ccc;"><strong>"Fix the component" (no context)</strong></td>
<td style="background:#FFEBEE; padding:8px 12px; border:1px solid #ccc;">"Fix the infinite re-render in #file:src/components/Feed.tsx. The <code>useEffect</code> runs on every render. Error: [paste console output]"</td>
</tr>
<tr>
<td style="padding:8px 12px; border:1px solid #ccc;"><strong>"Make it better" (vague)</strong></td>
<td style="padding:8px 12px; border:1px solid #ccc;">"Refactor #file:UserProfile.tsx to extract the avatar upload logic into a custom <code>useAvatarUpload</code> hook"</td>
</tr>
<tr>
<td style="background:#FFEBEE; padding:8px 12px; border:1px solid #ccc;"><strong>"Write tests" (underspecified)</strong></td>
<td style="background:#FFEBEE; padding:8px 12px; border:1px solid #ccc;">"Write RTL tests for #file:LoginForm.tsx covering: valid submission, empty fields, incorrect password error, and loading state"</td>
</tr>
<tr>
<td style="padding:8px 12px; border:1px solid #ccc;"><strong>"Build the whole feature" (too broad)</strong></td>
<td style="padding:8px 12px; border:1px solid #ccc;">"Start with step 1: create the <code>useProductSearch</code> hook with debouncing. We'll build the UI component next."</td>
</tr>
<tr>
<td style="background:#FFEBEE; padding:8px 12px; border:1px solid #ccc;"><strong>Pasting 300 lines of JSX inline</strong></td>
<td style="background:#FFEBEE; padding:8px 12px; border:1px solid #ccc;">"See #file:src/pages/Dashboard.tsx. Focus on the <code>MetricsPanel</code> component (around line 85)."</td>
</tr>
<tr>
<td style="padding:8px 12px; border:1px solid #ccc;"><strong>Repeating the same failed prompt</strong></td>
<td style="padding:8px 12px; border:1px solid #ccc;">"That didn't work — the types are wrong because the API returns <code>null</code> for optional fields. Try again accounting for that."</td>
</tr>
</table>

---

<table style="width:100%; border-collapse:collapse;">
<tr>
<td style="background:#00695C; color:white; padding:8px 16px; font-weight:bold;">0:43 – 0:45</td>
<td style="background:#E0F2F1; padding:8px 16px; color:#00695C; font-weight:bold; font-size:16px;">WRAP-UP: Live Demo & Transition to Module 3</td>
</tr>
</table>

## <span style="color:#0D47A1;">6. Live Demo: React Feature Prompting Workflow</span>

Let's put it all together. Here's a real-world prompting workflow that combines every technique from this module:

### <span style="color:#0D47A1;">6.1  The Task</span>

Build a reusable `<Pagination>` component and a `usePagination` hook that a `ProductList` page component can use to page through API results.

### <span style="color:#0D47A1;">6.2  The Prompting Workflow</span>

<table style="width:100%; border-collapse:collapse;">
<tr>
<td style="background:#FFF3E0; padding:14px 18px; border:1px solid #FFCC80;">
<strong style="color:#E65100;">🚀 LIVE DEMO: Full Prompting Workflow (React)</strong>
<ul style="color:#333; margin:10px 0; padding-left:20px;">
<li><strong>Step 1 (Persistent Instructions):</strong> Show the <code>copilot-instructions.md</code> — point out that TypeScript, Tailwind, named exports, and test co-location are already defined there</li>
<li><strong>Step 2 (CoT / Agent Planning):</strong> In Agent mode, ask Copilot to "plan the files and components needed for a reusable pagination feature — list each file and what it will contain. Wait for approval."</li>
<li><strong>Step 3 (One-Shot):</strong> Show an existing hook (e.g., <code>useSearch.ts</code>) as a pattern example, then ask Copilot to generate <code>usePagination.ts</code> following the same structure</li>
<li><strong>Step 4 (Zero-Shot):</strong> Ask Copilot to generate the <code>Pagination</code> component from the hook's return values</li>
<li><strong>Step 5 (Slash Command):</strong> Select the generated component → right-click → Copilot → Generate Tests (equivalent of <code>/tests</code>)</li>
<li><strong>Step 6 (Iteration):</strong> Review the generated tests, identify a missing edge case (page=0, totalPages=1), refine with a follow-up prompt</li>
<li><strong>Step 7 (Debugging):</strong> Use <code>#terminalLastCommand</code> to feed Copilot the failing test output and ask it to fix the component</li>
</ul>
</td>
</tr>
</table>

---

## <span style="color:#1A73E8;">MODULE 2 RECAP</span>

<table style="width:100%; border-collapse:collapse;">
<tr>
<td style="background:#E3F2FD; padding:10px 14px; border-bottom:1px solid #BBDEFB;">✅ Prompting is a skill, not just typing. Specific, structured prompts produce dramatically better React components than vague ones.</td>
</tr>
<tr>
<td style="padding:10px 14px; border-bottom:1px solid #BBDEFB;">✅ Persistent instructions (<code>copilot-instructions.md</code>) set project-wide rules; task prompts are your specific requests. They work together automatically.</td>
</tr>
<tr>
<td style="background:#E3F2FD; padding:10px 14px; border-bottom:1px solid #BBDEFB;">✅ Zero-shot for simple hooks and components, one-shot for building consistent component families, few-shot for design system patterns. One-shot is the sweet spot.</td>
</tr>
<tr>
<td style="padding:10px 14px; border-bottom:1px solid #BBDEFB;">✅ Chain-of-Thought and Agent mode "plan first" workflows force Copilot to think before coding — essential for multi-component features and page-level refactors.</td>
</tr>
<tr>
<td style="background:#E3F2FD; padding:10px 14px; border-bottom:1px solid #BBDEFB;">✅ Prompt hygiene matters: use <code>#file:</code> and <code>@workspace</code> for context, start fresh chats for distinct tasks, and sanitize all snippets before pasting.</td>
</tr>
<tr>
<td style="padding:10px 14px;">✅ Common anti-patterns (vague prompts, no context, too broad, repeating failures) waste time. Be specific, constrained, and iterative.</td>
</tr>
</table>

---

## <span style="color:#1A73E8;">QUICK REFERENCE CARD</span>

Keep this reference handy during labs and exercises:

<table style="width:100%; border-collapse:collapse;">
<tr>
<th style="background:#2E7D32; color:white; padding:8px 12px; text-align:left;">Technique</th>
<th style="background:#2E7D32; color:white; padding:8px 12px; text-align:left;">When to Use</th>
<th style="background:#2E7D32; color:white; padding:8px 12px; text-align:left;">Key Phrase / Action</th>
</tr>
<tr>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;"><strong>Zero-Shot</strong></td>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;">Simple, well-defined React tasks</td>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;">"Create a hook/component that..."</td>
</tr>
<tr>
<td style="padding:8px 12px; border:1px solid #ccc;"><strong>One-Shot</strong></td>
<td style="padding:8px 12px; border:1px solid #ccc;">Consistent component families</td>
<td style="padding:8px 12px; border:1px solid #ccc;">"Follow this pattern: [example]. Now create..."</td>
</tr>
<tr>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;"><strong>Few-Shot</strong></td>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;">Design system, complex prop mapping</td>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;">"Here are 3 examples: [examples]. Now handle..."</td>
</tr>
<tr>
<td style="padding:8px 12px; border:1px solid #ccc;"><strong>CoT / Agent Planning</strong></td>
<td style="padding:8px 12px; border:1px solid #ccc;">Multi-component, multi-file features</td>
<td style="padding:8px 12px; border:1px solid #ccc;">"Before writing any code, list the components..." or use Agent mode</td>
</tr>
<tr>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;"><strong>#file: reference</strong></td>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;">Providing specific file context</td>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;">"See #file:Component.tsx, focus on the useEffect..."</td>
</tr>
<tr>
<td style="padding:8px 12px; border:1px solid #ccc;"><strong>@workspace</strong></td>
<td style="padding:8px 12px; border:1px solid #ccc;">Architectural or cross-project questions</td>
<td style="padding:8px 12px; border:1px solid #ccc;">"@workspace Where is X managed in this app?"</td>
</tr>
<tr>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;"><strong>New Chat</strong></td>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;">Switching tasks, context is stale</td>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;">Click + (New Chat) to start fresh</td>
</tr>
<tr>
<td style="padding:8px 12px; border:1px solid #ccc;"><strong>Negative Constraints</strong></td>
<td style="padding:8px 12px; border:1px solid #ccc;">Preventing unwanted patterns</td>
<td style="padding:8px 12px; border:1px solid #ccc;">"Do NOT use class components. Do NOT use inline styles."</td>
</tr>
</table>

---

## <span style="color:#1A73E8;">TRANSITION TO MODULE 3</span>

You've now mastered the fundamental prompting techniques for GitHub Copilot in a React context. In Module 3, we'll build on this foundation with advanced patterns: problem decomposition for multi-file component features, the ReAct-style iteration loop, generation controls, iterative refinement strategies, and creating `copilot-instructions.md` files engineered for team-wide consistency.

---

<div style="text-align:center; color:#666; font-size:12px; padding:20px 0;">
Vibe Coding with GitHub Copilot | React Developer Track<br>
Module 2 — Prompting Techniques: Fundamentals
</div>
