<div style="text-align:center; padding: 20px 0;">

<span style="font-size:14px; color:#666666; font-weight:bold; letter-spacing:2px;">MODULE 1</span>

# <span style="color:#0D47A1;">Big Picture & Safety Primer</span>

<hr style="border: 3px solid #1A73E8; width:80%;">

</div>

<table style="width:100%; border-collapse:collapse;">
<tr>
<td style="background:#E3F2FD; text-align:center; padding:10px; border:1px solid #BBDEFB; width:25%;">
<span style="font-size:12px; color:#666;">Duration</span><br><strong style="color:#0D47A1;">45–60 min</strong>
</td>
<td style="background:#E3F2FD; text-align:center; padding:10px; border:1px solid #BBDEFB; width:25%;">
<span style="font-size:12px; color:#666;">Format</span><br><strong style="color:#0D47A1;">Lecture + Demo</strong>
</td>
<td style="background:#E3F2FD; text-align:center; padding:10px; border:1px solid #BBDEFB; width:25%;">
<span style="font-size:12px; color:#666;">Audience</span><br><strong style="color:#0D47A1;">React Developers</strong>
</td>
<td style="background:#E3F2FD; text-align:center; padding:10px; border:1px solid #BBDEFB; width:25%;">
<span style="font-size:12px; color:#666;">Day / Position</span><br><strong style="color:#0D47A1;">Day 1 / Opening</strong>
</td>
</tr>
</table>

---

## <span style="color:#1A73E8;">LEARNING OBJECTIVES</span>

By the end of this module, participants will be able to:

1. Explain what vibe coding is, where the term originated, and how it fits into professional React development
2. Describe how AI (specifically GitHub Copilot) integrates into each phase of the SDLC for frontend teams
3. Identify the strengths and limitations of AI-assisted coding for React component development, testing, and refactoring
4. Apply a practical Privacy/IP/Licensing checklist before using GitHub Copilot on any React codebase
5. Successfully install, authenticate, and run their first GitHub Copilot interaction in a React project

---

## <span style="color:#1A73E8;">SESSION TIMING BREAKDOWN</span>

<table style="width:100%; border-collapse:collapse;">
<tr>
<td style="background:#00695C; color:white; padding:8px 14px; width:120px; font-weight:bold; font-size:13px;">0:00 – 0:12</td>
<td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Section 1: What Is Vibe Coding? — Origin, Definition & Spectrum</td>
</tr>
<tr><td colspan="2" style="height:4px;"></td></tr>
<tr>
<td style="background:#00695C; color:white; padding:8px 14px; font-weight:bold; font-size:13px;">0:12 – 0:25</td>
<td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Section 2: AI in the SDLC — Where GitHub Copilot Fits</td>
</tr>
<tr><td colspan="2" style="height:4px;"></td></tr>
<tr>
<td style="background:#00695C; color:white; padding:8px 14px; font-weight:bold; font-size:13px;">0:25 – 0:35</td>
<td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Section 3: Strengths vs. Limits — Honest Assessment</td>
</tr>
<tr><td colspan="2" style="height:4px;"></td></tr>
<tr>
<td style="background:#00695C; color:white; padding:8px 14px; font-weight:bold; font-size:13px;">0:35 – 0:45</td>
<td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Section 4: Privacy / IP / Licensing Checklist</td>
</tr>
<tr><td colspan="2" style="height:4px;"></td></tr>
<tr>
<td style="background:#00695C; color:white; padding:8px 14px; font-weight:bold; font-size:13px;">0:45 – 0:55</td>
<td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Section 5: Hands-On Setup — GitHub Copilot Installation & First React Interaction</td>
</tr>
<tr><td colspan="2" style="height:4px;"></td></tr>
<tr>
<td style="background:#00695C; color:white; padding:8px 14px; font-weight:bold; font-size:13px;">0:55 – 1:00</td>
<td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Wrap-Up: Course Repo Tour & Guardrails</td>
</tr>
</table>

---

<table style="width:100%; border-collapse:collapse;">
<tr>
<td style="background:#00695C; color:white; padding:8px 16px; font-weight:bold;">0:00 – 0:12</td>
<td style="background:#E0F2F1; padding:8px 16px; color:#00695C; font-weight:bold; font-size:16px;">SECTION 1: What Is Vibe Coding?</td>
</tr>
</table>

## <span style="color:#0D47A1;">1. What Is Vibe Coding?</span>

### <span style="color:#0D47A1;">1.1  The Origin Story</span>

The term **vibe coding** was coined by **Andrej Karpathy** (co-founder of OpenAI, former Director of AI at Tesla) on February 6, 2025. In a post on X (formerly Twitter) that went viral with millions of views, he wrote:

<table style="width:100%; border-collapse:collapse;">
<tr>
<td style="border-left:5px solid #1A73E8; background:#E3F2FD; padding:16px 20px;">
<em style="color:#0D47A1; font-size:15px;">"There's a new kind of coding I call 'vibe coding', where you fully give in to the vibes, embrace exponentials, and forget that the code even exists. I just see stuff, say stuff, run stuff, and copy paste stuff, and it mostly works."</em>
<br><br>
<div style="text-align:right; color:#666; font-size:13px;">— Andrej Karpathy, February 2025</div>
</td>
</tr>
</table>

Karpathy described using AI tools combined with voice input, barely touching the keyboard. He would accept all AI suggestions without reviewing diffs, paste error messages back to the AI without comment, and let the codebase grow beyond his own comprehension. He deliberately called this approach suitable for "throwaway weekend projects."

### <span style="color:#0D47A1;">1.2  The Vibe Coding Spectrum</span>

In practice, "vibe coding" has evolved to mean different things to different people. Simon Willison, a well-known Python developer, drew an important distinction:

<table style="width:100%; border-collapse:collapse;">
<tr>
<td style="border-left:5px solid #2E7D32; background:#E8F5E9; padding:16px 20px;">
<em style="color:#2E7D32; font-size:15px;">"If an LLM wrote every line of your code, but you've reviewed, tested, and understood it all, that's not vibe coding in my book—that's using an LLM as a typing assistant."</em>
</td>
</tr>
</table>

This gives us a practical spectrum that every React developer needs to understand:

