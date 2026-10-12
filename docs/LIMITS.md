# Capabilities and limits

## What this repository provides

| Capability | Included behavior | What else would be needed |
| --- | --- | --- |
| Tasks and notes | Local JSON state; add, list, finish, and summarize on demand | Private backup or manual transfer for another machine |
| Day planning | A skill that proposes a plan from supplied context | Your review and accurate task information |
| Research | A focused research workflow; optional live-search launch flag | Working search tools in the host and access to needed sources |
| Message drafting | Text prepared for review | An actual communication tool and explicit authorization to send |
| Email and calendar | No built-in connection or automatic reading | Eligible host integrations, account connection, permissions |
| Browser/computer actions | No browser driver or desktop automation | Tools actually provided by the host, plus access and approval |
| Voice | No voice client, phone calls, or audio service | A separately supported host feature |
| Mobile | No mobile app or state synchronization | A supported host workflow and separately arranged file access |
| Reminders and monitoring | Due-date labels only; no notifications or polling | A separately configured scheduler or reminder service |
| Persistent memory | Explicit local tasks and notes survive CLI runs | This checkout's data; no automatic import of other chats |

Installing instructions cannot grant unavailable tools, subscription features, account access, or operating-system permissions. Check what the current host exposes before promising an action.

## On demand, not always on

The helper exits after its command finishes. The launcher starts an interactive session only with `--run`. Nothing in the starter watches an inbox, wakes on a timer, checks overdue tasks while you're away, or resumes work after your computer closes.

An open Codex session can continue working and consuming usage according to its own behavior. Close it when you're finished. This repository is not a process supervisor or a kill switch for work started elsewhere.

## Usage controls are modest and honest

The helper's task and note operations do not call a model. `context --max-chars N` limits the brief to 500–12,000 characters, not the full session's token count. Tasks are considered by due date, then priority; only the ten most recent notes are considered. Whole records can be omitted when they do not fit, so check the full task list or relevant saved notes when completeness matters.

Brief inputs, explicit skills, focused tasks, disabled-by-default search, and no automatic delegation are intended to avoid unnecessary work. They cannot guarantee a particular number of requests, tokens, credits, or dollars. They do not enforce a subscription budget or stop Codex at a spending threshold.

OpenAI's plan allowance and API billing are different. Check current account limits with `/status` or the [usage guidance linked from pricing](https://learn.chatgpt.com/docs/pricing). Available models and limits can change; this starter deliberately does not pin a model, quota, exact price, or claimed savings percentage.

## Reliability boundaries

- Language-model output can be wrong; verify important claims and source dates.
- A saved task is not proof that an external action happened.
- A due date is not an appointment or reminder.
- Local JSON is not a multi-user database. Avoid simultaneous writers and keep backups.
- The notebook is intentionally small: at most 1,000 tasks and 1,000 notes, with a 2 MB state limit. Individual text fields accept up to 1,000 characters.
- Read-only mode protects against routine filesystem writes, but it is not a promise of offline operation or isolation from every inherited integration.
- Project instructions express intent. Actual controls come from the installed Codex version, sandbox, permissions, and your reviews.

For privacy and sharing details, read [SECURITY.md](SECURITY.md).
