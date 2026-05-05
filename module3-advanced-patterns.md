<div style="text-align:center; padding: 20px 0;">

<span style="font-size:14px; color:#666666; font-weight:bold; letter-spacing:2px;">MODULE 3</span>

# <span style="color:#0D47A1;">Advanced Patterns & Workflows</span>

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
<span style="font-size:12px; color:#666;">Day / Position</span><br><strong style="color:#0D47A1;">Day 1 / Third</strong>
</td>
</tr>
</table>

---

## <span style="color:#1A73E8;">LEARNING OBJECTIVES</span>

By the end of this module, participants will be able to:

1. Decompose complex, multi-file React features into manageable sub-tasks that GitHub Copilot can execute reliably
2. Apply the ReAct (Reason + Act) framework to guide Copilot through iterative React development workflows
3. Control Copilot's output style and reasoning depth using prompt techniques — from conventional boilerplate to creative architectural exploration
4. Use iterative refinement strategies to transform first-draft React components into production-ready code
5. Build and maintain team `copilot-instructions.md` files that enforce consistent React standards across engineering teams

---

## <span style="color:#1A73E8;">SESSION TIMING BREAKDOWN</span>

<table style="width:100%; border-collapse:collapse;">
<tr>
<td style="background:#00695C; color:white; padding:8px 14px; width:120px; font-weight:bold; font-size:13px;">0:00 – 0:10</td>
<td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Section 1: Problem Decomposition — Breaking Down Complex React Features</td>
</tr>
<tr><td colspan="2" style="height:4px;"></td></tr>
<tr>
<td style="background:#00695C; color:white; padding:8px 14px; font-weight:bold; font-size:13px;">0:10 – 0:18</td>
<td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Section 2: The ReAct Framework — Reason + Act</td>
</tr>
<tr><td colspan="2" style="height:4px;"></td></tr>
<tr>
<td style="background:#00695C; color:white; padding:8px 14px; font-weight:bold; font-size:13px;">0:18 – 0:26</td>
<td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Section 3: Controlling Copilot's Output Style and Reasoning Depth</td>
</tr>
<tr><td colspan="2" style="height:4px;"></td></tr>
<tr>
<td style="background:#00695C; color:white; padding:8px 14px; font-weight:bold; font-size:13px;">0:26 – 0:34</td>
<td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Section 4: Iterative Refinement — From Good to Great</td>
</tr>
<tr><td colspan="2" style="height:4px;"></td></tr>
<tr>
<td style="background:#00695C; color:white; padding:8px 14px; font-weight:bold; font-size:13px;">0:34 – 0:42</td>
<td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Section 5: Team copilot-instructions.md — Scaling Standards Across Engineers</td>
</tr>
<tr><td colspan="2" style="height:4px;"></td></tr>
<tr>
<td style="background:#00695C; color:white; padding:8px 14px; font-weight:bold; font-size:13px;">0:42 – 0:45</td>
<td style="background:#E0F2F1; padding:8px 14px; color:#00695C; font-weight:bold;">Wrap-Up & Transition to Module 4</td>
</tr>
</table>

---

<table style="width:100%; border-collapse:collapse;">
<tr>
<td style="background:#00695C; color:white; padding:8px 16px; font-weight:bold;">0:00 – 0:10</td>
<td style="background:#E0F2F1; padding:8px 16px; color:#00695C; font-weight:bold; font-size:16px;">SECTION 1: Problem Decomposition — Breaking Down Complex React Features</td>
</tr>
</table>

## <span style="color:#0D47A1;">1. Problem Decomposition — Breaking Down Complex React Features</span>

### <span style="color:#0D47A1;">1.1  Why Decomposition Matters</span>

The biggest mistake developers make with AI coding tools is giving them tasks that are too large. When you ask Copilot to "build an entire product dashboard with filtering, sorting, pagination, a shopping cart, and authentication," it tries to do everything at once — and the result is usually mediocre and hard to review.

<table style="width:100%; border-collapse:collapse;">
<tr>
<td style="border-left:5px solid #1A73E8; background:#E3F2FD; padding:16px 20px;">
<em style="color:#0D47A1; font-size:15px;">"The art of vibe coding is knowing how big a bite the AI can chew. Small, focused React tasks produce dramatically better components than big, vague ones."</em>
</td>
</tr>
</table>

Problem decomposition is the discipline of breaking a large React feature into smaller, well-defined sub-tasks that each produce a concrete, testable output — a type definition, a hook, a component, a test file.

### <span style="color:#0D47A1;">1.2  The Decomposition Framework</span>

Follow this 4-step approach for any React feature that would take more than 5 minutes of manual coding:

<table style="width:100%; border-collapse:collapse;">
<tr>
<th style="background:#1A73E8; color:white; padding:8px 12px; text-align:left;">Step</th>
<th style="background:#1A73E8; color:white; padding:8px 12px; text-align:left;">Action</th>
<th style="background:#1A73E8; color:white; padding:8px 12px; text-align:left;">React Example</th>
</tr>
<tr>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;"><strong>1. Scope</strong></td>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;">Define the full outcome you want</td>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;">"Build a product listing page with search, filtering by category, pagination, and add-to-cart"</td>
</tr>
<tr>
<td style="padding:8px 12px; border:1px solid #ccc;"><strong>2. Split</strong></td>
<td style="padding:8px 12px; border:1px solid #ccc;">Break into 3–7 independent sub-tasks</td>
<td style="padding:8px 12px; border:1px solid #ccc;">"Step 1: TypeScript types. Step 2: <code>useProductSearch</code> hook. Step 3: <code>ProductCard</code> component. Step 4: <code>FilterPanel</code> component. Step 5: <code>ProductList</code> page. Step 6: Tests."</td>
</tr>
<tr>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;"><strong>3. Sequence</strong></td>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;">Order by dependencies (what needs to exist first?)</td>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;">Types first (no deps) → Hook (needs types) → Components (need hook + types) → Page (assembles components) → Tests (needs everything)</td>
</tr>
<tr>
<td style="padding:8px 12px; border:1px solid #ccc;"><strong>4. Specify</strong></td>
<td style="padding:8px 12px; border:1px solid #ccc;">Write a clear, constrained prompt for each sub-task</td>
<td style="padding:8px 12px; border:1px solid #ccc;">"Create a <code>useProductSearch</code> hook that accepts a query string and returns <code>{ products, isLoading, error, page, setPage }</code>. Use React Query. TypeScript generic over the product type."</td>
</tr>
</table>

### <span style="color:#0D47A1;">1.3  Multi-File Feature Decomposition</span>