<table style="width:100%; border-collapse:collapse;">
<tr>
<th style="background:#0D47A1; color:white; padding:10px 12px; text-align:left;">Level</th>
<th style="background:#0D47A1; color:white; padding:10px 12px; text-align:left;">Approach</th>
<th style="background:#0D47A1; color:white; padding:10px 12px; text-align:left;">Appropriate For</th>
</tr>
<tr>
<td style="background:#F5F5F5; padding:10px 12px; border:1px solid #CCC;"><strong>Pure Vibe Coding</strong></td>
<td style="background:#F5F5F5; padding:10px 12px; border:1px solid #CCC;">Accept all Copilot suggestions without review. Tab through everything.</td>
<td style="background:#F5F5F5; padding:10px 12px; border:1px solid #CCC;">Weekend prototypes, throwaway demos, personal learning experiments</td>
</tr>
<tr>
<td style="padding:10px 12px; border:1px solid #CCC;"><strong>Guided Vibe Coding</strong></td>
<td style="padding:10px 12px; border:1px solid #CCC;">Use Copilot for first drafts of components and hooks, review key logic, test outputs, iterate via chat prompts.</td>
<td style="padding:10px 12px; border:1px solid #CCC;">Internal dashboards, proof-of-concepts, rapid UI prototypes</td>
</tr>
<tr>
<td style="background:#F5F5F5; padding:10px 12px; border:1px solid #CCC;"><strong>AI-Assisted Engineering</strong></td>
<td style="background:#F5F5F5; padding:10px 12px; border:1px solid #CCC;">Copilot generates React code; engineer reviews, tests, understands, and owns every component and hook.</td>
<td style="background:#F5F5F5; padding:10px 12px; border:1px solid #CCC;">Production React apps, component libraries, customer-facing features</td>
</tr>
</table>

<table style="width:100%; border-collapse:collapse;">
<tr>
<td style="border-left:5px solid #1A73E8; background:#E3F2FD; padding:14px 18px;">
<strong style="color:#0D47A1;">⭐ KEY POINT:</strong> <span style="color:#0D47A1;">This course teaches AI-Assisted Engineering (Level 3) using GitHub Copilot. You will leverage Copilot for speed and productivity, but you will always review, test, and understand the React code it generates. This is the professional standard for enterprise frontend development.</span>
</td>
</tr>
</table>

### <span style="color:#0D47A1;">1.3  Why This Matters Now</span>

- GitHub reported that Copilot users complete coding tasks up to 55% faster, with measurable gains in React component scaffolding and test writing
- By 2025, over 77% of Fortune 500 companies had adopted GitHub Copilot across their engineering teams
- GitHub Copilot Workspace launched in 2025 with full issue-to-PR automation, letting React developers go from a GitHub issue directly to a working branch with proposed changes
- Major React-based product teams began embedding Copilot Agent mode into their daily sprint workflows in early 2026, automating recurring patterns like form validation, routing, and API integration

<table style="width:100%; border-collapse:collapse;">
<tr>
<td style="border-left:5px solid #1A73E8; background:#E3F2FD; padding:14px 18px;">
<strong style="color:#0D47A1;">⭐ KEY POINT:</strong> <span style="color:#0D47A1;">You're not building throwaway weekend apps in this course. You're building production-grade React components, custom hooks, and tested feature modules. That's why we focus on the professional end of this spectrum — using GitHub Copilot as a productivity multiplier while maintaining engineering rigor.</span>
</td>
</tr>
</table>

---

<table style="width:100%; border-collapse:collapse;">
<tr>
<td style="background:#00695C; color:white; padding:8px 16px; font-weight:bold;">0:12 – 0:25</td>
<td style="background:#E0F2F1; padding:8px 16px; color:#00695C; font-weight:bold; font-size:16px;">SECTION 2: AI in the SDLC</td>
</tr>
</table>

## <span style="color:#0D47A1;">2. AI in the Software Development Lifecycle</span>

AI-assisted coding isn't just about writing components faster. GitHub Copilot can assist at every phase of the React SDLC. Here's how it maps to a typical frontend team's daily work:

<table style="width:100%; border-collapse:collapse;">
<tr>
<th style="background:#1A73E8; color:white; padding:10px 12px; text-align:left;">SDLC Phase</th>
<th style="background:#1A73E8; color:white; padding:10px 12px; text-align:left;">GitHub Copilot Capability</th>
<th style="background:#1A73E8; color:white; padding:10px 12px; text-align:left;">React Use Case Example</th>
</tr>
<tr>
<td style="background:#F5F5F5; padding:10px 12px; border:1px solid #CCC;"><strong>Requirements</strong></td>
<td style="background:#F5F5F5; padding:10px 12px; border:1px solid #CCC;">Analyze design specs, generate user stories, clarify acceptance criteria via Copilot Chat</td>
<td style="background:#F5F5F5; padding:10px 12px; border:1px solid #CCC;">Parse a Figma handoff description and generate component prop requirements</td>
</tr>
<tr>
<td style="padding:10px 12px; border:1px solid #CCC;"><strong>Design</strong></td>
<td style="padding:10px 12px; border:1px solid #CCC;">Propose component architecture, suggest folder structure, recommend React design patterns</td>
<td style="padding:10px 12px; border:1px solid #CCC;">Design a feature module structure with compound components and custom hooks</td>
</tr>
<tr>
<td style="background:#F5F5F5; padding:10px 12px; border:1px solid #CCC;"><strong>Implementation</strong></td>
<td style="background:#F5F5F5; padding:10px 12px; border:1px solid #CCC;">Generate components, scaffold hooks, add TypeScript types, complete repetitive JSX patterns</td>
<td style="background:#F5F5F5; padding:10px 12px; border:1px solid #CCC;">Scaffold a paginated data table component with sorting, filtering, and loading states</td>
</tr>
<tr>
<td style="padding:10px 12px; border:1px solid #CCC;"><strong>Testing</strong></td>
<td style="padding:10px 12px; border:1px solid #CCC;">Generate Jest + React Testing Library tests, write mocks for API calls, add accessibility assertions</td>
<td style="padding:10px 12px; border:1px solid #CCC;">Auto-generate RTL test suites for a custom <code>useAuth</code> hook and its consuming components</td>
</tr>
<tr>
<td style="background:#F5F5F5; padding:10px 12px; border:1px solid #CCC;"><strong>Code Review</strong></td>
<td style="background:#F5F5F5; padding:10px 12px; border:1px solid #CCC;">Review PRs, flag accessibility issues, identify unnecessary re-renders, suggest React best practices</td>
<td style="background:#F5F5F5; padding:10px 12px; border:1px solid #CCC;">Review a teammate's PR for missing dependency arrays, prop drilling issues, and missing key props</td>
</tr>
<tr>
<td style="padding:10px 12px; border:1px solid #CCC;"><strong>Deployment</strong></td>
<td style="padding:10px 12px; border:1px solid #CCC;">Generate GitHub Actions workflows, write Vite/Webpack config, automate release notes</td>
<td style="padding:10px 12px; border:1px solid #CCC;">Set up a CI pipeline that runs lint, Jest tests, and Lighthouse accessibility checks on every PR</td>
</tr>
<tr>
<td style="background:#F5F5F5; padding:10px 12px; border:1px solid #CCC;"><strong>Maintenance</strong></td>
<td style="background:#F5F5F5; padding:10px 12px; border:1px solid #CCC;">Debug from console errors, explain legacy class components, refactor to modern hooks</td>
<td style="background:#F5F5F5; padding:10px 12px; border:1px solid #CCC;">Convert a legacy class component with lifecycle methods to a modern functional component with hooks</td>
</tr>
<tr>
<td style="padding:10px 12px; border:1px solid #CCC;"><strong>Documentation</strong></td>
<td style="padding:10px 12px; border:1px solid #CCC;">Generate JSDoc, Storybook stories, README files, prop-type documentation</td>
<td style="padding:10px 12px; border:1px solid #CCC;">Auto-generate Storybook stories for every variant of a design system Button component</td>
</tr>
</table>

