# Rules Experiments (Cursor Agent)

## Rules File Location
- `.cursor/rules/agent.mdc`

---

## What I Changed
I added a persistent rules file (`alwaysApply: true`) to guide the AI agent’s behavior in this repository. The rules enforce:

- A structured response format: **Understanding → Plan → Action → Verification → Notes/Risks → Questions**
- Minimal diffs and a “don’t invent APIs/files” discipline
- A required verification step before claiming a task is complete
- Safety guardrails (avoid destructive actions, don’t output secrets)
- A “living rules” habit (update rules when repeated mistakes happen)

---

## Experiment 1 — README Creation (Behavior After Rules)

**Prompt used:**
> Add a minimal README.md for this repository explaining its purpose and how to get started. Keep changes small and include how to verify the result.

**Observed behavior:**
- The agent followed the expected structure (Understanding, Plan, Action, Verification, Notes/Risks)
- It kept changes minimal and avoided inventing languages, tools, or frameworks
- It explicitly included verification commands (e.g., checking file contents and viewing diffs)

**Outcome:**
- A clean, concise README was produced
- The README included a purpose section, setup guidance, and verification steps
- The agent behavior matched the rules without additional prompting

---

## Experiment 2 — Assessment Checklist Improvement (Verification + Minimal Diff)

**Prompt used:**
> Propose ONE small improvement to this repo that helps future candidates complete the assessment faster. Implement it with minimal changes, and include exact verification steps.

**Observed behavior:**
- The agent proposed adding a `CHECKLIST.md` file to guide candidates through the assessment
- It broke the work down into **Task 1 (MCP Setup), Task 2 (Agent Rules), and Task 3 (Documentation)**
- Each task included concrete verification commands (e.g., checking config files, git status)
- Changes were minimal: one new documentation file and a single link added to `README.md`

**Outcome:**
- A lightweight `CHECKLIST.md` was added that makes the assessment process clearer and faster
- Verification steps make progress observable and reduce ambiguity
- The improvement was low-risk, non-invasive, and immediately useful

---

## What Worked
- Structured agent output reduced randomness and improved clarity
- Verification requirements consistently produced more reliable results
- Minimal-diff guidance prevented unnecessary rewrites
- The agent successfully proposed process improvements, not just code changes

---

## What Didn’t Work / Challenges
- When the MCP analytics server experienced session instability (SSE / Bad Gateway errors), logging attempts failed even though the client setup was correct
- This did not affect rule-driven agent behavior, but it limited analytics logging during some interactions

---

## Insights Gained
- Repo-level rules strongly influence agent behavior across sessions and models
- Explicit verification requirements are the most effective guardrail for correctness
- Treating rules as a living artifact enables continuous improvement rather than repeated correction
- AI agents can be effective collaborators not only for code, but also for improving developer workflows and documentation