When a React feature touches multiple files, decomposition becomes even more critical. Copilot handles multi-file features best when you follow this discipline:

<table style="width:100%; border-collapse:collapse;">
<tr>
<th style="background:#1A73E8; color:white; padding:8px 12px; text-align:left;">Approach</th>
<th style="background:#1A73E8; color:white; padding:8px 12px; text-align:left;">Why It Works</th>
</tr>
<tr>
<td style="background:#E3F2FD; padding:8px 12px; border:1px solid #ccc;"><strong>Types first, implementation second</strong></td>
<td style="background:#E3F2FD; padding:8px 12px; border:1px solid #ccc;">Define TypeScript interfaces and hook return shapes before any JSX. This aligns props expectations across all components and prevents cross-component type inconsistencies.</td>
</tr>
<tr>
<td style="padding:8px 12px; border:1px solid #ccc;"><strong>Hooks before components</strong></td>
<td style="padding:8px 12px; border:1px solid #ccc;">Build the data/logic layer (custom hooks, store slices, API functions) before the UI layer. Components become thin wrappers over well-tested hooks.</td>
</tr>
<tr>
<td style="background:#E3F2FD; padding:8px 12px; border:1px solid #ccc;"><strong>Tests alongside each unit</strong></td>
<td style="background:#E3F2FD; padding:8px 12px; border:1px solid #ccc;">Ask Copilot to generate tests immediately after each hook or component. Catch contract mistakes while context is still fresh in the chat.</td>
</tr>
<tr>
<td style="padding:8px 12px; border:1px solid #ccc;"><strong>Explicit <code>#file:</code> references</strong></td>
<td style="padding:8px 12px; border:1px solid #ccc;">Use <code>#file:</code> to show Copilot exactly which files to read and follow. Never assume it will find the right component from a name alone.</td>
</tr>
</table>

**Example — Decomposed multi-file prompt sequence for a product listing feature:**

```text
# Prompt 1: Define the TypeScript types (no dependencies)
"Create src/types/product.ts with TypeScript interfaces:
Product { id, name, price, category, imageUrl, inStock },
ProductFilters { category?, priceMin?, priceMax?, inStockOnly },
ProductSearchResult { products: Product[], total: number, page: number, pageSize: number }"

# Prompt 2: Build the data hook (depends on types)
"Create src/hooks/useProductSearch.ts — a React Query hook that
accepts ProductFilters and page number, fetches from /api/products,
and returns { data: ProductSearchResult, isLoading, error, refetch }.
Reference #file:src/types/product.ts for the type definitions."

# Prompt 3: Build the presentational component (depends on types)
"Create src/components/ProductCard.tsx — receives a Product as a prop,
shows name, price (formatted with Intl.NumberFormat), category badge,
and an 'Add to Cart' button that is disabled when inStock is false.
Reference #file:src/types/product.ts"

# Prompt 4: Assemble the page (depends on hook + component)
"Create src/pages/ProductListPage.tsx — uses useProductSearch from
#file:src/hooks/useProductSearch.ts and renders a grid of ProductCard
components from #file:src/components/ProductCard.tsx. Include loading
skeleton and empty/error states."

# Prompt 5: Tests (depends on all of the above)
"Write RTL tests in src/hooks/useProductSearch.test.ts covering:
successful fetch, loading state, error state, and page change.
Use MSW for API mocking. Reference #file:src/hooks/useProductSearch.ts"
```

<table style="width:100%; border-collapse:collapse;">
<tr>
<td style="border-left:5px solid #1A73E8; background:#E3F2FD; padding:14px 18px;">
<strong style="color:#0D47A1;">⭐ KEY POINT:</strong> <span style="color:#0D47A1;">Decomposition is not about writing more prompts — it's about writing better prompts. Each React sub-task should be small enough that Copilot produces excellent code on the first try, reducing the need for frustrating back-and-forth iteration. Types → hooks → components → tests is the natural sequence that mirrors a senior React developer's own workflow.</span>
</td>
</tr>
</table>

---

<table style="width:100%; border-collapse:collapse;">
<tr>
<td style="background:#00695C; color:white; padding:8px 16px; font-weight:bold;">0:10 – 0:18</td>
<td style="background:#E0F2F1; padding:8px 16px; color:#00695C; font-weight:bold; font-size:16px;">SECTION 2: The ReAct Framework — Reason + Act</td>
</tr>
</table>

## <span style="color:#0D47A1;">2. The ReAct Framework — Reason + Act</span>

### <span style="color:#0D47A1;">2.1  What Is ReAct?</span>

ReAct (Reason + Act) is a prompting pattern where you ask Copilot to alternate between reasoning about the problem and taking concrete actions. Instead of a single prompt that produces a final answer, you guide Copilot through a think-do-review loop.

<table style="width:100%; border-collapse:collapse;">
<tr>
<th style="background:#1A73E8; color:white; padding:8px 12px; text-align:left;">Traditional Approach</th>
<th style="background:#1A73E8; color:white; padding:8px 12px; text-align:left;">ReAct Approach</th>
</tr>
<tr>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;">One big prompt → One big React page</td>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;">Multiple small prompts → Incremental, reviewable progress</td>
</tr>
<tr>
<td style="padding:8px 12px; border:1px solid #ccc;">Hope Copilot decomposes the components correctly</td>
<td style="padding:8px 12px; border:1px solid #ccc;">Verify the component plan before any code is written</td>
</tr>
<tr>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;">Type errors and prop mismatches compound silently</td>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;">Errors caught early at each step before the tree grows</td>
</tr>
<tr>
<td style="padding:8px 12px; border:1px solid #ccc;">Hard to redirect when the component architecture is wrong</td>
<td style="padding:8px 12px; border:1px solid #ccc;">Easy to correct the architecture before anything is implemented</td>
</tr>
</table>

### <span style="color:#0D47A1;">2.2  The ReAct Loop in GitHub Copilot</span>