### <span style="color:#0D47A1;">2.1  What Is GitHub Copilot, Specifically?</span>

GitHub Copilot is Microsoft and GitHub's AI-powered coding assistant. Unlike simple snippet libraries or basic autocomplete, Copilot is a multi-modal AI tool that works across different interaction styles:

<table style="width:100%; border-collapse:collapse;">
<tr>
<th style="background:#1A73E8; color:white; padding:10px 12px; text-align:left;">Capability</th>
<th style="background:#1A73E8; color:white; padding:10px 12px; text-align:left;">What This Means In Practice (React)</th>
</tr>
<tr>
<td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><strong>Inline completions</strong></td>
<td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Ghost-text suggestions appear as you type. Press <kbd>Tab</kbd> to accept. Completes entire JSX blocks, hook logic, and event handlers.</td>
</tr>
<tr>
<td style="padding:10px 12px; border:1px solid #CCC;"><strong>Copilot Chat panel</strong></td>
<td style="padding:10px 12px; border:1px solid #CCC;">A conversational interface inside VS Code. Ask questions about your React codebase, get explanations, request refactors, brainstorm architecture.</td>
</tr>
<tr>
<td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><strong>Inline Chat (<kbd>Ctrl+I</kbd>)</strong></td>
<td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Open a prompt directly in the editor. Select a component, hit <kbd>Ctrl+I</kbd>, and type "add loading and error states". Copilot edits in-place.</td>
</tr>
<tr>
<td style="padding:10px 12px; border:1px solid #CCC;"><strong>Slash commands</strong></td>
<td style="padding:10px 12px; border:1px solid #CCC;"><code>/fix</code>, <code>/explain</code>, <code>/tests</code>, <code>/doc</code> — dedicated commands for the most common tasks. <code>/tests</code> auto-generates RTL tests for selected code.</td>
</tr>
<tr>
<td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><strong>Agent mode</strong></td>
<td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Autonomously edits multiple files to complete a multi-step task. Example: "Add a dark mode toggle to the app" — Copilot updates the context, the toggle component, and the CSS variables.</td>
</tr>
<tr>
<td style="padding:10px 12px; border:1px solid #CCC;"><strong>@workspace context</strong></td>
<td style="padding:10px 12px; border:1px solid #CCC;">Use <code>@workspace</code> in chat to give Copilot full visibility of your React project. It understands your component tree, imports, and file structure.</td>
</tr>
<tr>
<td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><strong>Custom instructions</strong></td>
<td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">The <code>.github/copilot-instructions.md</code> file sets project-level context: your tech stack, coding standards, naming conventions, and guardrails.</td>
</tr>
<tr>
<td style="padding:10px 12px; border:1px solid #CCC;"><strong>PR summaries</strong></td>
<td style="padding:10px 12px; border:1px solid #CCC;">On GitHub.com, Copilot can auto-generate PR descriptions, summarize diffs, and suggest reviewers.</td>
</tr>
</table>

### <span style="color:#0D47A1;">2.2  GitHub Copilot vs. Other AI Coding Tools</span>

For context, here's how GitHub Copilot compares to tools you may have heard about. This course exclusively uses GitHub Copilot:

<table style="width:100%; border-collapse:collapse;">
<tr>
<th style="background:#0D47A1; color:white; padding:10px 12px; text-align:left;">Feature</th>
<th style="background:#0D47A1; color:white; padding:10px 12px; text-align:left;">GitHub Copilot</th>
<th style="background:#0D47A1; color:white; padding:10px 12px; text-align:left;">Other Tools (Cursor, Tabnine, Claude Code, etc.)</th>
</tr>
<tr>
<td style="background:#F5F5F5; padding:10px 12px; border:1px solid #CCC;"><strong>Interface</strong></td>
<td style="background:#F5F5F5; padding:10px 12px; border:1px solid #CCC;">Native VS Code extension + GitHub.com integration</td>
<td style="background:#F5F5F5; padding:10px 12px; border:1px solid #CCC;">Separate IDEs, web interfaces, or terminal CLIs</td>
</tr>
<tr>
<td style="padding:10px 12px; border:1px solid #CCC;"><strong>Agency</strong></td>
<td style="padding:10px 12px; border:1px solid #CCC;">Agent mode — multi-file edits, terminal command execution</td>
<td style="padding:10px 12px; border:1px solid #CCC;">Varies: some suggestion-only, some fully agentic</td>
</tr>
<tr>
<td style="background:#F5F5F5; padding:10px 12px; border:1px solid #CCC;"><strong>Context</strong></td>
<td style="background:#F5F5F5; padding:10px 12px; border:1px solid #CCC;"><code>@workspace</code>, open tabs, <code>#file</code> references, <code>#selection</code></td>
<td style="background:#F5F5F5; padding:10px 12px; border:1px solid #CCC;">Usually limited to open file or explicit context passing</td>
</tr>
<tr>
<td style="padding:10px 12px; border:1px solid #CCC;"><strong>GitHub Integration</strong></td>
<td style="padding:10px 12px; border:1px solid #CCC;">Native: PR summaries, issue-to-branch, Actions awareness</td>
<td style="padding:10px 12px; border:1px solid #CCC;">Limited or requires plugins</td>
</tr>
<tr>
<td style="background:#F5F5F5; padding:10px 12px; border:1px solid #CCC;"><strong>Customization</strong></td>
<td style="background:#F5F5F5; padding:10px 12px; border:1px solid #CCC;"><code>.github/copilot-instructions.md</code>, custom extensions, personal instructions</td>
<td style="background:#F5F5F5; padding:10px 12px; border:1px solid #CCC;">Varies by tool</td>
</tr>
<tr>
<td style="padding:10px 12px; border:1px solid #CCC;"><strong>CI/CD Integration</strong></td>
<td style="padding:10px 12px; border:1px solid #CCC;">GitHub Actions-aware, Copilot Workspace for issue-to-PR</td>
<td style="padding:10px 12px; border:1px solid #CCC;">Often separate from deployment pipeline</td>
</tr>
<tr>
<td style="background:#F5F5F5; padding:10px 12px; border:1px solid #CCC;"><strong>Pricing</strong></td>
<td style="background:#F5F5F5; padding:10px 12px; border:1px solid #CCC;">Individual $10/mo · Business $19/mo · Enterprise $39/mo</td>
<td style="background:#F5F5F5; padding:10px 12px; border:1px solid #CCC;">Varies by tool and provider</td>
</tr>
</table>

