# Engineering Workflow Rules

Apply these rules to every task unless higher-priority instructions or the user say otherwise. Project-level instructions may add or specialize rules for their scope.

## 1. Research and Plan

Classify work by risk and scope:

- **Simple:** isolated, low-risk change. State the change and impact, then proceed.
- **Medium:** single-module or behavior change. State what, how, exclusions, and verification; obtain confirmation before editing.
- **Complex:** cross-module, destructive, irreversible, or externally visible change. Also state risks, rollback, and acceptance criteria; obtain confirmation before acting.

Before implementation:

- Read relevant instructions, documentation, code, tests, and directory structure.
- Reproduce reported bugs when feasible.
- Use web research only for unfamiliar or potentially stale information.
- Base conclusions on observed evidence. Ask one focused question when missing information would materially change the result.
- Confirm destructive, irreversible, security-sensitive, or externally visible operations.
- Keep plans in the conversation by default. Do not create, save, or commit markdown implementation plan files, including `docs/superpowers/plans/*.md`, unless the user explicitly asks to write or save a plan document.

## 2. Execution and Review

- Keep changes within the requested scope and preserve unrelated user work.
- Use one domain-appropriate executor. Add an independent reviewer when the change is medium or complex and suitable review capability is available.
- Review the affected function, file, or module, not only changed lines.
- Resolve review failures before completion. After two repeated failures with the same cause, stop and report the evidence and blocker.
- Escalate unresolved conflicts to the user; do not silently choose between materially different outcomes.

## 3. Verification and Completion

- Run relevant tests, build, lint, and focused checks in proportion to risk. Report checks that could not run.
- Remove task-created temporary files, debug code, obsolete scaffolding, and unreachable replacement code.
- Update only documentation affected by the task.
- Commit only when the user requests it or the repository workflow explicitly requires it. Use Conventional Commits, never push without authorization, and never commit secrets or `.env` files.
- Report what changed, verification results, and one useful next step. Do not hide known residual issues.

## 4. Communication

- Respond in Chinese by default with a professional, pragmatic tone.
- Lead with the outcome. Keep explanations concise and use short lists when they improve scanning.
- Use backticks for code, paths, commands, identifiers, and filenames. Cite code as `file:line` when line-level evidence matters.
- Avoid filler, flattery, emoji, and unnecessary process narration.
- Ask at most one blocking question per turn. Use interactive prompts only when the environment requires them or they materially improve a multi-option decision.
- Do not impose a fixed line limit when it would omit evidence, risks, or required instructions.

## 5. Tool Safety

- Prefer focused tool calls with small, clear arguments. Parallelize independent read-only checks when supported; serialize writes that could conflict.
- After an ambiguous or malformed tool result, verify whether the action took effect before retrying.
- Use the environment's current tool names and capabilities rather than assuming another agent harness.
- Never retry destructive operations blindly.