<table style="width:100%; border-collapse:collapse;">
<tr>
<th style="background:#1A73E8; color:white; padding:8px 12px; text-align:left;">Phase</th>
<th style="background:#1A73E8; color:white; padding:8px 12px; text-align:left;">What You Do</th>
<th style="background:#1A73E8; color:white; padding:8px 12px; text-align:left;">Copilot Prompt / Action</th>
</tr>
<tr>
<td style="background:#E3F2FD; padding:8px 12px; border:1px solid #ccc;"><strong>Reason</strong></td>
<td style="background:#E3F2FD; padding:8px 12px; border:1px solid #ccc;">Ask Copilot to analyze the problem and outline an approach</td>
<td style="background:#E3F2FD; padding:8px 12px; border:1px solid #ccc;">"Analyze #file:src/context/CartContext.tsx and explain what needs to change to support multi-currency pricing."</td>
</tr>
<tr>
<td style="padding:8px 12px; border:1px solid #ccc;"><strong>Act</strong></td>
<td style="padding:8px 12px; border:1px solid #ccc;">Ask Copilot to implement one specific step from the plan</td>
<td style="padding:8px 12px; border:1px solid #ccc;">"Now add a <code>currency: string</code> field to the cart state and a <code>setCurrency</code> action to #file:src/context/CartContext.tsx."</td>
</tr>
<tr>
<td style="background:#E3F2FD; padding:8px 12px; border:1px solid #ccc;"><strong>Observe</strong></td>
<td style="background:#E3F2FD; padding:8px 12px; border:1px solid #ccc;">Review the output, run tests, check for TypeScript errors</td>
<td style="background:#E3F2FD; padding:8px 12px; border:1px solid #ccc;">Check VS Code Problems panel, run <code>npm test</code>, paste <code>#terminalLastCommand</code> if tests fail</td>
</tr>
<tr>
<td style="padding:8px 12px; border:1px solid #ccc;"><strong>Reflect</strong></td>
<td style="padding:8px 12px; border:1px solid #ccc;">Ask Copilot to evaluate its own work</td>
<td style="padding:8px 12px; border:1px solid #ccc;">"Review the CartContext changes you just made. Are there any components that consume cart state that now have incorrect types?"</td>
</tr>
<tr>
<td style="background:#E3F2FD; padding:8px 12px; border:1px solid #ccc;"><strong>Iterate</strong></td>
<td style="background:#E3F2FD; padding:8px 12px; border:1px solid #ccc;">Refine based on the reflection</td>
<td style="background:#E3F2FD; padding:8px 12px; border:1px solid #ccc;">"Good catch — update #file:src/components/CartSummary.tsx to use the new currency field when formatting prices."</td>
</tr>
</table>

### <span style="color:#0D47A1;">2.3  ReAct Prompt Templates for React</span>

**Template 1: Analysis Before Refactoring**

```text
# Step 1: Reason — understand before touching
"Before making any changes, analyze #file:src/components/ProductList.tsx
and #file:src/hooks/useProductSearch.ts. What are the current
responsibilities of each? Where is filtering logic — in the component
or the hook? Are there any concerns that overlap?"

# [Review Copilot's analysis — confirm understanding is correct]

# Step 2: Act — one specific change based on the analysis
"Good analysis. Move the filter transformation logic from ProductList.tsx
into useProductSearch.ts. The component should only pass raw filter
values; the hook handles the API query string construction.
Keep the hook's return shape unchanged."
```

**Template 2: Test-Driven ReAct**

```text
# Step 1: Write the contract (tests) before the implementation
"Write RTL test cases for a useSingleFieldValidation hook that manages a
single form field's value, validation state, and touched state.
Cover: initial state, value change, blur triggers validation,
clear resets state. Don't implement the hook yet — tests only."

# [Review tests — confirm they describe the right behavior]

# Step 2: Implement to pass the tests
"Now implement the useSingleFieldValidation hook so all the tests in
#file:src/hooks/useSingleFieldValidation.test.ts pass. The hook should
accept a validator function and an initial value."
```

**Template 3: Agent Mode Full-Cycle ReAct**

```text
# In Copilot Chat — switch to Agent mode

# Step 1: Reason — explore and plan
"@workspace I need to add row selection with a bulk action toolbar
to the DataTable component. Before writing any code:
1. List the files you will modify
2. Describe the state changes required
3. Describe the new props that DataTable will need
4. Identify any components that consume DataTable that may need updates
Wait for my approval."

# [Review and approve OR redirect the plan]

# Step 2: Execute with checkpoints
"Proceed. After each file, pause and summarize what you changed
so I can review before moving to the next file."
```

<table style="width:100%; border-collapse:collapse;">
<tr>
<td style="border-left:5px solid #1A73E8; background:#E3F2FD; padding:14px 18px;">
<strong style="color:#0D47A1;">⭐ KEY POINT:</strong> <span style="color:#0D47A1;">ReAct turns AI-assisted React development from a "hope it produces the right component tree" approach into a controlled, verifiable process. Each cycle gives you a checkpoint where you can correct course — especially important when Copilot's first interpretation of a complex UI feature doesn't match your intent.</span>
</td>
</tr>
</table>

---

<table style="width:100%; border-collapse:collapse;">
<tr>
<td style="background:#00695C; color:white; padding:8px 16px; font-weight:bold;">0:18 – 0:26</td>
<td style="background:#E0F2F1; padding:8px 16px; color:#00695C; font-weight:bold; font-size:16px;">SECTION 3: Controlling Copilot's Output Style and Reasoning Depth</td>
</tr>
</table>

## <span style="color:#0D47A1;">3. Controlling Copilot's Output Style and Reasoning Depth</span>

Unlike the underlying AI models, GitHub Copilot does not expose temperature or thinking budget sliders to users. However, you have significant control over Copilot's output style and reasoning quality through **how you frame your prompts** and **which mode you use**.

### <span style="color:#0D47A1;">3.1  Directing Output Style: Conventional vs. Creative</span>

You can steer Copilot between "safe, standard" output and "exploratory, inventive" output through explicit prompt framing:

<table style="width:100%; border-collapse:collapse;">
<tr>
<th style="background:#1A73E8; color:white; padding:8px 12px; text-align:left;">Output Style</th>
<th style="background:#1A73E8; color:white; padding:8px 12px; text-align:left;">When to Use</th>
<th style="background:#1A73E8; color:white; padding:8px 12px; text-align:left;">Prompt Framing</th>
</tr>
<tr>
<td style="background:#E3F2FD; padding:8px 12px; border:1px solid #ccc;"><strong>Conservative / Standard</strong></td>
<td style="background:#E3F2FD; padding:8px 12px; border:1px solid #ccc;">Boilerplate code, matching an existing pattern, team-standard components, config files, test scaffolding</td>
<td style="background:#E3F2FD; padding:8px 12px; border:1px solid #ccc;">"Use the most conventional React pattern for this." / "Follow the pattern in #file:Component.tsx exactly." / "Use the standard approach, no clever tricks."</td>
</tr>
<tr>
<td style="padding:8px 12px; border:1px solid #ccc;"><strong>Creative / Exploratory</strong></td>
<td style="padding:8px 12px; border:1px solid #ccc;">Brainstorming architecture, exploring hooks patterns, looking for a better solution to a known problem</td>
<td style="padding:8px 12px; border:1px solid #ccc;">"Explore 3 different ways to implement this." / "What's the most elegant approach, even if unconventional?" / "Don't just use the obvious solution — consider alternative patterns."</td>
</tr>
<tr>
<td style="background:#E3F2FD; padding:8px 12px; border:1px solid #ccc;"><strong>Exhaustive Enumeration</strong></td>
<td style="background:#E3F2FD; padding:8px 12px; border:1px solid #ccc;">Design system components, variant mapping, test case generation</td>
<td style="background:#E3F2FD; padding:8px 12px; border:1px solid #ccc;">"Generate ALL variants." / "Be comprehensive — don't miss any edge case." / "List every possible state this component can be in."</td>
</tr>
</table>