<table style="width:100%; border-collapse:collapse;">
<tr>
<td style="border-left:5px solid #1A73E8; background:#E3F2FD; padding:14px 18px;">
<strong style="color:#0D47A1;">⭐ KEY POINT:</strong> <span style="color:#0D47A1;">We chose GitHub Copilot for this course because it lives natively inside VS Code — the environment where React developers already work — and it integrates directly with GitHub workflows. You don't need to switch tools. Copilot meets you exactly where your React code lives.</span>
</td>
</tr>
</table>

---

<table style="width:100%; border-collapse:collapse;">
<tr>
<td style="background:#00695C; color:white; padding:8px 16px; font-weight:bold;">0:25 – 0:35</td>
<td style="background:#E0F2F1; padding:8px 16px; color:#00695C; font-weight:bold; font-size:16px;">SECTION 3: Strengths vs. Limits</td>
</tr>
</table>

## <span style="color:#0D47A1;">3. Strengths vs. Limitations — An Honest Assessment</span>

Before you start using GitHub Copilot in a React project, it's critical to understand what it does well and where it falls short. Being realistic about capabilities will save you hours of frustration and prevent costly mistakes.

### <span style="color:#0D47A1;">3.1  What GitHub Copilot Does Well (React Context)</span>

<table style="width:100%; border-collapse:collapse;">
<tr>
<th style="background:#2E7D32; color:white; padding:10px 12px; text-align:left;">Strength</th>
<th style="background:#2E7D32; color:white; padding:10px 12px; text-align:left;">Practical Impact on React Projects</th>
</tr>
<tr>
<td style="background:#E8F5E9; padding:10px 12px; border:1px solid #CCC;"><strong>Component scaffolding</strong></td>
<td style="background:#E8F5E9; padding:10px 12px; border:1px solid #CCC;">Generates complete, typed React components from a description or a filename comment — props interface, JSX structure, and export in seconds</td>
</tr>
<tr>
<td style="padding:10px 12px; border:1px solid #CCC;"><strong>Hook generation</strong></td>
<td style="padding:10px 12px; border:1px solid #CCC;">Writes <code>useState</code>, <code>useEffect</code>, <code>useCallback</code>, and custom hooks with correct dependency arrays and TypeScript generics</td>
</tr>
<tr>
<td style="background:#E8F5E9; padding:10px 12px; border:1px solid #CCC;"><strong>Test generation</strong></td>
<td style="background:#E8F5E9; padding:10px 12px; border:1px solid #CCC;">Generates comprehensive Jest + React Testing Library suites including user-event interactions, async state updates, and accessibility checks</td>
</tr>
<tr>
<td style="padding:10px 12px; border:1px solid #CCC;"><strong>Code comprehension</strong></td>
<td style="padding:10px 12px; border:1px solid #CCC;">Explains unfamiliar hooks, render prop patterns, HOCs, and complex state machines — invaluable when onboarding to a large codebase</td>
</tr>
<tr>
<td style="background:#E8F5E9; padding:10px 12px; border:1px solid #CCC;"><strong>Refactoring at scale</strong></td>
<td style="background:#E8F5E9; padding:10px 12px; border:1px solid #CCC;">Converts class components to functional, extracts custom hooks from large components, reorganizes prop drilling into Context, across multiple files at once</td>
</tr>
<tr>
<td style="padding:10px 12px; border:1px solid #CCC;"><strong>Boilerplate elimination</strong></td>
<td style="padding:10px 12px; border:1px solid #CCC;">Form validation logic, API integration layers, router configuration, and loading/error state wrappers — generated in one prompt</td>
</tr>
<tr>
<td style="background:#E8F5E9; padding:10px 12px; border:1px solid #CCC;"><strong>Documentation</strong></td>
<td style="background:#E8F5E9; padding:10px 12px; border:1px solid #CCC;">Generates JSDoc, prop descriptions, Storybook story files, and README sections from existing component code</td>
</tr>
<tr>
<td style="padding:10px 12px; border:1px solid #CCC;"><strong>Debugging speed</strong></td>
<td style="padding:10px 12px; border:1px solid #CCC;">Paste a React error boundary trace or a console warning — Copilot diagnoses the issue and suggests a fix. Especially strong on common Re-render and hook-ordering issues.</td>
</tr>
</table>

### <span style="color:#0D47A1;">3.2  Where GitHub Copilot Has Limitations (React Context)</span>

