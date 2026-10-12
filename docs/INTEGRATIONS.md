# Optional integrations

Start with the local notebook. Add one connection only when a concrete task needs it. This repository does not install connectors, supply credentials, or build a custom API backend.

The [official CLI guide](https://learn.chatgpt.com/docs/codex/cli) describes plugins and MCP, and illustrates Gmail, Google Calendar, and Google Drive. That is not a guarantee for your account or rollout. Inspect the tools available in your actual session; do not assume a connection in ChatGPT chat also appears in Codex CLI. Checked 2026-10-10.

## A small connection checklist

1. **Define the source and task.** Name the account, folder, calendar, or site and the exact result you want. Avoid granting whole-account access just to answer one question.
2. **Inspect available tools.** Use your host's plugin/MCP controls. Check publisher, official source, requested permissions, and what each exposed tool can read or change. Prefer read-only access where supported.
3. **Connect deliberately.** Approve the connection yourself using the service's supported sign-in flow. Keep passwords, API keys, tokens, and connection secrets out of this repository and its notes.
4. **Verify one authorized item.** Ask for a small read of an item you chose. Confirm the account, title, date, and source link. An installed integration is not proof of usable access.
5. **Draft first.** Review the proposed message, event, document change, or form values. Give explicit approval for sending or applying it, with the recipient/destination and final content clear.
6. **Check the result.** Ask for the resulting message, event, or file link and verify it. Keep only a short, approved summary in the notebook. Disable unneeded access using the host's controls.

The launcher sets app access off by default. Enabling a selected integration is a separate opt-in host configuration step; inspect the resulting tool list. `--write` grants workspace editing, and `--research` enables web search. Neither switch connects accounts. Review the [security caveats](SECURITY.md#inherited-tools-and-settings) and [official configuration reference](https://learn.chatgpt.com/docs/config-file/config-reference) before changing settings.

## Good first checks

| Source | Small read to verify | Review before changes |
| --- | --- | --- |
| Email | One message or thread you identify | Exact sender account, recipient, subject, body, attachments |
| Calendar | One named event or a narrow date range | Timezone, date/time, invitees, meeting link, any notifications |
| Browser | One public page using an available browser tool | Site identity, login, uploads, form values, final submission |
| Files | One selected local file or connected document | Correct version, destination, overwrite risk, sharing audience |

If a tool is missing, stop at a local draft or use material you deliberately provide. Do not install an arbitrary server or broaden permissions just to bypass that gap. Search is not browser control; reading a file does not authorize sharing it.

## A quality ladder

- **No model:** use the helper for task bookkeeping and context extraction.
- **Lighter available model:** routine plans, short summaries, straightforward drafts.
- **Stronger supported model:** difficult reasoning, conflicting evidence, complicated research, or consequential analysis. Give it the relevant facts and a clear stopping point.
- **Independent verification:** check important conclusions against reliable sources or qualified judgment, regardless of model choice.

Choose through `/model`, review `/status`, and keep searches narrowly scoped. Useful quality matters more than always selecting the smallest model; no choice guarantees accuracy or a fixed usage saving.

Run the [acceptance check](ACCEPTANCE.md) before relying on the starter. Integration-specific checks remain your responsibility: this release has not been tested against your accounts.
