---
name: asking-clarifying-questions
description: Asks targeted clarifying questions when requirements are ambiguous or underspecified. Use when requests lack critical details, have multiple valid interpretations, mention vague requirements, or assume unclear context. Prevents wrong work by gathering essential information upfront.
allowed-tools: AskUserQuestion Read Grep Glob
---

# Asking Clarifying Questions

Ask the minimum necessary clarifying questions to avoid doing wrong work. Use this when requirements are underspecified or when multiple plausible interpretations exist.

## Clarification workflow

Copy and use this checklist when requirements are unclear:

```
Clarification Progress:
- [ ] Step 1: Discover what's knowable (read files, check patterns)
- [ ] Step 2: Identify must-have questions (1-5 only)
- [ ] Step 3: Ask with clear options and defaults
- [ ] Step 4: Confirm understanding
- [ ] Step 5: Proceed with work
```

## Step 1: Discover first

Before asking questions, explore what you can determine on your own. Read config files (package.json, .env), check existing patterns in the codebase, review project structure, and look at similar implementations. Don't ask questions you can answer with quick discovery.

## Step 2: Identify must-have questions

Ask 1-5 questions maximum that eliminate whole branches of work. Focus on questions where the answer significantly changes your approach. Typical categories include objective (what changes vs stays), scope (which files or components), constraints (compatibility, performance, style), done criteria (what defines success), and environment (versions, dependencies, tools).

If multiple plausible interpretations exist, the request is underspecified.

## Step 3: Ask with AskUserQuestion tool

Structure questions to be easy to answer:

Use short headers (max 12 characters like "Scope", "Approach", "Testing"). Provide 2-4 options per question. Give clear descriptions showing tradeoffs. Mark recommended defaults based on project patterns. Set `multiSelect: true` when choices aren't mutually exclusive.

**Scope question example:**

```typescript
{
  question: "What scope should this change have?",
  header: "Scope",
  options: [
    { label: "Minimal (Recommended)", description: "Only files directly needed" },
    { label: "With refactoring", description: "Also improve surrounding code" }
  ]
}
```

**Approach question example:**

```typescript
{
  question: "Which implementation approach?",
  header: "Approach",
  options: [
    { label: "Option A (Recommended)", description: "Specific tradeoffs" },
    { label: "Option B", description: "Different tradeoffs" }
  ]
}
```

## Step 4: Handle "you decide" requests

When the user asks you to proceed without specifics, state your assumptions as a numbered list (2-5 items max) based on project patterns, then use AskUserQuestion to confirm. Only proceed after confirmation.

## Step 5: Confirm and proceed

Restate requirements in 1-3 sentences including key constraints and success criteria. List any remaining assumptions. Start work only after confirmation.

## Anti-patterns

Don't ask questions you can discover yourself. Don't ask open-ended questions without providing specific options. Don't overwhelm with 10+ questions when 3 would suffice. Don't hide the recommended option. Don't ask about non-critical details when existing patterns work fine.

## When you've succeeded

You asked only questions that eliminate significant uncertainty. Each question offered clear, distinct choices with sensible defaults. Questions were easy to answer quickly. You confirmed understanding before starting work. You avoided asking things discoverable through exploration.