**React examples:**

```text
# Conservative (following existing pattern):
"Create a SkeletonCard component following the exact same
Tailwind + TypeScript pattern as #file:src/components/UserCard.tsx.
Match the prop naming, export style, and class structure precisely."

# Creative (exploring alternatives):
"We need a way to handle optimistic UI updates for the cart.
Explore 3 different approaches — compare their trade-offs
in terms of complexity, error recovery, and user experience."

# Exhaustive (design system completeness):
"Generate the full AlertBanner component covering ALL severity
variants: info, success, warning, error, and critical.
Include dismissible and non-dismissible versions of each."
```

### <span style="color:#0D47A1;">3.2  Controlling Reasoning Depth</span>

The depth of analysis Copilot applies before generating code is directly proportional to how much you prompt it to think. More explicit reasoning prompts produce substantially better results for complex React tasks:

<table style="width:100%; border-collapse:collapse;">
<tr>
<th style="background:#1A73E8; color:white; padding:8px 12px; text-align:left;">Reasoning Level</th>
<th style="background:#1A73E8; color:white; padding:8px 12px; text-align:left;">Best For</th>
<th style="background:#1A73E8; color:white; padding:8px 12px; text-align:left;">Prompt Trigger</th>
</tr>
<tr>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;"><strong>Direct / Immediate</strong></td>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;">Standard components, simple hooks, known patterns</td>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;">(No special trigger — just state the task directly)</td>
</tr>
<tr>
<td style="padding:8px 12px; border:1px solid #ccc;"><strong>Step-by-Step</strong></td>
<td style="padding:8px 12px; border:1px solid #ccc;">Multi-step logic, complex hook interactions, data transformation</td>
<td style="padding:8px 12px; border:1px solid #ccc;">"Think step by step..." / "Walk me through your reasoning before generating..."</td>
</tr>
<tr>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;"><strong>Deep Analysis</strong></td>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;">Architecture decisions, performance optimization, state management strategy</td>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;">"Before answering, reason through the trade-offs carefully..." / "Analyze all the implications before recommending..."</td>
</tr>
<tr>
<td style="padding:8px 12px; border:1px solid #ccc;"><strong>Critical Review</strong></td>
<td style="padding:8px 12px; border:1px solid #ccc;">Security review, accessibility audit, edge case analysis</td>
<td style="padding:8px 12px; border:1px solid #ccc;">"Be critical and thorough. Don't just confirm what I wrote is fine — actively look for problems." </td>
</tr>
</table>

**Examples of reasoning depth prompts:**

```text
// Direct (no special prompt needed — quick boilerplate):
"Add a loading spinner variant to the Button component."

// Step-by-step (explain the logic before coding):
"Think step by step about how to implement infinite scroll
in a React component using IntersectionObserver. Explain
the approach before writing any code."

// Deep analysis (architectural decision with trade-offs):
"Before recommending an approach, reason through the trade-offs
of these three options for handling global notification state:
React Context + useReducer, Zustand store, or a dedicated
React Query mutation observer. Consider: bundle size, testing
isolation, devtools support, and our Zustand existing usage."

// Critical review (find problems, not confirm quality):
"Review #file:src/hooks/useAuth.ts critically. Actively look for
security issues, race conditions, missing error cases, and
XSS risks. Don't give me a summary of what it does — I want
a list of things that could go wrong."
```

### <span style="color:#0D47A1;">3.3  Mode Selection: Matching the Mode to the Task</span>

The Copilot mode you use is the most powerful output control available — more impactful than any prompt phrasing:

<table style="width:100%; border-collapse:collapse;">
<tr>
<th style="background:#0D47A1; color:white; padding:8px 12px; text-align:left;">Mode</th>
<th style="background:#0D47A1; color:white; padding:8px 12px; text-align:left;">Best React Use Cases</th>
<th style="background:#0D47A1; color:white; padding:8px 12px; text-align:left;">Limitation</th>
</tr>
<tr>
<td style="background:#E3F2FD; padding:8px 12px; border:1px solid #ccc;"><strong>Inline completion</strong></td>
<td style="background:#E3F2FD; padding:8px 12px; border:1px solid #ccc;">Completing JSX props, writing hook parameters, finishing import statements, boilerplate repetition</td>
<td style="background:#E3F2FD; padding:8px 12px; border:1px solid #ccc;">No chat context — only sees open editor files and recent code</td>
</tr>
<tr>
<td style="padding:8px 12px; border:1px solid #ccc;"><strong>Inline Chat (<kbd>Ctrl+I</kbd>)</strong></td>
<td style="padding:8px 12px; border:1px solid #ccc;">Refactoring a specific function, adding a prop to a component, explaining a block of JSX</td>
<td style="padding:8px 12px; border:1px solid #ccc;">Scoped to the active file — limited project-wide awareness</td>
</tr>
<tr>
<td style="background:#E3F2FD; padding:8px 12px; border:1px solid #ccc;"><strong>Copilot Chat</strong></td>
<td style="background:#E3F2FD; padding:8px 12px; border:1px solid #ccc;">Designing new hooks/components, debugging, architectural questions, generating tests</td>
<td style="background:#E3F2FD; padding:8px 12px; border:1px solid #ccc;">You apply suggestions manually — doesn't edit files directly</td>
</tr>
<tr>
<td style="padding:8px 12px; border:1px solid #ccc;"><strong>Agent mode</strong></td>
<td style="padding:8px 12px; border:1px solid #ccc;">Multi-file feature work, refactors touching 3+ files, full feature scaffolding with tests</td>
<td style="padding:8px 12px; border:1px solid #ccc;">Can make broad changes — always review the plan before proceeding</td>
</tr>
</table>