<table style="width:100%; border-collapse:collapse;">
<tr>
<th style="background:#C62828; color:white; padding:10px 12px; text-align:left;">Limitation</th>
<th style="background:#C62828; color:white; padding:10px 12px; text-align:left;">What This Means For Your React Code</th>
</tr>
<tr>
<td style="background:#FFEBEE; padding:10px 12px; border:1px solid #CCC;"><strong>Hallucination</strong></td>
<td style="background:#FFEBEE; padding:10px 12px; border:1px solid #CCC;">May suggest non-existent React APIs, deprecated lifecycle methods (e.g., <code>componentWillMount</code>), or incorrect hook signatures. Always verify against the official React docs.</td>
</tr>
<tr>
<td style="padding:10px 12px; border:1px solid #CCC;"><strong>Stale knowledge</strong></td>
<td style="padding:10px 12px; border:1px solid #CCC;">May suggest patterns from older React versions. Always cross-check suggestions against the current React 18+ and library-specific docs.</td>
</tr>
<tr>
<td style="background:#FFEBEE; padding:10px 12px; border:1px solid #CCC;"><strong>Context limits</strong></td>
<td style="background:#FFEBEE; padding:10px 12px; border:1px solid #CCC;">Very large component trees may exceed context. Use <code>@workspace</code> and <code>#file</code> references to explicitly tell Copilot which files are relevant.</td>
</tr>
<tr>
<td style="padding:10px 12px; border:1px solid #CCC;"><strong>Design system blind spots</strong></td>
<td style="padding:10px 12px; border:1px solid #CCC;">Copilot has no knowledge of your internal component library or custom design tokens. It may generate raw HTML when you want <code>&lt;Button variant="primary"&gt;</code> from your shared library.</td>
</tr>
<tr>
<td style="background:#FFEBEE; padding:10px 12px; border:1px solid #CCC;"><strong>Subtle logic bugs</strong></td>
<td style="background:#FFEBEE; padding:10px 12px; border:1px solid #CCC;">Common pitfalls: missing <code>useEffect</code> cleanup causing memory leaks, stale closures in event handlers, and race conditions in concurrent-mode React. Generated code looks right but has edge-case bugs.</td>
</tr>
<tr>
<td style="padding:10px 12px; border:1px solid #CCC;"><strong>Security blind spots</strong></td>
<td style="padding:10px 12px; border:1px solid #CCC;">May generate XSS-vulnerable patterns like <code>dangerouslySetInnerHTML</code> with unsanitized input, or suggest storing tokens in <code>localStorage</code> without noting the XSS risk.</td>
</tr>
<tr>
<td style="background:#FFEBEE; padding:10px 12px; border:1px solid #CCC;"><strong>Non-deterministic output</strong></td>
<td style="background:#FFEBEE; padding:10px 12px; border:1px solid #CCC;">The same prompt may generate structurally different components each time. Results are probabilistic — always anchor suggestions with specific examples and context.</td>
</tr>
<tr>
<td style="padding:10px 12px; border:1px solid #CCC;"><strong>Over-engineering</strong></td>
<td style="padding:10px 12px; border:1px solid #CCC;">May suggest a full Redux slice when a single <code>useState</code> suffices. Or proposes a render-props pattern when a simple hook would be cleaner. Guide Copilot with constraints.</td>
</tr>
</table>

<table style="width:100%; border-collapse:collapse;">
<tr>
<td style="border-left:5px solid #C62828; background:#FFEBEE; padding:14px 18px;">
<strong style="color:#C62828;">⚠️ WARNING:</strong> <span style="color:#C62828;">Never blindly trust AI-generated React code in a production environment. A 2025 security analysis found that a significant percentage of AI-built web apps had XSS or authentication vulnerabilities in their React frontends. Professional AI-assisted engineering means: generate fast, review thoroughly, test rigorously.</span>
</td>
</tr>
</table>

### <span style="color:#0D47A1;">3.3  The Right Mental Model</span>

Think of GitHub Copilot as a brilliant, extremely fast junior React developer who:

- Has read millions of React codebases and knows patterns from all of them
- Works at superhuman speed but sometimes makes confident mistakes about hooks or rendering behavior
- Never gets tired, never gets frustrated, and can iterate 50 times without complaint
- Needs clear direction and benefits enormously from specific, detailed prompts and context
- Does NOT understand your design system, your team's component conventions, or the real-world UX consequences of bugs

<table style="width:100%; border-collapse:collapse;">
<tr>
<td style="border-left:5px solid #1A73E8; background:#E3F2FD; padding:14px 18px;">
<strong style="color:#0D47A1;">⭐ KEY POINT:</strong> <span style="color:#0D47A1;">Your job is not to write JSX anymore. Your job is to think clearly about component design, direct Copilot precisely, review the generated code critically, and write the tests that prove it works. Copilot handles the typing. You handle the thinking.</span>
</td>
</tr>
</table>

<table style="width:100%; border-collapse:collapse;">
<tr>
<td style="background:#FFF3E0; padding:16px 20px; border:1px solid #FFCC80;">
<strong style="color:#E65100; font-size:15px;">💬 GROUP DISCUSSION (3 minutes)</strong>
<ul style="color:#333; margin:10px 0; padding-left:20px;">
<li>In pairs, discuss: What is one React task in your daily work that you think GitHub Copilot could help with, and one task where you think human judgment is irreplaceable?</li>
<li>Think about: component architecture decisions, accessibility reviews, performance optimization, business logic encoding</li>
<li>Be ready to share one insight with the group</li>
</ul>
</td>
</tr>
</table>

---

<table style="width:100%; border-collapse:collapse;">
<tr>
<td style="background:#00695C; color:white; padding:8px 16px; font-weight:bold;">0:35 – 0:45</td>
<td style="background:#E0F2F1; padding:8px 16px; color:#00695C; font-weight:bold; font-size:16px;">SECTION 4: Privacy / IP / Licensing Checklist</td>
</tr>
</table>

## <span style="color:#0D47A1;">4. Privacy, IP & Licensing Checklist</span>

Before using GitHub Copilot on any project codebase, every developer needs to understand the risks and the guardrails. This section gives you a practical, actionable checklist you can apply from Day 1.

### <span style="color:#0D47A1;">4.1  The Three Risk Categories</span>

<table style="width:100%; border-collapse:collapse;">
<tr>
<th style="background:#C62828; color:white; padding:10px 12px; text-align:left;">Risk Category</th>
<th style="background:#C62828; color:white; padding:10px 12px; text-align:left;">What Could Go Wrong</th>
<th style="background:#C62828; color:white; padding:10px 12px; text-align:left;">Mitigation</th>
</tr>
<tr>
<td style="background:#F5F5F5; padding:10px 12px; border:1px solid #CCC;"><strong>Data Exposure</strong></td>
<td style="background:#F5F5F5; padding:10px 12px; border:1px solid #CCC;">Proprietary React code, business logic, or API integration patterns get transmitted to GitHub's AI infrastructure and could inform model training</td>
<td style="background:#F5F5F5; padding:10px 12px; border:1px solid #CCC;">Use Copilot Business or Enterprise (no training on your code by default); never paste secrets, tokens, or PII into chat prompts</td>
</tr>
<tr>
<td style="padding:10px 12px; border:1px solid #CCC;"><strong>IP Contamination</strong></td>
<td style="padding:10px 12px; border:1px solid #CCC;">Copilot may suggest code that is substantially similar to GPL or copyleft-licensed open-source code from its training data, creating licensing obligations for your project</td>
<td style="padding:10px 12px; border:1px solid #CCC;">Enable the "Duplication Detection" filter in Copilot settings; review generated code for attribution; avoid asking Copilot to reproduce specific library implementations verbatim</td>
</tr>
<tr>
<td style="background:#F5F5F5; padding:10px 12px; border:1px solid #CCC;"><strong>Code Quality Risk</strong></td>
<td style="background:#F5F5F5; padding:10px 12px; border:1px solid #CCC;">Copilot generates React code with security vulnerabilities (XSS, insecure auth patterns), accessibility violations, or performance anti-patterns that make it into production</td>
<td style="background:#F5F5F5; padding:10px 12px; border:1px solid #CCC;">Mandatory code review for all AI-generated code; automated testing with Jest + RTL + axe-core; never skip the review step</td>
</tr>
</table>

