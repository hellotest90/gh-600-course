# Agent team for Mona's Project Pulse dashboard

This project will use a small custom agent team to coordinate planning, design, implementation, and execution through GitHub Copilot CLI in a Codespace.

## Custom agents

| Agent | Target model | Responsibility | Agent definition |
| --- | --- | --- | --- |
| Orchestrator | Claude Opus 4.7 (copilot) | Breaks the work into phases, delegates tasks to specialist agents, and coordinates the overall delivery of the Project Pulse dashboard. | `.github/agents/orchestrator.agent.md` |
| Planner | Claude Opus 4.7 (copilot) | Researches the repo and requirements, identifies edge cases, and produces an implementation plan with file ownership, dependencies, and validation expectations. | `.github/agents/planner.agent.md` |
| Designer | Gemini 3.1 Pro (copilot) | Creates the UI/UX direction, information hierarchy, accessibility, and polished dashboard styling for the Project Pulse frontend. | `.github/agents/designer.agent.md` |
| Coder | GPT-5.5 (copilot) | Implements the logic and code changes in the assigned file scope, fixes bugs, and validates behavior before reporting completion. | `.github/agents/coder.agent.md` |

## Team workflow

The Orchestrator will use GitHub Copilot CLI in a Codespace to coordinate the team. It will gather a plan from the Planner, delegate design work to the Designer, and assign implementation work to the Coder while keeping file scopes clear and minimizing overlap. The result is a structured, multi-agent workflow for building Mona's Project Pulse dashboard.