<table style="width:100%; border-collapse:collapse;">
<tr>
<td style="border-left:5px solid #1A73E8; background:#E3F2FD; padding:14px 18px;">
<strong style="color:#0D47A1;">⭐ KEY POINT:</strong> <span style="color:#0D47A1;">When a Copilot response feels shallow or incorrect for a complex React task, the first fix is to add reasoning depth to your prompt ("think step by step," "reason through trade-offs") before rephrasing the task itself. Deeper reasoning often resolves the issue without any other change.</span>
</td>
</tr>
</table>

### <span style="color:#0D47A1;">3.4  Combining Controls for Maximum Quality</span>

<table style="width:100%; border-collapse:collapse;">
<tr>
<th style="background:#0D47A1; color:white; padding:8px 12px; text-align:left;">React Task Type</th>
<th style="background:#0D47A1; color:white; padding:8px 12px; text-align:left;">Output Style</th>
<th style="background:#0D47A1; color:white; padding:8px 12px; text-align:left;">Reasoning Depth</th>
<th style="background:#0D47A1; color:white; padding:8px 12px; text-align:left;">Mode</th>
</tr>
<tr>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;">Boilerplate / config files</td>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;">Conservative</td>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;">Direct</td>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;">Inline or Chat</td>
</tr>
<tr>
<td style="padding:8px 12px; border:1px solid #ccc;">Standard component implementation</td>
<td style="padding:8px 12px; border:1px solid #ccc;">Conservative</td>
<td style="padding:8px 12px; border:1px solid #ccc;">Direct</td>
<td style="padding:8px 12px; border:1px solid #ccc;">Chat</td>
</tr>
<tr>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;">Complex state management design</td>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;">Exploratory</td>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;">Deep analysis</td>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;">Chat</td>
</tr>
<tr>
<td style="padding:8px 12px; border:1px solid #ccc;">Architecture planning</td>
<td style="padding:8px 12px; border:1px solid #ccc;">Exploratory</td>
<td style="padding:8px 12px; border:1px solid #ccc;">Deep analysis</td>
<td style="padding:8px 12px; border:1px solid #ccc;">Chat (Agent for execution)</td>
</tr>
<tr>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;">Multi-file feature scaffolding</td>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;">Conservative (follow standards)</td>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;">Step-by-step plan first</td>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;">Agent mode</td>
</tr>
<tr>
<td style="padding:8px 12px; border:1px solid #ccc;">Debugging a re-render issue</td>
<td style="padding:8px 12px; border:1px solid #ccc;">Conservative</td>
<td style="padding:8px 12px; border:1px solid #ccc;">Deep analysis</td>
<td style="padding:8px 12px; border:1px solid #ccc;">Chat with <code>#terminalLastCommand</code></td>
</tr>
<tr>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;">Security / accessibility audit</td>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;">Critical</td>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;">Critical review (find problems)</td>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;">Chat with <code>#file:</code> refs</td>
</tr>
</table>

---

<table style="width:100%; border-collapse:collapse;">
<tr>
<td style="background:#00695C; color:white; padding:8px 16px; font-weight:bold;">0:26 – 0:34</td>
<td style="background:#E0F2F1; padding:8px 16px; color:#00695C; font-weight:bold; font-size:16px;">SECTION 4: Iterative Refinement — From Good to Great</td>
</tr>
</table>

## <span style="color:#0D47A1;">4. Iterative Refinement — From Good to Great</span>

### <span style="color:#0D47A1;">4.1  The Refinement Mindset</span>

First-draft code from Copilot is like a first PR from a new team member — it captures the intent and broad structure, but it almost always needs review and feedback before it's production-ready. The React developers who get the most value from Copilot treat the first output as a starting point, not a final product.

The iterative refinement cycle for React:

<table style="width:100%; border-collapse:collapse;">
<tr>
<th style="background:#1A73E8; color:white; padding:8px 12px; text-align:left;">Cycle</th>
<th style="background:#1A73E8; color:white; padding:8px 12px; text-align:left;">Prompt Pattern</th>
<th style="background:#1A73E8; color:white; padding:8px 12px; text-align:left;">What Improves</th>
</tr>
<tr>
<td style="background:#E3F2FD; padding:8px 12px; border:1px solid #ccc;"><strong>1. Generate</strong></td>
<td style="background:#E3F2FD; padding:8px 12px; border:1px solid #ccc;">"Create a <code>DataTable</code> component with sorting and pagination using React Query."</td>
<td style="background:#E3F2FD; padding:8px 12px; border:1px solid #ccc;">Initial component structure and core logic</td>
</tr>
<tr>
<td style="padding:8px 12px; border:1px solid #ccc;"><strong>2. Evaluate</strong></td>
<td style="padding:8px 12px; border:1px solid #ccc;">"Review the component you just wrote. What are the potential issues with accessibility, performance, and edge cases?"</td>
<td style="padding:8px 12px; border:1px solid #ccc;">Copilot self-identifies weaknesses in its own output</td>
</tr>
<tr>
<td style="background:#E3F2FD; padding:8px 12px; border:1px solid #ccc;"><strong>3. Harden</strong></td>
<td style="background:#E3F2FD; padding:8px 12px; border:1px solid #ccc;">"Add proper handling for: empty data array, all rows loading, API error state, and keyboard navigation for sorting."</td>
<td style="background:#E3F2FD; padding:8px 12px; border:1px solid #ccc;">Robustness — handles all UI states correctly</td>
</tr>
<tr>
<td style="padding:8px 12px; border:1px solid #ccc;"><strong>4. Optimize</strong></td>
<td style="padding:8px 12px; border:1px solid #ccc;">"The component re-renders on every parent state change. Add <code>React.memo</code> and <code>useCallback</code> to the sort handlers. Justify each addition."</td>
<td style="padding:8px 12px; border:1px solid #ccc;">Performance — prevents unnecessary re-renders</td>
</tr>
<tr>
<td style="background:#E3F2FD; padding:8px 12px; border:1px solid #ccc;"><strong>5. Document</strong></td>
<td style="background:#E3F2FD; padding:8px 12px; border:1px solid #ccc;">"Add a JSDoc comment to the component and its props interface. Include a usage example in the JSDoc."</td>
<td style="background:#E3F2FD; padding:8px 12px; border:1px solid #ccc;">Maintainability — future developers understand intent</td>
</tr>
</table>

### <span style="color:#0D47A1;">4.2  Effective Feedback Prompts</span>

How you give feedback to Copilot directly determines how well it improves. Specific, constrained feedback produces targeted fixes; vague feedback produces guesswork:

<table style="width:100%; border-collapse:collapse;">
<tr>
<th style="background:#C62828; color:white; padding:8px 12px; text-align:left;">Vague Feedback (Avoid)</th>
<th style="background:#2E7D32; color:white; padding:8px 12px; text-align:left;">Specific Feedback (Use This)</th>
</tr>
<tr>
<td style="background:#FFEBEE; padding:8px 12px; border:1px solid #ccc;">"This doesn't work"</td>
<td style="background:#E8F5E9; padding:8px 12px; border:1px solid #ccc;">"The <code>useEffect</code> on line 24 fires on every render because <code>filters</code> is a new object reference each time. Move it to a <code>useMemo</code> or compare with deep equality."</td>
</tr>
<tr>
<td style="background:#FFEBEE; padding:8px 12px; border:1px solid #ccc;">"Make it faster"</td>
<td style="background:#E8F5E9; padding:8px 12px; border:1px solid #ccc;">"The component re-renders 12 times on a single filter change (measured with React DevTools profiler). The root cause is the <code>onRowClick</code> callback being recreated in the parent. Wrap it in <code>useCallback</code>."</td>
</tr>
<tr>
<td style="background:#FFEBEE; padding:8px 12px; border:1px solid #ccc;">"The tests are wrong"</td>
<td style="background:#E8F5E9; padding:8px 12px; border:1px solid #ccc;">"<code>test_adds_to_cart</code> uses <code>getByTestId</code> but our <code>copilot-instructions.md</code> says to use <code>getByRole</code>. Replace all <code>getByTestId</code> with accessible queries."</td>
</tr>
<tr>
<td style="background:#FFEBEE; padding:8px 12px; border:1px solid #ccc;">"It's not clean enough"</td>
<td style="background:#E8F5E9; padding:8px 12px; border:1px solid #ccc;">"The component is 180 lines. Extract the sort logic (lines 45–80) into a <code>useSortState</code> hook and the row rendering (lines 100–140) into a <code>TableRow</code> component."</td>
</tr>
<tr>
<td style="background:#FFEBEE; padding:8px 12px; border:1px solid #ccc;">"Try again"</td>
<td style="background:#E8F5E9; padding:8px 12px; border:1px solid #ccc;">"The approach of fetching all pages upfront won't work for large datasets. Switch to cursor-based pagination: fetch only the current page, and pass the cursor returned by the API for the next fetch."</td>
</tr>
</table>

### <span style="color:#0D47A1;">4.3  The Context-Reset + Refine Pattern</span>

For long refinement sessions, use this pattern to prevent context window degradation in Copilot Chat:

```text
# Phase 1: Initial generation (3–4 chat messages)
"Create the DataTable component with sorting and pagination..."
"Add loading and error states..."
"Add accessibility attributes..."

# Phase 2: Start a new chat for the refinement pass
# (Click + New Chat — this clears the accumulated context)

# Phase 3: Refine with focused, fresh context
"Review #file:src/components/DataTable.tsx and optimize
the sort handlers to prevent unnecessary re-renders.
The component currently re-renders on every keystroke in
the search bar even when no sort state has changed."

# Phase 4: Start another new chat for the final polish pass
# New Chat again

# Phase 5: Final quality pass
"Do a final review of #file:src/components/DataTable.tsx.
Check for: TypeScript type completeness, JSDoc coverage,
missing ARIA attributes, error boundary support, and
any test helper testid attributes that should be roles instead."
```

<table style="width:100%; border-collapse:collapse;">
<tr>
<td style="border-left:5px solid #1A73E8; background:#E3F2FD; padding:14px 18px;">
<strong style="color:#0D47A1;">⭐ KEY POINT:</strong> <span style="color:#0D47A1;">The best Copilot users follow the rule of three: generate, refine once for correctness and robustness, refine again for quality and maintainability. Three focused passes consistently produces React code that's ready for code review — rather than one long, divergent conversation.</span>
</td>
</tr>
</table>

---

<table style="width:100%; border-collapse:collapse;">
<tr>
<td style="background:#FFF3E0; padding:16px 20px; border:1px solid #FFCC80;">
<strong style="color:#E65100;">💬 THINK-PAIR-SHARE (2 minutes)</strong>
<ul style="color:#333; margin:8px 0; padding-left:20px;">
<li>Think of a React feature you built recently that took more than 30 minutes. How would you decompose it into Copilot-sized sub-tasks?</li>
<li>What would your first prompt be? What would your most important refinement prompt look like?</li>
<li>Share with the person next to you. We'll hear 1–2 examples from the group.</li>
</ul>
</td>
</tr>
</table>

---

<table style="width:100%; border-collapse:collapse;">
<tr>
<td style="background:#00695C; color:white; padding:8px 16px; font-weight:bold;">0:34 – 0:42</td>
<td style="background:#E0F2F1; padding:8px 16px; color:#00695C; font-weight:bold; font-size:16px;">SECTION 5: Team copilot-instructions.md — Scaling Standards Across Engineers</td>
</tr>
</table>

## <span style="color:#0D47A1;">5. Team copilot-instructions.md — Scaling Standards Across Engineers</span>

### <span style="color:#0D47A1;">5.1  From Personal to Team Standards</span>

In Module 2, we introduced `copilot-instructions.md` as a project-level system prompt. Now we'll build a team-calibrated file that ensures every React developer on your team gets consistent, standards-compliant components from Copilot — regardless of their individual prompting skill level.

<table style="width:100%; border-collapse:collapse;">
<tr>
<th style="background:#0D47A1; color:white; padding:8px 12px; text-align:left;">Personal Instructions (VS Code Settings)</th>
<th style="background:#0D47A1; color:white; padding:8px 12px; text-align:left;">Team copilot-instructions.md</th>
</tr>
<tr>
<td style="background:#E3F2FD; padding:8px 12px; border:1px solid #ccc;">Applies to you across all repos</td>
<td style="background:#E3F2FD; padding:8px 12px; border:1px solid #ccc;">Applies to everyone who opens this repo with Copilot</td>
</tr>
<tr>
<td style="padding:8px 12px; border:1px solid #ccc;">Your individual style preferences</td>
<td style="padding:8px 12px; border:1px solid #ccc;">Team-agreed React architecture and quality standards</td>
</tr>
<tr>
<td style="background:#E3F2FD; padding:8px 12px; border:1px solid #ccc;">Not version-controlled with the project</td>
<td style="background:#E3F2FD; padding:8px 12px; border:1px solid #ccc;">Lives in `.github/` — version-controlled, PR-reviewed, onboards new engineers automatically</td>
</tr>
<tr>
<td style="padding:8px 12px; border:1px solid #ccc;">Convenience and style</td>
<td style="padding:8px 12px; border:1px solid #ccc;">Quality gates, architecture guardrails, and compliance</td>
</tr>
</table>