### <span style="color:#0D47A1;">4.2  GitHub Copilot's Data Handling</span>

Understanding how your React code is handled when using GitHub Copilot:

<table style="width:100%; border-collapse:collapse;">
<tr>
<th style="background:#0D47A1; color:white; padding:10px 12px; text-align:left;">Aspect</th>
<th style="background:#0D47A1; color:white; padding:10px 12px; text-align:left;">GitHub Copilot Policy</th>
</tr>
<tr>
<td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><strong>Individual plan</strong></td>
<td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Code snippets (prompts) may be used to improve Copilot models by default. You can opt out in your GitHub settings under Copilot > Suggestions.</td>
</tr>
<tr>
<td style="padding:10px 12px; border:1px solid #CCC;"><strong>Business / Enterprise plan</strong></td>
<td style="padding:10px 12px; border:1px solid #CCC;">Prompts and suggestions are NOT used for model training. This is the recommended tier for commercial React development. Data is retained for 28 days for abuse detection, then deleted.</td>
</tr>
<tr>
<td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><strong>Code transmission</strong></td>
<td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Copilot sends surrounding code context to GitHub's AI service for inference. Your code is in transit to external servers — treat it accordingly.</td>
</tr>
<tr>
<td style="padding:10px 12px; border:1px solid #CCC;"><strong>Duplication detection</strong></td>
<td style="padding:10px 12px; border:1px solid #CCC;">Enable this filter to block suggestions that match public code with ≥150 characters. Find it in: VS Code Settings → GitHub Copilot → Suggestions: Filter Options.</td>
</tr>
<tr>
<td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;"><strong>Copilot Chat history</strong></td>
<td style="background:#E3F2FD; padding:10px 12px; border:1px solid #CCC;">Chat logs are stored locally in VS Code's session state and within your GitHub account. They are not saved permanently on your machine by default.</td>
</tr>
<tr>
<td style="padding:10px 12px; border:1px solid #CCC;"><strong>IP indemnification</strong></td>
<td style="padding:10px 12px; border:1px solid #CCC;">Copilot Enterprise includes IP indemnification: GitHub will defend you if a third party claims that Copilot suggestions infringed their copyright. Only applies with duplication detection enabled.</td>
</tr>
</table>

### <span style="color:#0D47A1;">4.3  The Safety Checklist</span>

Use this checklist before every AI-assisted React development session:

<table style="width:100%; border-collapse:collapse;">
<tr>
<td style="background:#E8F5E9; padding:16px 20px; border:1px solid #A5D6A7;">
<strong style="color:#2E7D32; font-size:15px;">✅ PRE-SESSION SAFETY CHECKLIST</strong>
<ul style="color:#333; margin:10px 0; padding-left:20px;">
<li><strong>CLASSIFY</strong> your codebase: Is it open-source, internal, or confidential? Use Copilot Business/Enterprise for any proprietary React app.</li>
<li><strong>STRIP SECRETS:</strong> Never include API keys, auth tokens, environment variables, or backend URLs in Copilot Chat prompts. Use placeholder names like <code>YOUR_API_KEY</code>.</li>
<li><strong>SCRUB PROPRIETARY LOGIC:</strong> If your React app contains trade-secret business logic (e.g., proprietary pricing algorithms, unique UX flows), work on the structural pattern — not the live implementation — with Copilot.</li>
<li><strong>CHECK YOUR PLAN:</strong> Are you using Copilot Individual (opt out of training) or Copilot Business/Enterprise (training-off by default)?</li>
<li><strong>REVIEW ALL OUTPUT:</strong> Every line of Copilot-generated React code must be reviewed before committing. No exceptions.</li>
<li><strong>RUN TESTS:</strong> Copilot-generated components must pass your existing Jest + RTL test suite plus new tests for the generated code.</li>
<li><strong>TAG AI CODE:</strong> Use a commit message convention (e.g., <code>[copilot-assisted]</code>) so teammates know which code involved AI generation.</li>
<li><strong>CHECK LICENSES:</strong> If Copilot generates code that looks like it may come from a specific open-source library, verify license compatibility — especially GPL vs. MIT.</li>
</ul>
</td>
</tr>
</table>

### <span style="color:#0D47A1;">4.4  What NOT to Send to GitHub Copilot</span>

<table style="width:100%; border-collapse:collapse;">
<tr>
<td style="border-left:5px solid #C62828; background:#FFEBEE; padding:14px 18px;">
<strong style="color:#C62828;">⚠️ WARNING:</strong> <span style="color:#C62828;">NEVER send the following to GitHub Copilot Chat or include in prompts:</span>
</td>
</tr>
</table>

- Customer data, PII (personally identifiable information), or GDPR-protected information
- Proprietary business logic, trade secrets, or patented algorithms
- Security credentials: API keys, OAuth tokens, JWTs, passwords, certificates
- Internal infrastructure details: backend URLs, internal service names, database schemas with real data
- Export-controlled technology or ITAR-regulated materials
- Compliance-sensitive code subject to regulatory audit (HIPAA, PCI-DSS, etc.)

### <span style="color:#0D47A1;">4.5  Safe Alternatives for Sensitive Code</span>

When you need Copilot help with React code that contains sensitive elements:

- **Abstract the problem:** Replace proprietary component names with generic ones (`<PricingCalculator>` instead of `<AcmeCorp_Q4PromoEngine>`)
- **Work on the pattern, not the content:** Ask Copilot to help with the data-fetching hook pattern, then manually adapt it to your proprietary API
- **Use `.github/copilot-instructions.md` guardrails:** Configure your project's instructions file to tell Copilot which patterns to use and which files are off-limits for suggestions
- **Isolate sensitive sections:** Keep business-critical logic in separate utility functions that you don't open in your editor during Copilot sessions

---

<table style="width:100%; border-collapse:collapse;">
<tr>
<td style="background:#00695C; color:white; padding:8px 16px; font-weight:bold;">0:45 – 0:55</td>
<td style="background:#E0F2F1; padding:8px 16px; color:#00695C; font-weight:bold; font-size:16px;">SECTION 5: Hands-On Setup — Installation & First React Interaction</td>
</tr>
</table>

## <span style="color:#0D47A1;">5. Hands-On: GitHub Copilot Installation & First React Interaction</span>

