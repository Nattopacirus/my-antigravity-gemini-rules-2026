## 1. Think Before Coding

**Don't assume. Don't hide confusion. Surface tradeoffs.**

Before implementing:
- State your assumptions explicitly. If uncertain, ask.
- If multiple interpretations exist, present them - don't pick silently.
- If a simpler approach exists, say so. Push back when warranted.
- If something is unclear, stop. Name what's confusing. Ask.

## 2. Simplicity First

**Minimum code that solves the problem. Nothing speculative.**

- No features beyond what was asked.
- No abstractions for single-use code.
- No "flexibility" or "configurability" that wasn't requested.
- No error handling for impossible scenarios.
- If you write 200 lines and it could be 50, rewrite it.

Ask yourself: "Would a senior engineer say this is overcomplicated?" If yes, simplify.

## 3. Surgical Changes

**Touch only what you must. Clean up only your own mess.**

When editing existing code:
- Don't "improve" adjacent code, comments, or formatting.
- Don't refactor things that aren't broken.
- Match existing style, even if you'd do it differently.
- If you notice unrelated dead code, mention it - don't delete it.

When your changes create orphans:
- Remove imports/variables/functions that YOUR changes made unused.
- Don't remove pre-existing dead code unless asked.

The test: Every changed line should trace directly to the user's request.

## 4. Goal-Driven Execution

**Define success criteria. Loop until verified.**

Transform tasks into verifiable goals:
- "Add validation" → "Write tests for invalid inputs, then make them pass"
- "Fix the bug" → "Write a test that reproduces it, then make it pass"
- "Refactor X" → "Ensure tests pass before and after"

For multi-step tasks, state a brief plan:
```
1. [Step] → verify: [check]
2. [Step] → verify: [check]
3. [Step] → verify: [check]
```

Strong success criteria let you loop independently. Weak criteria ("make it work") require constant clarification.

---

**These guidelines are working if:** fewer unnecessary changes in diffs, fewer rewrites due to overcomplication, and clarifying questions come before implementation rather than after mistakes.

**Rule: Agent Workspace Context** Whenever the user runs a custom command (like /create-stories) or requests a new task, you MUST ALWAYS use the list_dir or view_file tools to check the .agents and .antigravity directories for any relevant .md guideline files before taking any action or generating any output.

**Rule: Automated Workflow Visualization**
Whenever you create, update, or modify any Markdown (`.md`) file, you MUST analyze the content for procedural steps, system architectures, or sequential logic. If any part of the process can be reasonably explained or clarified using a visual flow, you MUST generate and embed a corresponding workflow diagram directly into the document using **Mermaid** syntax (wrapped in ` ```mermaid ` blocks). 

CRITICAL REQUIREMENT: Every sequential step or interaction within the diagram MUST be explicitly numbered (e.g., "1. Verify Input", "2. Process Data", "3. Save to DB") to clearly define the chronological order of the workflow. Ensure the diagrams are logical, clear, and accurately reflect the written guidelines.

**Important Rule**
No Partial Execution: If a task has multiple explicitly defined sub-items or endpoints in the plan, you MUST implement all of them. If you feel it's too large and want to break it down, you MUST stop and ask for my permission first. NEVER silently skip or defer items.

If you are given complex instructions, code architecture, refactoring, or ambiguous commands, please refrain from acting immediately. Instead, use the AskUserQuestion tool to ask questions one by one until you have enough information for good practice. Small modifications or clear, contextually complete commands can then be implemented immediately.


# Rule: Delivery Checklist (API vs UI Integrity)
Before completing any task and presenting it to the user, you MUST verify the following:
1. **Type mismatches:** Ensure there is no type mismatch between the Backend and Frontend (e.g., String from DOM vs Number from DB). If a loose or strict equality check is used, ensure the types match perfectly via casting.
2. **JSON Response Completeness:** Ensure that the JSON response payload from the Backend contains all the fields that the UI expects and uses.
If any risks or mismatches are found, YOU MUST FIX THEM IMMEDIATELY before concluding the implementation.

# CONTEXT MANAGEMENT & TOKEN CONSERVATION PROTOCOL

## 1. Scratchpad Protocol (State Externalization)
- Never rely on long chat context. Maintain project state strictly in `.agents/context_tracker.md`.
- Update `.agents/context_tracker.md` immediately upon completing any milestone or subtask using this format:
  ```markdown
  # Active Task: [Current Feature / Story]
  - Status: [IN_PROGRESS | COMPLETED | BLOCKED]
  - Architecture & Decisions: [Key choices & rationale]
  - Modified Files: [Exact file paths created/edited]
  - Blocker / Assumptions: [Unresolved issues or errors]
  - Next Step: [Single, immediate next action]