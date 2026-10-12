# Setup

## 1. Prepare your machine

Use Python 3.10 or newer. No `pip install` is needed for this repository. Check your interpreter:

```sh
python --version
```

On macOS/Linux, try `python3`. On Windows, try `py -3 --version` and use `py -3 companion.py ...` for the commands below.

Install Codex using the instructions for your platform on the [official CLI page](https://learn.chatgpt.com/docs/codex/cli). Installation methods change; use the current official option rather than an installer copied from a random tutorial. Sign in with ChatGPT to use your eligible subscription.

If your Windows workflow needs Linux tools, follow OpenAI's [WSL2 guide](https://learn.chatgpt.com/docs/windows/wsl). Keep Python, Codex, the terminal, and this checkout in the same environment. Native Windows and WSL are separate installations.

## 2. Try the local helper

From the repository directory:

```sh
python companion.py doctor
python companion.py demo
python -m unittest discover -s tests -v
```

The demo does not initialize or edit your real state. `doctor` is a local readiness check, not proof of subscription entitlement, working authentication, or every host capability.

Create your private task store only when ready:

```sh
python companion.py init
python companion.py add "Prepare next week's plan" --priority 2 --next "Choose one outcome"
python companion.py list
python companion.py context --max-chars 6000
```

The data belongs to this checkout. A new clone does not inherit it. Back it up privately if you need it elsewhere; the shareable export deliberately omits it.

Use `list --all` to include completed tasks. Use `edit TASK_ID` with `--title`, `--due`, `--priority`, or `--next` to correct a task. `notes` shows saved note numbers; `forget NUMBER` immediately removes the selected local note. Recheck numbers after each deletion, because they can shift. Copies in backups and previous chats remain.

## 3. Start a session deliberately

```sh
python companion.py launch
python companion.py launch --run
```

The first command previews arguments as JSON. The second starts interactive Codex. There is no automatic API-key fallback. If ChatGPT login or account access fails, resolve that through Codex rather than adding an API key to this project.

The launcher's defaults are read-only, ChatGPT authentication, human-reviewed approval requests, no live search, no spawned agents, and apps disabled by default. Existing per-app overrides, MCP servers, hooks, and other inherited settings still need your review. See [security](SECURITY.md).

Opt into only what the task needs:

```sh
python companion.py launch --research --run
python companion.py launch --write --run
```

`--research` enables live web search; `--write` selects workspace-write. You can combine them. Neither option promises access to email, a browser, or other external services.

Inside Codex, inspect `/model` and `/status`. Choose an available lighter model and modest reasoning effort for simple work. Use a stronger setting only if the task warrants it. See the [CLI command examples](https://learn.chatgpt.com/docs/codex/cli) and [usage guidance](https://learn.chatgpt.com/docs/pricing).

## 4. Use the project guidance

Open Codex in this repository so it can discover its `AGENTS.md` and `.agents/skills/`. Global and parent-directory guidance may also apply; ask Codex which instruction files it loaded if behavior is surprising. [OpenAI documents the discovery order](https://learn.chatgpt.com/docs/agent-configuration/agents-md).

Use `$day-plan`, `$research-brief`, `$draft-reply`, or `$wrap-up` explicitly. The included skill metadata disables implicit invocation; see the [official skills guide](https://learn.chatgpt.com/docs/build-skills). If a skill does not appear, check the working directory and restart Codex.

## Optional configuration

The example in `config/companion.example.toml` is a reference, not an installer. Nothing here overwrites your global Codex configuration. Prefer the launcher for per-session choices; review and merge any lasting changes yourself using the [current configuration reference](https://learn.chatgpt.com/docs/config-file/config-reference).

Current interactive approval settings are `approval_policy = "on-request"` and `approvals_reviewer = "user"`. Old guides recommending `approval_policy = "untrusted"` are outdated. Human review applies to approval requests; it does not mean every allowed action requires a click.

## Troubleshooting

- **`codex` not found:** finish the official installation, restart your terminal, and confirm it is on that environment's PATH.
- **Unsupported configuration key:** check `codex --version`, update through the official installation route, and compare the current configuration reference. Do not solve this by disabling safeguards.
- **No local state:** run `init` in the intended checkout. Do not substitute unrelated personal files.
- **Codex cannot save a wrap-up:** use `--write` for an authorized editing session, or update tasks yourself with the helper.
- **No search or integrations:** `--research` enables search only. Verify actual installed tools and their permissions separately.
- **Usage limit reached:** inspect `/status` and the account's usage page. Wait for the stated reset or make an explicit account decision; the starter does not buy credits or change plans.