### <span style="color:#0D47A1;">5.2  Anatomy of a Team copilot-instructions.md</span>

A well-structured team instructions file for a React project has five sections:

```markdown
# GitHub Copilot Instructions — React Dashboard App

## 1. Project Context
React 18 + TypeScript 5 single-page application.
Stack: Vite, React Router v6, React Query v5, Zustand,
Tailwind CSS v3, Jest, React Testing Library, MSW.
Target browsers: Chrome/Edge latest 2 versions.
Node: 20 LTS. Deploy target: Vercel.

## 2. Component Standards
- Functional components with hooks only — no class components ever
- Named exports for all components: `export function MyComponent`
- TypeScript prop interface defined immediately above each component
- All prop interfaces named `[ComponentName]Props`
- Max component length: 100 lines of JSX (extract hooks or sub-components if longer)
- No inline styles — Tailwind utility classes only
- Use `clsx` for conditional class strings
- Components must handle these states when applicable: loading, error, empty, and populated

## 3. State Management & Data Fetching
- Server state: React Query exclusively (no raw useEffect for API calls)
- Client UI state: useState for component-local, Zustand for cross-component
- No prop drilling deeper than 2 levels — use Zustand if needed
- All API fetches through the service functions in `src/api/` — no fetch/axios calls in components
- API base URL via `import.meta.env.VITE_API_BASE_URL` — never hardcoded

## 4. Testing Requirements
- Jest + React Testing Library for all components and hooks
- Query with `getByRole`, `getByLabelText`, `getByText` — never `getByTestId`
- Every component test must include at least one `axe` accessibility check
- API calls mocked with MSW (never mock fetch or axios directly)
- Co-locate tests: `Button.tsx` → `Button.test.tsx`
- Test naming: `it('should [expected behavior] when [condition]', ...)`

## 5. Safety Guardrails
- NEVER use `dangerouslySetInnerHTML` with unsanitized strings
- NEVER hardcode API keys, auth tokens, or backend URLs
- NEVER use array indexes as React keys for dynamic lists
- Sanitize all user input before rendering (use DOMPurify for HTML content)
- All forms must use controlled components with validation
- Log errors through the `src/utils/logger.ts` utility — never raw console.error in production code
```

### <span style="color:#0D47A1;">5.3  Advanced copilot-instructions.md Techniques</span>

**Technique 1: Scoped Instruction Files for Feature Areas**

Copilot supports additional instruction files with `applyTo` patterns in `.github/instructions/`. This lets you add module-specific rules that don't pollute the global file:

```markdown
<!-- .github/instructions/forms.instructions.md -->
---
applyTo: "src/components/forms/**,src/hooks/use*Form*"
---
## Form-Specific Standards
- All form components use React Hook Form — no manual onChange handlers
- Every input must have a corresponding label (htmlFor + id pattern)
- Validation schemas defined with Zod, passed to useForm's resolver
- Form submission handlers must show loading state and disable submit button
- Display field-level errors from Zod validation below each input
- NEVER call APIs directly from form submit handlers — use mutation hooks
```

```markdown
<!-- .github/instructions/api.instructions.md -->
---
applyTo: "src/api/**,src/hooks/use*Query*,src/hooks/use*Mutation*"
---
## API Layer Standards
- All query hooks return { data, isLoading, error } shapes
- All mutation hooks return { mutate, isPending, error } shapes  
- Every API function has explicit TypeScript return type annotation
- Include retry logic for network errors (React Query default retries are fine)
- Log API errors with request context via src/utils/logger.ts
```

**Technique 2: Negative Rules for Known Pitfalls**

Explicitly list patterns your team has encountered and wants to prevent. These are the highest-value lines in any instructions file:

```markdown
## Anti-Patterns — Do NOT Generate These

- Do NOT use array index as React key: `key={index}` — use stable IDs
- Do NOT add `useEffect` for derived state — use `useMemo` instead
- Do NOT use `&&` for React conditional rendering when the left side can be 0 or ''
  (use ternary operator: `{condition ? <Component /> : null}`)
- Do NOT put business logic inside components — extract to custom hooks
- Do NOT mutate Zustand state directly — always use store actions
- Do NOT create union types for component variants as strings without a const enum
- Do NOT use `any` type — use `unknown` with type guards if the shape is uncertain
```

**Technique 3: Reference Implementations**

Instead of lengthy rule descriptions, point Copilot to exemplar files in your codebase:

```markdown
## Reference Implementations — Follow These Patterns

- For new data-fetching hooks: follow the pattern in `src/hooks/useProducts.ts`
- For new page components: follow the layout structure in `src/pages/ProductListPage.tsx`
- For new form features: follow the pattern in `src/components/forms/LoginForm.tsx`
- For new Zustand store slices: follow `src/stores/cartStore.ts`
- For RTL tests: follow the structure in `src/components/DataTable.test.tsx`
```

<table style="width:100%; border-collapse:collapse;">
<tr>
<td style="border-left:5px solid #1A73E8; background:#E3F2FD; padding:14px 18px;">
<strong style="color:#0D47A1;">⭐ KEY POINT:</strong> <span style="color:#0D47A1;">A team <code>copilot-instructions.md</code> is a living document. Start with 10–15 rules, commit it to the repo, and add new rules every time Copilot generates code that violates your standards. The file grows organically into a comprehensive coding standard that's always enforced — automatically, on every engineer's machine, without code reviews needing to catch the same issues repeatedly.</span>
</td>
</tr>
</table>

<table style="width:100%; border-collapse:collapse;">
<tr>
<td style="border-left:5px solid #C62828; background:#FFEBEE; padding:14px 18px;">
<strong style="color:#C62828;">⚠️ WARNING:</strong> <span style="color:#C62828;">Never put sensitive information in <code>copilot-instructions.md</code>. Since the file is sent to GitHub's AI services as part of every Chat interaction, it must never contain API keys, auth tokens, internal server addresses, proprietary business logic details, or any information that should not leave your environment. Use generic placeholders like <code>process.env.VARIABLE_NAME</code> instead of actual values.</span>
</td>
</tr>
</table>

---

<table style="width:100%; border-collapse:collapse;">
<tr>
<td style="background:#00695C; color:white; padding:8px 16px; font-weight:bold;">0:42 – 0:45</td>
<td style="background:#E0F2F1; padding:8px 16px; color:#00695C; font-weight:bold; font-size:16px;">WRAP-UP: Putting It All Together</td>
</tr>
</table>

## <span style="color:#0D47A1;">6. Putting It All Together</span>

Let's see how the patterns from this module combine into a complete workflow for a realistic React task.

### <span style="color:#0D47A1;">6.1  Complete Workflow Example</span>

