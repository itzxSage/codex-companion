# Codex Companion

A small, on-demand personal-assistant starter for Codex: keep a local task list, carry a short context brief between sessions, plan your day, research a question, and draft a reply.

Designed for someone using Codex with ChatGPT Plus. This is an independent starter project, not an OpenAI product or a recreation of a hosted assistant service. It has no background worker, polling loop, API dependency, or automatic account connections.

## What you get

- A Python 3.10+ command-line helper using only the standard library
- Local tasks and notes in an ignored `.companion/state.json` file
- A bounded context brief instead of rereading an ever-growing transcript
- Four explicit-use Codex skills: day plan, research brief, draft reply, and wrap-up
- A preview-first launcher and source-only ZIP export
- Tests, setup instructions, and clear security and capability limits

## Five-minute quickstart

Prerequisites: Python 3.10+ and a current [Codex CLI installation](https://learn.chatgpt.com/docs/codex/cli). Sign in with your ChatGPT account. [Codex is included with Plus](https://learn.chatgpt.com/docs/pricing), subject to your account's current limits.

Download or clone this repository, open its folder in a terminal, then run:

```sh
python companion.py doctor
python companion.py demo
python companion.py init
python companion.py add "Plan a weekend hike" --priority 2 --next "Pick a route"
python companion.py context --max-chars 6000
python companion.py launch
```

Use `python3` if that's your Python 3 executable. On Windows, `py -3` can replace `python` in every example.

`demo` uses temporary synthetic data. `init` creates your real local state. `launch` only prints the proposed Codex arguments; it does not start a model session.

When you're ready:

```sh
python companion.py launch --run
```

Inside Codex, enter `/model` and select an available lighter model for everyday tasks, then use `/status` to inspect the session and remaining limits. Choose a stronger supported model for difficult or high-consequence analysis, and still verify important conclusions. No model name is hardcoded here. Before doing sensitive work, review the [inherited-tool caveat](docs/SECURITY.md#inherited-tools-and-settings).

For a first session, try:

```text
Help me set this up. Ask what name to use for me, my timezone, and my top three priorities. Suggest what would be useful to remember, but save only details I explicitly approve. Keep personal drafts under work/.
```

Answer only what you're comfortable sharing. Saving requires a write-enabled session or a local `note`/`add` command.

Try this prompt inside Codex:

```text
$day-plan Use my local task brief. Suggest three priorities and a realistic next step for each. Keep it short.
```

The launch defaults to a read-only filesystem sandbox. Add `--write` only when you want Codex to save changes in the workspace. Add `--research` for live web search. These switches do not start anything unless you also pass `--run`.

## Everyday commands

```sh
python companion.py list
python companion.py list --all
python companion.py add "Renew library books" --due 2030-01-15 --priority 1 --next "Check renewal options"
python companion.py note "Prefer a short plan with one concrete next step."
python companion.py notes
python companion.py edit TASK_ID --priority 1 --next "Choose a time to start"
python companion.py done TASK_ID
python companion.py context --max-chars 4000
```

Replace the sample date and `TASK_ID` with your own values. Priority 1 is highest; 3 is lowest. Due dates are task labels, not scheduled reminders.

To clear a task's due date, use `edit TASK_ID --due none`. To remove a saved note, run `notes`, check its current number, then run `forget NUMBER`. This permanently removes that local note without another prompt; it does not erase backups or earlier chats.

Use these skills explicitly in a Codex prompt:

| Skill | Useful for |
| --- | --- |
| `$day-plan` | Choosing a small, actionable plan from your current tasks |
| `$research-brief` | Answering one question with sources and stated uncertainty |
| `$draft-reply` | Preparing a message for your review |
| `$wrap-up` | Summarizing progress and proposing the next starting point |

Drafting never means sending. No skill creates a permanent background process. Skills are instructions, so results still need judgment and review.

## Keep usage modest

Do bookkeeping with the local helper. Give Codex one focused outcome and only the relevant brief. Start with a lighter available model, ask for concise results, and enable research only when needed. These are usage-reduction choices, not a provider-enforced spending cap or a promise of particular savings. See [limits](docs/LIMITS.md).

## Test and share

```sh
python -m unittest discover -s tests -v
python companion.py export ../codex-companion-starter.zip
```

Export includes only the project's explicit source allowlist. It excludes `.companion/` and `work/`. Inspect the archive before sharing: private text manually added to a public source file would still be included.

## Read next

- [Setup and troubleshooting](docs/SETUP.md)
- [Opt-in email, calendar, browser, and file integrations](docs/INTEGRATIONS.md)
- [Five-minute acceptance check](docs/ACCEPTANCE.md)
- [Capabilities, usage, and limits](docs/LIMITS.md)
- [Security and safe sharing](docs/SECURITY.md)
- [Official sources, checked 2026-10-10](docs/SOURCES.md)
