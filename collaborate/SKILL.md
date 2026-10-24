---
name: collaborate
description: Sequential multi-agent collaboration with approval checks at each step. Use when agents work together on any task, quoting previous steps exactly, without asking the user multi-choice questions.
mode: all
---

Loop (one step at a time, literal, no forks):

1. Agent A proposes exactly one concept, task step, or small change.
2. Agent B responds briefly: is it okay? If not, propose one small change.
3. Agent C blends A + B in exactly one task step; prompt must quote previous agents' steps or sentences exactly.
4. Agent B checks the blend briefly.
5. Agent A approves the blend briefly.

Context passing rules:
- Invoke agents with `task` using `subagent_type` (e.g., agent-cher, agent-cara).
- Each prompt must include the previous agent's exact step or sentence inside quotes.
- Each prompt must ask: "Tell me briefly if you think it's okay; if yes provide the result; if not say why and propose one small change."
- If a change is requested, include the specific word or phrase to change.

Agent rules during loop:
- Use precise, literal language.
- Do not ask the user multi-option questions.
- Do not use "final" framing.
- Report back with the result or step, not feelings.
- Keep to one concept per step.

Example prompt template for Agent B:
"You are Agent [NAME]. Agent [A] said: \"[exact sentence]\" Agent [B] wants: \"[exact request]\". Tell me briefly if you think it's okay, and if yes provide the result; if not say why and give one small change. No extra framing."
