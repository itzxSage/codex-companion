---
name: day-plan
description: Turn the owner’s selected tasks into a short realistic daily plan when explicitly requested.
---

# Day Plan

Read a bounded notebook brief with `python companion.py context` only if the owner wants to use saved tasks. Ask for today's available time and timezone if deadlines depend on them; otherwise mark assumptions. Select up to three outcomes, explain dependencies, and suggest the next concrete action. Identify stale or overdue tasks for confirmation rather than treating them as current. Do not edit a calendar or contact anyone. If calendar tools are actually connected and the owner requested a live schedule check, read the relevant date range only. Ask before recording changes to the notebook unless task tracking was requested. Output a short plan, a blocker if any, and the best first step.