### <span style="color:#0D47A1;">5.1  Prerequisites Verification</span>

Before installing GitHub Copilot, verify these are already set up on your machine:

```bash
# Check Node.js version (need 18+)
node --version

# Check npm
npm --version

# Check Git
git --version

# Check VS Code
code --version

# Verify you have a GitHub account at github.com
# (Copilot requires a GitHub account with an active subscription)
```

### <span style="color:#0D47A1;">5.2  Installing GitHub Copilot in VS Code</span>

GitHub Copilot is a VS Code extension — no separate CLI or installer needed:

**Step 1: Install the GitHub Copilot extension**

```bash
# Option A: From the terminal
code --install-extension GitHub.copilot

# Option B: From VS Code UI
# Open VS Code → Extensions (Ctrl+Shift+X / Cmd+Shift+X)
# Search: "GitHub Copilot"
# Install "GitHub Copilot" by GitHub (the official extension)
```

**Step 2: Verify GitHub Copilot Chat is available**

In current VS Code builds, Copilot Chat may be bundled with the GitHub Copilot extension or shown as a separate installed extension. If the Chat icon appears in the Activity Bar or the Copilot Chat panel opens, you do not need to install anything else.

```bash
# If Chat is not available, install the companion extension:
code --install-extension GitHub.copilot-chat
```

**Step 3: Verify installation**

```bash
# Both extensions should appear in:
# VS Code → Extensions → Installed

# You should see either one bundled Copilot extension or both:
# ✅ GitHub Copilot
# ✅ GitHub Copilot Chat (if your VS Code version lists it separately)
```

### <span style="color:#0D47A1;">5.3  Authentication</span>

GitHub Copilot authenticates through your GitHub account — no separate API key needed:

<table style="width:100%; border-collapse:collapse;">
<tr>
<th style="background:#00695C; color:white; padding:10px 12px; text-align:left;">Step</th>
<th style="background:#00695C; color:white; padding:10px 12px; text-align:left;">Action</th>
</tr>
<tr>
<td style="background:#E0F2F1; padding:10px 12px; border:1px solid #CCC;"><strong>1. Sign in to GitHub</strong></td>
<td style="background:#E0F2F1; padding:10px 12px; border:1px solid #CCC;">In VS Code: click the Accounts icon (bottom-left) → "Sign in with GitHub" → complete the browser OAuth flow</td>
</tr>
<tr>
<td style="padding:10px 12px; border:1px solid #CCC;"><strong>2. Authorize Copilot</strong></td>
<td style="padding:10px 12px; border:1px solid #CCC;">VS Code will prompt you to authorize GitHub Copilot for your account. Click "Authorize GitHub Copilot".</td>
</tr>
<tr>
<td style="background:#E0F2F1; padding:10px 12px; border:1px solid #CCC;"><strong>3. Verify activation</strong></td>
<td style="background:#E0F2F1; padding:10px 12px; border:1px solid #CCC;">The Copilot icon should appear in the VS Code status bar (bottom-right). A filled icon = active. A dimmed icon = not connected.</td>
</tr>
<tr>
<td style="padding:10px 12px; border:1px solid #CCC;"><strong>4. Check subscription</strong></td>
<td style="padding:10px 12px; border:1px solid #CCC;">If the icon shows an error, verify your Copilot subscription at <code>github.com/settings/copilot</code>. Free trial available for new accounts.</td>
</tr>
</table>

### <span style="color:#0D47A1;">5.4  Verify Copilot is Working</span>

Open any JavaScript or TypeScript file and do a quick sanity check:

```tsx
// Create a new file: src/components/Greeting.tsx
// Start typing the comment below and watch Copilot suggest the component:

// A greeting component that displays a personalized welcome message
```

Copilot should suggest a complete React component. Press `Tab` to accept. If you see ghost-text suggestions, Copilot is working correctly.

### <span style="color:#0D47A1;">5.5  Your First Copilot Chat Interaction</span>

Now let's use Copilot Chat on a runnable React + TypeScript project:

```bash
# Create a small React project for this first Chat exercise
npm create vite@latest vibe-coding-react -- --template react-ts
cd vibe-coding-react

# Install dependencies
npm install

# Open in VS Code
code .
```

Open the Copilot Chat panel (`Ctrl+Alt+I` / `Cmd+Alt+I`) and try these prompts:

```text
@workspace Explain the structure of this React project and list the main components

@workspace What testing libraries does this project use?

@workspace How is routing configured in this app?

/explain #file:src/App.tsx
```

<table style="width:100%; border-collapse:collapse;">
<tr>
<td style="background:#FFF3E0; padding:16px 20px; border:1px solid #FFCC80;">
<strong style="color:#E65100; font-size:15px;">🚀 HANDS-ON EXERCISE: First Interaction (5 minutes)</strong>
<ul style="color:#333; margin:10px 0; padding-left:20px;">
<li>Clone the course repo and open it in VS Code</li>
<li>Open Copilot Chat and ask: <em>"@workspace Explain the structure of this React project"</em></li>
<li>Ask: <em>"@workspace What components exist and what do they do?"</em></li>
<li>Create a new file <code>src/components/WelcomeBanner.tsx</code>, type a comment describing what it should do, and press <kbd>Tab</kbd> to accept Copilot's inline suggestion</li>
<li>Select the generated component, right-click → "Copilot" → "Generate Tests" to see <code>/tests</code> in action</li>
<li>Type <code>/help</code> in the Copilot Chat panel to see all available slash commands</li>
<li><strong>Raise your hand if you get stuck at any step</strong> — that's what we're here for!</li>
</ul>
</td>
</tr>
</table>

<table style="width:100%; border-collapse:collapse;">
<tr>
<td style="border-left:5px solid #1A73E8; background:#E3F2FD; padding:14px 18px;">
<strong style="color:#0D47A1;">⭐ KEY POINT:</strong> <span style="color:#0D47A1;">Congratulations! If you just completed those steps, you've already used AI to analyze a React codebase, get contextual explanations, and scaffold a new component faster than typing from scratch. This is the foundation everything else in this course builds on.</span>
</td>
</tr>
</table>

---

<table style="width:100%; border-collapse:collapse;">
<tr>
<td style="background:#00695C; color:white; padding:8px 16px; font-weight:bold;">0:55 – 1:00</td>
<td style="background:#E0F2F1; padding:8px 16px; color:#00695C; font-weight:bold; font-size:16px;">WRAP-UP: Course Repo Tour & Guardrails</td>
</tr>
</table>

## <span style="color:#0D47A1;">6. Course Repository Tour & Guardrails</span>

