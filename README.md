# Antigravity Gemini Rules 🚀

A battle-tested `GEMINI.md` ruleset for **Antigravity IDE**, customized by a CPE undergrad juggling classes and client freelance deadlines to stop AI from hallucinating, breaking production code, or over-engineering simple features.

---

## Why This Exists

Freelancing taught me that broken API contracts and unrequested refactors kill project margins. This ruleset forces Gemini to act like a disciplined junior engineer who asks before breaking things and delivers verified, working code.

* **Personal Archive:** I put this repo together primarily as a backup for my own workflow so I never lose it across machine setups, clean installs, or future projects.
* **Community Credit:** The foundation was adapted from community rulesets floating around the web a while back. I honestly lost the original link/thread, but full credit to whoever authored that initial baseline—I've just iterated on it with rules forged from real client headaches.

### Key Rules

* **Think Before Coding:** Forces explicit assumptions upfront and clarifies ambiguity instead of silently guessing.
* **Simplicity First:** Prioritizes minimal code solutions over unnecessary abstractions and speculative features.
* **Surgical Changes:** Mandates edits strictly related to the task; prohibits refactoring adjacent working code.
* **Goal-Driven Execution:** Requires testable success criteria and step-by-step verification.
* **No Partial Execution:** Forbids skipping or deferring sub-tasks without explicit permission.
* **Delivery Checklist:** Enforces contract checks between Frontend and Backend, eliminating type mismatches and missing JSON payload fields before handoff.

---

## Setup

1. Drop `GEMINI.md` into the root directory of your project.
2. Verify that Antigravity tools (`list_dir`, `view_file`, and `AskUserQuestion`) are accessible by the agent.
3. Maintain project context guidelines within `.agents/` or `.antigravity/` folders for automated discovery.

---

## Freelancer Tip: Token Optimization (Opt-in Mermaid Diagrams)

The configuration includes an automated workflow visualization rule requiring a numbered Mermaid diagram for every `.md` file update.

* **Token-Saving Mode:** Comment out or delete the `Rule: Automated Workflow Visualization` block if working on brief notes or fast iterations.
* **Documentation Mode:** Retain the rule when building architecture specs or client-facing process workflows.