**Task:** Add sortable column headers and row selection with a bulk-delete action to an existing `DataTable` component.

<table style="width:100%; border-collapse:collapse;">
<tr>
<td style="background:#FFF3E0; padding:14px 18px; border:1px solid #FFCC80;">
<strong style="color:#E65100;">🚀 WORKFLOW DEMONSTRATION:</strong>
<ul style="color:#333; margin:10px 0; padding-left:20px;">
<li><strong>Step 1 (Decompose):</strong> Break into sub-tasks: sortable column type changes, sort state hook, row selection state hook, bulk action toolbar component, updated <code>DataTable</code> wiring, tests</li>
<li><strong>Step 2 (ReAct — Reason):</strong> "Analyze #file:src/components/DataTable.tsx. What would need to change to support sortable columns and multi-row selection? List every prop, type, and state change needed."</li>
<li><strong>Step 3 (ReAct — Act):</strong> "Now add a <code>useSortState</code> hook that tracks <code>{ sortKey, sortDirection }</code> and provides a <code>toggleSort(key)</code> function. Use #file:src/hooks/useProductSearch.ts as a structural reference."</li>
<li><strong>Step 4 (Observe):</strong> Apply the hook code, check TypeScript errors in VS Code Problems panel</li>
<li><strong>Step 5 (Refine):</strong> "The <code>toggleSort</code> callback is recreated on every render. Wrap it in <code>useCallback</code> with the correct dependencies."</li>
<li><strong>Step 6 (Team Instructions):</strong> Point out how <code>copilot-instructions.md</code> standards were automatically applied: named export, TypeScript interface, no inline styles, <code>getByRole</code> in tests</li>
</ul>
</td>
</tr>
</table>

---

## <span style="color:#1A73E8;">MODULE 3 RECAP</span>

<table style="width:100%; border-collapse:collapse;">
<tr>
<td style="background:#E3F2FD; padding:10px 14px; border-bottom:1px solid #BBDEFB;">✅ <strong>Problem decomposition:</strong> Types → hooks → components → tests. Sequence by dependencies. Each sub-task should be small enough for Copilot to nail on the first try.</td>
</tr>
<tr>
<td style="padding:10px 14px; border-bottom:1px solid #BBDEFB;">✅ <strong>ReAct framework:</strong> Reason before acting. Analyze → Implement → Observe → Reflect → Iterate. Catch component architecture mistakes before the code tree grows.</td>
</tr>
<tr>
<td style="background:#E3F2FD; padding:10px 14px; border-bottom:1px solid #BBDEFB;">✅ <strong>Output style control:</strong> "Follow the existing pattern exactly" for conservative output. "Explore alternatives" for creative exploration. Depth triggers ("think step by step") for complex tasks.</td>
</tr>
<tr>
<td style="padding:10px 14px; border-bottom:1px solid #BBDEFB;">✅ <strong>Reasoning depth:</strong> Add explicit reasoning prompts for architecture decisions. Use critical review prompts ("actively look for problems") for security and accessibility work.</td>
</tr>
<tr>
<td style="background:#E3F2FD; padding:10px 14px; border-bottom:1px solid #BBDEFB;">✅ <strong>Iterative refinement:</strong> Generate → evaluate → harden → optimize → document. Three focused passes produces PR-ready React code. Start a new chat between passes to keep context clean.</td>
</tr>
<tr>
<td style="padding:10px 14px;">✅ <strong>Team copilot-instructions.md:</strong> Version-controlled team standards that Copilot enforces automatically for every developer. Start with 10–15 rules, grow organically. Scoped instruction files for feature-area-specific rules.</td>
</tr>
</table>

---

## <span style="color:#1A73E8;">QUICK REFERENCE CARD</span>

<table style="width:100%; border-collapse:collapse;">
<tr>
<th style="background:#2E7D32; color:white; padding:8px 12px; text-align:left;">Pattern</th>
<th style="background:#2E7D32; color:white; padding:8px 12px; text-align:left;">When to Use</th>
<th style="background:#2E7D32; color:white; padding:8px 12px; text-align:left;">Key Phrase / Action</th>
</tr>
<tr>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;"><strong>Decomposition</strong></td>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;">Features touching 2+ files or components</td>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;">"First, let's break this into steps: types, hook, component, tests..."</td>
</tr>
<tr>
<td style="padding:8px 12px; border:1px solid #ccc;"><strong>ReAct: Reason</strong></td>
<td style="padding:8px 12px; border:1px solid #ccc;">Before any complex component refactor</td>
<td style="padding:8px 12px; border:1px solid #ccc;">"Analyze #file:Component.tsx and explain what needs to change..."</td>
</tr>
<tr>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;"><strong>ReAct: Act</strong></td>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;">After reviewing the analysis</td>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;">"Now implement [specific step]..."</td>
</tr>
<tr>
<td style="padding:8px 12px; border:1px solid #ccc;"><strong>Conservative output</strong></td>
<td style="padding:8px 12px; border:1px solid #ccc;">Matching existing component patterns</td>
<td style="padding:8px 12px; border:1px solid #ccc;">"Follow the pattern in #file:X.tsx exactly"</td>
</tr>
<tr>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;"><strong>Deep reasoning</strong></td>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;">Architecture decisions, state management</td>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;">"Think step by step..." / "Reason through the trade-offs..."</td>
</tr>
<tr>
<td style="padding:8px 12px; border:1px solid #ccc;"><strong>Iterative refine</strong></td>
<td style="padding:8px 12px; border:1px solid #ccc;">After first-draft component is generated</td>
<td style="padding:8px 12px; border:1px solid #ccc;">"Review and identify issues, then fix..." (new chat per pass)</td>
</tr>
<tr>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;"><strong>Team instructions</strong></td>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;">Project setup, enforcing team conventions</td>
<td style="background:#F5F5F5; padding:8px 12px; border:1px solid #ccc;">Add rules to <code>.github/copilot-instructions.md</code></td>
</tr>
</table>

---

## <span style="color:#1A73E8;">TRANSITION TO MODULE 4</span>

You've now learned both fundamental (Module 2) and advanced (Module 3) prompting patterns for GitHub Copilot in React. In Module 4, you'll take a deep dive into GitHub Copilot's tool surfaces — the three interaction modes, context variables, Agent mode, and configuration. Lab 1 is Module 6, where you'll put everything into practice on a real React codebase.

---

<div style="text-align:center; color:#666; font-size:12px; padding:20px 0;">
Vibe Coding with GitHub Copilot | React Developer Track<br>
Module 3 — Advanced Patterns & Workflows
</div>