### <span style="color:#0D47A1;">6.1  Repository Structure</span>

The course repo is a React + TypeScript project built with Vite, organized to support hands-on labs throughout the course:

```text
vibe-coding-react/
├── .github/
│   ├── copilot-instructions.md   # Project context for GitHub Copilot
│   └── workflows/                # GitHub Actions CI/CD pipelines
├── public/                       # Static assets
├── src/
│   ├── components/               # Reusable React components
│   │   └── ui/                   # Low-level design system primitives
│   ├── hooks/                    # Custom React hooks
│   ├── context/                  # React Context providers
│   ├── pages/                    # Page-level route components
│   ├── utils/                    # Pure utility functions
│   ├── types/                    # Shared TypeScript type definitions
│   └── App.tsx                   # Root component and router setup
├── tests/
│   ├── components/               # React Testing Library component tests
│   └── hooks/                    # Custom hook unit tests
├── labs/
│   ├── lab1_scaffold/            # Lab 1 starter files
│   ├── lab2_refactor/            # Lab 2 starter files
│   ├── lab3_testing/             # Lab 3 starter files
│   └── solutions/                # Reference solutions (review after the lab)
├── package.json
├── vite.config.ts
└── tsconfig.json
```

### <span style="color:#0D47A1;">6.2  The copilot-instructions.md File</span>

This is the most important configuration file for GitHub Copilot. It lives at `.github/copilot-instructions.md` and tells Copilot about your project's tech stack, coding standards, and guardrails. Let's look at the course repo's instructions file:

```markdown
# GitHub Copilot Instructions

## Project
React 18 + TypeScript training project for the Vibe Coding with GitHub Copilot course.
Stack: React 18, TypeScript 5, Vite, React Router v6, Jest, React Testing Library, Tailwind CSS.

## Coding Standards
- Always use TypeScript — no plain `.js` files
- Use functional components with hooks only — no class components
- Use named exports for all components: `export function MyComponent`
- Prefer composition over inheritance; use custom hooks to share logic
- All components must have TypeScript prop interfaces defined above the component

## Testing
- Use Jest + React Testing Library for all component and hook tests
- Test user behavior, not implementation details — use `getByRole`, `getByText`
- Include at least one accessibility assertion per component test (use `axe-core`)
- Minimum test coverage target: 80%
- Test files live alongside source files: `Button.tsx` → `Button.test.tsx`

## Safety Guardrails
- NEVER suggest or generate code that uses `dangerouslySetInnerHTML` with unsanitized input
- NEVER include hardcoded API keys, tokens, or secrets
- ALWAYS use mock data from the `/src/mocks/` directory for development and tests
- When proposing a multi-file change, explain the plan in chat before making edits
```

<table style="width:100%; border-collapse:collapse;">
<tr>
<td style="border-left:5px solid #1A73E8; background:#E3F2FD; padding:14px 18px;">
<strong style="color:#0D47A1;">⭐ KEY POINT:</strong> <span style="color:#0D47A1;"><code>copilot-instructions.md</code> is like an onboarding document for your AI pair programmer. The more specific and well-written it is, the better Copilot performs in your React project. It will consistently use your stack, your conventions, and your naming patterns. We'll create and refine this file throughout the course.</span>
</td>
</tr>
</table>

### <span style="color:#0D47A1;">6.3  Course Guardrails</span>

To keep this training productive and safe, we follow these ground rules:

<table style="width:100%; border-collapse:collapse;">
<tr>
<td style="background:#E0F2F1; padding:16px 20px; border:1px solid #80CBC4;">
<strong style="color:#00695C; font-size:15px;">🛡️ COURSE GROUND RULES</strong>
<ul style="color:#333; margin:10px 0; padding-left:20px;">
<li><strong>DO</strong> use the course repository and the provided mock data for all exercises</li>
<li><strong>DO</strong> experiment freely — Git lets you revert any Copilot-generated change you don't like</li>
<li><strong>DO</strong> ask questions at any time — there are no dumb questions in AI-assisted development</li>
<li><strong>DO NOT</strong> paste real production React code, customer data, or proprietary business logic into Copilot Chat during training</li>
<li><strong>DO NOT</strong> share your GitHub credentials or personal access tokens with other participants</li>
<li><strong>DO NOT</strong> run destructive commands (<code>rm -rf</code>, force-push to main) without checking with the instructor first</li>
<li><strong>REPORT</strong> any unexpected behavior, errors, or concerning Copilot outputs to the instructor</li>
</ul>
</td>
</tr>
</table>

---

## <span style="color:#1A73E8;">MODULE 1 RECAP</span>

<table style="width:100%; border-collapse:collapse;">
<tr>
<td style="background:#E3F2FD; padding:10px 14px; border-bottom:2px solid white;">✅ Vibe coding was coined by Karpathy (Feb 2025). Professional use = AI-Assisted Engineering where you review everything.</td>
</tr>
<tr>
<td style="padding:10px 14px; border-bottom:2px solid white;">✅ GitHub Copilot is a multi-modal tool: inline completions, Copilot Chat, Agent mode, slash commands, and PR summaries — all natively inside VS Code.</td>
</tr>
<tr>
<td style="background:#E3F2FD; padding:10px 14px; border-bottom:2px solid white;">✅ Copilot is strong at React component scaffolding, hook generation, test writing, and refactoring. Weak at design system awareness, subtle hook bugs, and security by default.</td>
</tr>
<tr>
<td style="padding:10px 14px; border-bottom:2px solid white;">✅ Always apply the safety checklist: classify your code, strip secrets, enable duplication detection, review all output, run tests, and tag AI-generated commits.</td>
</tr>
<tr>
<td style="background:#E3F2FD; padding:10px 14px; border-bottom:2px solid white;">✅ GitHub Copilot is installed, authenticated, and you've run your first codebase analysis and component scaffolding interaction.</td>
</tr>
<tr>
<td style="padding:10px 14px;">✅ The course repo has <code>copilot-instructions.md</code> guardrails, a typed React + Vite structure, and lab starter files ready for the next modules.</td>
</tr>
</table>

---

## <span style="color:#1A73E8;">TRANSITION TO MODULE 2</span>

Now that you understand the big picture and have GitHub Copilot running inside VS Code, we're ready to learn the language that makes AI-assisted React development effective: **prompting**. In Module 2, you'll master the techniques that turn vague requests into precise, well-structured component generation — from props interfaces to custom hooks to complete feature modules.

---

<div style="text-align:center; color:#666; font-size:12px; padding:20px 0;">
Vibe Coding with GitHub Copilot | React Developer Track<br>
Module 1 — Big Picture & Safety Primer
</div>
